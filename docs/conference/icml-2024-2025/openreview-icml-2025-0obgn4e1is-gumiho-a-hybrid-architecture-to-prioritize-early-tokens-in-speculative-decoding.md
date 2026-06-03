---
title: "Gumiho: A Hybrid Architecture to Prioritize Early Tokens in Speculative Decoding"
title_zh: Gumiho：一种优先处理早期token的投机解码混合架构
authors: "Jinze Li, Yixing Xu, Haiduo Huang, Xuanwu Yin, Dong Li, Edith C. H. Ngai, Emad Barsoum"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=0ObGn4e1IS"
tags: ["query:llm"]
score: 8.0
evidence: 面向大语言模型的投机解码加速
tldr: 本文发现投机解码中草稿序列的早期token比后期token更重要，据此提出Gumiho混合架构。该方法通过专门处理早期token的模块提高预测准确性，后续token则使用简化处理。实验结果表明，Gumiho显著提升了多token生成的成功率和整体解码速度，为LLM推理加速提供了新方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-0obgn4e1is/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1600, \"height\": 737, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0obgn4e1is/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 861, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0obgn4e1is/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 687, \"height\": 620, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0obgn4e1is/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 684, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0obgn4e1is/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 687, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-0obgn4e1is/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1410, \"height\": 1231, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-0obgn4e1is/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 855, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0obgn4e1is/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1769, \"height\": 1224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0obgn4e1is/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 625, \"height\": 171, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0obgn4e1is/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 616, \"height\": 362, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0obgn4e1is/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1657, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0obgn4e1is/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1771, \"height\": 830, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-0obgn4e1is/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1782, \"height\": 1181, \"label\": \"Table\"}]"
motivation: 现有投机解码假设所有token同等重要，导致早期token预测不准确，限制加速效果。
method: 提出Gumiho混合架构，对早期token使用更精细的预测头，后期token简化处理，以提高整体接受率。
result: 实验证明Gumiho在多个LLM上显著提升投机解码的加速比，验证了早期token优先策略的有效性。
conclusion: 通过优先关注早期token，Gumiho有效提升了投机解码的效率，为LLM推理加速提供了新思路。
---

## Abstract
Speculative decoding (SPD) aims to accelerate the auto-regressive token generation process of a target Large Language Model (LLM). Some approaches employ a draft model with multiple heads to predict a sequence of future tokens, where each head handles a token in the sequence. The target LLM verifies the predicted sequence and accepts aligned tokens, enabling efficient multi-token generation. However, existing methods assume that all tokens within a sequence are equally important, employing identical head structures and relying on a single-generation paradigm, either serial or parallel. To this end, we theoretically demonstrate that initial tokens in the draft sequence are more important than later ones. Building on this insight, we propose Gumiho, a hybrid model combining serial and parallel heads. Specifically, given the critical importance of early tokens, we employ a sophisticated Transformer architecture for the early draft heads in a serial configuration to improve accuracy. For later tokens, we utilize multiple lightweight MLP heads operating in parallel to enhance efficiency. By allocating more advanced model structures and longer running times to the early heads, Gumiho achieves improved overall performance. The experimental results demonstrate that our method outperforms existing approaches, fully validating its effectiveness. Our code is available at https://github.com/AMD-AIG-AIMA/Gumiho.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究问题**：大语言模型（LLM）自回归推理速度慢，投机解码（Speculative Decoding）通过小型草稿模型生成多个候选token，再由目标LLM并行验证来加速。现有方法（如Medusa、Eagle、Hydra）使用统一结构的多头模型预测未来token序列，但均假设所有token重要性相同，采用单一串行或并行范式。
- **关键洞察**：论文从理论和实验两个角度证明，草稿序列中的**早期token**比后期token更重要——因为第一个被拒绝的token会导致其后的所有草稿token被丢弃，即使它们本身正确。因此，提升早期token的预测精度能更有效地增加每轮可接受的token数（τ）。
- **研究目标**：提出一种优先关注早期token的混合架构，在保持效率的同时提高投机解码的整体加速比。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：基于“早期token更重要”的理论证明，将草稿生成分为两阶段：
  - **早期token（前两个）**：使用较复杂的**串行Transformer头（两层）** 依次生成，利用全上下文依赖提高精度。
  - **后期token（后续五个）**：使用多个轻量级**并行MLP头**同时生成，提升效率。
