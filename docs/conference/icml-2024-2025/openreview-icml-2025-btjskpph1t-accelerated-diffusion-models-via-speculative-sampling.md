---
title: Accelerated Diffusion Models via Speculative Sampling
title_zh: 通过投机采样加速扩散模型
authors: "Valentin De Bortoli, Alexandre Galashov, Arthur Gretton, Arnaud Doucet"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=BTJSkPpH1t"
tags: ["query:llm-sd"]
score: 7.0
evidence: 投机采样用于加速，与投机解码方法相关
tldr: 该论文将投机采样技术从大型语言模型扩展到扩散模型，提出无需训练草稿模型的简单有效策略。通过将扩散过程视为连续马尔可夫链，利用快速的草稿模型生成候选样本，再根据目标模型进行接受或拒绝。实验表明，该方法在多种扩散模型上实现了近一半的推理步骤缩减，同时保持了生成质量，为加速扩散模型推理提供了新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-btjskpph1t/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1416, \"height\": 642, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-btjskpph1t/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 481, \"height\": 900, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-btjskpph1t/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 687, \"height\": 978, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-btjskpph1t/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 886, \"height\": 591, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-btjskpph1t/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1131, \"height\": 774, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-btjskpph1t/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 876, \"height\": 580, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-btjskpph1t/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 870, \"height\": 569, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-btjskpph1t/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1290, \"height\": 456, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-btjskpph1t/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1246, \"height\": 382, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-btjskpph1t/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1791, \"height\": 570, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-btjskpph1t/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1066, \"height\": 454, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-btjskpph1t/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1251, \"height\": 453, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-btjskpph1t/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1053, \"height\": 817, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-btjskpph1t/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1060, \"height\": 1056, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-btjskpph1t/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1059, \"height\": 1056, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-btjskpph1t/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 602, \"height\": 609, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-btjskpph1t/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1222, \"height\": 157, \"label\": \"Table\"}]"
motivation: 现有投机采样仅限于离散序列，无法直接应用于扩散模型的连续生成过程，导致推理速度瓶颈。
method: 将投机采样扩展到连续马尔可夫链，设计多种草稿策略，包括无需训练的通用方法，通过快速草稿模型生成候选并用目标模型验证。
result: 在多种扩散模型上推理步骤减半，生成质量几乎无损，显著加速了采样过程。
conclusion: 提出了一种即插即用的扩散模型加速框架，拓展了投机采样的应用范围。
---

## Abstract
Speculative sampling is a popular technique for accelerating inference in Large Language Models by generating candidate tokens using a fast draft model and then accepting or rejecting them based on the target model's distribution. While speculative sampling was previously limited to discrete sequences, we extend it to diffusion models, which generate samples via continuous, vector-valued Markov chains. In this context, the target model is a high-quality but computationally expensive diffusion model. We propose various drafting strategies, including a simple and effective approach that does not require training a draft model and is applicable out-of-the-box to any diffusion model. We demonstrate significant generation speedup on various diffusion models, halving the number of function evaluations while generating exact samples from the target model. Finally, we also show how this procedure can be used to accelerate Langevin diffusions to sample unnormalized distributions.

---

## 论文详细总结（自动生成）

# 论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：扩散模型生成高质量样本，但推理过程需要多步迭代，计算开销大。大型语言模型（LLM）中常用的投机采样（speculative sampling）加速方法此前仅适用于离散序列，无法直接应用于扩散模型的连续、向量值马尔可夫链生成过程。
- **整体含义**：本文首次将投机采样技术从LLM扩展到扩散模型，提出一种无需训练草稿模型、可即插即用的加速框架，在保持生成质量的同时大幅减少函数评估次数，为扩散模型推理加速提供了新思路。

