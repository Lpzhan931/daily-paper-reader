---
title: "AdaSPEC: Selective Knowledge Distillation for Efficient Speculative Decoders"
title_zh: AdaSPEC：面向高效投机解码器的选择性知识蒸馏
authors: "Yuezhou Hu, Jiaxin Guo, Xinyu Feng, Tuo Zhao"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=zNLlglSOwD"
tags: ["query:llm"]
score: 8.0
evidence: 针对大语言模型高效投机解码器的选择性知识蒸馏方法
tldr: 针对知识蒸馏与投机解码目标不匹配的问题，提出AdaSPEC，通过选择性蒸馏使草稿模型专注于高接受率token的学习，提升草稿模型与目标模型的匹配度，实验验证了在多种LLM上实现更高加速比。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-znllglsowd/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 863, \"height\": 446, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-znllglsowd/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1080, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-znllglsowd/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1078, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-znllglsowd/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 573, \"height\": 316, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-znllglsowd/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1442, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-znllglsowd/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1026, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-znllglsowd/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1026, \"height\": 219, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-znllglsowd/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1032, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-znllglsowd/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1103, \"height\": 376, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-znllglsowd/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 806, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-znllglsowd/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 396, \"height\": 183, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-znllglsowd/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 561, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-znllglsowd/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1444, \"height\": 940, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-znllglsowd/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1438, \"height\": 285, \"label\": \"Table\"}]"
motivation: 传统知识蒸馏目标是最小化KL散度，与投机解码最大化接受率的目标不符，草稿模型容量受限导致性能次优。
method: 提出选择性知识蒸馏方法AdaSPEC，根据token接受率调整蒸馏权重，优先学习决定性token。
result: 在多个LLM上取得比传统蒸馏更高的加速比，且不增加推理开销。
conclusion: 通过对齐蒸馏目标与投机解码的接受率，可大幅提升草稿模型的预测质量，实现更高效推理。
---

## Abstract
Speculative Decoding (SD) accelerates large language model inference by employing a small draft model to generate predictions, which are then verified by a larger target model. The effectiveness of SD hinges on the alignment between these models, which is typically enhanced by Knowledge Distillation (KD). However, conventional KD methods aim to minimize the KL divergence between the draft and target models across all tokens, a goal that is misaligned with the true objective of SD, which is to maximize token acceptance rate. Therefore, draft models often struggle to fully assimilate the target model's knowledge due to capacity constraints, leading to suboptimal performance. To address this challenge, we propose AdaSPEC, a novel method that incorporates selective token filtering into the KD process. AdaSPEC utilizes a reference model to identify and filter out difficult-to-fit tokens, enabling the distillation of a draft model that better aligns with the target model on simpler tokens. This approach improves the overall token acceptance rate without compromising generation quality. We evaluate AdaSPEC across diverse tasks, including arithmetic reasoning, instruction-following, coding, and summarization, using model configurations of 31M/1.4B and 350M/2.7B parameters. Our results demonstrate that AdaSPEC consistently outperforms the state-of-the-art DistillSpec method, achieving higher acceptance rates across all tasks (up to 15\%). The code is publicly available at \url{https://github.com/yuezhouhu/adaspec}.

---

## 论文详细总结（自动生成）

### 1. 核心问题与整体含义
- **研究动机**：投机解码（Speculative Decoding, SD）通过小型草稿模型生成候选 token，再由大型目标模型验证，以加速大语言模型推理。SD 的效果关键取决于草稿模型与目标模型的对齐程度，通常通过知识蒸馏（Knowledge Distillation, KD）来增强。
- **存在的问题**：传统 KD 方法最小化所有 token 上的 KL 散度，这与 SD 的真实目标（最大化 token 接受率）并不匹配。草稿模型容量有限，难以全面吸收目标模型知识，在困难 token 上浪费资源，导致对简单 token 的学习也不充分，整体接受率次优。
- **整体含义**：AdaSPEC 通过选择性 token 过滤，让草稿模型专注于容易学习且能被接受的 token，在不降低生成质量的前提下提升 token 接受率，从而更高效地实现 SD 加速。

### 2. 方法论
- **核心思想**：利用一个参考模型来识别并过滤掉“困难”token，使草稿模型在蒸馏时只针对“容易”token 进行对齐，更有效地利用有限容量。
- **关键技术细节**：
  - **第一阶段：参考模型蒸馏**。将参考模型 \( M_{\text{ref}} \) （初始化为草稿模型副本）通过 DistillSpec 框架（最小化前向 KL 散度）从目标模型 \( M_p \) 蒸馏，得到一个可作为 token 过滤器的参考模型。
  - **第二阶段：选择性草稿模型蒸馏**。对于每个 token \( w \)，计算其相对于目标模型的 KL 散度损失：\( L_{\text{draft}}(w) = \text{KL}(P \| Q) \)、\( L_{\text{ref}}(w) = \text{KL}(P \| R) \)，然后求差 \( \Delta L(w) = L_{\text{draft}}(w) - L_{\text{ref}}(w) \)。选取 \( \Delta L \) 最大的前 \( k \times 100\% \) 的 token 构成集合 \( S \)（这些 token 对草稿模型而言即“困难”但可学习的 token）。最终蒸馏损失只计算集合 \( S \) 中的 token，并除以 \( k \) 归一化，从而让草稿模型只聚焦于这些较易对齐的 token。
