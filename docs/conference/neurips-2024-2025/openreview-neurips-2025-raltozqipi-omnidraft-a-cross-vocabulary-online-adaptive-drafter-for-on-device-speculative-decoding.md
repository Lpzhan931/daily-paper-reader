---
title: "OmniDraft: A cross-vocabulary, online adaptive drafter for on-device speculative decoding"
title_zh: OmniDraft：用于设备端投机解码的跨词汇在线自适应猜测模型
authors: "Ramchalam Kinattinkara Ramakrishnan, Zhaocong Yuan, Shaojie Zhuo, Chen Feng, Yicheng Lin, Chenzheng Su, Xiaopeng Zhang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=RALtozQipi"
tags: ["query:llm"]
score: 8.0
evidence: 跨词汇在线自适应猜测模型用于设备端投机解码
tldr: 本文提出OmniDraft框架，使单个猜测模型能适配任意目标模型并动态适应用户数据。通过在线n-gram缓存和混合蒸馏微调解决跨词汇不匹配问题，在设备端部署场景下显著提升投机解码的速度和适应性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-raltozqipi/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1429, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-raltozqipi/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1377, \"height\": 713, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-raltozqipi/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1406, \"height\": 717, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-raltozqipi/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1376, \"height\": 714, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-raltozqipi/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1372, \"height\": 710, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-raltozqipi/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1376, \"height\": 710, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-raltozqipi/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1441, \"height\": 729, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-raltozqipi/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1552, \"height\": 1263, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-raltozqipi/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1038, \"height\": 529, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-raltozqipi/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1360, \"height\": 691, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-raltozqipi/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1452, \"height\": 364, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raltozqipi/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1451, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raltozqipi/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1456, \"height\": 733, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raltozqipi/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1103, \"height\": 202, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raltozqipi/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1455, \"height\": 469, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raltozqipi/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1454, \"height\": 372, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raltozqipi/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 554, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raltozqipi/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1403, \"height\": 226, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raltozqipi/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1000, \"height\": 148, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raltozqipi/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 525, \"height\": 499, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raltozqipi/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1451, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raltozqipi/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1101, \"height\": 181, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raltozqipi/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 726, \"height\": 366, \"label\": \"Table\"}]"
motivation: 现有猜测模型需要针对特定目标模型离线训练，无法适应在线多变的部署环境。
method: 引入在线n-gram缓存和混合蒸馏微调，使单猜测模型通用且适应数据分布变化。
result: 在多种目标模型和设备上实现一致的延迟改进。
conclusion: 统一在线自适应猜测框架可显著提升设备端解码效率。
---

## Abstract
Speculative decoding generally dictates having a small, efficient draft model that is either pretrained or distilled offline to a particular target model series, for instance, Llama or Qwen models. However, within online deployment settings, there are two major challenges: 1) usage of a target model that is incompatible with the draft model; 2) expectation of latency improvements over usage and time. In this work, we propose OmniDraft, a unified framework that enables a single draft model to operate with any target model and adapt dynamically to user data. We introduce an online n-gram cache with hybrid distillation fine-tuning to address the cross-vocabulary mismatch across draft and target models; and further improve decoding speed by leveraging adaptive drafting techniques. OmniDraft is particularly suitable for on-device LLM applications where model cost, efficiency and user customization are the major points of contention. This further highlights the need to tackle the above challenges and motivates the “one drafter for all” paradigm. We showcase the proficiency of the OmniDraft framework by performing online learning on math reasoning, coding and text generation tasks. Notably, OmniDraft enables a single Llama-68M model to pair with various target models including Vicuna-7B, Qwen2-7B and Llama3-8B models for speculative decoding; and additionally provides up to 1.5-2x speedup.

---

## 论文详细总结（自动生成）