## 2. 论文提出的方法论
- **核心思想**：将扩散模型的采样过程视为连续马尔可夫链，利用一个快速（但可能质量较低）的草稿模型生成候选样本，然后根据目标扩散模型（高质量但计算昂贵）的分布对候选进行接受或拒绝，从而在保持目标分布不变的前提下跳过部分计算步骤。
- **关键技术细节**：
  - **连续马尔可夫链扩展**：将投机采样的拒绝-接受机制从离散token推广到连续状态空间，定义了针对连续扩散过程的正确性条件。
  - **多种草稿策略**：提出多种草稿模型设计方式，包括：
    - **无需训练的通用策略**：直接使用目标模型本身但减少步数或使用更简单的数值求解器作为草稿，无需额外训练即可应用于任何扩散模型。
    - **可训练的策略**：如果需要更高效率，也可以训练一个轻量级草稿模型。
  - **算法流程**（文字说明）：
    1. 从当前状态出发，用草稿模型快速生成一个候选样本（例如通过少量步数或低成本求解器）。
    2. 计算目标扩散模型下该候选样本的接受概率（基于模型似然或跳转分布差异）。
    3. 以该概率接受候选；若拒绝，则回退到当前状态并可能进行修正（类似Metropolis-Hastings步骤）。
    4. 重复上述过程直至达到预设步数，最终生成样本。
- **理论保证**：证明了该方法能精确采样目标扩散模型的分布，无偏性成立。

## 3. 实验设计
- **使用的数据集/场景**：论文未在元数据中明确列出具体数据集，但提及在“多种扩散模型”上测试，包括图像生成和概率分布采样任务（如Langevin扩散用于未归一化分布采样）。
- **基准（benchmark）**：未详细说明对比基线，但推测包括原始未加速的扩散模型、其他加速方法（如蒸馏、步数缩减等）。
- **对比方法**：元数据仅提到“与投机解码方法相关”，未列出具体对比方法名，实验部分可能对比了不同草稿策略以及无加速情况。

## 4. 资源与算力
- **未明确说明**：元数据中未提供GPU型号、数量、训练时长等具体算力信息。论文可能侧重于算法设计和理论分析，实验规模较小，因此未强调算力消耗。

## 5. 实验数量与充分性
- **实验数量**：元数据提到“在多种扩散模型上”验证，并展示“推理步骤减半”的效果。但未给出具体实验组数（如不同模型、不同草稿策略、不同任务数量）。另外，论文包含多张表格和图表（如元数据中列出Table 1-11，Figure 1-6），说明实验较为丰富。
- **充分性与公平性**：
  - **优点**：覆盖了多种扩散模型（图像生成、Langevin扩散），并比较了不同草稿策略（有/无训练），消融实验可能探讨了步数、接受率等影响。
  - **不足**：元数据未提供详细消融结果或与SOTA加速方法的定量对比，因此难以判断是否全面。此外，实验是否使用相同种子、相同硬件设置等细节未知。

## 6. 论文的主要结论与发现
- **主要结论**：投机采样可成功扩展至连续马尔可夫链的扩散模型，在不牺牲生成质量的前提下将函数评估次数减少约一半。
- **关键发现**：
  - 无需训练草稿模型的通用策略即可取得显著加速，适用性广。
  - 该方法同样可加速Langevin扩散，用于采样未归一化分布，拓展了投机采样的应用范围。
  - 生成的样本与目标模型精确一致（无偏采样）。

## 7. 优点
- **方法创新**：将投机采样从离散序列拓展到连续空间，填补了扩散模型加速领域的一项空白。
- **即插即用**：提出的无需训练的草稿策略可直接应用于任何现有扩散模型，无需修改或额外训练，降低了使用门槛。
- **理论正确性**：提供了无偏采样的理论保证，与蒸馏等近似方法不同，保证生成样本与目标模型分布完全相同。
- **实验丰富**：在多种任务上验证（图像生成、未归一化分布采样），并对比了不同策略，证明了方法的普适性。

## 8. 不足与局限
- **实验覆盖不足**：元数据中未明确列出具体数据集（如CIFAR-10、ImageNet等），也未与当前主流的加速方法（如DDIM、DPM-solver、蒸馏等）进行直接性能对比，因此加速效果的实际领先程度待检验。
- **草稿模型效率**：虽然提出了无需训练的通用策略，但其采样效率受限于草稿模型与目标模型的接近程度；若草稿模型与目标差异过大，拒绝率可能较高，加速效果有限。
- **计算开销**：拒绝-接受步骤需要计算目标模型的分布信息，可能引入额外开销，在每一步减少的函数评估次数与拒绝计算成本之间需权衡。
- **应用限制**：方法假设扩散过程为马尔可夫链，对于非马尔可夫的扩散过程（如某些基于ODE的采样器）可能需要调整；此外，对条件生成或高维复杂分布的效果未在元数据中展示。
- **资源与复现**：未提供代码、超参数设置或详细的算力信息，影响可复现性。

（完）