- **关键技术细节**：
  - **串行部分**：类似Eagle-2，将LLM隐藏状态与当前token嵌入拼接后，通过全连接层降维，输入两层Transformer生成前两个草稿token。
  - **并行部分**：五个相同的两层MLP（含ReLU激活）共享串行部分输出的特征，并行预测后续五个位置的token。
  - **全树注意力（Full Tree Attention, FTA）**：针对Eagle-2动态树机制中短候选路径丢弃的问题，允许平行生成的token之间任意组合，从更长路径中“借用”token补充短路径，增加候选长度且无额外计算开销。
- **理论支撑**：给出定理3.1并详细证明：在保持总接受概率不变的前提下，通过增大早期token接受概率、降低后期token接受概率（即重分配概率），可以提升期望接受长度E[L]。证明过程首先将分散的调整量集中到相邻位置，再逐项比较，使用几何级数缩放和归纳法得出不等式关系。

## 3. 实验设计

- **使用的数据集/场景**：六种基准测试，覆盖多轮对话（MT-Bench）、代码生成（HumanEval）、数学推理（GSM8K）、指令遵循（Alpaca）、摘要（CNN/Daily Mail）、问答（Natural Questions）。
- **Benchmark**：以**加速比（Speedup）和平均接受token数（τ）** 为主要指标，对比两种温度设置（Temperature=0 和 1）。
- **对比方法**：Medusa、Hydra、Eagle、Eagle-2（现有SOTA）。其中Medusa和Hydra只在Temperature=0时对比。
- **目标LLM**：7种模型：Vicuna-7B/13B, Llama2-Chat-7B/13B/70B, Llama3-Instruct-8B/70B。

## 4. 资源与算力

- **训练硬件**：使用 **8 × AMD Instinct MI250 GPU** 进行训练。
- **推理硬件**：单块MI250 GPU用于7B/13B模型；70B模型需 4 × MI250 GPU。附录也提供了NVIDIA A100的结果。
- **训练数据**：ShareGPT数据集。
- **训练细节**：训练10个epoch，优化器AdamW，学习率Vicuna为2e-4，LLaMA2为1e-4，批次大小4，损失函数包含回归损失和分类损失，权重分别为1和0.1。

## 5. 实验数量与充分性

- **实验数量**：主表（Table 1）包含所有7种目标模型×6个数据集×2种温度的完整结果，以及消融实验（串行头深度、并行头宽度、FTA有效性、各组件耗时）。
- **充分性评价**：实验覆盖多种规模（7B~70B）、多种架构（Vicuna, LLaMA2/3）和两种采样温度，对比方法是当前SOTA。消融实验深入分析了各模块贡献。但**缺乏与独立草稿模型方法（如使用T5-small）的对比**，且所有对比均在同一硬件上完成，公平性较好。总体充分且客观。

## 6. 主要结论与发现

- Gumiho在所有设置下**一致优于现有SOTA方法Eagle-2**，加速比提升4.5%~15.8%（尤其70B模型增益明显，如LLaMA2-70B提升11.7%，LLaMA3-70B提升15.8%）。
- 混合架构有效：串行Transformer头提高了早期token精度，并行MLP头缩短了草稿生成时间（图3显示Gumiho的草稿时间始终低于Eagle-2）。
- 全树注意力机制进一步提升了平均接受token数，且无额外计算开销。
- 理论证明与实验结果一致：优先提升早期token精度可增加期望接受长度。

## 7. 优点（方法与实验设计亮点）

- **理论创新**：首次严格证明草稿序列中早期token重要性更高，并给出数学定理和详细证明。
- **架构创新**：串行+并行混合设计巧妙平衡精度和效率，符合“资源分配给关键位置”的直觉。
- **全树注意力新颖**：在不增加计算量的前提下，利用平行生成token的可组合性弥补短候选路径，提升τ。
- **实验全面**：覆盖多种模型、数据集和温度，消融实验深入，且提供了AMD和NVIDIA双平台结果。

## 8. 不足与局限

- **显存开销**：相比Eagle和Medusa，Gumiho使用了两层Transformer加五个MLP，模型参数量更大，训练时GPU显存消耗更高。
- **未与独立草稿模型方法对比**：如T5-small加速T5-XXL等，缺少跨范式对比。
- **并行头数量限制**：消融实验表明MLP头数量过多会因共享嵌入信息过载而性能下降，需要谨慎调参。
- **仅覆盖了自推断（self-drafting）类别**，未探索与独立草稿模型结合的可能性。
- **对生成质量的影响未直接评估**：论文使用加速比和τ，但未报告生成文本质量指标（如BLEU、GPT-4评分），虽声称无损加速，但缺失量化验证。

（完）
