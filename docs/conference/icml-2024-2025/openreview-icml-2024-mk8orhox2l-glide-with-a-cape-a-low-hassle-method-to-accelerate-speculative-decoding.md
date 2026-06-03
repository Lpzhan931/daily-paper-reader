---
title: "GliDe with a CaPE: A Low-Hassle Method to Accelerate Speculative Decoding"
title_zh: GliDe with a CaPE：一种低干扰的投机解码加速方法
authors: "Cunxiao Du, Jing Jiang, Xu Yuanchen, Jiawei Wu, Sicheng Yu, Yongqi Li, Shenggui Li, Kai Xu, Liqiang Nie, Zhaopeng Tu, Yang You"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=mk8oRhox2l"
tags: ["query:llm"]
score: 8.0
evidence: 加速投机解码的改进方法
tldr: 本文提出两种低干扰的投机解码改进：GliDe通过重用目标LLM的KV缓存设计草稿模型架构，CaPE利用草稿模型置信度扩展候选token。两种方法均无需修改目标模型，显著降低解码延迟，实验验证了有效性和实际加速效果。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-mk8orhox2l/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 844, \"height\": 267, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mk8orhox2l/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 863, \"height\": 368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mk8orhox2l/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1518, \"height\": 638, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mk8orhox2l/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 838, \"height\": 548, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mk8orhox2l/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 796, \"height\": 526, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mk8orhox2l/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 829, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mk8orhox2l/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 901, \"height\": 373, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mk8orhox2l/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 647, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mk8orhox2l/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1777, \"height\": 427, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mk8orhox2l/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1772, \"height\": 405, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-mk8orhox2l/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1721, \"height\": 960, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mk8orhox2l/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 875, \"height\": 197, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mk8orhox2l/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 873, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mk8orhox2l/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1300, \"height\": 435, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mk8orhox2l/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 913, \"height\": 364, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mk8orhox2l/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1718, \"height\": 829, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mk8orhox2l/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1710, \"height\": 1181, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mk8orhox2l/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1700, \"height\": 2344, \"label\": \"Table\"}]"
motivation: 标准投机解码的草稿模型效率有限，需要更细致的加速策略。
method: 提出GliDe，重用目标模型KV缓存的草稿模型；提出CaPE，基于置信度扩展候选token。
result: 实验表明，两种方法显著降低了预期解码延迟，实际运行时间也大幅减少。
conclusion: GliDe和CaPE作为插件式改进，有效提升了投机解码的速度，且易于集成。
---

## Abstract
Speculative decoding is a relatively new decoding framework that leverages small and efficient draft models to reduce the latency of LLMs. In this study, we introduce GliDe and CaPE, two low-hassle modifications to vanilla speculative decoding to further improve the decoding speed of a frozen LLM. Specifically, GliDe is a modified draft model architecture that reuses the cached keys and values from the target LLM, while CaPE is a proposal expansion method that uses the draft model's confidence scores to help select additional candidate tokens for verification. Extensive experiments on different benchmarks demonstrate that our proposed GliDe draft model significantly reduces the expected decoding latency. Additional evaluation using walltime reveals that GliDe can accelerate Vicuna models up to 2.17x and further extend the improvement to 2.61x with CaPE. We will release our code, data, and the trained draft models.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）在自回归解码时逐token生成，推理延迟高，影响实时应用。投机解码（Speculative Decoding）使用一个小而快的草稿模型先预测多个token，再由目标LLM并行验证，以加速推理。但现有草稿模型与目标模型的一致性不足，提案接受率有限，导致加速效果不理想。
- **整体含义**：作者旨在通过两种低成本改进——修改草稿模型架构以重用目标模型KV缓存（GliDe）以及基于置信度动态扩展候选token（CaPE），在不改变目标模型的前提下，进一步提升投机解码的加速比，使加速更易落地。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 2.1 GliDe（Glimpse Draft Model）
- **核心思想**：让草稿模型在生成提案时，能够“瞥见”目标模型在上一轮验证后缓存的键值对（KV cache），从而让草稿模型的预测分布更接近目标模型。
- **关键技术细节**：
  1. 在草稿模型的每个Transformer层中，在自注意力子层和前馈子层之间插入一个**交叉注意力子层**。
  2. 该交叉注意力利用目标模型上层（靠近输出层）的KV缓存：草稿模型当前步的隐向量通过线性投影生成查询，与目标模型的键值进行多头注意力。
  3. 训练时采用**块状注意力掩码**（block-wise attention mask）来模拟推理时KV缓存的延迟（即草稿模型只能访问已验证的prefix，不能访问当前块内未来token）。
  4. 草稿模型保持自回归生成，结构宽而浅（如7B/13B目标使用1层草稿，33B使用2层，隐藏维度4096）。

