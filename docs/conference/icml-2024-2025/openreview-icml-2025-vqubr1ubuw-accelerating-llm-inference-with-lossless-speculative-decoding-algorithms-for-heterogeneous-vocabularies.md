---
title: Accelerating LLM Inference with Lossless Speculative Decoding Algorithms for Heterogeneous Vocabularies
title_zh: 异构词表下的无损投机解码算法加速大语言模型推理
authors: "Nadav Timor, Jonathan Mamou, Daniel Korat, Moshe Berchansky, Gaurav Jain, Oren Pereg, Moshe Wasserblat, David Harel"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=vQubr1uBUw"
tags: ["query:llm"]
score: 9.0
evidence: 针对异构词表的无损投机解码加速LLM推理
tldr: 针对投机解码中草稿模型与目标模型需共享词表的限制，本文提出三种无损投机解码方法，允许异构词表使用现成模型，无需额外训练。在摘要和编程任务上验证了加速效果，显著拓展了投机解码的适用性，对LLM高效推理有重要价值。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 现有投机解码要求草稿与目标模型共享词表，限制了草稿模型来源。
method: 提出三种无损投机解码方法，通过概率重映射消除词表依赖，无需训练。
result: 在摘要和编程任务上实现加速，且保持目标分布不变。
conclusion: 本文方法扩大了投机解码的模型选择范围，实现了灵活高效的LLM加速。
---

## Abstract
Accelerating the inference of large language models (LLMs) is a critical challenge in generative AI. Speculative decoding (SD) methods offer substantial efficiency gains by generating multiple tokens using a single target forward pass. However, existing SD approaches require the drafter and target models to share the same vocabulary, thus limiting the pool of possible drafters, often necessitating the training of a drafter from scratch. We present three new SD methods that remove this shared-vocabulary constraint. All three methods preserve the target distribution (i.e., they are lossless) and work with off-the-shelf models without requiring additional training or modifications. Empirically, on summarization, programming, and long-context tasks, our algorithms demonstrate significant speedups of up to 2.8x over standard autoregressive decoding. By enabling any off-the-shelf model to serve as a drafter and requiring no retraining, this work substantially broadens the applicability of the SD framework in practice.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：投机解码（Speculative Decoding, SD）能通过单次目标模型前向传播生成多个 token，显著加速大语言模型推理。但现有 SD 方法要求草稿模型与目标模型**共享相同词表**，这大大限制了草稿模型的选择范围，通常需要从零训练一个专用草稿模型，成本高昂且难以复用。
- **整体含义**：本文提出**三种无损（lossless）的 SD 算法**，消除了共享词表的约束，允许使用任意现成的（off-the-shelf）模型作为草稿模型，无需任何额外训练或修改。这极大地拓展了 SD 的实用性和灵活性，为 LLM 推理加速提供了更广泛的解决方案。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
利用**文本字符串作为中间表示**或**词表交集投影**，在异构词表间建立映射，使得草稿 token 可以转换为目标 token 进行验证，同时保证输出分布与自回归解码一致（即无损）。

### 三种算法

#### ① 字符串级精确匹配（SLEM, Algorithm 2）
- **流程**：
  1. 将输入 prompt 用草稿词表 tokenize。
  2. 草稿模型自回归生成 i 个 draft token。
  3. 将 draft token 拼接成文本，再按目标词表重新 tokenize，得到目标 token 序列 \((t_1, t_2, \dots, t_m)\)。
  4. 执行一次目标模型前向传播，计算该序列对应的 logits，并采样得到目标候选 token。
  5. 比较 draft 与目标 token，找到第一个不匹配的位置，接受之前的所有 token 并替换为采样 token。
- **关键假设**：目标词表可被草稿词表表达，反之亦然（即 \(T \twoheadrightarrow D^*\) 且 \(D^* \twoheadrightarrow T^*\)）。通常常见 tokenizer 满足此条件。
- **支持非单射 tokenizer**：通过查找旧序列与新序列的最大重叠（后缀/前缀匹配）来对齐，减少规范化不一致的影响。

