---
title: Cross-Attention Speculative Decoding
title_zh: 交叉注意力投机解码
authors: "Wei Zhong, Manasa Bharadwaj, Yixiao Wang, Nikhil Verma, Yipeng Ji, Chul Lee"
date: 2025-05-09
pdf: "https://openreview.net/pdf?id=2Ke2B4zps8"
tags: ["query:llm"]
score: 8.0
evidence: 基于交叉注意力的LLM投机解码
tldr: 针对现有投机解码方法依赖复杂自注意力架构的问题，本文提出Budget EAGLE（Beagle），首个基于交叉注意力的投机解码模型。它消除了池化和融合模块，简化了结构，提升了训练效率。实验表明，Beagle在性能上与领先的自注意力方法（如EAGLE-v2）持平，同时具有更好的泛化性。该工作为投机解码提供了更简洁高效的架构选择。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-2ke2b4zps8/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1599, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2ke2b4zps8/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1450, \"height\": 461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2ke2b4zps8/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1448, \"height\": 310, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2ke2b4zps8/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1017, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2ke2b4zps8/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1354, \"height\": 362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2ke2b4zps8/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1011, \"height\": 519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2ke2b4zps8/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1444, \"height\": 379, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2ke2b4zps8/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1447, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2ke2b4zps8/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1449, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2ke2b4zps8/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1406, \"height\": 533, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2ke2b4zps8/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1171, \"height\": 594, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2ke2b4zps8/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1445, \"height\": 379, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-2ke2b4zps8/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1447, \"height\": 653, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2ke2b4zps8/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1446, \"height\": 654, \"label\": \"Table\"}]"
motivation: 现有自注意力投机解码模型架构复杂、难以泛化，需要更简单且性能相当的替代方案。
method: 设计交叉注意力Transformer解码器作为草稿模型，无需池化或辅助组件，直接预测目标模型特征。
result: 在多个LLM基准上达到与EAGLE-v2相当的性能，训练效率更高，架构更简洁。
conclusion: 交叉注意力投机解码是一种简化且有效的LLM加速方法。
---

## Abstract
Speculative decoding (SD) is a widely adopted approach for accelerating inference in large language models (LLMs), particularly when the draft and target models are well aligned. However, state-of-the-art SD methods typically rely on tightly coupled, self-attention-based Transformer decoders, often augmented with auxiliary pooling or fusion layers. This coupling makes them increasingly complex and harder to generalize across different models.
We present Budget EAGLE (Beagle), the first, to our knowledge, cross-attention-based Transformer decoder SD model that achieves performance on par with leading self-attention SD models (EAGLE-v2) while eliminating the need for pooling or auxiliary components, simplifying the architecture, improving training efficiency, and maintaining stable memory usage during training-time simulation. To enable effective training of this novel architecture, we propose Two-Stage Block-Attention Training, a new method that achieves training stability and convergence efficiency in block-level attention scenarios.
Extensive experiments across multiple LLMs and datasets show that Beagle achieves competitive inference speedups and higher training efficiency than EAGLE-v2, offering a strong alternative for architectures in speculative decoding.

---

## 论文详细总结（自动生成）

# 论文总结：Cross-Attention Speculative Decoding

## 一、核心问题与整体含义（研究动机与背景）

- **问题**：主流投机解码（Speculative Decoding, SD）方法（如 EAGLE 系列）依赖自注意力（self-attention）架构，并通常需要辅助池化层（pooling）或融合层（fusion layers），导致模型结构复杂、耦合紧密、难以在不同模型间泛化，且训练与部署成本高。
- **目标**：设计一种更简约、高效且易于推广的 SD 草稿模型架构，在保持与 SOTA（如 EAGLE‑v2）相当性能的同时，简化结构、降低训练开销并维持稳定的内存使用。
- **意义**：为 LLM 推理加速提供一种更加轻量、可复用的替代方案，推动 SD 在实际工业部署中的易用性和可扩展性。

