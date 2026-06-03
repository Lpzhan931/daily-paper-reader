---
title: Speculative Decoding with CTC-based Draft Model for LLM Inference Acceleration
title_zh: 基于CTC草稿模型的投机解码用于大语言模型推理加速
authors: "Zhuofan Wen, Shangtong Gui, Yang Feng"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=pGeAcYhnN5"
tags: ["query:llm"]
score: 9.0
evidence: 基于CTC的草稿模型用于投机解码加速LLM推理
tldr: 本文针对投机解码中草稿模型常忽略token间相关性的问题，提出基于CTC的草稿模型。该模型以非自回归方式生成草稿，但通过CTC对齐建模token之间的依赖，提高了草稿的接受率。实验表明，该方法在多个LLM上实现更高的推理加速，同时保持输出质量。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-pgeacyhnn5/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1317, \"height\": 1434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pgeacyhnn5/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1437, \"height\": 742, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pgeacyhnn5/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1448, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pgeacyhnn5/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1290, \"height\": 587, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pgeacyhnn5/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1289, \"height\": 595, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-pgeacyhnn5/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1057, \"height\": 572, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pgeacyhnn5/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1054, \"height\": 242, \"label\": \"Table\"}]"
motivation: 现有草稿模型非自回归生成忽略token相关性，导致接受率低。
method: 提出CTC-based draft model，利用连接时序分类建模草稿token间的相关性。
result: 显著提高草稿接受率，加速LLM推理。
conclusion: 改进草稿模型可有效提升投机解码性能。
---

## Abstract
Inference acceleration of large language models (LLMs) has been put forward in many application scenarios and speculative decoding has shown its advantage in addressing inference acceleration. Speculative decoding usually introduces a draft model to assist the base LLM where the draft model produces drafts and the base LLM verifies the draft for acceptance or rejection. In this framework, the final inference speed is decided by the decoding speed of the draft model and the acceptance rate of the draft provided by the draft model. Currently the widely used draft models usually generate draft tokens for the next several positions in a non-autoregressive way without considering the correlations between draft tokens. Therefore, it has a high decoding speed but an unsatisfactory acceptance rate. In this paper, we focus on how to improve the performance of the draft model and aim to accelerate inference via a high acceptance rate. To this end, we propose a CTC-based draft model which strengthens the correlations between draft tokens during the draft phase, thereby generating higher-quality draft candidate sequences. Experiment results show that compared to strong baselines, the proposed method can achieve a higher acceptance rate and hence a faster inference speed.

---

## 论文详细总结（自动生成）

# 基于CTC草稿模型的投机解码用于大语言模型推理加速——论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

大语言模型（LLMs）在文本生成任务中表现出色，但其自回归逐token生成方式导致严重的推理延迟问题。投机解码（Speculative Decoding）作为一种有效的加速策略，引入一个轻量级草稿模型（draft model）快速生成候选tokens，然后由基础LLM并行验证并决定接受或拒绝，从而降低整体推理步数。

现有草稿模型多采用非自回归（NAR）方式并行生成多个未来tokens，虽然解码速度快，但忽略了各候选token之间的依赖关系，导致草稿质量不高、接受率（acceptance rate）偏低，最终限制了加速效果。

本文的核心动机是：**在不显著增加草稿模型解码时间的前提下，提升草稿序列的合理性，从而提高接受率，进而实现更快的推理加速。**

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
基于连接时序分类（Connectionist Temporal Classification, CTC）算法，设计一种新的草稿模型——**CTC-drafter**。该模型以非自回归方式并行生成草稿，但通过引入空白符（blank token）和重复token，并在训练时使用序列级CTC损失函数，迫使模型在概率分配中隐含地建模token间的依赖关系，从而生成更合理、更易被基础LLM接受的候选序列。

### 关键技术细节
- **模型结构**：在基础LLM的最后一层隐藏状态上，插入一个**注意力草稿模块**（Attention Draft Module），该模块包含一层Transformer层，用于并行预测多个位置的token概率分布。之后通过LM Head得到每个位置的概率。
- **CTC变换模块**：在验证阶段，对原始候选序列进行CTC变换——移除连续重复token和空白符，并相应地修改注意力掩码，使基础LLM能够正确验证。
- **训练策略**：
  - 固定基础LLM参数，仅训练草稿模块的Transformer层。
  - 训练目标为**序列级CTC损失**，而不是传统的交叉熵损失。CTC损失通过对齐所有可能的路径（含空白和重复）来计算标签概率，迫使模型学习更好的上下文连接。
  - 采用知识蒸馏：用基础LLM在原始数据上贪婪解码得到蒸馏标签 \( Y_{\text{distill}} \)，作为训练目标，使草稿模型更好地模仿基础LLM的行为。
- **推理过程**：
  - 当前步输入解码历史，基础LLM生成隐藏状态和第一个token（如“my”）。
  - 草稿模块基于隐藏状态输出后续多个位置的概率分布，每位置选取top-k tokens。
  - 通过树状组合生成候选序列，经CTC变换后并行送交基础LLM验证。
  - 选择最长的可接受序列作为当前步输出，更新解码历史。

## 3. 实验设计

