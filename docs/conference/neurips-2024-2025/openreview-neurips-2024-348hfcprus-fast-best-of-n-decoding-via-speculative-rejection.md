---
title: Fast Best-of-N Decoding via Speculative Rejection
title_zh: 通过投机拒绝实现快速最佳N解码
authors: "Hanshi Sun, Momin Haider, Ruiqi Zhang, Huitao Yang, Jiahao Qiu, Ming Yin, Mengdi Wang, Peter Bartlett, Andrea Zanette"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=348hfcprUs"
tags: ["query:llm"]
score: 7.0
evidence: LLM对齐的投机拒绝方法
tldr: 该论文针对大语言模型的对齐问题，提出了一种推理时的对齐方法Fast Best-of-N Decoding via Speculative Rejection。它利用投机拒绝机制来加速传统的Best-of-N解码，避免了复杂的后训练过程。实验表明，该方法在保持对齐质量的同时显著降低了推理开销。这项工作为高效的大模型对齐提供了新的思路，属于投机解码在LLM推理加速中的应用变体。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-348hfcprus/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1451, \"height\": 547, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-348hfcprus/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 580, \"height\": 463, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-348hfcprus/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1445, \"height\": 1188, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-348hfcprus/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1435, \"height\": 612, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-348hfcprus/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1437, \"height\": 433, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-348hfcprus/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1459, \"height\": 430, \"label\": \"Table\"}]"
motivation: 后训练对齐方法复杂度高，推理时对齐方法Best-of-N需要大量计算，本文旨在通过投机拒绝加速Best-of-N。
method: 设计投机拒绝机制，在候选样本生成过程中提前拒绝不符合偏好的样本，减少不必要的多次模型调用。
result: 在多个基准上，该方法与后训练对齐效果相当，但推理速度显著提升。
conclusion: 投机拒绝是一种有效的推理时对齐加速手段，可替代复杂的后训练过程。
---

## Abstract
The safe and effective deployment of Large Language Models (LLMs) involves a critical step called alignment, which ensures that the model's responses are in accordance with human preferences. Prevalent alignment techniques, such as DPO, PPO and their variants, align LLMs by changing the pre-trained model weights during a phase called post-training. While predominant, these post-training methods add substantial complexity before LLMs can be deployed. Inference-time alignment methods avoid the complex post-training step and instead bias the generation towards responses that are aligned with human preferences. The best-known inference-time alignment method, called Best-of-N, is as effective as the state-of-the-art post-training procedures. Unfortunately, Best-of-N requires vastly more resources at inference time than standard decoding strategies, which makes it computationally not viable. In this work, we introduce Speculative Rejection, a computationally-viable inference-time alignment algorithm. It generates high-scoring responses according to a given reward model, like Best-of-N does, while being between 16 to 32 times more computationally efficient.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题背景**：大语言模型（LLM）在部署前需要进行“对齐”（alignment），以确保生成内容符合人类偏好。现有的主流对齐方法（如DPO、PPO及变体）属于**后训练对齐**，需要修改模型权重，增加了部署前的大量复杂步骤。
- **推理时对齐**：另一类方法称为推理时对齐，无需后训练，直接通过改变解码策略来提升生成质量。其中最具代表性的方法是 **Best-of-N（BoN）**：对同一提示生成N个候选响应，再用奖励模型选出得分最高的一个。BoN在效果上可与最先进的后训练方法媲美。
- **核心问题**：BoN的致命缺点是计算成本极高——生成N个候选响应需要大量GPU资源（实用中N在4–128，但为达到与后训练方法相当的效果常需N=1000–60000），这在单GPU上无法实现，通常需要数十甚至上百块GPU，使其在实际部署中几乎不可行。
- **论文目标**：提出一种计算上可行的推理时对齐算法 **Speculative Rejection**，在保持与BoN相当的对齐质量的同时，将计算效率提升16–32倍（即只需单GPU即可模拟大N的BoN效果）。

## 2. 论文提出的方法论

