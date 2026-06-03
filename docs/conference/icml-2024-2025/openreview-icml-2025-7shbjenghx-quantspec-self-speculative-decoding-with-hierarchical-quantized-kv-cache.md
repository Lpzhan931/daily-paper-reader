---
title: "QuantSpec: Self-Speculative Decoding with Hierarchical Quantized KV Cache"
title_zh: QuantSpec：基于分层量化KV Cache的自投机解码
authors: "Rishabh Tiwari, Haocheng Xi, Aditya Tomar, Coleman Richard Charles Hooper, Sehoon Kim, Maxwell Horton, Mahyar Najibi, Michael W. Mahoney, Kurt Keutzer, Amir Gholami"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=7SHbJENgHX"
tags: ["query:llm"]
score: 8.0
evidence: 结合KV Cache量化的自投机解码
tldr: 本文提出QuantSpec框架，针对长上下文LLM推理中KV Cache成为瓶颈的问题，结合自投机解码与分层量化KV Cache。草稿模型共享目标模型架构但使用量化缓存，从而提升接受率并降低内存占用和延迟。实验表明QuantSpec在边缘设备上实现显著加速。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-7shbjenghx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 861, \"height\": 519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-7shbjenghx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1778, \"height\": 534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-7shbjenghx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1752, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-7shbjenghx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1589, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-7shbjenghx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 856, \"height\": 368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-7shbjenghx/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1787, \"height\": 554, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-7shbjenghx/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1080, \"height\": 923, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-7shbjenghx/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1064, \"height\": 890, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-7shbjenghx/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1064, \"height\": 714, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-7shbjenghx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1782, \"height\": 883, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-7shbjenghx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 765, \"height\": 258, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-7shbjenghx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 693, \"height\": 256, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-7shbjenghx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1669, \"height\": 583, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-7shbjenghx/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1666, \"height\": 535, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-7shbjenghx/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 861, \"height\": 273, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-7shbjenghx/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1497, \"height\": 1260, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-7shbjenghx/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1669, \"height\": 941, \"label\": \"Table\"}]"
motivation: 长上下文推理中KV Cache是主要瓶颈，现有投机解码因KV Cache优化不足导致接受率低。
method: 提出QuantSpec，使用分层量化KV Cache的草稿模型，与目标模型共享架构但缓存精度更低，实现自投机解码。
result: 实验显示QuantSpec在多个长上下文任务上显著降低延迟，同时保持生成质量。
conclusion: 通过量化KV Cache结合自投机解码，QuantSpec有效加速了LLM在资源受限场景下的推理。
---

## Abstract
Large Language Models (LLMs) are increasingly being deployed on edge devices for long-context settings, creating a growing need for fast and efficient long-context inference. In these scenarios, the Key-Value (KV) cache is the primary bottleneck in terms of both GPU memory and latency, as the full KV cache must be loaded for each decoding step. While speculative decoding is a widely accepted technique to accelerate autoregressive decoding, existing methods often struggle to achieve significant speedups due to inefficient KV cache optimization strategies and result in low acceptance rates. To address these challenges, we propose a novel self-speculative decoding framework, QuantSpec, where the draft model shares the architecture of the target model but employs a hierarchical 4-bit quantized KV cache and 4-bit quantized weights for acceleration. QuantSpec maintains high acceptance rates ($>$90\%) and reliably provides consistent end-to-end speedups upto $\sim2.5\times$, outperforming other self-speculative decoding methods that use sparse KV cache for long-context LLM inference. QuantSpec also reduces the memory requirements by $\sim 1.3\times$ compared to these alternatives.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）在长上下文推理中，Key-Value（KV）缓存成为主要的性能瓶颈。随着上下文长度增长，KV缓存占用大量GPU显存并且每次解码都需要加载完整缓存，导致高延迟。现有的投机解码方法虽能加速自回归生成，但往往因KV缓存优化策略不当而导致草稿与目标模型之间的接受率低，最终加速效果有限。
- **整体含义**：本文旨在通过结合量化技术与自投机解码，在不牺牲生成质量的前提下，显著提升长上下文LLM推理的吞吐量并降低显存占用，尤其适用于资源受限的边缘设备。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：提出QuantSpec——一种自投机解码框架。草稿模型与目标模型共享相同架构，但使用4比特量化权重和分层的4比特量化KV缓存。由于架构相同，草稿与目标模型的对齐更好，接受率更高；量化则减少了内存带宽需求，加速解码。
- **关键技术细节**：
  - **分层量化KV缓存**：将INT8表示分解为高4位和低4位两个INT4缓存。草稿模型仅加载高4位（INT4），目标模型加载全部8位（INT8），从而无需存储两份缓存。预填充阶段计算FP16 KV缓存的INT4表示，并进一步量化残差得到低4位。
  - **双全精度缓存缓冲区**：维护大小为2×组大小（G）的全精度缓冲区，分为两部分。草稿模型生成新token时存入全精度区，验证后每G步才对前一半进行量化并移动。这避免了频繁量化/反量化开销，并支持灵活丢弃拒绝token的缓存。
  - **量化策略**：键缓存沿通道轴量化，值缓存沿token轴量化，采用非对称量化、分组大小为128（等于头维度）。草稿模型还使用4比特量化权重。
