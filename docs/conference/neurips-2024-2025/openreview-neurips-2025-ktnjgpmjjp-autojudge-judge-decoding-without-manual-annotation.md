---
title: "AutoJudge: Judge Decoding Without Manual Annotation"
title_zh: AutoJudge：无需人工标注的评判解码
authors: "Roman Garipov, Fedor Velikonivtsev, Ivan Ermakov, Ruslan Svirschevski, Vage Egiazarian, Max Ryabinin"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=ktNJgpmjjP"
tags: ["query:llm-sd"]
score: 9.0
evidence: 通过评判分类器实现宽松验证的损耗性投机解码
tldr: 本文提出AutoJudge方法，通过任务特定的损耗性投机解码加速LLM推理。它识别对下游质量不重要的token，放松分布匹配约束，并用一个轻量分类器判断哪些不匹配的token可安全接受，在不牺牲最终答案质量的前提下提升速度。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ktnjgpmjjp/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1355, \"height\": 497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ktnjgpmjjp/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1394, \"height\": 685, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ktnjgpmjjp/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1391, \"height\": 684, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ktnjgpmjjp/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1403, \"height\": 685, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ktnjgpmjjp/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1400, \"height\": 679, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ktnjgpmjjp/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1399, \"height\": 679, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ktnjgpmjjp/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 705, \"height\": 700, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ktnjgpmjjp/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1406, \"height\": 686, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ktnjgpmjjp/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1400, \"height\": 686, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ktnjgpmjjp/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1404, \"height\": 681, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ktnjgpmjjp/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 671, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ktnjgpmjjp/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1397, \"height\": 683, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ktnjgpmjjp/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1402, \"height\": 684, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ktnjgpmjjp/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1106, \"height\": 1055, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1461, \"height\": 803, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 718, \"height\": 344, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 718, \"height\": 344, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 700, \"height\": 346, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 699, \"height\": 342, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 700, \"height\": 346, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 715, \"height\": 344, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 685, \"height\": 342, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 720, \"height\": 348, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 770, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 721, \"height\": 346, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 714, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 726, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 682, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 684, \"height\": 342, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 492, \"height\": 423, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 754, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1369, \"height\": 361, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ktnjgpmjjp/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1204, \"height\": 142, \"label\": \"Table\"}]"
motivation: 现有投机解码要求严格分布匹配，限制了加速潜力。
method: 通过半贪心搜索找出可跳过的不匹配token，并训练分类器在线判断。
result: 在保持下游任务质量的同时实现更快的生成速度。
conclusion: 损耗性投机解码是可行的，且能通过自动方法实现。
---

