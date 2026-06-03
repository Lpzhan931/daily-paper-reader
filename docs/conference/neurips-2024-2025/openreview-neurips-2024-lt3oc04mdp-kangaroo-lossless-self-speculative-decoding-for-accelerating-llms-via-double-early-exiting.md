---
title: "Kangaroo: Lossless Self-Speculative Decoding for Accelerating LLMs via Double Early Exiting"
title_zh: Kangaroo：基于双早退的无损自投机解码加速LLM推理
authors: "Fangcheng Liu, Yehui Tang, Zhenhua Liu, Yunsheng Ni, Duyu Tang, Kai Han, Yunhe Wang"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=lT3oc04mDp"
tags: ["query:llm"]
score: 8.0
evidence: 使用双早退策略的LLM自投机解码加速方法
tldr: 针对传统投机解码需要额外训练草稿模型的高成本问题，本文提出Kangaroo框架，利用目标LLM的浅层子网络和LM头构建自草稿模型，通过双早退策略实现自验证。该方法无需额外训练即可加速推理，且保持采样分布不变。实验表明在多个LLM上取得显著加速，为高效LLM推理提供了低成本方案。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-lt3oc04mdp/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 602, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-lt3oc04mdp/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 717, \"height\": 473, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-lt3oc04mdp/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1328, \"height\": 738, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-lt3oc04mdp/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 657, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-lt3oc04mdp/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1411, \"height\": 672, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-lt3oc04mdp/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 711, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-lt3oc04mdp/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1405, \"height\": 503, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-lt3oc04mdp/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1404, \"height\": 691, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-lt3oc04mdp/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1403, \"height\": 690, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-lt3oc04mdp/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1447, \"height\": 568, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-lt3oc04mdp/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-lt3oc04mdp/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1449, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-lt3oc04mdp/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1444, \"height\": 259, \"label\": \"Table\"}]"
motivation: 训练独立草稿模型成本高且不实用，需要利用目标模型自身结构实现投机解码。
method: 使用目标LLM的浅层子网络作为草稿模型，通过双早退策略实现自草的草稿与验证。
result: 在多个LLM上实现无损加速，显著降低推理延迟。
conclusion: Kangaroo提供了一种无需额外训练的LLM投机解码方法，推动了高效推理技术的发展。
---

## Abstract
Speculative decoding has demonstrated its effectiveness in accelerating the inference of large language models (LLMs) while maintaining an identical sampling distribution. However, the conventional approach of training separate draft model to achieve a satisfactory token acceptance rate can be costly and impractical. In this paper, we propose a novel self-speculative decoding framework \emph{Kangaroo} with \emph{double} early exiting strategy, which leverages the shallow sub-network and the \texttt{LM Head} of the well-trained target LLM to construct a self-drafting model. Then, the self-verification stage only requires computing the remaining layers over the \emph{early-exited} hidden states in parallel. To bridge the representation gap between the sub-network and the full model, we train a lightweight and efficient adapter module on top of the sub-network. One significant challenge that comes with the proposed method is that the inference latency of the self-draft model may no longer be negligible compared to the big model. To boost the token acceptance rate while minimizing the latency of the self-drafting model, we introduce an additional \emph{early exiting} mechanism for both single-sequence and the tree decoding scenarios. Specifically, we dynamically halt the small model's subsequent prediction during the drafting phase once the confidence level for the current step falls below a certain threshold. This approach reduces unnecessary computations and improves overall efficiency. Extensive experiments on multiple benchmarks demonstrate our effectiveness, where Kangaroo achieves walltime speedups up to 2.04$\times$, outperforming Medusa-1 with 88.7\% fewer additional parameters. The code for Kangaroo is available at https://github.com/Equationliu/Kangaroo.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）在自回归解码时受限于内存带宽瓶颈，导致推理延迟高、并行度不足。传统的投机解码（Speculative Decoding）通过训练一个独立的草稿模型来生成多个候选 token，再由大模型并行验证，从而加速推理。然而，训练独立的草稿模型成本高昂且不实用，尤其是在需要为不同 LLM 分别训练草稿模型时，训练开销和部署复杂度都难以接受。
- **核心问题**：如何在**不额外训练独立草稿模型**的前提下，实现无损（lossless）的投机解码加速，同时保持与原始模型完全相同的采样分布。
- **整体含义**：论文提出了一种**自投机解码框架 Kangaroo**，利用目标 LLM 本身的**浅层子网络**和**LM Head**构造自草稿模型，通过**双早退（double early exiting）** 策略，在降低计算成本的同时实现显著的推理加速（最高 2.04× 加速比），且仅需极少的额外参数（约为 Medusa 的 11.3%），为 LLM 高效推理提供了一种低成本、实用的方案。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- **自草稿模型**：直接取用目标 LLM 的前 ℓ 层（浅层子网络），并在其顶部训练一个轻量级适配器（Adapter）网络，然后复用目标模型的 LM Head 来输出条件概率分布，从而构成一个无需额外大模型的草稿模型。
- **双早退**：
  1. **层级早退**（Layer-level early exiting）：草稿阶段只运行浅层子网络（不运行完整模型），加速草稿生成。
  2. **Token级动态早退**（Token-level dynamic early exiting）：在草稿阶段，根据草稿模型对当前 token 的 top-1 置信度是否低于阈值 η 来决定是否提前停止生成，避免对困难 token 浪费计算；同时将该 token 的隐藏状态提前退出，后续由大模型并行验证。