#### ② 词表交集投影（TLI, Algorithm 4）
- **流程**：
  1. 将草稿分布 \(q\) 投影到两个词表的交集 \(T \cap D\) 上，得到新分布 \(q'(x) = q(x)/\sum_{t\in T}q(t)\)（若 \(x \in T\)），否则为 0。
  2. 使用标准 SD 的拒绝采样方法（Algorithm 5），以目标分布 \(p\) 和调整后的草稿分布 \(q'\) 进行验证。
- **理论保证**（Theorem 4.1）：TLI 的预期接受率 ≥ 直接取词表并集的简单方法（Algorithm 1），且无损。

#### ③ 字符串级拒绝采样（SLRS, Algorithm 3）
- **流程**：
  1. 从草稿模型自回归采样字符串 \(d_1 \oplus \dots \oplus d_i\)，直到满足一个前瞻停止条件。
  2. 按目标词表重新 tokenize，取第一个目标 token \(t_1\)。
  3. 定义 \(\psi(t) = \sum_{\text{所有能生成以 }t\text{ 开头的草稿序列}} \prod q(d_j)\)，即草稿序列产生目标 token \(t\) 的总概率。
  4. 执行标准拒绝采样：若 \(p(t_1) \geq \psi(t_1)\) 则接受；否则以概率 \(p(t_1)/\psi(t_1)\) 接受，否则拒绝并从剩余分布中采样。
- **理论保证**（Theorem 3.2）：算法无损，且预期接受率高于 SLEM（Theorem 3.1）。
- **实际限制**：计算 \(\psi(t)\) 所需的草稿序列组合数随目标 token 长度**指数增长**，导致计算开销极大，目前仅适用于短 token 的草稿模型（如 MambaByte）。

## 3. 实验设计

- **数据集**：
  - **文本摘要**：CNN/DailyMail
  - **代码生成**：HumanEval
  - **长上下文任务**：SCROLLS
- **目标模型**：Mixtral-8x22B, DeepSeek-R1-Distill-Qwen (7B/14B/32B), CodeLlama-13B, phi-4 等（这些模型缺乏共享词表的草稿模型或在其家族内词表异构）。
- **草稿模型**：Qwen2.5-0.5B-Instruct, vicuna-68m, tiny-starcoder-py, CodeLlama-7B, DeepSeek-R1-Distill-Qwen-1.5B 等。
- **对比方法**：
  - 自回归解码（Autoregressive, AR）
  - 标准 SD（Algorithm 5，适用于同词表情况，仅用于有同词表草稿的模型）
- **评估指标**：首次 token 生成时间（TTFT）、每个 token 生成时间（TPOT）、每秒 token 数（Tok/s）及相对于 AR 的加速比。
- **硬件**：H100 NVL (1或4卡), RTX 6000, A6000, A100 80GB PCIe。

## 4. 资源与算力

- 文中未统一给出总训练计算量，因为方法**无需训练**，仅需推理。
- 各实验具体硬件配置已在上文列出（如“4 * H100 NVL”、“1 * RTX 6000”等），多数实验仅使用 1 或 2 张 GPU，部分高显存模型（如 Mixtral-8x22B）使用 4 张 H100。
- 计算开销主要来自推理过程中的草稿模型和目标模型前向传播次数，具体数值未详细报告。

## 5. 实验数量与充分性

- **实验数量**：
  - 表1（SLEM）涵盖 7 个目标模型、3 个数据集、多种草稿模型，共约 20+ 种配置。
  - 表2（TLI）类似，约 15+ 种配置。
  - 附录中补充了更多模型（如 Gemma-2、Llama-3.1、DeepSeek-R1-Distill-Llama-70B 等），总实验组数超过 40 组。
- **充分性与公平性**：
  - 覆盖了多种规模、家族、词表大小的模型对，任务类型多样。
  - 对于有同词表草稿的模型，额外对比了标准 SD 方法，以展示异构方法的竞争力。
  - 所有结果均为无损确保，无需担心分布偏差。
  - **不足之处**：
    - 缺少对 **SLRS 的实证实验**（仅理论分析和复杂度计算），因为其实际可行性低。
    - 未做消融实验（如不同前瞻策略、不同草稿模型大小对加速的影响）。
    - 实验数据点较少（每个配置平均 30 个 prompt），统计显著性未明确报告。
    - 未在非英文或超长序列任务上验证。

## 6. 主要结论与发现

- **SLEM** 在异构词表场景下实现最高 **2.8 倍**加速（CodeLlama-13B + tiny-starcoder-py，HumanEval），通用情况下 1.4–2.1 倍。
- **TLI** 实现最高 **1.7 倍**加速（DeepSeek-R1-Distill-Llama-70B + Qwen2.5-0.5B，HumanEval），通用情况下 1.3–1.6 倍。
- **算法已被集成到 Hugging Face Transformers**，并因其通用性和有效性被设为异构 SD 的默认实现，说明在工业界获得了认可。
- 理论证明了 TLI 接受率优于简单的 union 策略，SLEM 和 SLRS 均无损，且 SLRS 预期接受率高于 SLEM，但计算复杂度使其不实用。
- **主要发现**：解除词表限制后，可以选用比同家族最小模型**更快、更小**的异构草稿模型，从而获得更高加速（如用 68M 参数的 vicuna-68m 加速 70B 目标的 Mixtral）。

## 7. 优点

1. **创新性**：首次系统性地解决异构词表下的无损 SD 问题，提出三种不同思路的方案。
2. **实用性**：所有方法均无需训练，直接使用现成模型，显著降低了 SD 的应用门槛。
3. **理论完备**：对每种算法给出了无损证明、接受率期望，并进行比较。
4. **实验覆盖面广**：涵盖了多种主流通用模型、代码模型、混合模型，以及不同硬件。
5. **开源集成**：代码已合入 Hugging Face Transformers，便于社区直接使用和再验证。
6. **可扩展性**：允许用户灵活选择任意草稿模型，尤其适用于无法获得同词表草稿的场景。

## 8. 不足与局限

1. **SLRS 方法不实用**：由于计算 \(\psi(t)\) 指数爆炸，实际无法用于主流词表，论文也承认仅适合特殊模型（如 MambaByte），但未做实证。
2. **对词表可表达性假设的依赖**：SLEM 要求 \(T \twoheadrightarrow D^*\) 和 \(D^* \twoheadrightarrow T^*\)，虽然常见词表满足，但少数极端情况可能失效（如词表不含完整字母表）。
3. **实验样本量较小**：每个实验仅 30 个 prompt，可能不足以反映真实负载下性能的统计稳定性。
4. **缺乏失败案例分析**：虽有部分配置加速比低于 1（如 DeepSeek-R1-Distill-Qwen-14B 在 CNN/DailyMail 上 SLEM 加速仅 0.73），但未深入分析原因。
5. **忽略延迟优化**：未考虑 KV cache 管理、批量调度等工程实践对最终加速的影响，结果更接近理想情况。
6. **语言和任务局限**：所有实验均为英文，未评估在多语言或需要精确格式（如数学推导）的任务上的表现。
7. **硬件不统一**：不同实验使用不同 GPU，导致加速比绝对值无法直接跨实验比较，仅在同配置下有意义。

（完）