## 二、方法论：核心思想、关键技术细节与流程

### 2.1 核心思想
- 用**交叉注意力（Cross‑Attention）** 替换自注意力，构建一个精简的 Transformer 解码器作为草稿模型，无需任何池化或辅助组件。
- 利用交叉注意力天然支持异构特征（低层 token 嵌入 vs. 高层状态）的特性，避免像 EAGLE 那样需要显式复制和拼接高层状态。
- 提出**两阶段块注意力训练（Two‑Stage Block‑Attention Training）** 方法，兼顾早期训练效率与后期推理对齐精度。

### 2.2 关键技术与算法流程

#### 草稿模型架构（Beagle）
- 仅含单层交叉注意力和一个 MLP 层（无自注意力子层）。
- 公式（1）：  
  \( y_n = \text{CrossAttn}(h_{1:n-1}, e(t_n)) + e(t_n) \)  
  \( h_n = \text{MLP}(y_n) + y_n \)  
  其中 \( e(t_n) \) 为 token 嵌入，\( h_{1:n-1} \) 为目标模型真实状态或前一步自回归生成状态。
- 交叉注意力中，查询来自当前 token 嵌入，键/值来自历史高层状态；且屏蔽对角线（\( j \ge i \)）以保证因果性。
- 推理时，KV 缓存仅需“懒惰追加”（lazy‑appending），每次 SD 迭代末可重置为仅含真实状态，减少内存操作。

#### 两阶段训练
- **早期阶段（Early Stage）**：使用多步并行预测损失 \( L_{\text{early}} \)。  
  采用“逆块注意力”掩码（inverse block attention）：在连续窗口内，掩掉查询位置的未来局部键，迫使模型在同一窗口内同时预测多个未来 token（多 token 预测）。  
  损失计算公式（4）：  
  \( L_{\text{early}} = -\frac{1}{N} \sum_{n \in w_0} \sum_{j=1}^{k} \mathbb{E}_{t \sim p_{n+j}} [\log q_n^{(j)}(t)] \)

- **晚期阶段（Late Stage）**：使用训练时仿真损失 \( L_{\text{late}} \)。  
  模拟实际推理中的自回归展开过程：在第 i 步仿真中，用已预测的 token 状态更新 KV 缓存，并让下一查询访问这些更新后的状态。损失考虑第 i 步到第 j 步的预测贡献，并加权。  
  公式（6）及其特例：\( L_{\text{late}} = L(k, i, \beta^*) \)，其中权重 \( \beta_{i,j} = k - i + 1 \)。  
  该损失更紧密地近似期望接受长度（expected acceptance length），且 GPU 内存占用恒定。

## 三、实验设计

### 3.1 数据集
- **训练集**：ShareGPT（约 60K 对话），与基线方法保持一致。
- **推理评估集**：
  - MT‑Bench（多轮对话）
  - GSM‑8K（数学推理）
  - CNN‑Daily（摘要）
  每项评估使用超过 2,100 条输入（含对话轮次）。

### 3.2 基准（Benchmark）
- 目标模型：Vicuna‑7B、LLaMA‑2‑7B、LLaMA‑3‑7B。
- 对比方法：
  - 无 SD 基线（None）
  - TGI（HuggingFace 辅助生成）
  - Medusa（并行解码）
  - Self‑Spec（自投机解码）
  - Clover‑2（交叉注意力方法）
  - **EAGLE‑v2**（目前最先进的自注意力 SD 方法）
- 评估指标：生成速度（tokens/sec）、加速比（Speedup）、接受长度（τ）、峰值 GPU 内存（M）。

### 3.3 实验环境
- 推理：HuggingFace Transformers，BF16，单 GPU（A6000 Ada 或 A10G）。
- 训练：TF32，混合精度，离线生成目标模型隐藏状态。

## 四、资源与算力

