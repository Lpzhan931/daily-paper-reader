---
title: "SpeCache: Speculative Key-Value Caching for Efficient Generation of LLMs"
title_zh: SpeCache：用于大语言模型高效生成的投机性键值缓存
authors: "Shibo Jie, Yehui Tang, Kai Han, Zhi-Hong Deng, Jing Han"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=PQIrsaIQdn"
tags: ["query:llm"]
score: 8.0
evidence: 投机性KV缓存卸载提升大语言模型效率
tldr: 本文提出SpeCache，利用CPU大容量内存卸载完整的KV缓存，并在解码时动态获取所需KV对，避免了传统压缩导致的信息丢失。在长序列任务中，SpeCache在保持生成精度的同时大幅降低GPU显存占用，提升了LLM的端到端吞吐量。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-pqirsaiqdn/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 853, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqirsaiqdn/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1668, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqirsaiqdn/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1672, \"height\": 773, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqirsaiqdn/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 865, \"height\": 961, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqirsaiqdn/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 838, \"height\": 392, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-pqirsaiqdn/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1622, \"height\": 1330, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqirsaiqdn/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1618, \"height\": 937, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqirsaiqdn/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1551, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqirsaiqdn/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1671, \"height\": 371, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqirsaiqdn/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 820, \"height\": 305, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqirsaiqdn/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1718, \"height\": 900, \"label\": \"Table\"}]"
motivation: 长序列任务中KV缓存线性增长导致GPU显存不足，现有压缩方法会造成信息丢失。
method: 将完整KV缓存卸载到CPU内存，解码时根据预测动态预取相关KV对到GPU，实现无损且高效的缓存管理。
result: "在多种长文本基准上，显存占用降低50%以上，同时保持与全缓存几乎一致的生成质量。"
conclusion: 投机性KV缓存卸载是解决LLM长序列推理显存瓶颈的有效方法。
---

## Abstract
Transformer-based large language models (LLMs) have already achieved remarkable results on long-text tasks, but the limited GPU memory (VRAM) resources struggle to accommodate the linearly growing demand for key-value (KV) cache as the sequence length increases, which has become a bottleneck for the application of LLMs on long sequences. Existing KV cache compression methods include eviction, merging, or quantization of the KV cache to reduce its size. However, compression results in irreversible information forgetting, potentially affecting the accuracy of subsequent decoding. In this paper, we propose SpeCache, which takes full advantage of the large and easily expandable CPU memory to offload the complete KV cache, and dynamically fetches KV pairs back in each decoding step based on their importance measured by low-precision KV cache copy in VRAM. To avoid inference latency caused by CPU-GPU communication, SpeCache speculatively predicts the KV pairs that the next token might attend to, allowing us to prefetch them before the next decoding step which enables parallelization of prefetching and computation. Experiments on LongBench and Needle-in-a-Haystack benchmarks verify that SpeCache effectively reduces VRAM usage while avoiding information forgetting for long sequences without re-training, even with a 10x high KV cache compression ratio.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：Transformer-based LLM在长文本任务中，key-value (KV) cache随序列长度线性增长，导致有限GPU显存（VRAM）成为瓶颈，限制长序列部署，尤其在边缘设备上。
- **现有方法局限**：
  - 架构修改（如GQA、线性注意力）需重新预训练，不适用于现有模型。
  - 后训练压缩（如逐出、合并、量化）会不可逆地丢失信息，可能影响后续解码精度。
  - 完全卸载到CPU内存虽可避免压缩损失，但频繁CPU-GPU通信引入巨大推理延迟。
- **核心观察**：LLM注意力具有高度稀疏性，且稀疏性依赖于查询（query）：每个查询仅关注少量KV对，且不同查询关注不同KV对。因此，动态预取而非静态压缩是更好的策略。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：SpeCache将完整16-bit KV缓存存储在CPU内存中，同时在GPU中维护一份低比特（2-bit甚至1-bit）KV缓存副本。在每一步解码时，利用低比特副本和额外解码的“投机token”预测下一token将关注的top-k重要KV对，并提前将它们从CPU预取到GPU，从而实现预取与计算的并行化，避免延迟增加。
- **关键技术细节**：
  - **三段式推理流程**：
    1. **Prefilling（预填充）**：逐层处理，每层注意力计算完成后，将原始16-bit KV缓存量化并卸载到CPU，释放GPU空间。
    2. **Pre-decoding（预解码）**：利用第一个输出token生成一个“投机token”作为下一token的近似，并记录该token的top-k KV对索引，开始预取对应的16-bit KV对。
    3. **Decoding（解码）**：每个解码步骤中同时解码两个token：输出token（准确）和投机token（近似）。投机token用于预测下一解码步骤的top-k KV对索引，从而提前预取。
  - **并行化实现**：预取操作与后续层的计算并行执行，利用LLM解码阶段的内存I/O瓶颈特性（GPU利用率低），同时解码两个token几乎不增加单步延迟。
  - **量化方法**：SpeCache可兼容任意后训练KV缓存量化方法。本文使用KIVI进行2-bit和1-bit量化，并针对1-bit场景改进了零点和缩放因子，以减小量化误差（假设权重均匀分布，调整量化区间中点）。
