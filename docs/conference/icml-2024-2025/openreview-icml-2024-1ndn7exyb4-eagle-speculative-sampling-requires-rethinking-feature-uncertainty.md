---
title: "EAGLE: Speculative Sampling Requires Rethinking Feature Uncertainty"
title_zh: EAGLE：投机采样需要重新思考特征不确定性
authors: "Yuhui Li, Fangyun Wei, Chao Zhang, Hongyang Zhang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=1NdN7eXyb4"
tags: ["query:llm"]
score: 9.0
evidence: 面向LLM的投机采样框架EAGLE
tldr: 针对LLM自回归解码耗时的问题，本文重新审视投机采样并提出EAGLE框架。通过将自回归移至特征层（次顶层）并引入提前一步的token序列解决特征不确定性，从而以极小开销实现精确特征预测。实验表明EAGLE在多种LLM上取得显著的推理加速，且不改变输出分布。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-1ndn7exyb4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1759, \"height\": 599, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-1ndn7exyb4/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 844, \"height\": 389, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-1ndn7exyb4/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 812, \"height\": 277, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-1ndn7exyb4/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 807, \"height\": 245, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-1ndn7exyb4/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 837, \"height\": 291, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-1ndn7exyb4/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 603, \"height\": 573, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-1ndn7exyb4/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 831, \"height\": 941, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-1ndn7exyb4/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 850, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-1ndn7exyb4/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1708, \"height\": 869, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-1ndn7exyb4/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1682, \"height\": 628, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-1ndn7exyb4/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 862, \"height\": 552, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-1ndn7exyb4/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 861, \"height\": 509, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-1ndn7exyb4/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 835, \"height\": 151, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-1ndn7exyb4/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 883, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-1ndn7exyb4/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 863, \"height\": 275, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-1ndn7exyb4/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 782, \"height\": 193, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-1ndn7exyb4/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 859, \"height\": 161, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-1ndn7exyb4/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1748, \"height\": 592, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-1ndn7exyb4/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1374, \"height\": 918, \"label\": \"Table\"}]"
motivation: token级自回归效率低，特征级自回归存在不确定性。
method: 在次顶层特征进行自回归预测，利用提前一步的token序列消除不确定性。
result: 在多种LLM上实现显著加速，且保持输出分布不变。
conclusion: EAGLE通过特征级投机采样实现了高效且无损的LLM加速。
---

## Abstract
Autoregressive decoding makes the inference of Large Language Models (LLMs) time-consuming. In this paper, we reconsider speculative sampling and derive two key observations. Firstly, autoregression at the feature (second-to-top-layer) level is more straightforward than at the token level. Secondly, the inherent uncertainty in feature (second-to-top-layer) level autoregression constrains its performance. Based on these insights, we introduce EAGLE (Extrapolation Algorithm for Greater Language-model Efficiency), a simple yet highly efficient speculative sampling framework. By incorporating a token sequence advanced by one time step, EAGLE effectively resolves the uncertainty, enabling precise second-to-top-layer feature prediction with minimal overhead. We conducted comprehensive evaluations of EAGLE, including all models from the Vicuna and LLaMA2-Chat series, the MoE model Mixtral 8x7B Instruct, and tasks in dialogue, code generation, mathematical reasoning, and instruction following. For LLaMA2-Chat 70B, EAGLE achieved a latency speedup ratio of **2.7x-3.5x**, doubled throughput, while maintaining the distribution of the generated text.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **问题**：大型语言模型（LLM）采用自回归解码，每个 token 一次前向传播，导致推理速度慢、计算成本高。
- **已有方法**：投机采样（Speculative Sampling）通过一个小型草稿模型快速生成多个候选 token，再由目标 LLM 并行验证，可在保持输出分布不变的前提下提升速度。
- **关键发现**：
  - 在特征层（即第二到顶层，LM Head 前一层的隐藏状态）进行自回归比在 token 层更简单、更规律。
  - 特征级自回归存在**不确定性**：由于采样随机性，相同的上文可能产生不同的 token，进而导致不同的后续特征序列，使得预测下一个特征变得困难。
- **论文目标**：提出 EAGLE（Extrapolation Algorithm for Greater Language-model Efficiency）框架，通过引入“提前一步的 token 序列”来消除特征不确定性，实现高效、无损的投机采样加速。

## 2. 方法论：核心思想与关键技术细节

- **核心思想**：
  - 在特征层进行自回归预测，而不是直接预测 token。
  - 将采样结果（即已生成的 token）作为草稿模型的输入，从而告诉模型“前面采样了什么”，消除特征不确定性。
- **草稿模型架构**：
  - 输入：特征序列（从目标 LLM 获取）和提前一步的 token 序列。
  - 流程：token 经过 Embedding 层（复用目标 LLM）得到嵌入，与特征拼接成 2×hidden_dim 向量，经 FC 层降维，再送入一个 Decoder Layer（单层 Transformer 解码器）预测下一个特征。
  - 预测的特征通过 LM Head（复用目标 LLM）得到分布并采样下一个 token。
- **训练**：
  - 目标：回归损失（Smooth L1 预测特征）+ 分类损失（交叉熵预测 token 分布），加权联合训练（w_cls=0.1）。
  - 数据增强：在训练时给特征添加均匀噪声 U(-0.1,0.1) 以提升对特征错误的鲁棒性。
