---
title: Fast Large Language Model Collaborative Decoding via Speculation
title_zh: 通过投机实现快速大语言模型协作解码
authors: "Jiale Fu, Yuchu Jiang, Junkai Chen, Jiaming Fan, Xin Geng, Xu Yang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=SGrJ8a9a5U"
tags: ["query:llm"]
score: 8.0
evidence: 通过推广投机解码、使用联合验证分布来加速协作解码
tldr: LLM协作解码质量高但计算成本大。CoS框架借鉴投机解码思想，将多个模型的输出分布联合进行验证，并交替角色提升效率。实验表明在保持生成质量的同时大幅加速，为多模型协作提供高效方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-sgrj8a9a5u/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 865, \"height\": 779, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sgrj8a9a5u/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 877, \"height\": 1273, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sgrj8a9a5u/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 863, \"height\": 1008, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sgrj8a9a5u/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1770, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sgrj8a9a5u/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 792, \"height\": 551, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sgrj8a9a5u/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1753, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sgrj8a9a5u/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 834, \"height\": 283, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sgrj8a9a5u/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 827, \"height\": 301, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sgrj8a9a5u/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 846, \"height\": 300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sgrj8a9a5u/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 819, \"height\": 307, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sgrj8a9a5u/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 878, \"height\": 285, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sgrj8a9a5u/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 858, \"height\": 303, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sgrj8a9a5u/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 845, \"height\": 307, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sgrj8a9a5u/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 847, \"height\": 308, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sgrj8a9a5u/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1768, \"height\": 388, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-sgrj8a9a5u/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 856, \"height\": 444, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sgrj8a9a5u/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 843, \"height\": 1007, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sgrj8a9a5u/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 829, \"height\": 810, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sgrj8a9a5u/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1791, \"height\": 1201, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sgrj8a9a5u/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1790, \"height\": 1682, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sgrj8a9a5u/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1027, \"height\": 379, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sgrj8a9a5u/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1279, \"height\": 841, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sgrj8a9a5u/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1299, \"height\": 1158, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sgrj8a9a5u/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 899, \"height\": 359, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sgrj8a9a5u/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 844, \"height\": 465, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sgrj8a9a5u/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1156, \"height\": 377, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sgrj8a9a5u/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1154, \"height\": 378, \"label\": \"Table\"}]"
motivation: LLM协作解码质量高但计算开销大，需要加速。
method: 提出CoS框架，基于投机解码，让模型轮流作为提议者和验证者，并联合验证分布。
result: 在保持协作解码质量的前提下显著提升推理速度。
conclusion: CoS将投机解码思想成功扩展到协作解码场景，实现高效加速。
---

## Abstract
Large Language Model (LLM) collaborative decoding techniques improve output quality by combining the outputs of multiple models at each generation step, but they incur high computational costs. In this paper, we introduce **Collaborative decoding via Speculation (CoS)**, a novel framework that accelerates collaborative decoding without compromising performance. Inspired by Speculative Decoding—where a small proposal model generates tokens sequentially, and a larger target model verifies them in parallel, our approach builds on two key insights: (1) the verification distribution can be the combined distribution of both the proposal and target models, and (2) alternating each model as the proposer and verifier can further enhance efficiency. We generalize this method to collaboration among *n* models and theoretically prove that CoS is never slower than standard collaborative decoding, typically achieving faster speed. Extensive experiments demonstrate CoS is **1.11x–2.23x** faster than standard collaborative decoding without compromising generation quality. Our code is available at https://github.com/Kamichanw/CoS/.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：LLM 协作解码（如加权集成、对比解码、解码时对齐）通过组合多个模型的输出分布来提升生成质量，但每个解码步需要所有模型分别进行一次前向传播，导致推理开销成倍增长，严重限制实际部署。
- **整体含义**：本文旨在在不牺牲协作解码质量的前提下，显著加速多模型联合推理。受投机解码（Speculative Decoding）的启发，作者提出 **CoS（Collaborative decoding via Speculation）**，将投机解码的思想引入协作场景，通过联合验证分布和交替提议框架实现加速。

### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：投机解码中，小模型快速生成候选令牌，大模型并行验证并接受/拒绝；验证分布通常是目标模型自身的分布。本文发现验证分布可以替换为任意联合分布（如加权平均、对比解码后的分布），从而使得生成的令牌遵循联合分布，实现协作解码的投机化。
- **关键技术细节**：
  - **Naive-CoS**：修改投机解码的验证公式，将接受条件中的目标分布替换为联合分布 \( r(x) = C(q(x), p(x)) \)，接受概率为 \( \min(1, r(x)/q(x)) \)，被拒绝时从残差分布重采样。理论上生成令牌服从联合分布 \( r(x) \)。
  - **Alternate Proposal Framework**：当所有提议令牌被接受时，大模型会产生一个“奖励令牌”，但该令牌服从大模型自身分布而非联合分布。为了利用该令牌，提出交替提议机制：将奖励令牌视为当前验证者的下一个提议，由原提议者进行验证，从而两个模型轮流担任提议者和验证者，进一步提升效率。
  - **推广到 n 个模型**：多个模型轮流对当前令牌打分（生成分布），同时自然产生奖励令牌。所有模型对同一令牌的打分完成后，利用联合分布进行验证，已打分的分布可丢弃，节省计算。
