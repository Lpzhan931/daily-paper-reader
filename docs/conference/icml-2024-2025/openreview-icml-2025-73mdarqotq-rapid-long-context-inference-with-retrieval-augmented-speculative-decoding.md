---
title: "RAPID: Long-Context Inference with Retrieval-Augmented Speculative Decoding"
title_zh: RAPID：基于检索增强投机解码的长上下文推理
authors: "Guanzheng Chen, Qilong Feng, Jinjie Ni, Xin Li, Michael Qizhe Shieh"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=73mDARqOtQ"
tags: ["query:llm"]
score: 8.0
evidence: 长上下文LLM推理加速，结合投机解码与检索增强
tldr: 长上下文LLM推理面临KV缓存导致的内存瓶颈，传统投机解码效果下降。RAPID方法引入检索增强的草案模型，在缩短的检索上下文中推测，加速推理并保持质量。实验表明在长序列生成中显著提升速度，同时兼容现有解码策略。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-73mdarqotq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 815, \"height\": 542, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-73mdarqotq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1654, \"height\": 499, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-73mdarqotq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 830, \"height\": 1003, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-73mdarqotq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1691, \"height\": 912, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-73mdarqotq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 798, \"height\": 231, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-73mdarqotq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 798, \"height\": 415, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-73mdarqotq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 629, \"height\": 303, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-73mdarqotq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1175, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-73mdarqotq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 771, \"height\": 230, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-73mdarqotq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1084, \"height\": 230, \"label\": \"Table\"}]"
motivation: 长上下文推理中KV缓存操作成为内存瓶颈，传统投机解码效果下降。
method: 提出RAPID框架，用检索增强的草案模型在缩短的上下文上推测，再经目标模型验证。
result: 在长上下文场景中实现显著加速，同时保持生成质量。
conclusion: RAPID有效结合RAG与投机解码，解决长上下文推理效率问题。
---

## Abstract
The emergence of long-context large language models (LLMs) offers a promising alternative to traditional retrieval-augmented generation (RAG) for processing extensive documents. However, the computational overhead of long-context inference presents significant efficiency challenges. While Speculative Decoding (SD) traditionally accelerates inference using smaller draft models, its effectiveness diminishes substantially in long-context scenarios due to memory-bound KV cache operations. We introduce Retrieval-Augmented Speculative Decoding (RAPID), which leverages RAG for both accelerating and enhancing generation quality in long-context inference. RAPID introduces the RAG drafter—a draft LLM operating on shortened retrieval contexts—to speculate on the generation of long-context target LLMs. Our approach enables a new paradigm where same-scale or even larger LLMs can serve as RAG drafters while maintaining computational efficiency. To fully leverage the potentially superior capabilities from stronger RAG drafters, we develop an inference-time knowledge transfer that enriches the target distribution by RAG. Extensive experiments on the LLaMA-3.1 and Qwen2.5 backbones demonstrate that RAPID effectively integrates the strengths of both RAG and long-context LLMs, achieving significant performance improvements (e.g., from 39.33 to 42.83 on InfiniteBench for LLaMA-3.1-8B) with more than 2$\times$ speedups for long-context inference. Our analyses also reveal the robustness of RAPID across various context lengths and retrieval quality.

---

## 论文详细总结（自动生成）

# RAPID: 长上下文推理中的检索增强投机解码——中文详细总结

## 1. 核心问题与整体含义（研究动机和背景）
长上下文大语言模型（LLMs）能够直接处理百万级词元的文档，为传统检索增强生成（RAG）提供了有前景的替代方案。然而，长上下文推理面临严重的计算效率瓶颈：处理庞大的键值（KV）缓存时，操作受限于内存带宽，导致显著延迟。传统投机解码（Speculative Decoding, SD）通过使用更小的草案模型生成多个候选词元并由目标模型验证来加速推理，但在长上下文场景中，由于KV缓存操作的内存瓶颈，小模型的速度优势急剧下降（例如，LLaMA-3.1-8B相对70B的吞吐量优势从1K上下文时的23.6倍降至128K时的9.4倍）。因此，需要一种新的方法来克服长上下文推理的效率挑战，同时保持甚至提升生成质量。

