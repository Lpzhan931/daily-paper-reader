---
title: List-Level Distribution Coupling with Applications to Speculative Decoding and Lossy Compression
title_zh: 列表级分布耦合及其在投机解码和损失压缩中的应用
authors: "Joseph Rowan, Buu Phan, Ashish J Khisti"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=GJbrk55Bt8"
tags: ["query:llm-sd"]
score: 7.0
evidence: 列表级分布耦合用于投机解码
tldr: 本文研究分布耦合问题的松弛版本，提出列表级分布耦合方法，并证明了下界引理。将该方法应用于投机解码，实现了多草稿投机采样，性能与现有基线相当且实现简单。此外，还将其应用于损失压缩。该工作为投机解码提供了新的理论视角和实用工具，特别是对多草稿场景有重要价值。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-gjbrk55bt8/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1371, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gjbrk55bt8/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 397, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gjbrk55bt8/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 463, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gjbrk55bt8/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 757, \"height\": 480, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gjbrk55bt8/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1452, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gjbrk55bt8/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 803, \"height\": 449, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1456, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1456, \"height\": 370, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 773, \"height\": 2353, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 831, \"height\": 2368, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1448, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1447, \"height\": 367, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1215, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1213, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1091, \"height\": 349, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 611, \"height\": 581, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 615, \"height\": 582, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 611, \"height\": 582, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 612, \"height\": 581, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 621, \"height\": 500, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 624, \"height\": 499, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 621, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 621, \"height\": 499, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 619, \"height\": 497, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 623, \"height\": 500, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 623, \"height\": 498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gjbrk55bt8/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 621, \"height\": 497, \"label\": \"Table\"}]"
motivation: 现有分布耦合方法在投机解码应用中存在局限性，需要更灵活的列表级耦合。
method: 扩展Gumbel-max采样实现列表级分布耦合，并建立列表匹配引理，应用于多草稿投机采样。
result: 在投机解码任务中达到与现有方法竞争的性能，同时支持多草稿场景。
conclusion: 列表级分布耦合是投机解码的一个有效理论框架，可推广到其他领域。
---

## Abstract
We study a relaxation of the problem of coupling probability distributions — a list of samples is generated from one distribution and an *accept* is declared if any one of these samples is identical to the sample generated from the other distribution.
We propose a novel method for generating samples, which extends the Gumbel-max sampling suggested in Daliri et al. (2025) for coupling probability distributions. We also establish a corresponding lower bound on the acceptance probability, which we call the *list matching lemma*.
We next discuss two applications of our setup.
First, we develop a new mechanism for multi-draft speculative sampling that is simple to implement and achieves performance competitive with baselines such as SpecTr and SpecInfer across a range of language tasks.
Our method also guarantees a certain degree of *drafter invariance* with respect to the output tokens which is not supported by existing schemes.
We also provide a theoretical lower bound on the token level acceptance probability.
As our second application, we consider distributed lossy compression with side information in a setting where a source sample is compressed and available to multiple decoders, each with independent side information.
We propose a compression technique that is based on our generalization of Gumbel-max sampling and show that it provides significant gains in experiments involving synthetic Gaussian sources and the MNIST image dataset.

---

## 论文详细总结（自动生成）

以下是基于论文 *List-Level Distribution Coupling with Applications to Speculative Decoding and Lossy Compression* 的详细中文总结：

---

### 1. 论文的核心问题与整体含义

- **研究动机**：传统分布耦合问题中，两个分布各生成一个样本，目标是最大化两者相等的概率（即最大耦合）。但在许多实际场景（如投机解码、分布式压缩）中，通信受限，双方不能直接获知对方分布，只能利用公共随机性进行协调采样。
- **松弛问题**：本文考虑一个变体：一方（Alice）从分布 \(p_X\) 生成 \(K\) 个样本（列表），另一方（Bob）从 \(q_Y\) 生成一个样本；若 Bob 的样本出现在 Alice 的列表中，则认为匹配成功。目的是在无通信前提下最大化该匹配概率。
- **整体意义**：论文提出一种新颖的 Gumbel-max 列表采样（GLS）方法，并建立列表匹配引理（LML）作为下界。该方法被成功应用于两个领域：多草稿投机解码（加速大模型推理）和分布式有损压缩（带边信息的多解码器场景），具有理论优雅性和实际竞争力。