## Abstract
We introduce AutoJudge, a method that accelerates large language model (LLM) inference with task-specific lossy speculative decoding. 
Instead of matching the original model output distribution token-by-token, we identify the generated tokens that affect the downstream quality of the response, relaxing the distribution match guarantee so that the "unimportant" tokens can be generated faster.
Our approach relies on a semi‑greedy search algorithm to test which of the mismatches between target and draft models should be corrected to preserve quality and which ones may be skipped.
We then train a lightweight classifier based on existing LLM embeddings to predict, at inference time, which mismatching tokens can be safely accepted without compromising the final answer quality.
We evaluate AutoJudge with multiple draft/target model pairs on mathematical reasoning and programming benchmarks, achieving significant speedups at the cost of a minor accuracy reduction. 
Notably, on GSM8K with the Llama 3.1 70B target model, our approach achieves up to ${\approx}2{\times}$ speedup \textit{over speculative decoding} at the cost of a ${\le} 1\%$ drop in accuracy.
When applied to the LiveCodeBench benchmark, AutoJudge automatically detects programming-specific important tokens, accepting ${\ge}25$ tokens per speculation cycle at a$~ 2\%$ drop in Pass@1. Our approach requires no human annotation and is easy to integrate with modern LLM inference frameworks.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）的推理速度瓶颈。传统投机解码（Speculative Decoding）通过小模型（draft model）生成候选 token，再由大模型（target model）并行验证，要求所有 token 严格匹配原始大模型分布（lossless）。但这种严格匹配在许多任务中过于保守：某些不匹配的 token（如微小措辞变化、风格差异）并不损害下游任务质量，却导致大量 token 被丢弃，限制了加速潜力。
- **整体含义**：提出一种**损耗性投机解码（lossy speculative decoding）**方法 AutoJudge，在不牺牲最终答案质量的前提下，允许跳过“不重要”的不匹配 token，从而显著提升生成速度。该方法无需人工标注，可自动为不同任务发现重要的 token 模式。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将投机解码中 token 的不匹配分为两类：**重要**（影响最终答案质量，必须由目标模型生成）和**不重要**（可被草稿模型替换而不改变答案）。通过一个半贪心搜索算法自动标注训练数据，训练一个轻量级分类器在推理时预测哪些不匹配 token 可以安全接受。
- **关键技术细节**：
  1. **重要 token 挖掘（Algorithm 1）**：  
     - 输入：提示词 x，草稿模型 θ_draft，目标模型 θ_target。  
     - 目标模型生成完整回应 y，提取答案 α。  
     - 计算草稿模型在 y 上的逐 token 预测，找出所有不匹配位置 I。  
     - 迭代处理最早的不匹配位置 t：将目标 token 替换为草稿 token eyt，继续用目标模型生成后续内容得到新回应 ŷ，提取答案 α̂。若 α̂ ≡ α（答案等价），则标记该 token 为不重要，更新 y=ŷ 并继续搜索；否则标记为重要，保留原 token。  
     - 输出所有不匹配位置及其重要性标签。  
  2. **分类器训练**：  
     - 使用上一步收集的 token 级标签训练逻辑回归（logistic regression）。  
     - 输入特征：草稿 token 被目标模型编码后的隐藏状态（连接草稿和目标模型的 hidden states），因推理时这些表示已存在。  
     - 使用 L2 正则化，经网格搜索选择最佳 C 值。  
  3. **推理阶段集成**：  
     - 将分类器插入标准投机解码验证阶段。当原始算法要拒绝一个不匹配 token 时，分类器预测其是否重要；若判为不重要，则接受该 token 并继续验证后续 token，否则拒绝。  
     - 可兼容任意投机解码算法（如 EAGLE-2、树状解码等）。

### 3. 实验设计：数据集、场景、对比方法

- **数据集与场景**：
  - **数学推理**：GSM8K（约 7.47K 训练 / 1.32K 测试），8-shot 和 0-shot 设置。
  - **编程任务**：LiveCodeBench（code_generation_lite，版本 v5，共 880 题，分 easy/medium/hard），零样本 Pass@1 评估。
  - **开放生成**（附录 L）：TriviaQA 问答和 Arena-Hard-Auto v2.0 创意写作，使用 LLM-as-a-judge 评估。
- **对比方法**：
  - 标准投机解码（lossless）。
  - Top-K 基线（接受不匹配 token 若其在目标模型 top-K 中，K 取 2,4,8,…|V|）。
  - 纯草稿模型解码。
  - 手动标注（附录 N，类似 Judge Decoding）。
- **模型对**：
  - Llama 3.2 1B Instruct（草稿） / Llama 3.1 8B Instruct（目标）
  - Llama 3.1 8B Instruct（草稿） / Llama 3.1 70B Instruct（目标）
  - Llama 3.1 8B Instruct（草稿） / Llama 3.1 405B Instruct（目标）
  - Qwen2.5 0.5B / 7B / 32B 系列（部分实验）
  - 额外 EAGLE-2 实验（Llama 3.1 8B + EAGLE head）。

### 4. 资源与算力

- 论文明确列出硬件：
  - 主要实验：NVIDIA A100-SXM4-80GB GPU，服务器配备双 Epyc 7742 CPU 和 1 TiB RAM。
  - 1B/8B 模型对：单张 A100-80GB。
  - 8B/70B 模型对：4 张 A100-80GB（张量并行）。
  - 8B/405B 模型对：8 张 H100-SXM5-80GB（FP8 精度）。
  - 离线（offloading）实验：单张 A100-80GB 配合 RAM 换出。
- 训练分类器仅需少量算力（逻辑回归），主要算力消耗在 Alg.1 的 token 挖掘阶段（大量目标模型推理）。论文未给出总 GPU 小时数，但提到由于挖掘可独立并行执行，且运行在低优先级可抢占硬件上，难以准确计量；同时给出每样本平均时间：1B/8B 约 65.6 秒/样本，8B/70B 约 706.4 秒/样本（GSM8K），8B/70B 在 LiveCodeBench 约 449 秒/样本。

### 5. 实验数量与充分性

