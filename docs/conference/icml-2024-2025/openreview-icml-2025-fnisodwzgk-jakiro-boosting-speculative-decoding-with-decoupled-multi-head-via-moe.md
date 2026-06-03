---
title: "Jakiro: Boosting Speculative Decoding with Decoupled Multi-Head via MoE"
title_zh: Jakiro：通过解耦多头MoE提升投机解码性能
authors: "Haiduo Huang, Fuwei Yang, Zhenhua Liu, Yixing Xu, Jinze Li, Yang Liu, Xuanwu Yin, Dong Li, Pengju Ren, Emad Barsoum"
date: 2025-01-15
pdf: "https://openreview.net/pdf?id=fNIsoDWzGk"
tags: ["query:llm"]
score: 9.0
evidence: 使用MoE增强投机解码的候选多样性
tldr: 针对投机解码中同一位置候选标记来自同一表示导致多样性不足的问题，本文提出Jakiro，利用混合专家模型解耦候选相关性，使各专家独立生成多样化候选。结合混合验证策略，在多个LLM基准上提升了加速比，展示了MoE增强投机解码的有效性。
source: ICML-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-fnisodwzgk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 727, \"height\": 781, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fnisodwzgk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1601, \"height\": 638, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fnisodwzgk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 625, \"height\": 715, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fnisodwzgk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 653, \"height\": 346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fnisodwzgk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 678, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fnisodwzgk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1597, \"height\": 637, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fnisodwzgk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1585, \"height\": 678, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-fnisodwzgk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1725, \"height\": 1336, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fnisodwzgk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 864, \"height\": 467, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fnisodwzgk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 860, \"height\": 236, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fnisodwzgk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 860, \"height\": 227, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fnisodwzgk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1782, \"height\": 1277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fnisodwzgk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1779, \"height\": 1213, \"label\": \"Table\"}]"
motivation: 树状采样中同一位置候选多样性不足，受限于单一表示。
method: 采用混合专家模型，每个专家独立生成候选，解耦表示相关性。
result: 在多种LLM上获得比基线更高的加速比。
conclusion: Jakiro通过MoE增强候选多样性，有效提升了投机解码效率。
---

## Abstract
Speculative decoding (SD) accelerates large language model inference by using a smaller draft model to predict multiple tokens, which are then verified in parallel by the larger target model. However, the limited capacity of the draft model often necessitates tree-based sampling to improve prediction accuracy, where multiple candidates are generated at each step. We identify a key limitation in this approach: the candidates at the same step are derived from the same representation, limiting diversity and reducing overall effectiveness. To address this, we propose Jakiro, leveraging Mixture of Experts (MoE), where independent experts generate diverse predictions, effectively decoupling correlations among candidates. Furthermore, we introduce a hybrid inference strategy, combining autoregressive decoding for initial tokens with parallel decoding for subsequent stages, and enhance the latter with contrastive mechanism in features to improve accuracy. Our method significantly boosts prediction accuracy and achieves higher inference speedups. Extensive experiments across diverse models validate the effectiveness and robustness of our approach, establishing a new SOTA in speculative decoding.

---

## 论文详细总结（自动生成）

# 论文详细总结：Jakiro: Boosting Speculative Decoding with Decoupled Multi-Head via MoE

## 1. 核心问题与整体含义（研究动机与背景）
- **问题**：大型语言模型（LLM）逐token解码导致推理延迟高，投机解码（Speculative Decoding, SD）利用小模型草稿预测多个token再由大模型并行验证，可无损加速。但草稿模型能力有限，常需树状采样生成多个候选以提高预测精度。
- **关键局限性**：现有方法（如Medusa、Eagle）中，同一层的候选token来自相同的特征表示，导致候选之间相关性过强，多样性不足，限制了预测准确性和加速效果。
- **整体含义**：本文旨在通过解耦同一层内候选token的表示相关性，提升草稿模型的预测多样性和准确率，从而进一步提高投机解码的推理加速比。

## 2. 方法论：核心思想、关键技术细节、公式/算法流程
### 2.1 核心思想
- 利用混合专家模型（Mixture of Experts, MoE）替代传统MLP层，为每个token分配多个专家，不同专家独立生成候选，实现同一层内候选的解耦。
- 引入混合推理策略：前几步使用自回归解码（保持与Eagle类似），最后两步改用并行解码，并通过对比机制（Contrastive Mechanism）进一步提升并行阶段的预测质量。

### 2.2 关键技术细节
- **动态解耦与MoE树构建**：
  - 在Eagle风格的草稿模型基础上，将LLM的MLP层替换为MoE层，包含N个候选专家，每次激活K个（默认K=2）。
  - 路由机制：根据当前隐藏状态与专家质心的相似度，选择top-K专家，每个专家独立计算，输出两个logits分布（左/右）。
  - 树结构构建：按照专家得分排序，得分高的专家对应左侧子树，得分低的对应右侧子树，形成MoE树（可兼容Eagle1静态树或Eagle2动态树）。
- **混合推理策略**：
  - 前γ-1步使用自回归解码（基于MoE特征）。
  - 最后一步（γ-1）使用并行解码，将两个专家的特征进行对比得到对比特征，再通过LM Head输出并行预测的logits。
- **对比机制**：在并行解码阶段，对两个激活专家的输出隐藏状态做线性组合：`f_const = β * f_top1 - α * f_top2`，其中β、α是可学习参数，用于增强预测区分度。

