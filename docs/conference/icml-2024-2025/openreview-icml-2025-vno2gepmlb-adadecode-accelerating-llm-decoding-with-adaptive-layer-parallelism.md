---
title: "AdaDecode: Accelerating LLM Decoding with Adaptive Layer Parallelism"
title_zh: AdaDecode：基于自适应层并行的LLM解码加速
authors: "Zhepei Wei, Wei-Lin Chen, Xinyu Zhu, Yu Meng"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=VnO2GEpmlb"
tags: ["query:llm"]
score: 7.0
evidence: 通过自适应层并行加速LLM解码，与投机解码对比
tldr: LLM自回归解码受限于顺序生成。AdaDecode方法采用自适应层并行，在不依赖额外草案模型的情况下实现加速。实验表明在长内容生成中降低延迟，避免了投机解码的额外内存开销，为解码加速提供新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-vno2gepmlb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1771, \"height\": 648, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vno2gepmlb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1781, \"height\": 594, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vno2gepmlb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1784, \"height\": 400, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vno2gepmlb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 812, \"height\": 432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vno2gepmlb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1773, \"height\": 428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vno2gepmlb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1785, \"height\": 422, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-vno2gepmlb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1763, \"height\": 374, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vno2gepmlb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1749, \"height\": 1097, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vno2gepmlb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1666, \"height\": 386, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vno2gepmlb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1698, \"height\": 206, \"label\": \"Table\"}]"
motivation: 自回归解码顺序依赖限制并行性，现有投机解码需额外草案模型。
method: 提出自适应层并行解码策略，根据上下文动态决定并行层数。
result: 在长内容生成中有效降低延迟，无需草案模型。
conclusion: AdaDecode提供一种轻量级解码加速方案，避免投机解码的缺点。
---

## Abstract
Large language models (LLMs) are increasingly used for long-content generation (e.g., long Chain-of-Thought reasoning) where decoding efficiency becomes a critical bottleneck: Autoregressive decoding is inherently limited by its sequential token generation process, where each token must be generated before the next can be processed. This sequential dependency restricts the ability to fully leverage modern hardware’s parallel processing capabilities. Existing methods like speculative decoding and layer skipping offer potential speedups but have notable drawbacks: speculative decoding relies on an auxiliary “drafter” model, which can be challenging to acquire and increases memory overhead, while layer skipping may introduce discrepancies in the generated outputs due to the missing key-value cache at skipped layers. In this work, we propose AdaDecode, which accelerates LLM decoding without requiring auxiliary models or changes to the original model parameters, while ensuring output consistency. AdaDecode leverages the insight that many tokens—particularly simple or highly-predictable ones—can accurately be generated at intermediate layers, as further layers often do not significantly alter predictions once the model reaches a certain confidence. By adaptively generating tokens at intermediate layers when confidence is high, AdaDecode enables the next token’s computation to begin immediately. The remaining layer computations for early-predicted tokens are deferred and executed in parallel with subsequent tokens when needed, maximizing hardware utilization and reducing decoding latency. A final verification step ensures that early predictions match the results of standard autoregressive decoding, preserving output parity. Experiments across diverse generation tasks shows that AdaDecode consistently achieves superior decoding throughput compared to baselines with up to 1.73$\times$ speedup, while guaranteeing output parity with standard autoregressive decoding.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机与背景）

大型语言模型（LLM）的自回归解码过程存在本质的顺序依赖——每个 token 的生成必须等待前一个 token 完全处理完毕，导致无法充分利用现代硬件的并行计算能力。随着模型规模持续增长（百亿至万亿参数）以及长内容生成场景（如长链式推理 CoT）的兴起，解码效率已成为关键瓶颈。

现有加速方法存在明显缺陷：
- **投机解码（Speculative Decoding）**：依赖额外的“草案模型”（drafter），增加了内存开销，且要求草案模型与主模型共享相同的 tokenizer 和词汇表，获取成本高。
- **层跳过（Layer Skipping）**：跳过部分层虽可减少计算，但会导致被跳过层的 KV cache 缺失，造成未来 token 预测的偏差，无法保证输出一致性。

作者提出 AdaDecode，旨在**在不依赖辅助模型、不修改原始模型参数的前提下，加速自回归解码并严格保证输出与标准解码一致**。

---

## 2. 方法论：核心思想、关键技术细节与算法流程

### 2.1 核心洞察
许多 token（尤其是简单、高可预测性的 token）在模型的**中间层**就已能达到足够的置信度，后续层往往不会显著改变预测结果。基于此，AdaDecode 允许在中间层**自信地提前预测**下一个 token，并**立即开始处理后续 token**，而将提前预测 token 的剩余层计算（KV cache）推迟到后续步骤中并行执行。

### 2.2 关键技术

