---
title: Accelerating Diffusion LLMs via Adaptive Parallel Decoding
title_zh: 通过自适应并行解码加速扩散大语言模型
authors: "Daniel Mingyi Israel, Guy Van den Broeck, Aditya Grover"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=xwqTt26NJf"
tags: ["query:llm"]
score: 5.0
evidence: 针对扩散LLM的自适应并行解码，反转投机解码设置
tldr: 本文提出自适应并行解码（APD）方法，通过动态调整并行采样的token数量来加速扩散大语言模型（dLLM）。该方法反转了投机解码的标准设置，利用辅助自回归模型的小模型联合概率，在保持质量的同时实现更快的生成速度。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwqtt26njf/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1419, \"height\": 364, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwqtt26njf/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 386, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwqtt26njf/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1445, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwqtt26njf/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1445, \"height\": 388, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwqtt26njf/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1436, \"height\": 524, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwqtt26njf/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1010, \"height\": 563, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-xwqtt26njf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1341, \"height\": 495, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xwqtt26njf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1453, \"height\": 169, \"label\": \"Table\"}]"
motivation: 扩散LLM理论上可并行生成，但实际速度不如自回归模型。
method: 定义dLLM边际概率与辅助自回归模型联合概率的乘法混合，动态调整并行采样数。
result: 在保持生成质量的前提下显著提升dLLM推理速度。
conclusion: 自适应并行解码为扩散LLM提供了一种有效的加速范式。
---

## Abstract
The generation speed of LLMs are bottlenecked by autoregressive decoding, where tokens are predicted sequentially one by one. Alternatively, diffusion large language models (dLLMs) theoretically allow for parallel token generation, but in practice struggle to achieve the speed of autoregressive models without significantly sacrificing quality. We therefore introduce adaptive parallel decoding (APD), a novel method that dynamically adjusts the number of tokens sampled in parallel. We achieve this by defining a multiplicative mixture between the dLLM marginal probabilities and the joint probability of sequences under a small auxiliary autoregressive model. This inverts the standard setup of speculative decoding, where the goal is to sample from a large autoregressive verifier by drafting from a smaller model. We further optimize APD by enabling KV caching and limiting the size of the masked input. Altogether, our method puts forward three tunable parameters to flexibly tradeoff throughput and quality. We show that APD provides markedly higher throughput with minimal quality degradations on downstream benchmarks.

---

## 论文详细总结（自动生成）

# 论文总结：Accelerating Diffusion LLMs via Adaptive Parallel Decoding

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：大型语言模型（LLM）的生成速度受限于自回归解码——每个 token 必须顺序预测，导致推理瓶颈。扩散大语言模型（dLLM）理论上支持并行生成 token，但在实际中如果不显著牺牲质量，速度无法匹敌自回归模型。
- **背景**：现有开源 dLLM（如 Dream、Llada）在并行生成时质量严重下降；即使采用从左到右解码（实际变为自回归），仍因缺乏 KV 缓存等优化而速度缓慢。
- **目标**：设计一种解码算法，能动态调整并行生成的 token 数量，在保持生成质量的同时大幅提升 dLLM 的吞吐量。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：
  - 将 dLLM 的生成顺序固定为“从左到右”（使其在行为上等于自回归模型），从而可以利用小型自回归模型来评估并行生成的联合概率质量。
  - 定义**乘法混合（product of experts）**：将 dLLM 的边缘概率 \(p_D\) 与小型自回归模型 \( \hat{p}_{AR} \) 的联合概率混合，得到目标分布 \(p_T \propto p_D^R \cdot \hat{p}_{AR}^{1-R}\)，其中 \(R \in [0,1]\) 控制信任权重。
  - 使用 **Gumbel-Softmax 技巧作为通用耦合器**：对 dLLM 采样一组候选 token，再对混合目标分布采样另一组 token，接受两序列中连续相同的部分（直到第一个不同 token）。第一个 token 总是接受。
- **关键技术细节**：
  - **KV 缓存**：采用滑动窗口方式（窗口大小 \(W\)），对距离当前 token 足够远的 token 缓存 KV，减少重计算，但引入轻微分布偏差（实验显示影响可忽略）。
  - **最大掩码前瞻长度 \(M\)**：限制输入中连续 [MASK] 的数量，降低注意力计算复杂度，同时可能影响生成长度和 [EOS] 概率。
  - **三个可调参数**：\(R\)（混合权重）、\(W\)（KV 窗口）、\(M\)（最大掩码长度），分别调节速度与质量的权衡。
- **算法流程简述**：
  1. 从 dLLM 获得当前位置起所有后续 token 的边缘 logits。
  2. 使用固定随机种子（Gumbel 噪声）从边缘分布采样得到候选序列 \(\hat{x}\)。
  3. 用小自回归模型计算 \(\hat{x}\) 的联合 logits。
  4. 计算乘法混合 logits = softmax(\(R \times\) 边缘 logits + \((1-R) \times\) 联合 logits)。
  5. 使用相同 Gumbel 噪声从混合分布采样得到目标序列 \(\hat{y}\)。
  6. 从位置开始比较 \(\hat{x}\) 和 \(\hat{y}\)，接受直到第一个不同 token，将接受部分追加到结果序列。
  7. 移动位置，重复直到序列结束。