- **实验数量**：
  - GSM8K：多组模型对（1B/8B、8B/70B、Qwen 系列），8-shot 和 0-shot，每个设置报告不同阈值下的精度与加速。
  - LiveCodeBench：两个模型对（1B/8B、8B/70B），5 折交叉验证。
  - vLLM 推理速度基准：三个模型对（1B/8B、8B/70B、8B/405B），附不同阈值下的 tokens/s 及加速比。
  - 消融实验（附录）：
    - 分类器输入选择（前 token vs. 后 token 嵌入、草稿/目标/两者 hidden states）。
    - 分类器类型（逻辑回归 vs. 随机森林 vs. MLP）。
    - 精度影响（BF16 vs. FP32）。
    - 与 EAGLE-2 结合。
    - 规则方法对比（数学符号过滤）。
    - 任务迁移（GSM8K→MATH-hard、长上下文）。
    - 手动标注对比。
    - 开放生成（问答、创意写作）。
- **充分性与公平性**：
  - 对比了 lossless 投机解码和 Top-K 基线，在多个阈值下绘制 speed-accuracy 曲线，清晰展示了 AutoJudge 的优越性。
  - 在 vLLM 中集成并与标准投机解码对比，优化了窗口大小（各自调优）以提供公平基准。
  - 提供了附录说明精度不稳定问题，并采用更稳定的 PyTorch/Transformers 实现报告关键指标，确保可重复性。
  - 总体实验设计较为全面，覆盖多种任务、模型规模、评价指标，消融实验深入。

### 6. 论文的主要结论与发现

- AutoJudge 能在数学推理和编程任务上大幅提升投机解码的加速效果。
  - 在 GSM8K 上（8B/70B 模型对），实现约 **2×** 速度提升（相比标准投机解码），代价是 ≤1% 精度下降。
  - 在 LiveCodeBench 上（8B/70B 模型对），每轮接受 ≥25 个 token（约 2× 标准投机解码），Pass@1 下降约 2%。
  - 与 EAGLE-2 结合可进一步加速。
- 无需人工标注即可自动发现任务特定的重要 token 模式。
- 分类器轻量（逻辑回归），部署开销极小，可方便集成到现有推理框架（如 vLLM）。
- 开放生成（问答）也能取得加速，但创意写作任务因类标签噪声大（重要 token 占比超 70%）导致收益有限。

### 7. 优点：方法或实验设计上的亮点

1. **无人工标注**：自动挖掘重要 token，避免 Judge Decoding 中昂贵且易错的手动标注，尤其适用于专业领域。
2. **通用性强**：可与任意投机解码算法（EAGLE、树状解码等）和推理框架集成；分类器仅在不匹配时调用，不改变主流程。
3. **轻量分类器**：逻辑回归输入来自现有 LLM hidden states，几乎零额外计算开销。
4. **半贪心搜索**：通过迭代替换并重新生成，考虑了 token 之间的联合影响，比独立判断更准确。
5. **实验充分**：在多种模型规模（1B/8B/70B/405B）、多种任务（数学、代码、问答、写作）上验证，消融实验覆盖分类器设计、精度选择、任务迁移等，对比基线合理。

### 8. 不足与局限

1. **依赖答案等价性判定**：方法需要能自动判断两个答案是否等价（如数学答案数值相等、代码通过测试）。对于没有明确质量判据的开放任务（如创意写作），效果受限（噪声大，重要 token 占比高）。
2. **计算成本**：重要 token 挖掘阶段（Algorithm 1）需要多次目标模型推理，尤其是在大规模模型上可能消耗较多算力。论文虽提到可通过 API 调用并行化，但未详细讨论工程优化。
3. **迁移性有限**：在 GSM8K 上训练的分类器迁移到 MATH-hard 结果不如 Top-K 基线，说明重要 token 模式可能随任务难度或类型变化，需要重新训练。
4. **精度与加速的权衡**：尽管可控，但极端加速时精度下降明显（如 GSM8K 上 1% 精度对应约 2× 加速，更高加速精度损失更大），用户需根据场景权衡。
5. **数值稳定性问题**：BF16 精度下并行/串行 forward 得到的 hidden states 不一致，影响分类器效果。论文提出改用 FP32 或仅使用目标模型并行计算隐藏状态作为解决，但增加了工程复杂度。
6. **手动标注对比不完全公平**：原始 Judge Decoding 的代码和数据未公开，作者只能按描述复现，手动标注结果更差，但这不能完全证明自动方法全面优于手动，可能与标注质量或数据量有关。

（完）