- **公式/算法流程**：INT8 KV缓存可表示为C<sub>INT8</sub> = 2⁴·C<sub>INT4_U</sub> + C<sub>INT4_L</sub>。量化后FP32值可还原为C<sub>FP32</sub> = C<sub>INT4_U</sub>·S<sub>INT4</sub> + C<sub>INT4_L</sub>·S<sub>INT4</sub>/24 + Z<sub>INT4</sub>。算法1给出了完整的Prefill和Decode流程，包括草稿生成、验证、接受/拒绝处理，以及缓存缓冲区的量化与移动。

### 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

- **数据集**：
  - 语言建模：PG-19（长文档建模）、WikiText-2、C4（用于量化精度验证）。
  - 长上下文摘要：∞BENCH Sum（平均输入≈171k tokens）、Multi-LexSum（平均≈90k tokens）。
- **场景与benchmark**：在Llama-2-7B-32K-Instruct和LWM-Text-Chat-128k两个模型上，分别在4k、8k、16k、32k、64k、128k等多种上下文长度下测量吞吐量（tokens/s）、峰值GPU内存和端到端加速比（相对于自回归基线）。
- **对比方法**：与两种基于稀疏KV的自投机解码方法对比——StreamingLLM和SnapKV（均来自MagicDec论文）。草稿KV预算设为上下文长度的1/4，与量化缓存大小匹配。此外还对比了FP16 FlashAttention基线。

### 4. 资源与算力

- 文中明确说明：所有实验在配备8块NVIDIA RTX A6000 GPU的节点上进行。未提及训练时长，仅涉及推理评估。使用A6000的硬件规格进行roofline分析（peak compute 与 memory BW）。

### 5. 实验数量与充分性

- **数量**：主表（Table 4）报告了两个模型在多个上下文长度（共约7个不同长度×2个数据集）上的结果，总共约14个情景。每个情景下对比了三种方法，并报告了接受率、显存、加速比。
- **消融实验**：图5展示了权重量化 vs KV缓存量化 vs 两者结合的加速比对比，验证了不同瓶颈下量化的贡献。附录H给出不同投机长度γ下的接受率曲线。附录G进行了γ超参数搜索。附录I额外在Mistral-7B-v0.3和Llama-3.1-8B上进行了验证。
- **公平性**：固定量化组大小128、残差长度256，输出token数90。投机长度γ通过搜索确定（表6）。与基线保持了相同预算。
- **充分性**：实验覆盖了短/中/长上下文、多个模型、多个任务类型（语言建模、摘要），且提供了内核加速对比（表5）。整体较为全面、客观。

### 6. 论文的主要结论与发现

- QuantSpec在各种上下文长度下均提供一致的加速，最高达约2.49×（128k上下文）。
- 接受率始终保持在90%以上，显著高于稀疏KV基线（后者在长上下文或复杂摘要任务中接受率下降严重）。
- 相比稀疏KV方法，QuantSpec峰值内存占用降低约1.3×，且在超长上下文（128k）下避免OOM。
- 量化KV缓存的内核相比FP16 FlashAttention实现约2.88倍加速（4-bit，128k上下文）。
- 消融证明：短上下文主要受益于权重量化，长上下文主要受益于KV量化，中等长度两者同等重要。

### 7. 优点

- **创新性**：首次将分层4比特KV缓存与自投机解码结合，实现缓存共享与低开销。
- **工程实用性**：双全精度缓冲区解决了量化与投机解码中频繁rollback的冲突；设计了自定义CUDA内核支持量化注意力。
- **结果稳健**：在多个模型、多个长度、多个任务上均取得一致加速，接受率高。
- **内存节省**：相比稀疏方法显存更低，且避免了因稀疏造成的信息丢失。

### 8. 不足与局限

- **未与更多近期方法对比**：如TriForce、EAGLE等，只对比了MagicDec中的StreamingLLM和SnapKV。
- **量化策略的调优**：尽管量化组大小和残差长度固定，但可能不是最优；且仅测试4-bit，未探索更低比特。
- **实验范围**：主要基于Llama-2和LWM两种架构，新架构（如Mistral、Llama 3.1）仅在附录中简单展示，未充分评估。
- **资源限制**：仅在A6000 GPU上测试，未在A100/H100等现代数据中心卡上验证；且未提及训练开销（但本文是推理优化，无需训练）。
- **与稀疏方法结合的可能性**：文中仅提到可结合但未实验，未展示协同效果。
- **潜在偏差**：固定输出90 token，长生成下的行为未充分验证；数据集选择偏重于摘要和书籍，可能不能完全代表所有长上下文场景。

（完）