---

### 2. 方法论

#### 2.1 核心思想
- **Gumbel-max 列表采样（GLS）**：共享 \(K\) 组 i.i.d. 指数分布随机变量 \(\{S^{(k)}_i\}\)，其中 \(S^{(k)}_i \sim \text{Exp}(1)\)。
- **采样规则**：
  - Bob 根据目标分布 \(q_Y\) 采样：\(Y = \arg\min_{1\le i\le N} \min_{1\le k\le K} S^{(k)}_i / q_i\)。
  - Alice 根据草稿分布 \(p_X\) 采样：\(X^{(k)} = \arg\min_{1\le i\le N} S^{(k)}_i / p_i\)，\(k=1,\dots,K\)。
- **匹配概率下界（列表匹配引理）**：
  \[
  \Pr[Y \in \{X^{(1)},\dots,X^{(K)}\}] \ge \sum_{j=1}^N \frac{K}{\sum_{i=1}^N [\max\{q_i/q_j, p_i/p_j\} + (K-1)q_i/q_j]}.
  \]
  条件化版本：\(\Pr[Y=j \text{匹配}|Y=j] \ge (1 + q_j/(K p_j))^{-1}\)。

#### 2.2 关键技术细节
- **多草稿投机解码应用**：
  - 算法 2 在每一解码步骤使用 GLS 耦合目标模型 \(M_b\) 和 \(K\) 个草稿模型 \(M_s\) 的分布，从当前活跃草稿集合中选取输出 token。
  - 证明该算法满足 **条件性草稿不变性**：给定相同的草稿 token 序列（无论由哪个草稿模型生成），输出分布完全相同。
  - 提供 token 级别接受概率的理论下界（命题 2）。
- **有损压缩应用**：
  - 编码器根据源 \(A\) 和 \(K\) 个解码器的独立边信息 \(T_k\)，选择索引 \(Y\) 并发送消息 \(\ell_Y\)（共 \(R = \log L_{\max}\) 比特）。
  - 解码器 \(k\) 利用边信息 \(T_k\) 和消息 \(\ell_j\)，通过 GLS 从 \(p_{W|T}\) 采样 \(X^{(k)}\)。
  - 利用条件 LML（定理 2）给出误差上界：\(\Pr[\text{error}] \le 1 - \mathbb{E}_{A,W,T}\left[ (1 + 2^{i(W;A|T)} / (K L_{\max}))^{-1} \right]\)，其中 \(i\) 为条件信息密度。
  - 通过重要性采样扩展到连续分布（附录 C），实现近似采样。

---

### 3. 实验设计

- **投机解码**：
  - **目标模型**：Qwen 2.5-7B；**草稿模型**：Qwen 2.5-0.5B（i.i.d. 草稿）；Llama 2-68M / Llama 3-1B（多样性实验）。
  - **数据集**：GSM8K、HumanEval、NaturalReasoning、MBPP、DROP。
  - **基准方法**：单草稿投机解码、SpecInfer、SpecTr、Daliri et al. (单草稿不变性方法)。
  - **评估指标**：块效率（BE，每次迭代接受 token 数）、令牌率加速比（相对单草稿的百分比）。
  - **配置**：草稿长度 \(L=4\)（i.i.d.）、\(L=5\)（多样性）；草稿数 \(K=2,4,6,8\)；温度变化（0.5-2.0）。
- **有损压缩**：
  - **合成高斯源**：\(A\sim\mathcal{N}(0,1)\)，\(T_k = A+\zeta\)，\(\sigma^2_{T|A}=0.5\)；通过改变 \(L_{\max}\) 控制速率，优化 \(\sigma^2_{W|A}\)。
  - **MNIST/CIFAR-10 图像压缩**：源为右半图像，边信息为左半随机 crop（MNIST 7×7，CIFAR-10 16×16）；使用 β-VAE 编码/解码器网络。
  - **基准方法**：基线方案（所有解码器共享同一组随机数，即 K=1 的 GLS）。
  - **评估**：匹配概率、均方误差（MSE）随速率变化曲线；对 K=1,2,3,4 分别测试。
- **额外分析**：随机 toy 分布对比（N=10 元素，K 从 1 到 20）；ROUGE 评分评估解码一致性消融（证明草稿不变性带来的稳定输出）。

