---
title: "EAGLE-3: Scaling up Inference Acceleration of Large Language Models via Training-Time Test"
title_zh: EAGLE-3：通过训练时测试扩展大语言模型的推理加速
authors: "Yuhui Li, Fangyun Wei, Chao Zhang, Hongyang Zhang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=4exx1hUffq"
tags: ["query:llm"]
score: 9.0
evidence: LLM推理加速的投机采样方法
tldr: 针对投机采样方法EAGLE随着数据规模增大改进有限的问题，本文提出EAGLE-3，放弃特征预测转而直接预测令牌。这使得模型能更有效地利用大规模训练数据，进一步提升推理加速效果。实验表明，EAGLE-3在多种LLM上取得了比前代更优的加速比，且训练成本可控。该工作推动了投机解码在LLM推理加速中的实际应用。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-4exx1huffq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1349, \"height\": 373, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4exx1huffq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1403, \"height\": 289, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4exx1huffq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 724, \"height\": 1011, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4exx1huffq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1328, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4exx1huffq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1446, \"height\": 696, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4exx1huffq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 706, \"height\": 1064, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4exx1huffq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 875, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4exx1huffq/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1419, \"height\": 425, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-4exx1huffq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1452, \"height\": 1026, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4exx1huffq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 937, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4exx1huffq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1342, \"height\": 179, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4exx1huffq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 906, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4exx1huffq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1210, \"height\": 180, \"label\": \"Table\"}]"
motivation: 现有EAGLE方法在数据规模增大时性能提升受限，需要更有效的预测范式。
method: 将特征预测改为直接令牌预测，利用训练时测试动态调整草稿模型。
result: 在多个LLM上相比EAGLE-2实现更高加速比，训练效率也得到提升。
conclusion: 直接令牌预测的投机采样是一种更具扩展性的LLM加速方案。
---

## Abstract
The sequential nature of modern LLMs makes them expensive and slow, and speculative sam- pling has proven to be an effective solution to this problem. Methods like EAGLE perform autoregression at the feature level, reusing top- layer features from the target model to achieve better results than vanilla speculative sampling. A growing trend in the LLM community is scaling up training data to improve model intelligence without increasing inference costs. However, we observe that scaling up data provides limited improvements for EAGLE. We identify that this limitation arises from EAGLE’s feature prediction constraints. In this paper, we introduce EAGLE-3, which abandons feature prediction in favor of direct token prediction and replaces reliance on top-layer features with multi-layer feature fusion via a technique named training-time test. These improvements significantly enhance performance and enable the draft model to fully benefit from scaling up training data. Our experiments include both chat models and reasoning models, evaluated on five tasks. The results show that EAGLE-3 achieves a speedup ratio up to 6.5x, with about 1.4x improvement over EAGLE-2. In the SGLang framework, EAGLE- 3 achieves a 1.38x throughput improvement at a batch size of 64.

---

## 论文详细总结（自动生成）

# 论文《EAGLE-3: Scaling up Inference Acceleration of Large Language Models via Training-Time Test》详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题背景**：大语言模型（LLM）自回归生成效率低、成本高。投机采样（Speculative Sampling）通过草稿模型快速生成候选令牌并由目标模型并行验证，是一种有效的加速方法。其中 EAGLE 系列（EAGLE、EAGLE-2）在特征层面进行自回归，复用目标模型顶层特征，加速效果优于标准投机采样。
- **核心问题**：随着训练数据规模增大，EAGLE 的加速提升有限。作者发现这一瓶颈源于 EAGLE 中的**特征预测约束**——草稿模型被迫预测与目标模型顶层特征一致的表示，限制了模型表达能力和数据利用效率。
- **整体意义**：本文提出 EAGLE-3，放弃特征预测，改为**直接令牌预测**，并通过**训练时测试（Training-Time Test）** 技术使草稿模型在训练时模拟多步自回归，从而实现随训练数据规模增加而加速性能持续提升的扩展规律，为 LLM 推理加速提供了更具可扩展性的方案。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
- 移除特征预测损失（\(l_{\text{fea}}\)），直接预测下一个令牌（token）。
- 在训练过程中模拟推理时的自回归过程（即“训练时测试”），使草稿模型适应自身预测的输入，缓解分布偏移。
- 将输入从仅用顶层特征扩展为**融合低、中、高多层特征**，以获取更丰富的语义信息。

