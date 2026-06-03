---
title: "BanditSpec: Adaptive Speculative Decoding via Bandit Algorithms"
title_zh: BanditSpec：基于Bandit算法的自适应投机解码
authors: "Yunlong Hou, Fengzhuo Zhang, Cunxiao Du, Xuan Zhang, Jiachun Pan, Tianyu Pang, Chao Du, Vincent Y. F. Tan, Zhuoran Yang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=ghkWIlliZ8"
tags: ["query:llm"]
score: 9.0
evidence: 基于bandit算法的自适应投机解码超参数选择
tldr: 投机解码性能依赖超参数配置，现有方法固定或需训练。BanditSpec将超参数选择建模为多臂赌博机问题，提出UCBSpec等在线学习算法，无需训练即可自适应调整，实验表明在多种模型和任务上优于固定配置，提升解码速度。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ghkwilliz8/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 832, \"height\": 558, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ghkwilliz8/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 861, \"height\": 453, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ghkwilliz8/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 844, \"height\": 809, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ghkwilliz8/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1742, \"height\": 903, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ghkwilliz8/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1382, \"height\": 561, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ghkwilliz8/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1739, \"height\": 352, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ghkwilliz8/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 578, \"height\": 562, \"label\": \"Table\"}]"
motivation: 投机解码超参数固定或需额外训练，缺乏在线自适应能力。
method: 将超参数选择建模为多臂赌博机问题，提出UCBSpec等算法在线调整。
result: 无需训练即可自适应选择最优配置，解码速度优于固定方法。
conclusion: BanditSpec为投机解码提供训练-free的在线自适应方案。
---

## Abstract
Speculative decoding has emerged as a popular method to accelerate the inference of Large Language Models (LLMs) while retaining their superior text generation performance. Previous methods either adopt a fixed speculative decoding configuration regardless of the prefix tokens, or train draft models in an offline or online manner to align them with the context. This paper proposes a training-free online learning framework to adaptively choose the configuration of the hyperparameters for speculative decoding as text is being generated. We first formulate this hyperparameter selection problem as a Multi-Armed Bandit problem and provide a general speculative decoding framework BanditSpec. Furthermore, two bandit-based hyperparameter selection algorithms, UCBSpec and EXP3Spec, are designed and analyzed in terms of a novel quantity, the stopping time regret. We upper bound this regret under both  stochastic and adversarial reward settings. By deriving an information-theoretic impossibility result, it is shown that the regret performance of UCBSpec is optimal up to universal constants. Finally, extensive empirical experiments with LLaMA3 and Qwen2 demonstrate that our algorithms are effective compared to existing methods, and  the throughput is close to the oracle best hyperparameter in simulated real-life LLM serving scenarios with diverse input prompts.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：大型语言模型（LLM）的自回归解码过程耗时严重，投机解码（Speculative Decoding）通过草稿模型快速生成候选 token 再由目标模型验证的方式加速推理，但其性能高度依赖超参数配置（如草稿模型、推测长度、树结构等）。现有方法要么固定配置（忽略上下文变化），要么需要离线或在线训练草稿模型，缺乏一种 **无需训练、在线自适应** 的通用超参数选择方案。
- **整体含义**：本文提出将投机解码中的超参数选择问题形式化为 **多臂赌博机（Multi-Armed Bandit, MAB）** 问题，通过在线学习的方式动态选择最优配置，从而在无需额外训练的情况下显著提升解码速度，且理论证明其遗憾界最优。

#### 2. 方法论
- **核心思想**：将每轮投机解码视为一次“拉臂”操作，每个候选超参数配置对应一个臂，臂的奖励定义为该轮生成的接受 token 数量。目标是使总解码轮数（停止时间）最小化，即最小化“停止时间遗憾”（stopping time regret）。
- **关键技术细节**：
  - **形式化建模**：提出通用框架 **BanditSpec**，将超参数选择问题转化为 MAB 问题。给定初始提示 `pt`、目标模型 `P`、候选超参数集 `S={S_i}` 和最大推测长度 `L`，算法以历史信息 `H_{t-1}` 为基础选择臂 `I_t`，执行投机解码子程序得到接受 token 序列，更新提示和历史。
  - **随机奖励场景**（接受 token 数量具有稳定均值）：设计 **UCBSpec** 算法，基于 UCB1 思想，采用自归一化的置信区间（self-normalized confidence bounds）来适应非独立同分布的奖励，并重新设计置信半径和停止规则。理论上给出了 `O(H·L² log E[len])` 的遗憾上界（H为问题难度参数），并通过信息论下界证明其最优性（与常数和L因子匹配）。
  - **对抗奖励场景**（接受 token 数量可能任意变化）：设计 **EXP3Spec** 算法，基于 EXP3 思想，使用自适应学习率序列以适应未知的停止时间。理论上给出了 `O(L·√(E[len]·K log K))` 的遗憾上界，及实例相关的 `O(L²K log K + L·√(min_i ST(ALG_i)·K log K))` 界。
- **算法流程**（文字说明）：
  - 初始化：提示 `pt_0`，历史 `H_0` 为空。
  - 循环直到生成 `<EOS>` token：
    1. 根据历史选择超参数索引 `I_t`（前K轮轮询，之后由 UCB/EXP3 规则决定）。
    2. 用所选超参数 `S_{I_t}` 执行投机解码子程序，得到接受 token 序列 `x_{I_t,t}`。
    3. 更新提示 `pt_t` 和历史 `H_t`。
    4. 更新算法内部统计量（对 UCB 更新均值、置信半径；对 EXP3 更新概率分布）。