## 2. 方法论：核心思想、关键技术细节、公式与算法流程
### 核心思想
RAPID将检索增强生成（RAG）与投机解码相结合：使用一个**RAG草案模型**（基于缩短的检索上下文运行的LLM）为长上下文目标模型生成候选词元，并通过**检索增强的目标分布**实现推理时的知识迁移，从而融合RAG和长上下文LLM的互补优势。

### 关键技术细节
- **RAG草案模型**：目标模型处理完整长上下文 $C$，而RAG草案模型仅处理检索到的压缩上下文 $C_S$（$|C_S| \ll |C|$）。检索通过将上下文分块（512词元/块）、使用BGE-M3嵌入并基于余弦相似度选取top-k块实现，检索长度限制在4096词元至输入长度的1/24之间。
- **自投机与向上投机**：RAPID支持两种设置：
  - 自投机（self-speculation）：目标LLM与RAG草案模型规模相同。
  - 向上投机（upward-speculation）：RAG草案模型规模大于目标LLM（例如用70B草案辅助8B目标）。
- **检索增强的目标分布**：为解决传统SD的严格接受准则可能拒绝高质量候选的问题，RAPID将RAG草案视为教师、目标模型视为学生，通过知识蒸馏的梯度推导出分布偏移项，得到增强后的目标分布 $\hat{p}(x_i)$：
  $$\hat{p}(x_i) = \text{softmax}\left(z(x_i)/T + \eta(q(x_i) - p(x_i))\right)$$
  其中 $\eta$ 控制知识迁移强度，$z(x_i)$ 为目标模型原始logits，$p(x_i)$ 为原始目标分布，$q(x_i)$ 为RAG草案分布。
- **验证与残差采样**：接受准则改为 $r \leq \min(1, \hat{p}(x')/q(x'))$。拒绝时，从调整后的残差分布采样，理论上保证最终采样分布与原始目标分布一致（附录B证明）。

### 算法流程（文字说明）
1. 对于每个解码步骤，RAG草案模型在检索上下文 $C_S$ 上生成 $\gamma$ 个候选词元。
2. 逐一验证：对每个候选，计算目标模型的原始logits $z$ 和分布 $p$，以及草案模型分布 $q$；根据公式（8）得到增强logits $\hat{z}$，进而得到 $\hat{p}$；按接受准则判断是否接受。
3. 若接受则保留候选，继续下一个；若拒绝则从残差分布采样，并终止该步的投机。
4. 重复直至生成完整序列。

## 3. 实验设计：数据集、基准、对比方法
### 数据集与基准
- **∞Bench**：包含长文本问答（En.QA，F1）、多项选择（En.MC，准确率）、摘要（En.Sum，ROUGE-L）三个任务，上下文长度超过100K词元。
- **LongBench v2**：多任务基准，涵盖多种上下文长度（8K–2M词元），实验中使用中截断使上下文限制在128K词元内。主要报告Overall分数及CoT子集结果。
- **多轮对话评测**：基于MT-Bench-101构造约122K词元历史对话的挑战集，由GPT-4-Turbo-1106作为评判器（LLM-as-a-Judge）打分。

### 对比方法
- **LC**：目标LLM直接在长上下文上生成。
- **RAG**：目标LLM在RAG草案模型使用的检索上下文上生成。
- **SD**：传统投机解码，使用与RAPID相同的草案模型但基于原始目标分布。
- **MagicDec**：利用StreamingLLM压缩草案模型KV缓存的方法。
- 附加实验中还对比了TriForce（基于LLaMA2-7B架构的层次投机解码）和MInference（稀疏注意力加速预填充）。

## 4. 资源与算力
论文明确说明了实验使用的GPU配置：
- 小模型（LLaMA-3.1-8B、Qwen2.5-7B）：单张NVIDIA A800 80GB GPU。
- 大模型（LLaMA-3.1-70B、Qwen2.5-72B）：8张A800 80GB GPU（分布式）。
- 向上投机配置：目标模型（8B/7B）用1张GPU，额外7张GPU服务于更大的RAG草案模型。
- 未明确说明训练时长或能耗，所有实验为推理阶段评估。