- **算法流程**（文字说明）：每个注意力层中，输入当前token和投机token，计算注意力时使用GPU中的低比特KV缓存加上已预取的top-k 16-bit KV缓存；计算过程中记录投机token的注意力分数最高的k个索引，用于下一轮预取；同时将新生成的KV对量化和卸载，淘汰不再需要的16-bit KV对。全部操作并行于后续层计算。

## 3. 实验设计
- **数据集/场景**：
  - **LongBench**：包含15个长文本任务（论文主表报告了10个代表性任务，完整结果在附录）：Qasper、MultiFieldQA、HotpotQA、2WikiMQA、MuSiQue、GovReport、MultiNews、PassageRetrieval、LCC、RepoBench-P等。
  - **Needle-in-a-Haystack (NIAH)**：压力测试，在长上下文中插入一句特定信息，评估模型检索能力，使用GPT-4评分（1-10分）。
- **对比方法**：
  - 完全KV缓存（16-bit）、InfLLM、StreamLLM、H2O、KIVI（2-bit和1-bit，不同组大小）。
  - 对比场景涵盖不同压缩率（0.25×、0.13×、0.11×等）。
- **模型**：LLaMA-2-7B-Chat、LLaMA-2-13B-Chat、Mistral-7B-Instruct-v0.2、LLaMA-3-8B-Instruct。序列长度根据模型最大上下文设置（LLaMA-2 4k、Mistral 32k、LLaMA-3 8k）。

## 4. 资源与算力
- **GPU型号**：单张NVIDIA A6000（48GB VRAM）。
- **训练时长**：SpeCache是训练无关（training-free）方法，无需额外训练，因此没有训练时长。仅需前向推理。
- **实验设置**：CPU-GPU传输使用PyTorch多流机制和`Tensor.copy()`实现，作者指出自定义低级算子可进一步提升效率。

## 5. 实验数量与充分性
- **实验数量**：
  - LongBench：在4个模型、多种量化设置（2-bit g=32/64, 1-bit g=32/64）上报告了平均性能，并与3种基线（InfLLM、StreamLLM、H2O）在两种压缩率下对比。
  - NIAH：在Mistral和LLaMA-3上对比16-bit、1-bit、SpeCache+1-bit三种设置。
  - 效率测试：3种上下文长度（2k/8k/32k）下的最大吞吐量对比。
  - 消融实验：
    1. 预取数量k的消融（k=0,16,32,64,128,256）。
    2. 与非投机预取（使用准确输出token而非投机token）的延迟和精度对比。
    3. 改进1-bit量化方法（原始KIVI vs 改进版）的消融。
  - 完整LongBench 15个任务结果见附录。
- **充分性评价**：实验覆盖了主流模型、多种压缩率、多种基线，消融实验较为全面。但缺乏在多GPU或分布式环境下的性能数据，且未对比更近期的量化方法（如ZipCache、KVQuant）。整体充分，结论可信。

## 6. 主要结论与发现
- SpeCache在保持与全精度KV缓存几乎一致的生成质量（LongBench平均精度下降<2%）的同时，可将GPU KV缓存大小压缩至10%（1-bit + g=64），优于H2O、InfLLM等基线。
- 在Needle-in-a-Haystack任务中，SpeCache恢复因1-bit量化丢失的长上下文检索能力，性能接近16-bit缓存。
- 吞吐量提升显著：在32k上下文下，SpeCache支持36 batch size（原始仅3），吞吐量提升4.6倍。
- 投机预取相比非投机预取可大幅降低解码延迟（如2-bit场景从877ms降至643ms），证明了并行化预取的重要性。
- 改进的1-bit量化方法对SpeCache性能至关重要，原始KIVI 1-bit导致模型崩溃，改进后性能恢复。

## 7. 优点
- **训练无关**：无需微调或预训练，即插即用。
- **避免信息损失**：完整KV缓存保存在CPU，仅动态预取，不因压缩永久丢失信息。
- **并行化预取**：投机token使预取与GPU计算重叠，几乎不增加解码延迟。
- **可组合性**：可与任意后训练量化方法结合，且量化精度越高，SpeCache效果越显著。
- **效率高**：在长序列和大batch下吞吐量提升明显，尤其适合GPU显存受限场景。

## 8. 不足与局限
- **依赖量化精度**：当低比特副本过于粗糙（如原始1-bit量化），投机预测的准确性可能下降，导致预取命中率降低。虽改进量化方法，但仍有限制。
- **硬件依赖**：实验仅在单张A6000上进行，未验证在多GPU、不同架构（如更慢CPU、PCIe带宽限制）下的表现。CPU-GPU传输带宽可能成为瓶颈。
- **额外内存开销**：GPU仍需保留低比特KV缓存和少量16-bit预取缓存，虽然远小于全精度，但并非完全“零额外”显存。
- **投机token的一次性开销**：预解码阶段增加了一个额外解码步骤，对于极短输出（如几句话）可能带来相对明显开销。
- **未与其他卸载方法（如FlexGen、ShadowKV）进行直接深度对比**，仅与压缩方法比较。
- **需用户调整超参数k**：k值影响性能与传输量之间的trade-off，不同场景可能需要手动调优。

（完）