### 2.3 公式与算法流程（文字描述）
- 输入token经过嵌入层，与前一时刻隐藏状态拼接，经降维层（Reduction FC）后进入LLM注意力层。
- 注意力输出u_i通过路由计算得分`s_{j,i}`，选取top-K专家。
- 每个专家输出特征与u_i残差相加，得到`f_i`。
- 两个得分最高的专家特征分别送入共享LM Head，得到两个logits分布（`logits_left, logits_right`），分别对应树左右分支。
- 训练损失：回归损失（Smooth L1预测下一特征） + 分类损失（CrossEntropy预测下一token）。并行解码对应的对比特征也参与回归和分类损失，权重分别为0.1和0.05。

## 3. 实验设计
### 3.1 数据集与场景
- **多任务评估**：MT-bench（多轮对话）、HumanEval（代码生成）、GSM8K（数学推理）、Alpaca（指令跟随）、CNN/Daily Mail（摘要）、Natural Questions（问答）。
- **模型覆盖**：Vicuna 7B/13B/33B、LLaMA2-chat 7B/13B/70B、LLaMA3-instruct 8B/70B，涵盖主流大小。
- **采样模式**：贪心（温度=0）和非贪心（温度=1）两种设置。

### 3.2 对比方法
- **基线**：标准投机采样（SpS，草稿模型为Vicuna-68M）、Medusa、Hydra、Eagle1、Eagle2。
- **对比条件**：仅比较基于投机采样且无需微调主干模型的方法，确保输出分布无损。

### 3.3 评估指标
- **Walltime speedup ratio**：端到端延迟加速比（相对自回归解码）。
- **Average acceptance length τ**：每轮验证平均接受的token数。

## 4. 资源与算力
- **训练**：使用ShareGPT数据集（68,000轮对话），学习率9e-5，AdamW优化器（β1=0.9, β2=0.95），梯度裁剪阈值0.5。
- **可训练参数量**：Vicuna 7B→0.35B，8B→0.56B，13B→0.88B，33B→1.42B，70B→1.87B。
- **训练时间**：70B模型约2-3天，使用4×A100 40GB GPU。
- **测试设备**：AMD MI250-64G、NVIDIA A40-45G、NVIDIA A100-40G。不同模型大小使用单卡/双卡/四卡（7B/8B/13B单卡，33B双卡，70B四卡）。
- **其他**：batch size=1（与主流方法一致）。

## 5. 实验数量与充分性
### 5.1 实验数量
- **主实验（表1）**：6个任务 × 多种模型（Vicuna 7B/13B, LLaMA2 7B/13B/70B, LLaMA3 8B/70B），在MI250上分别报告贪心和非贪心结果，共约25+条对比行。
- **补充实验（附录表5、表6）**：在A40和A100上复现相同模型和任务，验证跨设备鲁棒性。
- **消融实验**：
  - N-K设置（表3）：候选专家数N=2/3/4/5，激活数K=2。
  - 平行解码与对比机制消融（表4）：分别移除平行解码、移除对比机制、同时移除。
  - 模型大小覆盖（表2）：额外报告了LLaMA3-8B/70B、Vicuna-33B、LLaMA2-70B在贪心模式下的结果。
- **图2、图6、图7**：展示加速比和接受长度在多个设备上的分布。

### 5.2 充分性评价
- **充分**：覆盖多种任务类型（对话、代码、数学、指令、摘要、问答），多种模型规模（7B~70B），多种硬件，以及两种采样策略（贪心/非贪心）。
- **客观公平**：所有对比方法基于开源代码复现，且仅比较无损加速方法；指标标准化（加速比、接受长度）；报告平均值和多次运行结果。
- **不足**：未在更大模型（如100B+）或真实部署场景（如多轮对话吞吐）上测试；训练数据仅用了ShareGPT单数据集，可能存在领域偏差。

## 6. 主要结论与发现
- Jakiro在所有任务和模型上均取得最高加速比，贪心模式下平均加速比2.88x（Vicuna 7B）至3.07x（Vicuna 13B），相比Eagle2提升约10%~15%。
- 非贪心模式下，Jakiro*（含MoE加权解耦树结构）进一步提升加速，如Vicuna 7B均值2.84x（Eagle2为2.27x）。
- 平均接受长度τ在非贪心模式下显著提高（如Vicuna 7Bτ=5.32 vs Eagle2 τ=4.17），说明MoE增强了候选多样性。
- 消融实验证实：MoE解耦、平行解码、对比机制各自带来增益，三者结合效果最佳。

## 7. 优点（方法/实验设计亮点）
- **创新点**：首次将MoE引入投机解码的草稿树构建，解耦同层候选相关性，结构新颖。
- **高效性**：仅增加少量可训练参数（约0.3B~1.9B），无需改动主干模型，训练成本可控。
- **混合推理策略**：结合自回归与平行解码，并通过对比机制提升并行阶段质量，设计巧妙。
- **实验全面**：覆盖多模型、多任务、多设备、两种采样模式，结果一致性高，验证了鲁棒性。
- **开源复现**：对比基线均基于作者复现的公开代码，确保公平。

## 8. 不足与局限
- **实验覆盖有限**：仅在7B~70B模型上测试，未验证更大规模（如100B+）或更小模型（如<1B）的适用性。
- **训练数据单一**：仅使用ShareGPT对话数据，未在多种领域数据上验证泛化性。
- **仅关注延迟**：未评估吞吐量（throughput）或显存开销，实际部署中可能受内存限制。
- **MoE开销**：N-K设置中，K>2时计算成本增加，论文中仅默认K=2，未深入探索K>2的潜力（仅提及未来工作）。
- **非贪心模式下对比机制未充分解释**：对比机制的参数β、α如何学习，及其对分布一致性（losslessness）的影响未详细分析。
- **论文被ICML 2025拒稿**：可能意味着方法或实验存在评审人认为的不足（如贡献度、与现有工作的区分度等），需谨慎看待。

（完）