### 关键技术细节

1. **训练阶段（Training-Time Test）**：
   - 传统 EAGLE 训练时输入真实特征（无帽），预测带帽特征；测试时输入自身预测特征，导致训练-测试不一致。
   - EAGLE-3 在训练时也使用草稿模型自身预测的输出作为下一时间步输入，并调整注意力掩码以匹配树状依赖关系（见图6）。这相当于在训练中引入了多步自回归模拟。
   - 损失函数仅保留令牌预测损失（\(l_{\text{token}}\)），去除特征预测损失。

2. **推理阶段**：
   - 复用目标模型前向传播中多个中间层（低、中、高层）的特征，拼接后经全连接层融合为综合特征 \(g\)。
   - 将采样得到的令牌嵌入与前一草稿模型输出 \(a\) 拼接，输入单层 Transformer 解码器，再经 LM Head 获得下一个令牌。
   - 采用 EAGLE-2 提出的动态草稿树结构，根据上下文自适应调整草稿树形状。

3. **关键改动对比**：
   - EAGLE：输入为顶层特征序列，输出预测下一特征，损失包含特征预测 + 令牌预测。
   - EAGLE-3：输入为融合特征或自身预测，输出直接预测令牌，仅用令牌损失；训练时模拟多步自回归。

## 3. 实验设计

### 数据集与场景
- **多轮对话**：MT-bench
- **代码生成**：HumanEval
- **数学推理**：GSM8K
- **指令跟随**：Alpaca
- **摘要**：CNN/Daily Mail

### 目标模型
- Vicuna 13B
- LLaMA-Instruct 3.1 8B
- LLaMA-Instruct 3.3 70B
- DeepSeek-R1-Distill-LLaMA 8B

### 对比方法
- 标准投机采样（Standard Speculative Sampling, SpS）
- PLD、Lookahead、Medusa、Hydra、HASS、EAGLE、EAGLE-2
- 基线为 vanilla 自回归解码（速度比=1.00×）

### 评估指标
- **加速比（Speedup Ratio）**：相对于自回归解码的实际速度提升。
- **平均接受长度（τ）**：每个草稿-验证周期平均接受的令牌数。
- **接受率（n-α）**：第 n 个草稿令牌被接受的比率，反映草稿模型对目标模型的近似程度。

### 实现细节
- 使用 AdamW 优化器，学习率 5e-5，梯度裁剪 0.5。
- 训练数据：ShareGPT（~68K 条）、UltraChat-200K（~464K 条），对 DeepSeek-R1 额外使用 OpenThoughts-114k-math。
- 草稿模型为单层 Transformer，与 EAGLE 规模相当。
- 对 70B 模型使用 16×A100 GPU 训练约两周；其余模型使用 RTX 3090 测试；SGLang 实验在单卡 H100 上进行。

## 4. 资源与算力

- **训练资源**：
  - 70B 模型草稿模型：**16 张 A100 GPU**，训练约**两周**。
  - 8B/13B 模型草稿模型：文中未明确说明具体 GPU 数量和时长，但提及使用 16×A100 训练 70B 模型，且所有草稿模型训练数据量和计算量合理。
- **测试资源**：
  - 70B 模型：A100 GPU。
  - 其他模型：RTX 3090。
  - SGLang 实验：单张 H100 GPU。
- **注意**：小规模模型训练资源未完全披露，但论文提供了可复现的代码和参数设置，具备可复现性基础。

## 5. 实验数量与充分性

