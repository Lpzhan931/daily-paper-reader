---
title: "Sequoia: Scalable and Robust Speculative Decoding"
title_zh: "Sequoia: 可扩展且鲁棒的投机解码"
authors: "Zhuoming Chen, Avner May, Ruslan Svirschevski, Yu-Hsun Huang, Max Ryabinin, Zhihao Jia, Beidi Chen"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=rk2L9YGDi2"
tags: ["query:llm"]
score: 9.0
evidence: 可扩展且鲁棒的投机解码算法用于LLM
tldr: 本文针对投机解码中规模扩展和温度鲁棒性问题，提出Sequoia算法。通过动态规划搜索最优推测树结构，并设计新的采样与验证方法以在不同解码温度下保持高效。实验证明，Sequoia在多个LLM上实现更高的推理加速，且对超参数不敏感，为实用投机解码提供了可扩展的解决方案。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-rk2l9ygdi2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1360, \"height\": 534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rk2l9ygdi2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 695, \"height\": 362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rk2l9ygdi2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1446, \"height\": 392, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rk2l9ygdi2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1283, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rk2l9ygdi2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1375, \"height\": 1881, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rk2l9ygdi2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1478, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rk2l9ygdi2/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 586, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rk2l9ygdi2/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 586, \"height\": 469, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-rk2l9ygdi2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 352, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rk2l9ygdi2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1451, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rk2l9ygdi2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1449, \"height\": 761, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rk2l9ygdi2/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1448, \"height\": 603, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rk2l9ygdi2/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1090, \"height\": 340, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rk2l9ygdi2/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1088, \"height\": 339, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rk2l9ygdi2/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 731, \"height\": 140, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rk2l9ygdi2/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 732, \"height\": 165, \"label\": \"Table\"}]"
motivation: 现有投机解码在扩展推测预算和适应不同超参数方面受限。
method: 提出动态规划寻找最优树结构，以及温度鲁棒的采样与验证方法。
result: 在多种设置下均取得领先加速比且稳定。
conclusion: 树结构推测和鲁棒验证是提升投机解码扩展性的关键。
---

## Abstract
As the usage of large language models (LLMs) grows, it becomes increasingly important to serve them quickly and efficiently. While speculative decoding has recently emerged as a promising direction for accelerating LLM serving, existing methods are limited in their ability to scale to larger speculation budgets and adapt to different hyperparameters. This paper introduces Sequoia, a scalable and robust algorithm for speculative decoding. To improve scalability, Sequoia introduces a dynamic programming algorithm to find an optimal tree structure for the speculated tokens. To achieve robust speculative decoding, Sequoia uses a novel sampling and verification method that outperforms prior work across different decoding temperatures. Sequoia improves the decoding speed of Llama2-7B, Llama2-13B, and Vicuna-33B on an A100 GPU by up to $4.04\times$, $3.73\times$, and $2.27 \times$. To serve Llama3-70B-Instruct on a single L40 GPU through offloading, Sequoia reduces the per-token decoding latency to 0.60 s/token, $9.5\times$ faster than DeepSpeed-Zero-Inference.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）的推理速度受限于内存带宽瓶颈，生成每个 token 都需要加载全部参数，导致硬件利用率低。投机解码（Speculative Decoding）通过一个小型草稿模型快速生成多个候选 token，再由目标模型并行验证，从而在保持输出分布不变的前提下加速推理。然而，现有方法（如 SpecInfer、SpecTr）在扩展到更大的推测预算（更大、更深的 token 树）时效果有限，且对不同解码超参数（如温度）的鲁棒性差。

- **核心问题**：如何设计**可扩展**且**鲁棒**的基于树的投机解码算法——即树结构能随规模增大持续提升加速效果，且采样/验证方法在各种温度下均保持高效。