#### （1）轻量级中间层 LM 头（Lightweight LM Head）
- 在每个候选早期预测层 \( l^{(i)} \) 上添加一个可训练的 LM 头 \( \theta^{(i)} = \{ e_t^{(i)} \}_{t \in \mathcal{V}} \)（权重矩阵 \( E^{(i)} \in \mathbb{R}^{|\mathcal{V}| \times d} \)）。
- 训练目标：以最后一层的预测分布 \( p^*(t|h^*) \) 为监督，最小化 KL 散度：
  \[
  \mathcal{L}(\theta^{(i)}) = \mathrm{KL}\left( p^*(t|h^*) \parallel p_{\theta^{(i)}}(t|h^{(i)}) \right)
  \]
- 原始模型参数（包括最后一层 LM 头 \( E^* \)）**完全冻结**。
- **参数高效实现**：将 \( E^{(i)} \) 分解为 \( E^{(i)} = E^* T^{(i)} \)，其中 \( T^{(i)} \in \mathbb{R}^{d \times d} \) 为可学习变换矩阵。由于 \( d \ll |\mathcal{V}| \)，可大幅减少参数（如 Llama3.1-8B 中每头仅 16M 参数，而全参数化需 0.5B，节省约 31×）。

#### （2）自适应层并行（Adaptive Layer Parallelism）
- 当中间层 LM 头的预测概率超过阈值 \( \gamma \) 时，立即输出该 token 并**开始处理下一个 token 的前几层**。
- 已被提前预测的 token 的剩余层 KV cache 计算被**推迟**到后续解码步骤中**与其他 token 并行执行**（相同颜色的层可并行）。
- 算法流程（简化）：
  1. 处理用户 prompt，初始化 KV cache。
  2. 对当前 token \( t_i \)，从第 1 层开始顺序处理。
  3. 在每一候选中间层，若 \( p_{\theta^{(i)}}(t_{i+1}|h^{(i)}) > \gamma \)，则立即采样出 \( t_{i+1} \)，将当前 token 加入该层及之后所有层的并行处理列表，并 break 开始处理下一个 token。
  4. 若一直处理到最后一层，则对并行列表中的所有 token 进行验证（见下一步）。
  5. 当所有提前预测的 token 的 KV cache 计算完成后，执行验证。

#### （3）验证步骤（Verification）
- 使用修改的拒绝采样方案（类似投机解码）：
  - 接受概率：\( \min\left(1, \frac{p^*(t'|h^*)}{p_{\theta^{(i)}}(t'|h^{(i)})}\right) \)。
  - 若接受，继续验证下一个提前预测的 token。
  - 若拒绝，从调整后的分布 \( \mathrm{Normalize}(\max(0, p^* - p_{\theta^{(i)}})) \) 中重新采样替换 token，并丢弃后续所有 KV cache，恢复标准解码。
- 保证与标准自回归解码的**输出完全一致**。

### 2.3 算法总览
AdaDecode 整体流程见 Algorithm 1（原文）。核心循环：对当前 token，逐层处理，一旦中间层置信度足够高则提前预测并启动并行；所有提前预测的 token 的剩余层随后并行计算；最后验证，通过则继续，否则回退重采样。

---

## 3. 实验设计

### 3.1 数据集与任务
| 任务 | 数据集 | 评价指标 |
|------|--------|----------|
| 文本摘要 | XSum（测试集 1K 样本） | 吞吐量（tokens/s） |
| 代码生成 | HumanEval（164 样本） | 吞吐量 |
| 数学推理 | GSM8K（1K 样本） | 吞吐量 |

训练数据：XSum 用训练集 10K 样本；HumanEval 用 MBPP 全部 974 样本（无训练集时）；GSM8K 用 7.5K 训练样本。

### 3.2 基准方法
- **Vanilla Decoding**（标准自回归解码，作为 1× 基准）
- **SpecDecode**（投机解码）：使用较小的草案模型（如 Llama3.2-1B、CodeLlama-7B/13B）
- **Self-SpecDecode** / **SWIFT**：自投机解码（层跳过 + 验证）
- **LookAhead**：基于 Jacobi 解码的并行 n-gram 生成

### 3.3 骨干模型
- Llama3.1-8B-Instruct
- CodeLlama-13B-Instruct
- CodeLlama-34B-Instruct

所有方法均使用 instruction-tuned 版本及默认聊天模板，采样温度设为 0 以确保可复现。

### 3.4 硬件与训练配置
- **训练**：8× Nvidia A100 GPU，DeepSpeed ZeRO-3，FlashAttention，BF16 混合精度。
- **超参数**：Adam 优化器，100 epochs，batch size 128，学习率 5e-3，余弦学习率调度（3% warmup）。
- **推理**：在相同 GPU 上进行，最大新 token 数 512，阈值 γ=0.75，最大早期预测数 5。

---

