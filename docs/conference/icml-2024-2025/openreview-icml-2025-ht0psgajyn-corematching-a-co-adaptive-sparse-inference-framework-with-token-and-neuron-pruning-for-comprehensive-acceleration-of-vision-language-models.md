---
title: "CoreMatching: A Co-adaptive Sparse Inference Framework with Token and Neuron Pruning for Comprehensive Acceleration of Vision-Language Models"
title_zh: CoreMatching：通过token和神经元剪枝实现视觉语言模型全面加速的协同稀疏推理框架
authors: "Qinsi Wang, Hancheng Ye, Ming-Yu Chung, Yudong Liu, Yueqian Lin, Martin Kuo, Mingyuan Ma, Jianyi Zhang, Yiran Chen"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=HT0PSgajyN"
tags: ["query:vlm-spec"]
score: 9.0
evidence: token和神经元剪枝加速视觉语言模型推理
tldr: 本文首次研究了VLM中token稀疏和神经元稀疏之间的相互作用，并提出CoreMatching框架协同修剪两者。通过匹配重要token和神经元，在保持模型性能的同时大幅减少计算量和内存占用，实现了对多种VLM的全面加速。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 500, \"height\": 354}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-002.webp\", \"caption\": \"\", \"page\": 4, \"index\": 2, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-003.webp\", \"caption\": \"\", \"page\": 4, \"index\": 3, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-004.webp\", \"caption\": \"\", \"page\": 4, \"index\": 4, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-005.webp\", \"caption\": \"\", \"page\": 4, \"index\": 5, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-006.webp\", \"caption\": \"\", \"page\": 4, \"index\": 6, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-007.webp\", \"caption\": \"\", \"page\": 4, \"index\": 7, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-008.webp\", \"caption\": \"\", \"page\": 4, \"index\": 8, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-009.webp\", \"caption\": \"\", \"page\": 4, \"index\": 9, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-010.webp\", \"caption\": \"\", \"page\": 4, \"index\": 10, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-011.webp\", \"caption\": \"\", \"page\": 5, \"index\": 11, \"width\": 387, \"height\": 387}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-012.webp\", \"caption\": \"\", \"page\": 5, \"index\": 12, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-013.webp\", \"caption\": \"\", \"page\": 6, \"index\": 13, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-014.webp\", \"caption\": \"\", \"page\": 6, \"index\": 14, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-015.webp\", \"caption\": \"\", \"page\": 6, \"index\": 15, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-016.webp\", \"caption\": \"\", \"page\": 6, \"index\": 16, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-017.webp\", \"caption\": \"\", \"page\": 6, \"index\": 17, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-018.webp\", \"caption\": \"\", \"page\": 6, \"index\": 18, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-019.webp\", \"caption\": \"\", \"page\": 6, \"index\": 19, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-020.webp\", \"caption\": \"\", \"page\": 6, \"index\": 20, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-021.webp\", \"caption\": \"\", \"page\": 17, \"index\": 21, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-022.webp\", \"caption\": \"\", \"page\": 17, \"index\": 22, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-023.webp\", \"caption\": \"\", \"page\": 17, \"index\": 23, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-024.webp\", \"caption\": \"\", \"page\": 17, \"index\": 24, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-025.webp\", \"caption\": \"\", \"page\": 17, \"index\": 25, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-026.webp\", \"caption\": \"\", \"page\": 17, \"index\": 26, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-027.webp\", \"caption\": \"\", \"page\": 17, \"index\": 27, \"width\": 370, \"height\": 370}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ht0psgajyn/fig-028.webp\", \"caption\": \"\", \"page\": 17, \"index\": 28, \"width\": 370, \"height\": 370}]"
motivation: VLM推理成本高，但token稀疏和神经元稀疏被视为独立方法，未探索其协同作用。
method: 引入协同适应机制，联合修剪冗余token和神经元，利用二者之间的相互依赖实现更高效的稀疏化。
result: "在多个VLM基准上，实现了2-3倍加速，精度损失在1%以内。"
conclusion: token和神经元剪枝的协同优化是VLM推理加速的有效途径。
---