- **整体含义**：本文提出的 Sequoia 算法通过动态规划优化树拓扑结构，并引入无放回采样与覆盖性验证，实现了从设备端到卸载场景的显著加速（最高 9.5×），为投机解码的实用化提供了可扩展且稳定的方案。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：  
  - **树结构优化**：将推测树构建形式化为一个受限于树节点数的期望生成 token 数最大化问题，利用动态规划离线搜索最优拓扑。  
  - **鲁棒采样与验证**：对 SpecInfer 算法进行两点改进：①采用无放回采样（Sampling without replacement），避免重复提出已被拒绝的低质量 token；②当草稿模型所有候选 token 均被拒绝后，使用均匀分布填补剩余候选，确保最终能覆盖整个词汇表。

- **关键技术细节**：  
  - **位置接受假设**：假设验证算法接受第 k 个子 token 的概率只依赖于 k（而非上下文），从而将验证过程建模为一个接受向量 p = (p₁, p₂, …)。  
  - **动态规划（DP）**：定义状态 T(n, b) 为大小为 n、根节点有 b 个子节点的树的最大期望生成 token 数，递推式：  
    `T[n, b] = max_{1 ≤ m ≤ n-1} [ T[n-m, b-1] + p[b] · Tmax[m] ]`  
    其中 Tmax[m] = max_{0 ≤ j ≤ B} T[m, j]。算法可扩展支持最大深度约束和自推测（self-speculation）场景。  
  - **Sequoia 采样与验证算法（Algorithm 2）**：  
    - 初始化残差 R = 目标分布 P，草稿分布 D = Q，拒绝集 S = ∅。  
    - 循环 k 次：从 D 采样 token s，若随机数 r < R[s]/D[s] 则接受 s 并返回；否则更新 R = norm(max(R-D, 0))，将 s 加入 S，置 D[s] = 0；若 sum(D) = 0，则将 D 设为未被拒绝 token 上的均匀分布。  
  - **理论保证**：  
    - 满足“最优传输性质”（k=1 时接受率 = 1 – ‖P-Q‖₁/2）和“覆盖性质”（若草稿分布支持集大小为 k 且包含目标分布支持集，则最多 k 次推测后接受率为 1）。  
    - 证明 Sequoia 树在幂律接受率假设下，期望生成 token 数下界为 Ω(b·log n / log log n)，即随树规模对数增长，而现有树结构存在上限饱和。

### 3. 实验设计：数据集 / 场景、Benchmark、对比方法

- **数据集**：C4（en）、OpenWebText、CNN DailyMail、MT-Bench。  
- **场景**：  
  - **设备端**（on-device）：A100、L40 GPU，批量大小为 1。  
  - **卸载**（offloading）：L40 GPU（PCIe 4.0），将 Llama3-70B-Instruct 等模型参数卸载至 CPU 内存。  
- **基准方法**：  
  - 标准自回归解码（增量解码）。  
  - SpecInfer（[28]）及其典型的 5×8 树（设备端）和 16×48 树（卸载）。  
  - SpecTr、自顶向下采样（top-k sampling）作为对比基线。  
- **模型对**：  
  - 草稿模型：JackFram/Llama-68M（JF68M）、princeton-nlp/Sheared-Llama-1.3B（SL1.3B）、Llama2-7B-chat、Llama3-8B-Instruct。  
  - 目标模型：Llama2-7B、Llama2-13B、Vicuna-33B（设备端）；Llama2-70B-chat、Llama3-70B-Instruct（卸载）。  
- **评估指标**：每 token 生成时间（Time Between Tokens, TBT）、加速比（相对于增量解码）、每步平均生成 token 数。

### 4. 资源与算力

论文明确说明：  
- 设备端实验使用 **NVIDIA A100 (80GB PCIe)** 和 **L40** GPU，各 1 块。  
- 卸载实验使用 **L40 GPU** 并通过 **PCIe 4.0** 连接 CPU（31.5 GB/s 带宽）。  
- 未提供具体训练时长（本文方法无需训练），程序运行时间受推理实验规模影响。作者提供了代码供复现。

### 5. 实验数量与充分性

- **主要实验**：  
  - 设备端：3 个目标模型 × 2 种温度（0.0, 0.6） × 3 个数据集（C4、OpenWebText、CNN Daily） + MT-Bench 共约 18 组配置（表1、表3、表4）。  
  - 卸载：2 个目标模型 × 2 种温度 × MT-Bench 共 4 组（表2）。  
