---
title: "Speculate, then Collaborate: Fusing Knowledge of Language Models during Decoding"
title_zh: 先推测后协作：解码过程中融合语言模型的知识
authors: "Ziyao Wang, Muneeza Azmat, Ang Li, Raya Horesh, Mikhail Yurochkin"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=XCBYIfu9Fs"
tags: ["query:llm-sd"]
score: 8.0
evidence: 协作式投机解码用于大语言模型知识融合
tldr: 本文提出协作式投机解码（CoSD），利用草稿模型生成初始序列，并通过易学习的决策树决定何时调用辅助模型改进草稿。该方法无需额外训练即可融合多个大语言模型的知识，同时提升推理效率，在多种任务上实现了加速和性能提升。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-xcbyifu9fs/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1621, \"height\": 587, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xcbyifu9fs/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 841, \"height\": 464, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-xcbyifu9fs/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1606, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xcbyifu9fs/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1628, \"height\": 1164, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xcbyifu9fs/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1266, \"height\": 267, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xcbyifu9fs/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1586, \"height\": 945, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xcbyifu9fs/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 853, \"height\": 183, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xcbyifu9fs/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 697, \"height\": 233, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xcbyifu9fs/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 892, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xcbyifu9fs/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1096, \"height\": 193, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xcbyifu9fs/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1426, \"height\": 726, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xcbyifu9fs/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1764, \"height\": 875, \"label\": \"Table\"}]"
motivation: 不同大语言模型各有专长，但测试时融合知识通常需要训练或降低效率。
method: 设计基于草稿模型和决策树的协作投机解码框架，动态选择辅助模型参与生成。
result: 在多个NLP数据集上，CoSD既提升了生成质量，又实现了2-3倍的推理加速。
conclusion: 投机解码框架可有效用于LLM的知识融合与推理加速。
---

## Abstract
Large Language Models (LLMs) often excel in specific domains but fall short in others due to the limitations of their training. Thus, enabling LLMs to solve problems collaboratively by integrating their complementary knowledge promises to improve their performance across domains. To realize this potential, we introduce a novel Collaborative Speculative Decoding (CoSD) algorithm that enables efficient LLM knowledge fusion at test time without requiring additional model training. CoSD employs a draft model to generate initial sequences and an easy-to-learn rule or decision tree to decide when to invoke an assistant model to improve these drafts. CoSD not only enhances knowledge fusion but also improves inference efficiency, is transferable across domains, and offers greater explainability. Experimental results demonstrate that CoSD improves accuracy by up to 10% across benchmarks compared to existing methods, providing a scalable and effective solution for LLM-based applications. Our code has been released at https://github.com/ATP-1010/CoSD.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义

- **研究动机**：不同大语言模型（LLM）在各领域表现各有优劣，单一模型难以在所有任务上达到最优。现有知识融合方法（如模型合并、知识蒸馏、混合专家）通常需要重训练或访问模型内部状态（如隐藏层），限制了实际部署。
- **核心问题**：如何在**测试时高效融合多个LLM的互补知识**，无需额外训练，同时保持推理效率与可解释性。
- **整体含义**：论文提出协作式投机解码（CoSD）算法，利用投机解码框架实现模型间知识协同，在提升准确率的同时加速推理，为多LLM协同应用提供轻量化解。

## 2. 论文提出的方法论

- **核心思想**：借鉴投机解码的“草稿-验证”范式，但将验证目标从“匹配主模型”改为“融合两个模型的知识”。草稿模型（draft model）快速生成候选序列，辅助模型（assistant model）并行验证，通过概率比较决定是否替换草稿令牌。
- **关键技术细节**：
  - **生成阶段**：草稿模型自回归生成K个令牌；辅助模型基于同一前缀并行生成候选令牌（支持不同分词器时需解码-重编码）。
  - **验证策略**：
    - **基于规则（Rule-Based CoSD）**：同时满足三个条件才替换：(a) 两个模型预测令牌不同，(b) 草稿概率小于阈值α，(c) 辅助概率大于β倍草稿概率。
    - **基于决策树（Tree-Based CoSD）**：训练一个以两个概率为输入的二元决策树，输出1表示替换，0表示保留。训练数据来自领域数据中的正确令牌对（仅保留至少一个模型预测正确的情况）。
  - **迭代机制**：一旦发生替换，丢弃后续所有草稿令牌，从替换位置重新生成草稿，重复直到结束。
- **算法流程**（文字描述）：
  1. 草稿模型自回归生成K个令牌及其概率。
  2. 辅助模型并行生成K个候选令牌及其概率。
  3. 顺次检查每个位置：若满足替换条件（规则或决策树），则替换该令牌，丢弃后续令牌，回到步骤1重新草稿生成；否则保留草稿令牌，继续下一个位置。
  4. 输出最终序列。

## 3. 实验设计

