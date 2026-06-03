---
title: Inevitable Trade-off between Watermark Strength and Speculative Sampling Efficiency for Language Models
title_zh: 大语言模型中水印强度与投机采样效率之间不可避免的权衡
authors: "Zhengmian Hu, Heng Huang"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=6YKMBUiIsG"
tags: ["query:llm"]
score: 6.0
evidence: 水印与投机采样效率之间的权衡
tldr: 本文研究了在LLM中同时进行水印注入和投机采样的可能性，并证明了两者之间存在不可避免的权衡：水印强度越高，投机采样的加速效率越低。该发现对设计同时加速和保护生成内容的系统有重要指导意义。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-6ykmbuiisg/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1387, \"height\": 570, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-6ykmbuiisg/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1218, \"height\": 1136, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-6ykmbuiisg/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1230, \"height\": 1138, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-6ykmbuiisg/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1242, \"height\": 1139, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-6ykmbuiisg/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1220, \"height\": 1139, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-6ykmbuiisg/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1247, \"height\": 2149, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-6ykmbuiisg/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1287, \"height\": 2147, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-6ykmbuiisg/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1287, \"height\": 2146, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-6ykmbuiisg/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1321, \"height\": 2144, \"label\": \"Table\"}]"
motivation: 尚无方法同时加速推理和注入水印，本文探索其可行性。
method: 理论分析证明水印与投机采样效率之间的基本权衡。
result: 证明了整合水印和加速并非平凡，存在权衡。
conclusion: 必须权衡水印强度与加速效果，不可兼得。
---

## Abstract
Large language models are probabilistic models, and the process of generating content is essentially sampling from the output distribution of the language model. Existing watermarking techniques inject watermarks into the generated content without altering the output quality. On the other hand, existing acceleration techniques, specifically speculative sampling, leverage a draft model to speed up the sampling process while preserving the output distribution. However, there is no known method to simultaneously accelerate the sampling process and inject watermarks into the generated content. In this paper, we investigate this direction and find that the integration of watermarking and acceleration is non-trivial. We prove a no-go theorem, which states that it is impossible to simultaneously maintain the highest watermark strength and the highest sampling efficiency. Furthermore, we propose two methods that maintain either the sampling efficiency or the watermark strength, but not both. Our work provides a rigorous theoretical foundation for understanding the inherent trade-off between watermark strength and sampling efficiency in accelerating the generation of watermarked tokens for large language models. We also conduct numerical experiments to validate our theoretical findings and demonstrate the effectiveness of the proposed methods.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：大语言模型（LLMs）在生成内容时，既需要注入水印来保护知识产权，又需要投机采样（Speculative Sampling）来加速推理。然而，现有工作中没有能够同时实现这两个目标的方法。
- **核心问题**：是否可以同时保持最高水印强度和最高采样效率？
- **整体含义**：论文证明了在词汇大小大于2时，两者之间存在不可避免的权衡——无法同时维持最高的水印强度和最高的采样效率。这一发现为设计同时考虑加速和保护的生成系统提供了理论指导。

## 2. 论文提出的方法论
### 2.1 核心思想：Two Reweight Framework
- 提出一个通用框架 `two reweight framework`，同时对**目标模型**和**草稿模型**应用不同的重加权函数（均基于同一水印码E），以提高水印后草稿分布与水印后目标分布之间的重叠概率，从而改善采样效率。
- 框架形式化：水印化草稿分布为 `R'_E(Q)`，水印化目标分布为 `R_E(P)`，投机采样过程定义为条件分布 `A(j|i)`，最终生成分布为 `bR_E(P) = A ∘ R'_E(Q)`。
- 要求无偏性：`E_E[bR_E(P)] = P`。

### 2.2 关键技术：No-go 定理
- **定理1**（No-go Theorem）：当 `|Σ| > 2` 时，不存在非平凡的重加权函数 `R` 和 `R'` 以及投机过程 `A`，使得同时满足：
  1. 水印强度保持不变：`bR_E(P) = R_E(P)`
  2. 采样效率保持不变：`α(P,Q) = E_E[Σ_i A(i|i) R'_E(Q)(i)]`
- 证明基于两个引理：保持采样效率 → `R'_E(Q)` 无偏；同时保持两者 → `R'_E(Q)=R_E(Q)`。进而推出 `R_E(P)=P`，即重加权平凡。

### 2.3 两种实际算法（Algorithm 1）
- **Maintain Watermark Strength (MWS)**：
  - 令 `R'_E(Q) = R_E(Q)`，投机过程 `A` 基于水印化分布 `R_E(P)` 和 `R_E(Q)` 进行标准投机采样。
  - 效果：最终输出分布等于 `R_E(P)`，水印强度与原水印方法相同。
- **Maintain Sampling Efficiency (MSE)**：
  - 令 `R'_E(Q) = R_E(Q)`，但投机过程 `A` 基于**原始**分布 `P` 和 `Q` 进行标准投机采样。
  - 效果：平均接受概率与原无水的投机采样相同，采样效率保持不变，但水印强度下降。