### 2.1 核心思想
- **关键观察**：奖励模型可以在生成**早期阶段**就区分高质量与低质量的候选响应。具体而言，**部分生成的响应的得分与最终完成后的得分存在强正相关**（见图2和附录B的皮尔逊/肯德尔相关系数分析）。
- 基于此，可以在生成过程中提前终止那些“不太可能获得高最终得分”的候选响应，从而节省计算资源，而不损失最终输出质量。

### 2.2 算法流程（Algorithm 1）

1. **初始化**：根据GPU内存容量和提示长度，确定**初始批次大小** \( b_{\text{init}} \)（可远大于传统BoN能一次性处理的批次大小，例如5000）。
2. **循环生成与拒绝**（直到批次大小变为0）：
   - **早期生成阶段**：对当前批次 \( b \) 个响应，每个生成最多 \( \tau \) 个token（直至遇到EOS或即将OOM）。实际生成token数为 \( \tau_k = \min(\tau, \ell_k) \)，其中 \( \ell_k \) 为响应总长度。
   - **投机拒绝阶段**：
     - 使用奖励模型 \( s \) 评估每个部分响应（提示+已生成token）的得分，得到部分奖励集合 \( R_{\text{partial}} = \{ s(Y^{\le \tau_k}_k) \} \)。
     - 计算**截止阈值**：\( r_{\text{cut}} = q_\alpha(R_{\text{partial}}) \)，即部分奖励的 \( \alpha \) 分位数，其中 \( \alpha \in (0,1) \) 为**拒绝率**（超参数）。
     - 保留那些部分奖励 \( \ge r_{\text{cut}} \) 的响应，即**接受集合** \( I_{\text{accepted}} \)；其余被终止。
   - **更新批次**：\( b \leftarrow |I_{\text{accepted}}| \)，继续下一轮生成与拒绝。
3. **输出**：从所有完整生成的响应（包括在拒绝过程中提前完成的）中，选出最终奖励最高的响应 \( Y_{\text{SR}} \)。

### 2.3 关键公式
- 部分奖励：\( R_{\text{partial}} = \{ s(Y^{\le \tau_k}_k) : k = 1,\dots,b \} \)
- 截止阈值：\( r_{\text{cut}} = q_\alpha(R_{\text{partial}}) \)
- 接受索引集：\( I_{\text{accepted}} = \{ k : s(Y^{\le \tau_k}_k) \ge r_{\text{cut}} \} \)
- 最终输出：\( Y_{\text{SR}} = \arg\max_{k \in I} s(Y_k) \)

- **与BoN的关系**：当 \( \alpha = 0 \) 且初始批次大小等于N时，Speculative Rejection退化为BoN，因此它是BoN的**推广**。

## 3. 实验设计

- **数据集**：使用 **AlpacaFarm-Eval** 数据集（从AlpacaFarm中选取）。
- **场景**：三种生成模型与多种奖励模型组合：
  - 生成模型：Mistral-7B-v0.3、Llama-3-8B、Llama-3-8B-Instruct。
  - 奖励模型：RM-Mistral-7B、FsfairX-LLaMA3-RM、ArmoRM-Llama3-8B。
- **基准方法**：**Best-of-N（BoN）**，N取 120, 240, 480, 960, 1920, 3840。Bo-120可在单GPU上运行，更大N需要多GPU（每翻倍增加一倍GPU）。
- **对比指标**：
  - **相对GPU计算量**：定义为 \( (\text{BoN耗时} \times \text{GPU数}) / (\text{Bo-120耗时}) \)。
  - **改进得分（Improvement Score）**：归一化奖励得分（以Bo-120为基线100）。
  - **胜率（Win-Rate）与长度控制胜率（LC-Win-Rate）**：使用GPT-4-Turbo作为评判者，比较Speculative Rejection与各BoN的生成质量。
  - **困惑度（Perplexity）**：当奖励函数为响应平均概率（负对数似然）时的性能。

## 4. 资源与算力

- **硬件**：DGX节点，配备 **H100 GPU**（80GB显存）。
- **实现细节**：基于PyTorch，采用高效推理引擎，自动确定生成token数上限以避免OOM，并预分配KV缓存。
- **资源对比**：
  - Bo-120：单GPU。
  - Bo-240：2 GPU；Bo-480：4 GPU；... Bo-3840：32 GPU。
  - Speculative Rejection：始终仅用 **单GPU**。