# 论文《OmniDraft: A cross-vocabulary, online adaptive drafter for on-device speculative decoding》详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：传统的投机解码（Speculative Decoding）通常需要一个与目标模型高度对齐的小型猜测模型（draft model），该猜测模型需要针对特定目标模型系列（如Llama、Qwen）进行预训练或离线蒸馏。这导致两大挑战：
  1. **词汇不匹配**：不同目标模型使用不同的分词器和词汇表，导致猜测模型与目标模型无法直接进行投机解码。
  2. **缺乏在线自适应**：目标模型可能随用户个性化或任务切换而变化，离线训练的猜测模型无法动态适应，导致接受率下降。
- **整体含义**：为了解决上述问题，论文提出 **OmniDraft**——一个统一的投机解码框架，使单个猜测模型能够与任意目标模型配合工作，并在线上动态适应用户数据，特别适合设备端（on-device）LLM部署场景，兼顾模型成本、效率和用户定制。

## 2. 论文提出的方法论

- **核心思想**：通过引入在线n-gram缓存和混合蒸馏微调解决跨词汇不匹配，并结合自适应草稿技术进一步提升解码速度。
- **关键技术细节**：
  - **跨词汇n-gram缓存（Cross-vocabulary N-gram Cache）**：
    - 构建一个缓存 `C`，存储从猜测模型令牌序列（子词级）到目标模型令牌（完整词级）的映射，例如：`['f','la','ke']` → `'flake'`。
    - 在翻译层（translation layer）中，将猜测模型提议的多个子词令牌合并为目标词汇空间中的单个令牌，并调整其概率。
    - 采用修正的概率映射规则（公式2），确保剩余分布（residual distribution）近似正确，维持投机解码的拒绝采样机制。
  - **混合蒸馏损失（Hybrid Distillation Loss）**：
    - 对于直接映射的令牌，使用反向KL散度（reverse KL）进行监督。
    - 对于n-gram映射的令牌，使用最大对数似然（NLL）损失，并引入权重 `λ`（通常设为0.2）平衡两类令牌。
    - 整体损失：`L_cross_vocab_distill = L_DM + λ * L_N-gram`，实现在线蒸馏，使猜测模型持续对齐目标模型。
  - **在线自适应草稿（Online Adaptive Drafting）**：
    - 增加一个轻量级的接受率预测头 `f_ϕ`，以当前提议令牌的嵌入为输入，预测其被接受的概率。
    - 根据累积拒绝概率超过阈值 `γ` 来提前停止草稿生成，动态调整提议长度。
    - 提出两种训练变体：联合训练（Joint Distill + Adapt）和交错训练（Interleaved Distill + Adapt），后者通过更大的缓冲器缓解标签分布变化问题。
- **算法流程说明（文字描述）**：
  - 给定输入提示，猜测模型自回归生成 `k` 个令牌。
  - 通过n-gram缓存将猜测令牌翻译为目标词汇空间的令牌，并计算调整后的概率。
  - 目标模型并行计算这些令牌的概率，执行拒绝采样，接受部分或全部提议令牌，并生成修正令牌。
  - 将接受的目标令牌反向翻译为猜测令牌，更新上下文，并将新的n-gram映射加入缓存。
  - 使用接受的令牌和修正令牌进行在线混合蒸馏更新猜测模型，同时训练接受率预测头以动态调整草稿长度。

## 3. 实验设计

- **数据集与场景**：
  - GSM8K（数学推理）、Alpaca（指令跟随）、XSum（文本摘要）、MBPP+HumanEval（代码生成，合并使用）。
  - 每个数据集划分训练集和测试集（或从训练集中切分部分作为测试集）。
- **Benchmark**：
  - 基线方法：标准投机解码（SpD DM，直接词汇映射）、仅直接映射蒸馏（L_DM）、仅n-gram损失训练等。
  - 对比方法：`L_DM + λL_N-gram`（全量微调）、`L_DM + λL_N-gram + LoRA`（低秩适配）。
- **评估指标**：加速比（Speedup，基于墙钟时间）、接受率（Acceptance Rate，平均被接受令牌数与提议令牌数之比）。

## 4. 资源与算力