**算法流程**（文字说明）：
- 输入提示和上下文代码历史，逐步生成草稿序列（K个），在每一步检查上下文代码是否已出现过（防止重复使用），若已出现则跳过水印（保持无偏），否则使用水印重加权。
- 并行计算目标模型分布（同样跳过重复上下文）。
- 按保持水印强度或保持采样效率的方式决定是否接受草稿token，否则从残差分布中采样。
- 更新上下文代码历史。

## 3. 实验设计
### 3.1 数据集与场景
- **主要实验**：CNN_DailyMail 文本摘要任务。
- **额外实验**（附录H）：开放文本生成任务。

### 3.2 基准模型
- **目标模型**：Llama-7b 和 Llama-13b
- **草稿模型**：Llama-68m

### 3.3 对比方法
- Basic Sampling（基础采样）
- Vanilla Unbiased Watermark (VUW)（无加速的水印）
- Vanilla Speculative Sampling (VSpS)（无水的加速）
- Maintain Watermark Strength (MWS)（本文算法）
- Maintain Sampling Efficiency (MSE)（本文算法）

### 3.4 指标
- **AATPS**：平均每步接受token数（采样效率）
- **ANLPPT**：平均每token负对数p值（水印强度，基于maximin-LLR得分或U得分）
- **PTT**：每token时间（毫秒，衡量加速）
- **LOGPPL**：对数困惑度（验证输出质量不变）

### 3.5 变量设置
- 草稿序列长度 K = 1,2,3,4
- 重加权方案：DeltaGumbel 和 Gamma
- 水印检测方法：likelihood-based (maximin-LLR) 和 likelihood-agnostic (U score)

## 4. 资源与算力
- 论文明确说明：总计算成本约 **1200 A6000 GPU小时**（参见 Section 6 末尾）。
- 使用的 GPU 型号为 NVIDIA A6000。

## 5. 实验数量与充分性
- **实验组数**：主要结果见图2，附录H包含额外三组图（图3-5）和四张详细表格（表1-4），覆盖两种目标模型、两种任务、两种重加权、两种水印检测方法、四个 K 值、五种方法，总计约 2×2×2×2×4×5 ≈ 320 个实验点（部分组合可能省略，但非常充分）。
- **消融设计**：通过对比 MWS 与 VUW（水印强度是否保持）、MSE 与 VSpS（采样效率是否保持），直接验证理论。同时测量 LOGPPL 确认输出分布无偏。
- **公平性**：所有方法在同一环境下运行，使用相同的模型、数据、评价指标。误差条显示 3σ 置信区间。
- **评估**：实验设计系统、变量控制良好，足以支持主要结论。

## 6. 论文的主要结论与发现
- **理论发现**：在 `two reweight framework` 下，水印强度和采样效率无法同时达到最高水平，存在固有权衡。
- **算法效果**：
  - MWS 方法可以保持水印强度（与 VUW 相同），但采样效率略低于 VSpS（仍有显著加速）。
  - MSE 方法可以保持采样效率（与 VSpS 相同），但水印强度下降（介于 VUW 和 VSpS 之间）。
  - 两种方法均不改变输出质量（LOGPPL 一致）。
- **实用价值**：MWS 方法在保持强水印的同时，实现了比 VUW 更低的每token延迟，具有实际加速效果。

## 7. 优点
- **理论创新**：首次严格证明水印与投机采样之间的权衡，提出 no-go 定理，为领域奠定理论基础。
- **框架通用性**：`two reweight framework` 可扩展到多种投机采样变体（如整序列验证、树验证等）（见附录E讨论）。
- **算法实用性**：两种算法分别满足不同需求，且实现简单（Algorithm 1），实验验证有效。
- **实验全面**：覆盖多种模型、任务、重加权方案、水印检测方法、K值，结论鲁棒。
- **开源可复现**：提供完整代码和补充材料。

## 8. 不足与局限（基于附录G及论文内容）
- **理论假设**：no-go 定理依赖于 `two reweight framework`，其他框架可能规避此权衡。
- **实验规模**：仅使用 Llama-7b/13b 和草稿模型 Llama-68m，未涉及更大模型（如 70B）或更先进的草稿模型（如 Medusa、Eagle），加速比不代表 SOTA。
- **草稿序列长度选择**：未讨论如何自动选择最优 K，对部署有影响。
- **侧信道风险**：MWS 方法比 VSpS 稍慢，用户可能通过速度差异推断是否使用了水印，影响水印不可检测性。
- **变体验证缺失**：论文仅实现基本投机采样，虽在附录E讨论了扩展思路，但未进行实验验证树验证或多候选版本。
- **数据集单一**：主要实验仅在 CNN_DailyMail 上，开放文本生成作为补充，但任务多样性有限。

（完）