### 实验组数
- **主实验**（表1）：在 4 个目标模型、5 个任务、2 种温度（0 和 1）下对比了所有方法，共约 40+ 个速度比和接受长度数据。
- **消融实验**（表2）：在 MT-bench 和 GSM8K 上，针对“移除特征约束”和“融合多层特征”两项改进分别进行消融。
- **扩展规律实验**（图2、图8）：在不同数据规模（1×、2×、4×、8× ShareGPT）下对比 EAGLE-2、HASS、EAGLE-3 的速度比和接受长度。
- **批量吞吐测试**（表3、表4、表5）：在 SGLang 和 vLLM 框架下，测量不同 batch size（2~64）的吞吐提升。
- **接受率对比**（图7）：在 LLaMA-8B 上对比 EAGLE 和 EAGLE-3 的 n-α 曲线。

### 充分性与公平性
- 实验覆盖了聊天模型和推理模型，任务类型多样（对话、代码、数学、指令、摘要）。
- 所有方法使用相同目标模型权重、相同测试环境，保证了公平性。
- 消融实验清晰验证了每个改进点的贡献。
- 在 SGLang/vLLM 生产级框架中的测试增强了结果实用性。
- 论文未提供多次运行的标准差/误差棒，但该领域惯例如此，可接受。

## 6. 主要结论与发现

1. **EAGLE-3 显著优于前代方法**：在温度=0 时，平均加速比达 5.51×（Vicuna 13B），相比 EAGLE-2 提升约 1.4×；在温度=1 时也保持明显优势。
2. **新的扩展规律**：EAGLE-3 的加速比和接受长度随着训练数据量的增加而持续提升（几乎线性），而 EAGLE-2 和 HASS 提升微弱（图2、图8）。
3. **去除特征约束是关键**：直接令牌预测使草稿模型能充分利用大规模数据，而特征约束限制了表达。
4. **多层特征融合优于仅顶层特征**：提供更丰富的语义信息，进一步提升效果。
5. **在大批量场景下仍有效**：在 SGLang 中 batch size=64 时仍能提升 38% 吞吐，优于 EAGLE（接近 1.0× 甚至下降）。
6. 最高加速比达 6.5×，平均接受长度最高达 7.5。

## 7. 优点

- **方法创新性**：明确提出并解决了 EAGLE 系列因特征预测约束导致的数据扩展性问题，并提出“训练时测试”这一简洁有效的解决方案。
- **可扩展性强**：首次在投机采样中展示随训练数据增长而加速性能提升的规律，具有理论与实践价值。
- **实验全面**：覆盖多种模型类型、任务、生产框架（SGLang、vLLM），验证了方法在不同场景下的鲁棒性和实用性。
- **消融清晰**：通过分步消融（去特征约束 + 融合特征）量化了每项改进的贡献。
- **开源友好**：代码已公开，便于复现和社区应用。

## 8. 不足与局限

1. **实验统计不确定性**：未报告多次运行的误差棒或置信区间，鲁棒性验证稍欠。
2. **资源细节不完整**：除 70B 模型外，其他模型（8B/13B）的训练 GPU 数量和时长未明确说明，影响完全复现的精确性。
3. **模型规模限制**：受 GPU 限制，未测试 70B 以上模型（如 100B+），扩展性在更大模型上未知。
4. **任务单一性风险**：虽覆盖 5 个任务，但未涉及长文本生成、知识密集型任务等，可能低估或高估特定场景下的加速效果。
5. **训练额外成本**：EAGLE-3 需要较多训练数据（8× ShareGPT）才能充分发挥优势，对计算资源有限的团队构成门槛。
6. **对特殊模型（如推理模型）的适配**：DeepSeek-R1 的加速提升相对较小，可能因推理过程与草稿模型分布的差异，论文未深入分析原因。
7. **公平性讨论不足**：未讨论加速方法可能对不同模型族或架构的适用性，也未涉及公平性、偏差等社会影响。

（完）