- **未明确说明**：总实验耗时、具体训练时长等，但提供了代码仓库（GitHub）可复现。

## 5. 实验数量与充分性

- **实验组数**：
  - 效率评估（图3）：3种生成模型 × 3种奖励模型 = **9组**，每组展示6种BoN（不同N）和3–4种Speculative Rejection（不同α）的结果。
  - 胜率评估（表1）：3种生成模型 × 1种奖励模型（ArmoRM-Llama-3-8B），对比BoN六档与Speculative Rejection（α=0.5）的WR和LC-WR。
  - 概率最大化实验（表2）：3种生成模型 × 1种奖励（模型自身概率），对比BoN六档与Speculative Rejection（α=0.5）。
  - 相关性分析（附录B）：随机100个prompt，展示Pearson与Kendall相关系数分布。
- **充分性评价**：
  - 覆盖了多种生成模型（基座与指令微调）、多种奖励模型，场景较全面。
  - 采用客观指标（奖励得分、速度、胜率）和主观指标（GPT-4评判），实验设计基本公平。
  - 但未报告误差棒（计算成本高），且每个条件仅平均值基于100个prompt，统计显著性未明确展示，存在一定偏差风险。

## 6. 论文的主要结论与发现

- Speculative Rejection 在**单GPU**上即可达到与**BoN需要16–32 GPU**相当的奖励得分，计算效率提升16–32倍。
- 在胜率评估（GPT-4-Turbo）中，Speculative Rejection (α=0.5) 的平均WR达66.17%，LC-WR达70.01%，显著优于Bo-120（均为50%）且接近Bo-3840（62.89%/63.04%）。
- 在概率最大化任务中，Speculative Rejection 同样优于BoN，生成更低困惑度的响应，且速度更快（例如Mistral-7B上速度提升76.9倍）。
- 不同生成模型上性能提升幅度不同：对基座模型（Mistral-7B, Llama-3-8B）效果更明显；对已对齐的指令模型（Llama-3-8B-Instruct）提升较小，因其生成较短，拒绝轮次少。
- 拒绝率α是调控效率与质量的超参数：α越小（拒绝更保守），最终得分越高但延迟略增；α越大则加速更激进。

## 7. 优点

- **方法创新性**：将投机解码（Speculative Decoding）中的拒绝采样思想扩展到推理时对齐，提出动态批次大小与部分奖励驱动的早停策略，与传统的Pruning in Games有相似但独特的结构。
- **简单实用**：算法易于理解和实现，无需训练额外的模型或改变模型权重，可直接应用于任何自回归生成模型和奖励模型。
- **计算效率显著**：单GPU实现大N的BoN效果，大大降低了部署门槛。
- **通用性**：不仅适用于奖励模型对齐，还可用于最大化其他任意目标（如生成概率），框架具有良好泛化性。
- **公平对比**：与BoN在同等GPU资源（按计算量折算）下比较，且考虑了多GPU并行场景，避免不公平优势。

## 8. 不足与局限

- **依赖于部分-最终奖励的相关性**：该相关性会因prompt而异，论文未提供自适应调整拒绝率的方法，固定α可能在不同prompt上非最优。
- **奖励模型需要在线评估部分生成**：奖励模型需对每个部分响应进行评分，增加额外计算开销（虽远少于生成完整响应），且奖励模型通常针对完整响应训练，用于部分响应可能不够准确。论文建议未来可训练价值函数（value function）以提高精度。
- **实验局限性**：
  - 未报告误差线或置信区间，统计显著性欠缺。
  - 仅使用AlpacaFarm-Eval数据集，未在更广泛或对抗性prompt上验证。
  - 生成模型限于7B–8B规模，未评估更大模型（如70B）上的效率。
- **与其他推理加速方法的正交性**：论文指出Speculative Rejection可与投机解码等方法结合，但未做实验验证。
- **安全风险**：该方法虽然提升了对齐效率，但若奖励模型本身有偏差或易被攻击，可能导致早期错误拒绝或保留有害内容，论文未深入探讨安全鲁棒性。

（完）