### 2.2 CaPE（Confidence-Aware Proposal Expansion）
- **核心思想**：草稿模型在生成每个token时，根据其预测置信度动态决定为该位置额外提供多少个候选token（作为扩展集），以增加验证阶段的接受机会。
- **关键技术细节**：
  1. 在标准提案（长度为γ的贪婪序列）基础上，每个位置i关联一个扩展集X_i，包含K_i个次高概率的token。
  2. K_i由置信度p_i（即当前token的最高概率）决定：p_i越低，K_i越大。具体分段：p∈(0,0.3]→K=7，(0.3,0.6]→K=5，(0.6,0.8]→K=3，(0.8,1]→K=1。
  3. 扩展集的构建不增加草稿模型推理时间，因为可以同时进行（仅需取top-K）。
  4. 验证时，将所有扩展token线性化后送入目标模型，使用特殊的因果掩码保证每个token只能看到自己及之前原始提案中的token。
- **算法流程**（文字描述）：
  - 草稿模型自回归生成γ个贪婪token，同时记录每一步的概率分布。
  - 对每一步，根据置信度计算扩展集大小，取出相应数量的次高概率token。
  - 将贪婪序列与所有扩展token拼接成线性序列，构造验证注意力掩码，输入目标模型并行验证。

## 3. 实验设计

- **目标模型**：Vicuna 7B/13B/33B，Mistral 7B-instruct-v0.1。
- **草稿模型**：
  - GliDe（本文，1-2层，隐藏维度4096）。
  - 基线：LLaMA-68m、LLaMA-160m、LLaMA-45m（来自SpecInfer等）。
- **数据集**：
  - 预训练：SlimPajama-6B。
  - 微调：ShareGPT（SFT数据）。
  - 评估：GSM8K（数学推理）、Finance-Alpaca（金融QA）、Spider（Text-to-SQL）、CodeSearchNet-Python（代码生成）、MT-Bench（聊天基准）。
- **对比方法**：
  - 仅有GliDe vs Vanilla Drafter（无交叉注意力）。
  - 仅有GliDe vs LLaMA系列草稿模型。
  - GliDe+CaPE vs Medusa（多预测头）、GliDe+BeamSearch（束搜索，k=4）。
- **主要指标**：
  - 接受率（acceptance rate，α）。
  - 期望加速比（expected speedup，E(Spd.) = (1-α^(γ+1))/((1-α)(γc+1))，c为成本系数）。
  - 实际解码速度（tokens/s）和墙钟加速比。
  - 生成策略：使用投机采样（speculative sampling）或投机解码（speculative decoding）以匹配基线。

## 4. 资源与算力

论文中明确说明了训练资源：
- 对于7B和13B目标模型，使用**8块H800 GPU**，采用ZeRO-2优化。
- 对于33B目标模型，使用**16块H800 GPU**，采用ZeRO-3优化。
- 训练时间：
  - 7B目标：约7小时。
  - 13B目标：约10小时。
  - 33B目标：约100小时（主要耗时在前向目标模型获取KV缓存）。
- 所有推理实验在**单块H800 GPU**上使用**fp16**进行。
- 优化器：AdamW，学习率5e-4，batch size（含梯度累积）64，训练1个epoch。