- **关键公式与算法**：
  - 接受率 \( \alpha = 1 - \frac12 D_{TV}(q, r) \)。
  - 加权集合场景下 \( \alpha \ge \lambda \)（\(\lambda\) 为提议模型权重），保证加速。
  - 速度提升因子理论公式：标准投机解码为 \( \frac{(1-\alpha^\gamma)(1+c)}{(1-\alpha)(1+c\gamma)} \)；交替提议框架为 \( \frac{(1-\alpha^{\gamma_q})(1+c)}{(1-\alpha)(1+c\gamma_q - \alpha^{\gamma_p} c)} \)。

### 3. 实验设计
- **数据集与场景**：代码生成（HumanEval）、数学推理（GSM8K）、多任务理解（MMLU）、文本摘要（CNNDM）。
- **Benchmark**：对比标准协作解码（WE/CD）、并行协作解码（WE-P/CD-P，即同时调用所有模型）、投机解码（SD，直接用联合分布作为目标，但无交替提议）、CoS。
- **模型对配置**：
  - 加权集成（WE）：Llama-2-7B + Vicuna-7B、Qwen2.5-3B/1.5B + Qwen2.5-Coder 系列，以及三模型协作（Qwen2.5-1.5B + 其代码/数学版本）。
  - 对比解码（CD）：Llama-3.2-1B + Llama-3.1-8B、Llama-68M + Llama-2-7B、OPT-125M + OPT-13B。
- **超参数**：\(\lambda=0.5\)（WE），\(\mu=0.1\)（CD），温度 \(T=0,1\)，提议长度 \(\gamma\) 测试 1~5 并报告最优。

### 4. 资源与算力
- **GPU**：RTX 3090（除 Llama-Vicuna 对使用 A6000），另在 Ascend 910B3 NPU 上进行了验证（附录 C.5）。
- **训练时长**：本文为推理加速方法，未涉及训练，因此未报告训练时长。

### 5. 实验数量与充分性
- **实验数量**：覆盖 4 个数据集、5 组模型对（含三模型）、两种协作模式（WE/CD）、多种温度与超参数变体。消融实验包括：
  - 不同 \(\gamma\) 对加速的影响（图 6）。
  - 不同 \(\lambda\) 在 WE 中的加速效果（图 4）。
  - 不同 \(\mu\) 在 CD 中的加速效果（图 5）。
  - 交替提议框架的消融（附录 C.4）。
  - 质量-速度权衡实验（附录 C.1）。
- **充分性**：实验设计较为全面，对比了多种 baseline，验证了理论下界，并跨不同模型规模、不同任务类型进行了测试。实验条件（GPU 型号、温度等）有明确说明，结果客观。

### 6. 论文的主要结论与发现
- CoS 在保持生成质量（与标准协作解码输出的分布一致）的前提下，实现 **1.11x–2.23x** 的推理加速。
- 加权集成场景下，加速比更稳定且下界更高（至少 1.34x 两模型，1.27x 三模型），因接受率有理论下界 \(\lambda\)。
- 交替提议框架相比 Naive-CoS 进一步提升了加速（消融实验显示提升约 10-20%）。
- 理论上证明 CoS 永远不会慢于标准协作解码（Corollary 3.7），且几乎总是更快。
- CoS 可自然用于调整投机解码的质量-速度权衡（通过加权集成小模型分布），具有可解释性。

### 7. 优点
- **通用性强**：不限于特定协作方式（加权集成、对比解码、解码时对齐均可加速），且可推广到任意数量的模型。
- **理论保障完善**：证明了接受率下界、加速因子公式以及永不慢于标准的性质，提供可证的低效风险规避。
- **交替提议机制新颖有效**：巧妙利用奖励令牌，避免额外模型调用，进一步提升效率。
- **可解释的权衡**：通过调整权重 \(\lambda\) 实现推理速度与生成质量的平滑控制，且明确说明生成服从已知联合分布。

### 8. 不足与局限
- **模型对覆盖有限**：主要测试了开源系列（Llama、Vicuna、Qwen、OPT），未涉及更大规模模型（如 70B 以上）或更多样化的架构（如 MoE 模型）。加速比在大模型差异显著时可能变化。
- **评估维度单一**：仅报告了速度加速比和生成质量（与标准协作解码对比），未评估内存占用、延迟分布、服务吞吐等实际部署指标。
- **未考虑提议模型选择策略**：文中假设预定义默认提议模型，未讨论如何自动选择最优提议模型或动态切换策略。
- **实验设备限制**：仅在 RTX 3090/A6000 和 Ascend 910B3 上测试，未涵盖更广泛的硬件（如 A100、H100），可能影响加速比的绝对值。
- **消融实验不够完整**：虽然测试了 \(\gamma\) 和交替框架，但未深入分析不同 \(\gamma\) 组合（如提议者和验证者不同的 \(\gamma\)）以及三模型协作中的最优提议顺序。

（完）