- **公式与算法流程**（文字说明）：
  - 参考模型蒸馏：\( \min_{M_{\text{ref}}} \mathbb{E}_{x \sim D, y \sim P(y|x)} [\text{KL}(P(y|x) \| R(y|x))] \)
  - 选择性蒸馏：\( L_{\text{distill}} = \frac{1}{k \cdot |y|} \sum_{i=1}^{|y|} \mathbb{I}[y_i \in S] \cdot L_{\text{draft}}(y_i) \)，其中 \( S = \{ w \mid \Delta L(w) \text{ is among top } k \times 100\% \} \)。

### 3. 实验设计
- **数据集/场景**：涵盖五个代表性任务：GSM8K（算术推理）、Alpaca（指令跟随）、MBPP（代码生成）、CNN/Daily Mail（摘要）、XSUM（极端摘要）。
- **模型配置**：两种规模组合：（1）Pythia-31M → Pythia-1.4B（同族）；（2）CodeGen-350M → Phi-2（跨族但 tokenizer 对齐）。
- **Benchmark 与对比方法**：主要对比 state-of-the-art 方法 **DistillSpec**。实验设置包括“3-Epoch”固定训练时长和“Optimal-Epoch”可变 epoch 最大化性能两种模式。
- **额外对比**：还进行了消融实验（token 选择机制、训练方法、蒸馏方法、选择比例）、与先进 SD 方法 EAGLE 集成、更大模型 Qwen2.5-0.5B→32B 验证、混合数据集训练等。
- **公平性**：控制初始化和训练时长一致，采用与 DistillSpec 相同的参考模型训练框架，仅在选择性部分不同。

### 4. 资源与算力
- 论文在附录 A.6 中给出了 GPU 小时估算表（Table 10）。主要使用 **A100 GPU** 进行训练。
- 具体估算（部分示例）：
  - Pythia-31M→1.4B 配置下，3-Epoch 设置：GSM8K 约 13 GPU 小时；Optimal-Epoch 设置：CNN/Daily Mail 约 200 GPU 小时。
  - CodeGen-350M→Phi-2 配置下，3-Epoch：GSM8K 约 15 GPU 小时；Optimal-Epoch：CNN/Daily Mail 约 700 GPU 小时。
- 论文未提供精确的功耗或总算力，但基于实验轮数做了合理估算。

### 5. 实验数量与充分性
- **主要实验**：5 个任务 × 2 种模型配置 × 2 种训练设置 = **20 组**，每组报告 token 接受率 α。
- **消融实验**：4 个维度（token 选择机制、训练方法、蒸馏方法、选择比例），共计约 8 组。
- **额外实验**：壁钟加速（2 任务）、与 EAGLE 集成（1 任务）、更大模型（1 任务）、混合数据集（1 任务）——总计约 5 组。
- **充分性判断**：实验覆盖了算术推理、指令跟随、代码生成、摘要等多种能力，涉及同族与跨族模型，并进行了多模态消融。实验数量较充分，对比方法设置一致（同为 3-epoch 或 optimal-epoch），公平性较好。但未报告误差棒（因计算成本高），仅通过多设置验证趋势，统计显著性有待加强。

### 6. 主要结论与发现
- AdaSPEC 在所有任务和所有模型配置上 **一致优于** DistillSpec，token 接受率提升最高达 **15%**（如 Pythia-31M→1.4B 在 GSM8K 的 3-Epoch 实验中，接受率从 57.58% 提升至 62.63%）。
- 分析显示：AdaSPEC 的预测错误几乎构成 DistillSpec 错误集的子集，表明选择性训练有效减少了难以对齐的 token 干扰。
- 当目标模型与草稿模型规模差距越大时，AdaSPEC 的相对改进越显著（例如 31M→1.4B 比 350M→2.7B 提升更明显）。
- 与 EAGLE 等先进 SD 方法正交集成，可获得额外加速（如 Vicuna-7B 上速度提升 7.45%）。
- 在混合数据集上，AdaSPEC 仍保持较好表现，遗忘较少。

### 7. 优点
- **方法简洁有效**：仅需引入一个参考模型和简单的 token 过滤步骤，不增加推理开销，且易于实现（核心代码约百行）。
- **广泛的适用性**：在多种任务、模型规模、甚至跨族模型上均有效，且能集成到更先进的 SD 框架中（如 EAGLE）。
- **实验设计全面**：覆盖了多个重要维度，包括消融、壁钟测试、更大模型验证、混合数据集，验证了方法的鲁棒性和正交性。
- **代码开源**：方便复现和扩展。
- **理论动机清晰**：明确指出传统 KD 目标与 SD 目标的不匹配，并针对性解决。

### 8. 不足与局限
- **过滤策略简单**：仅基于 KL 散度差进行硬阈值选择，未来可探索更自适应的过滤方法（如动态调整比例 k 或考虑语义重要性）。
- **未结合树状或多步验证**：虽然已展示与 EAGLE 的集成，但论文指出可进一步结合树状验证或更复杂的多步推测框架提升效率。
- **实验统计性不足**：未提供多次运行的误差棒或置信区间，结果可能受随机性影响（但通过多任务多设置补偿）。
- **训练成本增加**：需要额外训练一个参考模型，虽不增加推理成本，但训练总计算量略高于直接蒸馏。
- **蒸馏函数选择**：论文选择前向 KL 散度，而 DistillSpec 使用 TVD（总变差距离）配合长时间训练（30 万步），两者训练策略差异可能影响对比公平性。论文认为前向 KL 在有限 epoch 下更优，但需更多验证。
- **应用限制**：当前实验限于 GPT-like decoder-only 模型，对于 encoder-decoder 架构或非自回归模型可能需调整。另外，对极长序列或 streaming 场景的适用性未探索。

（完）