- **消融实验**：  
  - 可扩展性：对比 Sequoia 树与 k 独立序列、单序列、二叉树在不同树大小下的生成 token 数（图1、图6）。  
  - 鲁棒性：对比 Sequoia 采样/验证与 SpecInfer、top-k 在不同温度下的接受率（图3）和最终加速比（图4右），还在不同 top-p 值下对比（表8）。  
  - 硬件感知优化：对比是否使用树优化器（图7）。  
- **公平与客观性**：  
  - 所有实验在相同硬件、相同数据集、相同树结构（除对比变量外）下进行。  
  - 树配置选择均通过硬件感知优化，避免过拟合。  
  - 对比 SpecInfer 时使用其默认树结构（5×8）并额外进行网格搜索（表5-7），表明 Sequoia 始终优于 SpecInfer 任意配置。  
- **充分性**：涵盖多模型、多数据集、多温度、多硬件场景，消融实验覆盖两个核心组件，较为充分。

### 6. 论文的主要结论与发现

- **可扩展性**：Sequoia 树期望生成 token 数随树规模对数增长（理论下界 Ω(b log n / log log n)），而 k 独立序列、单序列、二进制树均存在饱和上限。在实验规模下，Sequoia 树比 16 条独立序列多生成 33% token。
- **鲁棒性**：Sequoia 采样/验证算法在温度 0.2~1.0 范围内均保持最低拒绝率，而 SpecInfer/SpecTr 在低温下性能严重下降，top-k 在高温下较差。Sequoia 在固定树结构下相比 SpecInfer 和 top-k 分别提升最高 1.65× 和 1.27×。
- **端到端加速**：  
  - 设备端：Llama2-7B 达 4.04×，Llama2-13B 达 3.73×，Vicuna-33B 达 2.27×。  
  - 卸载：Llama3-70B-Instruct 延迟降至 0.60 s/token，比 DeepSpeed-Zero-Inference 快 9.5×。  
- **硬件感知优化**：自动选择最优树大小和深度，避免穷举搜索，在实际系统中获得额外加速。

### 7. 优点

- **理论贡献完整**：提出位置接受假设、幂律接受率假设，给出动态规划算法及可扩展性下界证明，理论分析扎实。  
- **方法论创新**：将树结构优化形式化为约束优化问题，用 DP 求解；采样/验证算法同时满足最优传输性质和覆盖性质，首次实现两者兼得。  
- **实验设计严谨**：  
  - 涵盖多种模型规模（68M~70B）、多种硬件（A100、L40）、多种推理场景（设备端、卸载）。  
  - 充分对比基线，包括对 SpecInfer 的网格搜索，排除偶然性。  
  - 消融实验分别验证树结构改进和采样验证改进的贡献。  
- **实用性**：方法可离线计算树结构，在线推理开销极低；提供代码开源，便于复现和应用。  
- **鲁棒性验证全面**：不仅报告平均加速比，还展示不同温度、top-p 下的性能，表明方法稳定。

### 8. 不足与局限

- **假设依赖性**：动态规划依赖“位置接受假设”和由少量样本估计的接受率向量，若实际分布与假设偏差较大，最优性可能下降。  
- **测量成本**：需要提前测量接受率向量（约 200 个样本），在不同模型/数据集/超参数组合下需重复测量，应用前有一定调校成本。  
- **未考虑批量推理**：实验集中于 batch size=1，未探讨多请求并发时的树结构优化（如 batch 模式下的 vLLM 等系统）。  
- **误差与统计显著性**：未报告误差棒或置信区间，结果可能存在一定随机波动，尽管通过 200 个样本平均来降低。  
- **硬件约束**：树的最大分支数 B 和深度 D 需要人为设定上限，理论上最优解可能超出设定范围。  
- **理论可扩展性下界仅依赖幂律接受率假设**：该假设在实验中观察到，但缺乏理论保证对所有模型和温度成立。

（完）