## 5. 实验数量与充分性

- **核心实验**：
  1. 对比GliDe与Vanilla Drafter（消融交叉注意力）：在4个数据集×3种目标模型共12组实验，全部展示提升。
  2. 对比GliDe与LLaMA基线：在4个数据集×4种目标模型共16组实验，报告接受率、成本系数和期望加速比。
  3. 对比GliDe+CaPE与Medusa、GliDe+BeamSearch：在Vicuna 7B/13B/33B上测量墙钟加速比（3组实验）。
  4. 额外实际解码速度对比（tokens/s）图。
- **消融与补充分析**：
  - 不同目标层KV缓存的影响（Mistral-7B上，4个数据集）。
  - C APE vs 固定大小扩展性能对比（仅一个数据集MT-Bench）。
  - 蒸馏的影响（表2，4个数据集）。
  - 推测阶段与验证阶段的时间分解（表3，3种目标模型）。
  - 批量服务性能（表4，不同batch size）。
  - 案例研究（表6-8，3个示例）。
- **充分性评价**：
  - 实验覆盖了多种目标模型规模（7B/13B/33B）和不同领域（数学、金融、SQL、代码、对话），较为全面。
  - 消融实验验证了两个核心组件的独立贡献（交叉注意力、置信度扩展）。
  - 与主流基线（LLaMA、Medusa）的对比公平，统计显著性检验（p<0.01）。
  - 不足：未在更大模型（如70B）或更多样化的硬件（如A100）上进行测试；批量服务的实验只限于小批量（OOM问题），对真实部署场景覆盖有限。

## 6. 论文的主要结论与发现

1. **GliDe显著提高接受率**：相比无交叉注意力的Vanilla Drafter，接受率提升5.4~23.5个百分点；相比LLaMA基线，平均提升约19.9%。
2. **GliDe成本极低**：成本系数c仅为5%~7%，即草稿模型耗时几乎是目标模型的5%~7%，可忽略不计。
3. **GliDe+CaPE获得最高加速**：在Vicuna-7B/13B/33B上，墙钟加速比分别达到2.5x、2.6x、2.6x，优于Medusa和GliDe+BeamSearch。
4. **CaPE优于固定扩展**：动态根据置信度调整扩展数量比固定使用4个候选token更有效。
5. **Beam Search不适用于该场景**：束搜索在推测阶段耗时增加过多（从5.5ms增至10.9ms），抵消了接受率提升的好处。
6. **目标模型上层KV缓存效果更好**：使用越靠近输出层的KV缓存，接受率越高。

## 7. 优点

- **方法简洁高效**：仅通过插入交叉注意力层和动态扩展集，无需修改目标模型，易于集成。
- **充分的实验验证**：在多种模型规模、多个数据集上验证，消融实验清晰，与主流基线公平对比。
- **实用性强**：实际墙钟加速比达到2.5x以上，且代码已开源。
- **分析深入**：包括不同层KV缓存效果、推测与验证时间分解、案例展示等，解释性强。

## 8. 不足与局限

- **非即插即用**：每个新LLM需要重新训练对应的GliDe草稿模型，尽管训练成本可控（7~100小时），但不如无训练方法灵活。
- **对tokenizer敏感**：不同LLM的tokenizer不同，需重新训练草稿模型。
- **批量服务有限**：在batch size较大或长上下文时出现OOM，未给出有效优化方案，离实际大规模部署还有距离。
- **实验覆盖不足**：未在更大模型（如70B）或更小设备（如边缘端）上测试；批量服务实验仅复制相同输入，与实际多用户场景有差距。
- **潜在偏差风险**：加速可能无意中加速有害或偏见内容的生成，论文虽提到但未提出缓解措施。
- **CaPE的阈值选择**：置信度分段的阈值（0.3,0.6,0.8）和对应K值（7,5,3,1）是通过初步实验确定的，可能不是最优通用设定。

（完）