## 3. 实验设计
- **基准模型与数据集**：
  - 扩散模型：Dream 7B Instruct（从 Qwen2.5 7B 蒸馏而来）。
  - 辅助自回归模型：Qwen2.5 0.5B（共享相同 tokenizer）。
  - 评估基准：GSM8K（数学）、GPQA（科学）、MATH（数学）、HumanEval（代码）。
- **对比方法**：
  - Dream 7B 的不同解码策略（随机、熵优先、置信度优先、从左到右、不同步数）。
  - Llada 8B 的类似策略。
  - Qwen2.5 7B 标准自回归解码。
  - 半自回归固定并行大小 \(k\) 的 naive 解码。
- **评估指标**：准确率（或 pass@1）和吞吐量（tokens/sec）。

## 4. 资源与算力
- **硬件**：单张 NVIDIA 24GB A5000 GPU，搭配 AMD EPYC 9124 CPU 服务器。
- **精度**：模型以 BF16 加载。
- **时间**：论文指出实验只需数小时（hours not days），未报告精确训练时长（本方法为推理方法，无需训练）。
- **注意**：未说明多 GPU 或分布式设置；实验规模属于中等。

## 5. 实验数量与充分性
- **实验数量**：较为充足，包括：
  - 三个参数（\(R, W, M\)）各自的 tradeoff 分析（含误差线）。
  - 不同参数组合的 Pareto 前沿比较。
  - 生成统计（平均并行 token 数）。
  - 定性示例（说服性写作提示）。
- **充分性评价**：
  - 实验覆盖了多种推理任务（数学、科学、代码、开放生成），对比了多种基线，并给出了统计误差。
  - **不足**：只测试了 Dream 7B 一种扩散模型（Llada 因 tokenizer 不兼容无法使用，论文承认这一点）；辅助模型也仅用了 Qwen2.5 0.5B，未验证其他组合；未与 Medusa、DynaMo 等并行解码方法直接比较（但论文在相关工作中简要提及）。
  - 总体而言，在给定设定下实验设计合理、结果可信，但泛化性证据不够广泛。

## 6. 主要结论与发现
- APD 能显著提升 dLLM 的吞吐量，同时质量仅略微下降。例如，在 GSM8K 上以平均 >5 token/iteration 并行时仍能保持 ≈80% 准确率（基线 83%）。
- 通过调整 \(R\) 可灵活控制速度-质量权衡：\(R=1\) 时完全信任 dLLM 一次生成所有 token（速度最快但质量最低）；\(R\) 较小则接受更多辅助模型约束，质量更高但速度较慢。
- 结合 KV 缓存和掩码限制可额外获得 2-3 倍提速，且质量损失可忽略。
- APD 配置下 Dream 7B 的吞吐量甚至超过 Qwen2.5 7B 自回归解码，且质量相近，在 Pareto 前沿上占据优势。
- 定性显示 APD 在开放写作任务中平均并行 2.9-3.4 token/iteration，说明其适用于多种场景。

## 7. 优点
- **方法创新**：反转投机解码的标准设置，用小型自回归模型验证大型扩散模型的并行采样，避免了传统投机解码中“大模型验证小模型”的低效。
- **灵活可调**：三个正交参数提供对速度-质量权衡的精细控制，适应不同应用需求。
- **工程优化**：将 KV 缓存和滑动窗口引入 dLLM，突破其架构限制，显著提升效率。
- **清晰分析**：通过 Pareto 前沿系统比较多种配置，证明 APD 的帕累托最优性。
- **结果显著**：在主流基准上达到接近自回归模型的质量，而速度大幅超越，展示了 dLLM 的实用潜力。

## 8. 不足与局限
- **依赖条件**：要求扩散模型与辅助模型共享 tokenizer，限制了方法的应用范围（Llada 因 tokenizer 不匹配无法使用）。
- **实验覆盖**：仅评估了一个扩散模型（Dream 7B）和一个小辅助模型（Qwen2.5 0.5B），未验证更大或更小模型组合，也未与 Medusa、DynaMo 等并行方法直接比较。
- **分布偏差**：KV 缓存和最大掩码限制可能引入与训练时不一致的推理分布，论文虽通过实验表明影响小，但理论保证不足。
- **非免费午餐**：参数调优仍存在 tradeoff，没有统一的“最优”设置；最大掩码 \(M\) 减少可能缩短生成推理链，从而影响复杂推理任务质量。
- **通用性局限**：辅助模型的准确性影响并行接受率；如果辅助模型偏差大，可能导致频繁拒绝或接受不良 token，降低效率或质量。
- **开放问题**：未探索在更大 scale 模型或实时场景下的表现，也未与其他推理加速技术（如量化、蒸馏）结合。

（完）