- **草稿生成**：使用树注意力（Tree Attention）在一次前向中生成树状草稿（深度 5，共 10 个 token），通过多次前向扩展得到更多候选。
- **验证阶段**：目标 LLM 对树状草稿进行单次前向，采用多轮投机采样（Multi-round Speculative Sampling）逐节点判定接受或重采样，保证输出分布与原始 LLM 一致。

## 3. 实验设计

- **数据集与场景**：
  - MT-bench（多轮对话，主要基准）
  - HumanEval（代码生成）
  - GSM8K（数学推理）
  - Alpaca（指令跟随）
- **模型系列**：
  - Vicuna 7B/13B/33B
  - LLaMA2-Chat 7B/13B/70B
  - Mixtral 8x7B Instruct（MoE）
- **对比方法**：
  - Vanilla（标准自回归解码）
  - Speculative Sampling（使用同系列小模型作为草稿）
  - DistillSpec（知识蒸馏改进）
  - Lookahead（n-gram + Jacobi 迭代）
  - Medusa（多个 MLP 头预测未来 token）
- **评测指标**：加速比（Walltime speedup）、平均接受长度 τ、接受率 α。仅在保证输出分布不变的方法间公平比较。

## 4. 资源与算力

- **训练数据**：ShareGPT 数据集，约 68,000 条对话。
- **训练时长**：1-2 天。
- **硬件配置**：
  - 70B 模型：4×A100 (40G) GPU
  - 7B/13B/33B 模型：单张 RTX 3090 即可训练
- **草稿模型参数量**：
  - 7B → 0.24B，13B → 0.37B，33B → 0.56B，70B → 0.99B，Mixtral 8x7B → 0.28B
- **推理硬件**：主要实验 batch size=1 的单 GPU 设置，部分实验结合 gpt-fast（量化 + 编译）在单张 RTX 3090 上运行。

## 5. 实验数量与充分性

- **实验数量**：非常充分。
  - 覆盖 7 种模型（含 MoE）、4 个数据集、2 种温度设置（0 和 1）。
  - 对比了 4 种基线方法（Speculative Sampling, DistillSpec, Lookahead, Medusa）。
  - 消融实验包括：树注意力 vs 链式、不同输入特征（token/feature/feature+unshifted-token/feature+shifted-token）、训练数据来源（固定数据集 vs 目标 LLM 生成）。
  - 附加实验：结合 gpt-fast 加速、不同 batch size 下的加速比和吞吐量。
- **公平性与客观性**：
  - 所有对比均在相同基准 MT-bench 上，且报告了 Lookahead/Medusa 原文数据。
  - EAGLE 保证输出分布不变，因此无需评估生成质量，仅测速度。
  - 消融实验设计合理，验证了各组件贡献。

## 6. 主要结论与发现

- **加速效果**：
  - 在 MT-bench 上，贪婪解码（T=0）加速比 2.1x–3.8x，非贪婪（T=1）加速比 2.1x–2.9x。
  - 对比 Lookahead 快 1.7x–2.1x，对比 Medusa 快 1.5x–1.6x。
  - 70B 模型达 2.7x–3.5x 加速，吞吐量翻倍。
- **平均接受长度**：3.2–4.5 个 token/前向。
- **代码生成任务**（HumanEval）加速效果最好，因代码模板固定。
- **与 gpt-fast 结合**：LLaMA2-Chat 7B 在单张 RTX 3090 上可达 160.4 tokens/s。
- **MoE 模型**：Mixtral 8x7B 加速比 1.5x，相对较低，因验证阶段需更多专家。
- **鲁棒性**：接受率随特征错误累积下降缓慢（0-α 到 4-α 差异小），表明 EAGLE 对特征误差不敏感。

## 7. 优点

- **方法简洁高效**：仅添加一个轻量级 Decoder Layer，训练成本低（1-2 天），参数少（<0.1B–1B）。
- **通用性强**：适用于任意自回归 LLM（至少理论上），无需 fine-tune 原始模型。
- **可靠性高**：严格保持输出分布不变（理论保证），无额外风险。
- **兼容性好**：可与量化、编译等其他加速技术并行使用。
- **消融实验充分**：清晰验证了特征级自回归、提前一步 token、树注意力等关键组件的有效性。

## 8. 不足与局限

- **MoE 模型加速有限**：对于 Mixtral 8x7B 仅 1.5x，因稀疏架构导致验证阶段计算效率下降。
- **显存开销略高**：树注意力和草稿模型占用更多显存，最大批处理大小略低于 vanilla（例如 7B 模型：vanilla 最大 bs=8，EAGLE 最大 bs=7）。
- **树结构未严格优化**：实验中使用的树结构基于直觉（高概率分支更深更宽），未进行系统调优，可能不是最优。
- **非贪婪设置加速较低**：由于采样随机性增加，接受率下降，加速比低于贪婪设置。
- **训练仍需特定数据**：虽然对训练数据不敏感，但依然需要 ShareGPT 等对话数据进行训练，对于封闭模型可能不适用。
- **可扩展性**：对于超大规模模型（如 200B+），草稿模型的训练成本可能仍然较高。

（完）