- **数据集与Benchmark**：
  - 通用问答：MMLU（使用tinyBenchmarks子集）
  - 数学推理：GSM8K（tinyBenchmarks）
  - 代码生成：HumanEval
  - 常识推理：HellaSwag（tinyBenchmarks）
  - 真实性：TruthfulQA（tinyBenchmarks）
- **实验场景**（6个模型对）：
  1. **互补知识融合**：Mistral 7B DARE vs Mistral 7B；Llama 3 Wissenschaft vs Llama 3 Bophades
  2. **灾难性遗忘恢复**：Mistral 7B vs Mistral Math 7B（微调模型）
  3. **能力不均衡**：TinyLlama vs Llama 2 Chat
  4. **不同分词器**：Llama 2 Chat vs WizardMath；Llama 2 Chat vs DeepSeek Coder
- **对比方法**：
  - 投机解码（Speculative Decoding）
  - 平均解码（Average Decoding）
  - Co-LLM（训练路由层）
  - CharED（字符级集成，仅用于不同分词器场景）
- **超参数设置**：Rule-based CoSD使用α=0.5, β=0.5（通过热力图确定）。Tree-based CoSD使用AlpacaEval数据集（3个样本）训练决策树，确保训练集与测试集不重叠。

## 4. 资源与算力

- 论文**未明确说明**使用的GPU型号、数量、训练时长等算力信息。
- 仅提及决策树训练使用“very few samples”（如AlpacaEval仅3个样本），几乎无额外计算开销；其他实验基于HuggingFace模型进行推理，未报告具体硬件配置。

## 5. 实验数量与充分性

- **实验组数**：共6个模型对×5个Benchmark=30组核心对比实验；另包含消融实验（α/β参数扫描）、决策树训练集影响实验、多模型协作实验（3个LLM）、效率测量实验等。
- **充分性与公平性**：
  - 覆盖了四种典型现实场景（互补知识、灾难性遗忘、能力不均衡、不同分词器），具有较强代表性。
  - 对比方法包括经典投机解码、平均集成、可训练路由方法（Co-LLM），基线选择合理。
  - 使用tinyBenchmarks加速评估，但可能降低统计显著性；未报告置信区间或多次重复实验。
  - 决策树训练集与测试集不重叠，验证了跨域迁移性，但训练样本极少（3-10个），可能依赖随机性。
- **总体评价**：实验设计系统，场景覆盖全面，但部分基准（如HumanEval）采样数量有限，统计稳健性可进一步强化。

## 6. 论文的主要结论与发现

- **性能提升**：CoSD在所有场景下均优于或持平最佳基线。互补知识融合中，平均准确率提升最高达10%（如Pair1平均分52.41 vs 基线50.90）。
- **灾难性遗忘恢复**：CoSD-Rule在所有任务上恢复甚至超过原始模型（如MMLU从61.45提升至62.41，GSM8K从25.01提升至45.47）。
- **不同分词器场景**：CoSD显著优于CharED（如Pair5 MMLU 50.65 vs 44.29）。
- **效率**：相比单独使用投机解码，CoSD仅增加少量延迟（如Pair3中131ms → 132ms），但知识融合效果显著提升。
- **可迁移性**：基于规则的CoSD超参数（α=0.5,β=0.5）在不同模型对和任务中表现稳定；决策树训练数据若与目标域匹配，效果略有提升。
- **可解释性**：规则和决策树均为白盒模型，便于理解与调试。

## 7. 优点

- **无需训练**：基于规则的CoSD完全无需额外训练，决策树训练仅需极少量样本，实用性强。
- **效率高**：利用投机解码并行验证，推理速度快于逐token集成，且仅需模型概率输出（无需隐藏状态），兼容API调用。
- **跨模型/分词器兼容**：支持不同架构、不同分词器的模型融合，扩展了应用范围。
- **可解释性强**：验证规则或决策树直观透明，便于用户调试和信任。
- **场景覆盖广**：在互补知识、灾难性遗忘、能力不均衡等四种典型场景均有效。

## 8. 不足与局限

- **依赖概率可靠性**：假设高概率对应高正确率，但模型可能对错误答案过度自信，导致替换后效果变差（论文在案例分析中承认此问题）。
- **弱模型主导局限**：若两个模型能力悬殊且强模型远优于弱模型，CoSD无额外增益，用户需事先了解模型相对优势。
- **统计稳健性**：基于tinyBenchmarks的少量样本评估可能引入噪声，未提供置信区间或多次重复实验。
- **决策树训练**：训练数据量极少，且仅使用两个概率作为特征，可能无法捕捉更复杂的分布差异；未与更复杂的分类器（如MLP）对比。
- **多模型扩展**：仅实验了三个模型，更多模型时验证复杂度线性增长，未提供优化策略。
- **理论分析缺失**：未提供收敛性、最优替换策略的理论保证，主要依赖实验验证。

（完）