- **训练硬件**：主要使用 NVIDIA A6000 Ada GPU（48 GiB）进行训练；部分实验在 A10G（24 GiB）上验证。
- **训练时长**：最大 20 个 epoch（前 10 个 epoch 早期阶段，后 10 个 epoch 晚期阶段）。具体训练时间未精确给出，但提到“在单一 24 GiB GPU 上可完整训练 7B 模型”。
- **论文未明确说明总 GPU 小时数**，也未给出具体训练收敛所需的时间数字，仅在附录中提及使用了 batch size 16、AdamW 优化器等配置。

## 五、实验数量与充分性

- **主要实验**：在 3 种目标模型 × 3 个评估集 × 2 种 GPU 的配置下，报告了速度、加速比、接受长度、峰值内存，共约 18 组核心对比。
- **消融实验**：
  - 窗口大小（k=1~5）对多 token 预测的影响。
  - 仿真步数（s=1~4）对接受率的影响。
  - 早期 vs 晚期训练阶段的损失有效性。
  - 动态树 vs 静态树、是否拼接（concatenate）KV 状态等推理配置。
  - 不同 batch size 的收敛性。
  - 随机掩码、MoE 等替代设计探索。
- **充分性与公平性**：
  - 所有基线均统一训练 epoch 数（20 个 epoch），使用相同数据集 ShareGPT。
  - 动态树超参数与 EAGLE‑v2 一致（depth=5, topk=10, candidates=60）。
  - 实验覆盖了通用对话、数学推理、摘要三类任务，具有代表性。
  - 但在更大规模模型（如 13B/70B）上的实验缺失，也缺少与更大量训练数据的 SOTA 方法（如 EAGLE‑v3）的直接对比。

## 六、主要结论与发现

1. **性能持平**：Beagle 在三种目标模型上取得与 EAGLE‑v2 几乎相同的加速比和接受长度，但在峰值内存上节省约 10%~15%。
2. **训练效率更高**：早期阶段（前 10 个 epoch）Beagle 的接受率始终优于 EAGLE‑v2，且训练速度更快（因为无需池化层和显式状态拼接）。
3. **两阶段训练有效**：早期多 token 预测（窗口 k=3 最优）能改善远期 token 接受率；晚期仿真训练可进一步突破由早期损失带来的性能瓶颈，提升所有步的预测精度。
4. **推理灵活性**：可关闭键/值拼接（仅损失 3% 速度），为内存受限场景提供选择。
5. **架构简洁性**：无需自注意力、池化或融合层，便于集成到不同 LLM 推理框架中。

## 七、优点（亮点）

- **架构创新**：首次证明纯交叉注意力草稿模型可匹敌自注意力 SOTA，简化了传统 SD 的复杂组件。
- **训练方法创新**：两阶段块注意力训练兼顾早期高效率（并行多 token 预测）与后期精准对齐（在线仿真），且保持 GPU 内存恒定。
- **实验严谨**：多数据集、多目标模型、多种 GPU 对比；消融实验系统全面，验证了每个设计选择的有效性。
- **实用导向**：降低内存占用，提供“无拼接”推理选项，有利于低算力环境部署。

## 八、不足与局限

1. **理论假设局限**：推导中假设远期 token 接受率按几何级数衰减（式 9），作者自述该假设未必严格成立，可能影响理论分析精度。
2. **实验规模受限**：
   - 仅测试 7B 级别模型，未扩展到 13B/70B 或更大模型。
   - 未与使用更多训练数据的方法（如 EAGLE‑v3，8× 数据）直接比较。
3. **训练开销未量化**：未提供完整训练 GPU 小时数，也没有说明两阶段训练相比单阶段训练的总时间增加比例。
4. **基线选择**：只对比了无损失解码方法，未涉及采样式采样（sampling‑based SD），且部分基线（如 Clover‑2）在更优硬件上的性能可能被低估。
5. **代码未公开**：论文声明不公开代码，对可重复性造成一定影响。
6. **应用范围**：当前仅针对文本 LLM，未涉及多模态或编码器‑解码器模型。

（完）