## 5. 实验数量与充分性
- 主要实验：在LLaMA-3.1（8B、70B）和Qwen2.5（7B、72B）两个系列上进行了自投机和向上投机的全面评估，覆盖∞Bench和LongBench v2，报告了性能（F1/准确率/ROUGE）和效率（预填充时间、加速比）。
- 补充分析：
  - 相对成功/失败分析（图2）：显示RAPID整合了目标和草案模型的优势，甚至出现两者都失败但RAPID成功的“涌现现象”。
  - 上下文长度与检索长度的影响（图3）：在4K–128K目标上下文和4K–32K检索长度下测试，展示一致优势。
  - 多轮对话质量评估（表2）：使用GPT-4评估生成质量与吞吐量。
  - 鲁棒性测试（表3）：在无关检索上下文中改变知识迁移强度$\eta$，检验性能变化。
  - 与其他方法（TriForce、MInference）的附加对比。
- **充分性评价**：实验覆盖多种模型规模、多种任务、多种设置（自/向上投机），并进行了消融和鲁棒性分析，设计较为全面。但未涉及更大规模模型（如LLaMA-3.1-405B）或更极端长度（>128K）的严格测试，可能存在一定偏差。

## 6. 主要结论与发现
- **效率与质量双提升**：RAPID在自投机设置中实现超过2倍加速（如LLaMA-3.1-8B达2.10×，LLaMA-3.1-70B达2.69×），同时性能优于单独使用长上下文或RAG。例如，∞Bench上LLaMA-3.1-8B从LC的39.33提升至42.83。
- **向上投机显著增强性能**：用70B草案辅助8B目标，性能从42.83提升至49.98（∞Bench），甚至超过70B单独使用LC的结果（45.07），且效率与8B目标相近。
- **检索增强分布的有效性**：相对于传统SD，RAPID在相同设置下获得更高接受率（75-85% vs 60-70%）和更大幅度的性能提升。
- **鲁棒性**：即使使用无关检索上下文，在合理$\eta$范围内（≤20）RAPID仍保持正收益；更强的草案模型（向上投机）表现出更好的鲁棒性。
- **实际应用优势**：在多轮对话任务中，RAPID质量评分（4.21）显著高于LC（2.82）和RAG（3.95），吞吐量达18.18 tok/s（1.7倍加速）。

## 7. 优点
- **方法创新性**：将RAG与投机解码有机结合，首次利用RAG草案模型实现长上下文的加速，并设计检索增强分布实现知识迁移，解决了传统SD在长上下文中的效率退化问题。
- **范式突破**：允许相同规模甚至更大规模的LLM作为草案模型（向上投机），打破了传统SD“草必须小于目标”的限制。
- **理论保证**：残差采样经过证明保持了目标模型分布的一致性（附录B），方法可被用作即插即用的解码策略。
- **实验全面深入**：覆盖多个模型族、多种任务、自/向上投机、消融、鲁棒性测试，分析详细（如相对成功/失败、涌现现象）。
- **开源代码**：论文附有GitHub代码链接，有利于复现和应用。

## 8. 不足与局限
- **实验覆盖的局限性**：仅测试了LLaMA-3.1和Qwen2.5系列，未涉及其他主流模型（如Gemini、GPT-4等闭源模型或Mistral等其他开源模型）。最大上下文仅128K，未验证超长（>1M）的表现。
- **检索质量的潜在偏差**：论文使用固定检索策略（BGE-M3 + 余弦相似度），未比较不同检索器或检索粒度的影响。在无关检索测试中，自投机设置下$\eta>20$时性能下降明显，说明对超参数较为敏感。
- **额外开销**：需额外运行RAG pipeline（嵌入、检索、筛选），尽管论文称其边际成本低（约1.43秒），但在对延迟极度敏感的场景中仍需考虑。
- **向上投机的资源需求**：向上投机需要额外GPU承载更大草案模型，虽然效率可观但硬件成本增加。
- **未讨论训练方面**：RAPID完全作为推理阶段方法，不涉及模型微调或预训练，可能无法充分适应特定领域。
- **多轮对话质量评估的局限性**：使用GPT-4作为评判者可能存在固有偏差，且仅测试了单次构造的数据集。

（完）