- **硬件**：单张 NVIDIA A100 GPU（40GB或80GB）。
- **软件环境**：PyTorch 2.1.0，CUDA 12.1，Ubuntu 22.04 LTS。
- **显存与计算**：训练和推理均使用同一GPU，训练步数小于1个epoch（在线学习设置）。论文未明确说明总训练时长或具体计算量，但提及每次实验在单个A100上完成。

## 5. 实验数量与充分性

- **实验组数**：论文进行了大量实验，涵盖：
  - 跨词汇在线蒸馏（表1：4个任务 × 2个目标模型 × 4种方法，共32组；加上LoRA变体）。
  - 在线自适应草稿（表2：4个任务 × 5种方法，共20组；以及LoRA变体表11）。
  - 消融实验：n-gram缓存有效性（表5：不同草稿长度）；损失函数比较（表6：温度0.01和1）；自适应草稿初始化与阈值分析（第4.3.5节）；模型规模扩展（表3：目标模型7B/14B/32B，猜测模型68M/160M）；LoRA秩消融（表12）；缓存大小与驱逐策略（表14）；数据集漂移与目标模型切换（附录）。
- **充分性与公平性**：
  - 实验覆盖了多种任务类型（数学、代码、摘要、指令）和多种模型组合（同族和跨族词汇）。
  - 对比了多种训练变体和基线，结果以平均3次不同种子的运行表示（论文声称，但主要表格未显式展示误差线）。
  - 部分消融实验（如自适应草稿阈值）报告了任务间差异，说明参数敏感性。
  - 整体上实验设计较为充分，但作者承认部分实验缺少误差条（因计算代价），且未报告所有结果的方差，可能影响统计显著性判断。

## 6. 论文的主要结论与发现

1. **跨词汇投机解码可行**：通过n-gram缓存和概率调整，即使猜测模型与目标模型词汇不同，也能实现有效的投机解码。
2. **在线蒸馏持续提升对齐**：混合蒸馏损失（`L_DM + λL_N-gram`）显著提高接受率，在GSM8K上使加速比从0.94x提升至1.70x（Llama-68M + Llama3-8B）。
3. **自适应草稿进一步加速**：在线联合或交错训练自适应草稿接受预测头，在多数任务上获得额外加速（例如GSM8K上从1.44x提升至2.15x）。
4. **单个猜测模型的通用性**：仅用68M参数的Llama模型即可与7B/8B级的目标模型（Vicuna、Qwen、Llama3）配合，实现1.5-2x加速，支持“一个猜测模型适应所有”的范式。
5. **设备端可行性**：n-gram缓存大小较小（如GSM8K仅1.372 MB），配合有效驱逐策略，适合内存受限设备。

## 7. 优点

- **创新性**：首次系统解决跨词汇投机解码的在线自适应问题，提出n-gram缓存与混合蒸馏结合的方案，并融入动态草稿长度调整。
- **实用性**：适用于边缘设备，降低部署成本；支持目标模型热切换和用户个性化，无需为每个目标单独训练猜测模型。
- **实验覆盖面广**：多任务、多模型、多训练变体，消融实验全面，验证了各组件贡献。
- **计算开销低**：n-gram缓存和轻量预测头附加开销小，在线训练仅需一次数据遍历，符合实际部署需求。

## 8. 不足与局限

1. **在线训练稳定性**：由于数据流仅单次迭代，训练可能不稳定，尤其在新分布上表现下降（如数据集漂移实验中看到短暂下降）。
2. **内存缓存限制**：n-gram缓存虽小，但随任务增长可能变大，需要优化驱逐策略；论文仅初步探索LRU和LFU。
3. **特殊令牌处理**：无直接映射的特殊令牌（如图片token）处理不够完善，限制多模态扩展。
4. **缺少误差统计分析**：主要结果未提供置信区间，影响结论的统计可靠性。
5. **自适应草稿训练挑战**：在在线设置中，预测头标签不断变化，导致收敛困难；联合训练变体可能过早退出，交错训练更优但不稳定。
6. **实验规模有限**：猜测模型最大只到160M，目标模型最大32B，更大规模下的性能尚未验证；LoRA实验显示秩增大收益递减。

（完）