#### 3. 实验设计
- **数据集/场景**：
  - **场景一（选择不同草稿模型）**：使用 SpecBench、Alpaca、Code Editor、Debug Bench 四个基准，涵盖多主题对话、代码编辑、代码调试等任务。
  - **场景二（选择不同推测长度）**：使用 Alpaca 作为测试集，模拟真实 LLM 服务环境（多种输入提示、不同 batch size 1~50），通过率测量（token/s）。
- **Benchmark 与方法**：
  - 目标模型：LLaMA3-8B-Instruct、Qwen2-7B-Instruct；附加实验使用 LLaMA-2-13B。
  - 对比方法：Vanilla（无投机）、PLD（检索）、REST（检索）、Suffix Tree（模型无关）、Eagle-2（参数量小的草稿模型），以及非适应性固定超参数方法。
  - 度量指标：平均接受 token 数（MAT）、吞吐量（Tokens/s）。
- **对比方式**：
  - 在主实验中，每个方法在所有提示上固定使用同一超参数；而 BanditSpec 方法可每轮自适应选择。
  - 在推测长度实验中，对比固定长度（γ=0~4）和 oracle 最优（hindsight最优）以及 worst-case 固定长度。

#### 4. 资源与算力
- 文中明确提到：主要实验在 **单张 NVIDIA A100 GPU** 上进行，batch size 设置为 1。
- 此外，另有一组附加实验在 **GeForce RTX 4090** 上运行以验证硬件无关性。
- **未明确说明训练时长**：由于 BanditSpec 是训练-free 方法，仅需在线推理，因此不涉及训练时长。实验耗时未给出具体数值，但提到每个数据集/方法的吞吐量通过多次运行取平均（16次独立运行以平滑硬件噪声）。

#### 5. 实验数量与充分性
- **实验组数**：
  - 场景一：覆盖4个数据集，2种目标模型，7种方法（含2种本文方法），共 4×2×7 = 56 组比较（加上附加模型 LLaMA-2-13B 和 RTX4090 各若干组）。
  - 场景二：在 Alpaca 上模拟 500 个样本，batch size 从1到50变化，每次结果取16次平均，对比固定长度与 oracle。
  - 此外还报告了内存利用率（Normalized Memory）、更大模型（13B）和不同硬件（4090）的补充实验。
- **充分性评价**：实验设计较为充分，覆盖了多样化的任务（对话、代码编辑、调试）、不同规模的目标模型（7B/8B/13B）和不同硬件（A100/4090）。对比方法包括多种主流的固定/非适应性方法，并采用了两个广泛使用的度量指标。消融实验上，还额外对比了随机奖励与对抗奖励假设下的算法表现，验证了实际场景更接近随机假设。总体而言，实验客观、公平，能有效支撑论文结论。

#### 6. 主要结论与发现
- BanditSpec 框架能够 **无需训练** 地自适应选择投机解码超参数，显著提高解码速度，在多个基准上 MAT 和 Token/s 均超越所有固定配置方法。
- UCBSpec 在实际场景中表现优于 EXP3Spec，说明真实 LLM 推理的接受 token 数量更接近随机奖励假设（稳定均值）而非对抗奖励。
- 在推测长度自适应场景中，BanditSpec 的吞吐量接近 **oracle 最优固定长度**，并大幅超过次优固定长度。
- 理论分析证明了 UCBSpec 在上界和下界上均达到最优（至多相差常数因子），EXP3Spec 也提供了有效的遗憾保证。

#### 7. 优点
- 方法创新性：将投机解码超参数选择与多臂赌博机理论结合，提出训练-free 在线自适应框架，具有较强的通用性。
- 理论深度：给出了停止时间遗憾的严格上界和下界，并证明算法最优性，填补了该领域理论分析的空白。
- 实验全面：覆盖多种模型、任务、硬件，对比方法丰富，并设计了模拟真实服务场景的吞吐量实验。
- 实用性强：无需额外训练或微调，直接利用现有投机解码方法作为子程序，部署简单，且在多种场景下均获得加速。
- 算法简洁：UCBSpec 和 EXP3Spec 均易于实现，计算开销小，符合加速推理的初衷。

#### 8. 不足与局限
- 实验覆盖的模型规模有限：主要为 7B/8B/13B，未涉及 70B 及以上更大模型，尽管方法理论上可扩展，但缺乏更大规模的验证。
- 在推测长度场景中，仅使用 Eagle-1 作为草稿模型（因 Eagle-2 不支持 batch 推理），可能限制了泛化性。
- 实验中的批量大小设置未涵盖非常大（如 >50）的批量，真实生产环境可能存在不同特征。
- 虽然理论证明了随机奖励假设下的最优性，但实际场景中的非平稳性（接受 token 均值随时间变化）未深入探讨，未来可拓展到非平稳赌博机。
- 部分数据集（如 SpecBench）的响应较短，可能限制 arm 拉动次数，论文虽用 Mixture-of-Agent 延长但未详细分析影响。
- 未与其他在线自适应方法（如 SpecDec++）进行直接比较（因 SpecDec++ 需要训练且模型不同），对比不够全面。

（完）