### 数据集与场景
- **MT-bench**：包含80个高质量多轮对话问题，覆盖写作、角色扮演、编程等8大类，用于评估加速性能。
- **GSM8K**：包含8500个小学数学应用题，用于评估在数学推理场景下的加速效果。

### Benchmark（评估指标）
- **平均每步接受token数（β）**：β = 总生成token数 / 基础LLM解码步数。
- **加速比（γ）**：γ = \( \overline{T}_{\text{vanilla}} / \overline{T}_{\text{spec}} \)，其中T为总推理时间，并对token数进行归一化。

### 对比方法
- **Vanilla**：无投机解码的标准自回归生成。
- **Medusa**（[3]）：在基础LLM上添加多个线性头（Medusa Heads）并行预测后续token，用树状结构组合候选序列。
- **Hydra**（[2]）：在Medusa基础上引入顺序依赖的草稿头（Hydra Heads），提高草稿质量。
- 本文方法：**CTC-drafter**。

### 基础LLM
- Vicuna-7B, Vicuna-13B, Vicuna-33B（基于LLaMA微调）。
- 补充实验：LLaMA-2-Chat 7B, 13B。

## 4. 资源与算力

论文明确说明：
- 所有训练任务在**4块24GB NVIDIA GeForce RTX 3090**上执行。
- 训练时长约**2天**。
- 使用FP16精度量化以节省显存和加速训练。
- 训练数据为ShareGPT数据集（Vicuna训练数据子集），最大序列长度设为2048。

## 5. 实验数量与充分性

### 实验组别
- **主实验**：在MT-bench和GSM8K两个数据集上，针对Vicuna-7B/13B/33B三种模型，对比Vanilla、Medusa、Hydra（仅MT-bench报告Hydra结果）、CTC-drafter。
- **消融实验**：
  - 模型结构消融：分别替换草稿模块（线性层+交叉熵 vs Transformer层+CTC损失）和验证模块（Medusa验证 vs CTC验证），分析各组件贡献。
  - 问题类别分析：在MT-bench的8个类别上比较CTC-drafter与Medusa的β值。
  - 时间消耗分析：测量CTC-drafter与Medusa各阶段时间占比。
- **跨模型泛化实验**：在LLaMA-2-Chat 7B/13B上重复主实验。

### 充分性与公平性
- 实验覆盖多个模型规模（7B~33B）和两个不同类型的任务（对话、数学），具有一定广度。
- 与Medusa、Hydra等强基线进行对比，且Medusa在相同设置下重新训练，确保公平。
- 消融实验系统性地分析了结构和损失函数的影响，支持方法有效性。
- 时间消耗分析表明，虽然CTC-drafter的草稿模块和CTC变换增加了额外时间（约20%），但整体加速效果仍优于其他方法，说明额外开销可被接受。
- 未报告多次重复实验的误差棒，统计显著性论证稍显不足。

## 6. 论文的主要结论与发现

- CTC-drafter在所有测试场景下均取得**最高的平均每步接受token数（β）和加速比（γ）**。例如在Vicuna-7B上，MT-bench中β=3.56，γ=2.78×，优于Medusa（β=2.58，γ=2.13×）和Hydra（β=3.04，γ=2.36×）。
- 使用CTC损失和Transformer层替代线性层能显著提升草稿质量（β从2.58提升至3.02），而CTC变换进一步将β提升至3.56。
- 在不同类别问题上，CTC-drafter均优于Medusa，尤其在编程类别上优势明显。
- 跨模型迁移（从Vicuna到LLaMA-2-Chat）时性能保持稳定，泛化性良好。
- 加速效果随基础LLM规模增大略有下降，原因在于草稿模块容量有限，难以追赶更大模型的能力。

## 7. 优点

- **创新性**：首次将CTC算法引入投机解码领域，利用CTC的对齐特性隐式建模token间依赖，突破了传统NAR方法忽略相关性的局限。
- **方法有效性**：通过序列级损失函数训练，使草稿模型更关注整体序列合理性，而非独立预测每个位置，从而显著提高接受率。
- **自适应性**：CTC变换模块使候选序列长度和内容自适应，无需固定草稿长度，便于迁移到不同基础模型。
- **实验设计全面**：涵盖多模型、多数据集、消融、时间分析及跨模型泛化，论证充分。

## 8. 不足与局限

- **额外时间开销**：CTC-drafter的草稿模块（Transformer层）和CTC变换增加了约20%的额外推理时间，虽然整体加速仍占优，但在某些资源受限场景下可能削弱优势。
- **训练复杂性**：需要基于基础LLM的隐藏状态训练额外Transformer层，且依赖知识蒸馏获取标签，训练流程较Medusa更复杂。
- **容量限制**：随着基础LLM规模增大，草稿模块的能力差距扩大，导致加速性能下降。论文未探索更大或更复杂的草稿模块设计。
- **评估指标**：仅报告平均加速比和接受token数，未给出多次运行的统计置信区间，缺乏误差估计。
- **应用限制**：方法基于贪婪解码验证，未集成核采样（Nucleus Sampling）等更灵活的验证准则；数学推理任务中在Vicuna-7B上加速效果不如MT-bench，提示对任务类型敏感。
- **未来方向**：作者提及可探索CRF、DAG等方法，但未在本文中实现；减少额外时间开销的策略也未深入。

（完）