## 4. 算力与资源

- 训练使用了 **8 张 Nvidia A100 GPU**，采用 DeepSpeed ZeRO-3 和 FlashAttention 加速。
- 训练时长未明确给出，仅提到训练了 100 epochs，batch size 128。
- 推理时未特别说明算力需求，但相比标准解码，AdaDecode 会引入额外并行计算（可能增加峰值显存），但整体吞吐量显著提升。

（论文未提供精确的训练时间或 GPU 小时数。）

---

## 5. 实验数量与充分性

### 5.1 主实验（表 2）
- 在 3 个任务 × 3 个骨干模型上共 9 组主实验，对比 4–5 种基线方法。
- 每个设置下报告吞吐量和加速比，最高加速 1.73×。

### 5.2 消融实验（表 3）
- 对 5 个变体进行消融：
  - 无验证（一致性降至 0.652）
  - 固定层早期预测（速度略降）
  - 使用原始 LM 头（速度反而降低）
  - 混合域训练 LM 头（速度下降）
  - 全参数化 LM 头（参数多但速度相近）
- 实验充分覆盖了各组件的贡献。

### 5.3 输出一致性分析（图 4）
- 在 HumanEval 上对比所有方法输出与标准解码的字符串匹配率，均接近 100%（0.97–0.99），说明数值精度导致微小偏差但整体一致。

### 5.4 超参数敏感度分析（图 5）
- 对阈值 γ 从 0 到 1 进行扫描，考察加速比、早期预测率、验证拒绝率。
- 发现 γ 在合理范围内（0.4–0.9）表现稳定，拒绝率仅约 5%，说明方法鲁棒。

### 5.5 基线超参数敏感性（附录 C，图 6）
- 对 SpecDecode（不同 n 和阈值）、Self-SpecDecode（贝叶斯优化迭代次数）进行扫描，指出基线需要仔细调参才能获得良好效果。

**结论**：实验设计充分、客观、公平。覆盖了多个任务、模型、基线，消融和敏感性分析完备，且公开代码和置信。未发现明显不公平比较（所有方法在同一硬件、相同温度下运行）。

---

## 6. 主要结论与发现

1. **AdaDecode 在多种任务和模型上一致优于所有基线**，最高达到 1.73× 加速（CodeLlama-34B 在 HumanEval 上）。
2. **严格保证输出一致性**：验证步骤确保与标准自回归解码的输出完全一致（实际一致性比率 0.996–0.999）。
3. **无需辅助模型或修改原模型参数**，仅需训练少量轻量级 LM 头（每头 16M 参数），内存开销极低。
4. **对超参数 γ 鲁棒**：在 0.4–0.9 范围内均能获得显著加速，拒绝率低。
5. **高位信心阈值下早期预测准确率高**：约 95% 的早期预测通过验证，说明中间层 LM 头能很好地逼近最终预测。

---

## 7. 优点

- **方法简洁高效**：仅需在中间层添加轻量级 LM 头（参数分解技巧），无需修改原模型架构或进行昂贵训练。
- **灵活性高**：早期预测可在任意中间层动态触发（自适应深度），而非固定层。
- **保证输出一致性**：通过验证步骤严格消除与标准解码的偏差，这是许多层跳过方法所不具备的。
- **实验严谨全面**：覆盖多个任务、模型、基线，消融和敏感性分析详尽，公开代码可复现。
- **实用性强**：无需额外草案模型，特别适合无法获取合适草案模型的场景；也可与水平加速方法（如树状投机解码）结合（虽附录显示需进一步优化但方向明确）。
- **参数高效**：轻量头设计比全参数化头节约 31× 参数，且性能相当。

---

## 8. 不足与局限

- **仅关注垂直加速**：论文主要针对层内并行（垂直加速），与水平加速（跨时间步）的集成效果不佳（附录 E 显示简单结合不提升性能），需要更深入的研究。
- **需要任务特定训练**：轻量级 LM 头需在目标任务训练数据上训练（专用头优于通用头），在训练数据缺失或快速切换到新任务时可能受限。不过训练量很小（100 epochs，可离线进行）。
- **潜在 FLOPs 浪费**：当早期预测被拒绝时，已计算的后续层 KV cache 被丢弃，造成计算浪费。但论文指出拒绝率仅约 5%，实际影响小。
- **未评估对生成长度极长（如>2048 tokens）的场景**：实验最大新 token 512，对超长文本的并行效率有待验证。
- **未与其他硬件优化（如 vLLM、FlashAttention）进行联合测评**：实际部署中可能需进一步调优。
- **依赖置信度阈值**：虽然鲁棒，但最优 γ 仍需简单调优（0.75 附近）。
- **伦理风险**：未直接涉及，但 LLM 解码加速可能放大现有问题（如幻觉、偏见），需谨慎使用。

---

（完）