### 关键技术细节
1. **适配器网络 A**：
   - 仅包含一个多头注意力层（MultiHead Attention）和两个归一化（LayerNorm）层，无 FFN，结构轻量。
   - 输入为浅层子网络输出的隐藏状态 f_t，输出为 f'_t = f_t + MultiHead(LayerNorm(f_t))。
   - 最后通过冻结的 LM Head 得到条件概率分布：Ms(x | x_t) = Softmax(W^T LayerNorm(f'_t))。
   - 参数总量：4N² + 2N（N 为隐藏维度），对 Vicuna-7B 为 67.1M，仅为 Medusa 的 11.3%（Medusa 为 591M）。

2. **训练**：
   - 冻结目标 LLM 的全部参数，仅训练适配器 A。
   - 优化目标为交叉熵损失，蒸馏目标 LLM 的条件概率分布：A* = argmin ∑_t ∑_x -M_b(x|x_t) log Ms(x|x_t)。
   - 训练数据：ShareGPT 数据集，10 个 epoch，AdamW 优化器。

3. **单序列解码流程**：
   - 草稿阶段：Ms 自回归生成 γ 个候选 token，同时保存每个 token 的浅层隐藏状态。
   - 动态停止：若 Ms 对当前 token 的 top-1 概率 ≤ η，则停止草稿。
   - 验证阶段：大模型剩余层 M_b[l:] 并行处理所有早期退出的隐藏状态，生成 logits，然后按照标准投机解码算法决定接受或拒绝。

4. **树解码扩展**：
   - 在每个草稿步骤，不取单一 top-1，而是选择 Top-K 个 token，并计算路径置信度（乘积）。
   - 当最高置信度低于阈值 η 或树大小超过预设最大值时停止扩展。
   - 实现了动态调整树深度和宽度，无需预定义静态树。

## 3. 实验设计

- **模型**：Vicuna-7B、Vicuna-13B；额外验证了 Llama2-13B-Chat。
- **基准数据集**：Spec-Bench，包含六个子任务：多轮对话（MT Bench）、翻译（Translation）、摘要（Summarization）、问答（QA）、数学推理（Math）、检索增强生成（RAG）。
- **评估指标**：
  - 端到端加速比（Walltime speedup ratio）
  - 压缩率（Compression Rate, CR）
  - 另外提出了**一致 token 接受率（CTAR）** 作为辅助指标。
- **对比方法**：
  - Lookahead、Medusa（含/不含树）、REST、SpS（使用 Vicuna-68M 作为草稿模型）、Draft&Verify。
- **实验设置**：
  - 超参数：ℓ=2（Vicuna-7B），ℓ=3（Vicuna-13B）；单序列 γ=6，η=0.6；树解码 Top-K=10，η=0.4。
  - 训练适配器：ShareGPT 数据集，10 个 epoch，8 x V100。

## 4. 资源与算力

- **训练**：适配器训练耗时约 24 小时，使用 8 块 NVIDIA V100 GPU。
- **推理**：未明确给出推理所需 GPU 型号和数量，但实验在 Spec-Bench 上完成，通常为单卡或多卡推理。论文未提及推理阶段的具体算力成本。

## 5. 实验数量与充分性

- **主要实验**：在 Vicuna-7B/13B 的 Spec-Bench 六个子任务上与四种以上 baseline 方法进行了对比（见表 1 和表 5）。
- **消融实验**：
  - 浅层子网络深度 ℓ 的影响（图 7a）
  - 动态早退阈值 η 的影响（图 7b）
  - 适配器架构的消融（表 2）：包括去掉 FFN、共享 LM Head、对比 1-Layer Transformer、MLP Only 等。
  - 温度采样下的加速效果（表 3）
  - 在 Llama2-13B-Chat 上的额外验证（附录表 4）。
- **充分性评价**：实验覆盖了多种模型规模（7B、13B）、多种任务类型和多种 baseline，消融实验全面，对比公平（均使用相同 Spec-Bench 和评估方式）。实验数量充足，结论可信。但未包含更大模型（如 33B 以上）的实验，且所有实验仅在一个基准套件（Spec-Bench）上进行，可能限制了泛化推论。

## 6. 论文的主要结论与发现

- **Kangaroo 在保持无损的前提下显著加速**：在 Vicuna-7B 上，单序列版本平均加速比 1.50×，树解码版本平均加速比 1.72×（最高 2.04× 在数学推理子任务）。
- **参数效率极高**：Kangaroo 的额外参数（67M）仅为 Medusa（591M）的 11.3%，但加速效果全面优于 Medusa（单序列场景）。
- **动态早退有效**：基于 top-1 概率的动态停止机制在压缩率和加速比之间取得了更好的平衡，优于固定步长草稿。
- **温度鲁棒性**：在小温度（T=0.2）下仍能保持接近贪婪解码的加速效果；直接使用未调整的 top-1 置信度作为停止准则优于调整后的置信度。
- **适配器设计最优**：仅含注意力+归一化层（无 FFN）的设计优于更复杂的 1-Layer Transformer 或 MLP-only 方案。

## 7. 优点

1. **无需独立草稿模型**：完全利用目标 LLM 自身的浅层子网络，训练成本极低。
2. **双重早退创新**：层级早退和 token 级动态早退的结合，既保证高效率又保持高接受率。
3. **轻量适配器**：仅含单头注意力+归一化，参数少，训练快，效果好。
4. **动态树解码**：避免了预定义静态树的局限，自适应调整树结构，提升并行效率。
5. **实验设置公平**：统一使用 Spec-Bench 评测，对比多种公开方法，消融实验设计系统。

## 8. 不足与局限

1. **表示鸿沟依然存在**：虽然适配器缓解了浅层子网络与完整模型之间的表示差距，但在某些复杂任务上该差距可能仍然影响性能（论文自身指出）。
2. **模型规模覆盖有限**：实验仅包含 7B 和 13B 模型，未在更大模型（如 33B、70B）上验证，限制了方法的通用性结论。
3. **训练数据单一**：适配器仅使用 ShareGPT 数据集训练，可能在其他领域分布上的泛化性未充分验证。
4. **未提供误差线**：实验结果未报告标准差或置信区间，统计显著性未明确。
5. **对温度敏感**：温度较高时加速效果下降（表 3），虽然设置了应对策略但性能退化仍然明显。
6. **仅评测了英文任务**：Spec-Bench 为英文基准，缺少多语言评估，可能不适用于中文或其他语言场景。

（完）