## Abstract
Vision-Language Models (VLMs) excel across diverse tasks but suffer from high inference costs in time and memory. Token sparsity mitigates inefficiencies in token usage, while neuron sparsity reduces high-dimensional computations, both offering promising solutions to enhance efficiency.
Recently, these two sparsity paradigms have evolved largely in parallel, fostering the prevailing assumption that they function independently. However, a fundamental yet underexplored question remains: Do they truly operate in isolation, or is there a deeper underlying interplay that has yet to be uncovered?
In this paper, we conduct the first comprehensive investigation into this question. By introducing and analyzing the matching mechanism between Core Neurons and Core Tokens, we found that key neurons and tokens for inference mutually influence and reinforce each other. Building on this insight, we propose CoreMatching, a co-adaptive sparse inference framework, which leverages the synergy between token and neuron sparsity to enhance inference efficiency. Through theoretical analysis and efficiency evaluations, we demonstrate that the proposed method surpasses state-of-the-art baselines on ten image understanding tasks and three hardware devices. Notably, on the NVIDIA Titan Xp, it achieved 5$\times$ FLOPs reduction and a 10$\times$ overall speedup.
Code is released at [https://github.com/wangqinsi1/2025-ICML-CoreMatching/tree/main](https://github.com/wangqinsi1/2025-ICML-CoreMatching/tree/main).

---

## 论文详细总结（自动生成）

根据您提供的论文内容，以下是结构化、深入、客观的中文总结，按照要求的要点展开。

---

## 论文中文总结

### 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：视觉语言模型（VLM）在多种任务上表现优异，但其推理过程消耗大量时间和内存。现有加速方法主要分为两类：**Token 稀疏**（利用图像 token 高度冗余，仅保留重要 token）和**神经元稀疏**（利用 FFN 层激活稀疏性跳过不活跃神经元）。这两类方法通常被视为相互独立并平行发展。
- **核心问题**：论文首次系统探究了一个被忽视的基本问题——**token 稀疏与神经元稀疏之间是否存在深层的相互作用？** 如果存在，能否通过协同利用两种稀疏性实现更全面的加速？
- **整体含义**：本文发现，重要的神经元（Core Neurons）与重要的 token（Core Tokens）之间相互影响、相互增强。基于此发现，作者提出 **CoreMatching**，一个协同自适应稀疏推理框架，同时剪枝冗余 token 和神经元，达到 VLM 推理的全面加速。

### 2. 方法论
- **核心思想**：通过分析 FFN 层中不同 token 激活的神经元集合与 Core Neurons 的交集大小，发现那些与 Core Neurons 交集最大的 token 对推理贡献最大。将这些 token 定义为 **Core Tokens**。在预填充阶段联合计算 Core Neurons 和 Core Tokens，在解码阶段只保留 Core Neurons 和 Core Tokens，实现双维度稀疏。
- **关键技术细节**：
  - **Core Neurons**：输入句子 s 中，统计所有 token 的 token-wise 核心神经元（每个 token 激活值最高的 ρ% 正激活神经元），再取出现频率最高的 β% 神经元作为句子级的 Core Neurons （公式 (3)）。
  - **Core Tokens**：每个 token x 激活的神经元集合 Γ(x) 与 Core Neurons C<sup>ρ</sup><sub>β</sub>(s) 的交集大小反映该 token 的信息量。利用最大几何距离法自适应确定阈值 Tk，保留交集大于等于 Tk 的 token 作为 Core Tokens（公式 (6)）。
  - **理论优势**：提出 **投影引导准则（Projection-guided Criterion）**，认为 token 的重要性应由 α<sub>iM</sub>V<sub>i</sub> 在 O<sub>M</sub> 上的投影而非单纯注意力分数来衡量。作者通过两个观察（W<sub>q</sub>W<sub>k</sub><sup>T</sup> ≈ θI，以及激活输出 A 的余弦相似度与共同激活神经元数成正比）推导出：投影值与 Γ(x<sub>i</sub>) ∩ C<sup>ρ</sup><sub>β</sub>(s) 成正比，从而从理论上证明了 Core Tokens 是更优的 token 选择指标。
- **算法流程**（文字说明）：
  1. **预填充阶段**：对每一层，捕获所有 token 的激活值，计算 token-wise 核心神经元，再统计得到句子级 Core Neurons，仅保留 Core Neurons 在设备上。在预定的第 l 层（如第 2 层），记录每个 token 激活的神经元集合，计算与 Core Neurons 的交集数，用最大几何距离法得到阈值 Tk，选出 Core Tokens，后续推理仅使用 Core Tokens。
  2. **解码阶段**：每层使用预填充阶段保留的 Core Neurons 进行推理，KV cache 中仅包含 Core Tokens。

### 3. 实验设计
- **数据集与场景**：涵盖 10 个标准图像理解任务（VQAv2、GQA、SciQA、TextVQA、POPE、MME、MMBench、SEED、VisWiz、MM-Vet），以及 OCR/图表/文档任务（DocVQA、InfoVQA、ChartQA、OCRBench、AI2D）和视频推理任务（MSVD-QA、MSRVT-QA、ActivityNet-QA）。
- **Benchmark 与对比方法**：
  - 对比方法包括：PruMerge+、FastV、VoCo-LLAMA、LLaVA-TRIM、Dynamic-LLaVA（token 稀疏），以及 PowerInfer（神经元稀疏）。
  - 基础模型：LLaVA-1.5-7B/13B、Qwen2.5-VL-3B/7B、Video-LLaVA。
  - 硬件：NVIDIA Titan Xp (12GB)、Quadro RTX 6000 (24GB)、A100。
- **评估指标**：任务准确率、TFLOPS、推理延迟（pre-filling/decoding）、内存占用等。

### 4. 资源与算力
- 论文未明确说明训练时长，因为 **CoreMatching 无需训练（training-free）**，是一种即插即用的方法。
- 推理硬件：使用单张 NVIDIA Titan Xp (12GB)、NVIDIA Quadro RTX 6000 (24GB)、NVIDIA A100。报告了在不同硬件上的延迟和内存数据。
- 模型精度：所有实验采用 FP16 精度。

### 5. 实验数量与充分性
- **实验数量**：非常丰富。
  - 在 LLaVA-1.5-7B/13B 上评估了 10 个标准任务。
  - 在 Qwen2.5-VL 上验证了 5 个 OCR/图表任务。
  - 在 Video-LLaVA 上验证了 3 个视频推理任务。
  - 消融实验：模块消融（token only、neuron only、both）在多种硬件和输出长度下对比；不同层的 token 需求分析；不同任务的核心 token 数量统计。
  - 跨硬件和跨模型泛化实验。
- **充分性与公平性**：
  - 对比方法包括当前最先进的 token 稀疏和神经元稀疏方法，覆盖了同类工作。
  - 报告了多种指标（准确率、FLOPs、延迟、内存），并进行了统计分析。
  - 消融实验设计合理，揭示了两个稀疏维度的贡献差异。
  - 论文提供了代码开源链接，有助于复现。
  - 总体而言，实验设计较为充分、客观、公平。

### 6. 主要结论与发现
- **核心发现**：Core Neurons 与 Core Tokens 之间存在匹配机制——能激活更多 Core Neurons 的 token 对最终输出贡献更大。这揭示了两类稀疏性的内在联系。
- **性能结论**：
  - CoreMatching 在全部 10 个标准任务上均达到或超过 SOTA 方法，大部分任务实现近乎无损的性能（如 LLaVA-1.5-7B 在 VQAv2 和 GQA 上 lossless）。
  - 在 Qwen2.5-VL 和 Video-LLaVA 上也验证了有效性和泛化性。
- **加速结论**：
  - 在 Titan Xp 上，预填充阶段加速 2.1×，解码阶段加速 9.2×，总加速比约 10×。
  - 大幅降低 KV cache 和 FFN 计算的内存占用（内存从 304.8 MB 降至 48.99 MB）。
- **理论贡献**：提出投影引导准则，理论证明其与 Core Tokens 的比例关系，为 token 重要性评估提供了新的更优指标。

### 7. 优点
- **首次揭示两类稀疏性的协同关系**：将以往独立发展的 token 稀疏和神经元稀疏统一在一个框架中，提供了新的视角。
- **无训练、即插即用**：无需额外训练或微调，可直接应用于现有 VLM。
- **理论分析深入**：通过矩阵正交性观察和激活相关性分析，从理论上解释了为什么核心 token 优于注意力分数选择。
- **自适应动态剪枝**：CoreMatching 根据数据分布自动确定阈值，无需预定义保留 token 数量，适应不同任务难度。
- **跨模型、跨硬件泛化好**：在 LLaVA、Qwen2.5-VL、Video-LLaVA 以及多个 GPU 上均表现稳定。
- **全面的加速效果**：同时减少 token 和神经元，在 pre-filling 和 decoding 阶段均获得显著加速，尤其改善解码延迟。

### 8. 不足与局限
- **实验覆盖仍有局限**：
  - 虽然测试了多个模型，但主要集中于 LLaVA 系列及 Qwen2.5-VL（一种动态分辨率模型），未在更多不同架构（如 BLIP-2、InstructBLIP）或其他 LLM 主干（如 LLaMA-2/3 全系列）上验证。
  - 视频任务仅测试了一个基础模型（Video-LLaVA），且视频 token 可能具有不同特性，需更多验证。
- **依赖假设的鲁棒性**：论文的理论推导基于两个观察（矩阵近似正交、cos(∠) 与共同激活神经元数成正比），该假设在实验中部分成立，但并非绝对精确。对于某些层或模型，偏差可能增大，理论保证可能减弱。
- **超参数敏感性**：方法使用了 ρ 和 β 两个超参数（固定为 0.2 和 0.4），论文未系统探讨其敏感度及对任务性能的影响。
- **性能损失依然存在**：虽然在多个任务上实现 lossless，但在 TextVQA 等任务上仍有少量下降（如 LLaVA-1.5-7B 从 58.2 降至 54.5），对精度要求极高的场景可能有影响。
- **无训练加速方法的固有限制**：未涉及训练阶段的优化，仅针对推理加速。对于需要实时资源管理的大规模部署，可能还需结合量化等其他技术。

（完）