---

### 4. 资源与算力

- **投机解码**：单块 NVIDIA RTX6000 Ada（48GB VRAM），每个配置（数据集+算法）约 1 小时。
- **合成高斯压缩**：NVIDIA Tesla T4（16GB），每轮完整实验（含多次随机种子和参数扫描）约 4 小时。
- **MNIST 压缩**：NVIDIA Tesla T4，β-VAE 训练 30 epoch 约 45 分钟；测试优化阶段每实例约 6 小时（含 5 次重复）。
- **CIFAR-10 压缩**：使用相同硬件，训练和测试时间类似。
- **总计算量**：未明确给出总量，但属于中等规模，可利用多 GPU 横向扩展。

---

### 5. 实验数量与充分性

- **投机解码**：
  - 5 个数据集 × 多种 K（2/4/6/8） × 多种温度组合，每个配置重复 5 次并报告标准误。
  - 包含 i.i.d. 草稿、多样草稿、强不变性变体对比。
  - 额外消融：ROUGE 一致性测试（200 个 prompt × 4 种子）。
  - 随机 toy 分布验证（100 实例）。
- **有损压缩**：
  - 高斯源：6 种速率（\(L_{\max}=2^1\) 到 \(2^6\)）× 4 种 K × 10 次重复。
  - MNIST：5 种速率 × 4 种 K × 5 次重复，参数网格搜索（\(N=2^7\)~\(2^{12}\)，β=0.15~0.95）。
  - CIFAR-10：类似规模。
- **充分性评价**：实验全面覆盖主要变量，报告了无偏估计的标准误差，对比了最强基线（SpecInfer、SpecTr、单草稿）。草稿不变性的消融实验增强了可信度。实验设计客观、公平，所有方法基于相同硬件和推理库。

---

### 6. 论文的主要结论与发现

1. **GLS 方法是有效的分布耦合工具**：其匹配概率下界在大 K 时趋于 1，并能在特殊情况下达到精确值。
2. **多草稿投机解码**：GLS 方法在块效率上与 SpecInfer/SpecTr 相当，且具备条件性草稿不变性（现有方法不具备）。在多样草稿、温度不匹配场景下，GLS 优于 SpecInfer。
3. **分布式有损压缩**：GLS 方案在合成高斯和 MNIST 任务中，随解码器数 \(K\) 增加显著降低失真，优于基线（尤其是低速率区域）。
4. **理论支撑**：列表匹配引理（LML）和条件 LML 提供了可证明的接受概率或误差下界，紧密贴合实际表现。

---

### 7. 优点

- **方法创新且简洁**：基于 Gumbel-max 的直观扩展，无复杂计算；伪代码清晰易实现。
- **理论坚实**：给出解析下界，且实验验证下界紧性。
- **草稿不变性**：首次在多草稿投机解码中实现条件性草稿不变性，保证输出分布与草稿模型解耦，增强鲁棒性和可重复性。
- **应用广泛**：适用于 i.i.d. 和多样草稿、离散和连续分布（通过重要性采样）。
- **实验规范**：详细描述硬件、超参数、重复次数、误差报告，确保可复现性。

---

### 8. 不足与局限

- **投机解码局限**：
  - 大型词汇表下需 top-K 剪枝降低内存和计算（实验中使用 151,936 词表，仍可处理但资源消耗大）。
  - 强不变性（附录 B）会显著降低性能，本文只提供条件性不变性。
  - 草稿与目标严重不对齐时，加速效果可能不显著。
- **压缩局限**：
  - 需要共享随机数种子（通常可提前约定并分摊成本），且要求编码器/解码器数值计算完全确定（浮点一致性）。
  - 目前仅验证中等尺度 MNIST/CIFAR-10，未扩展到高分辨率图像或更复杂源模型。
- **实验覆盖**：
  - 投机解码仅在 Qwen/Llama 系列模型上测试，未涵盖更多架构或更大规模（如 70B+）。
  - 压缩部分未与其他经典 Wyner-Ziv 或深度学习压缩方法（如 DVC）直接对比，仅与同框架基线对比。
- **泛化性**：GLS 在连续分布上仅通过重要性采样近似，尚未严格证明收敛性，依赖有限样本 N。

---

（完）
