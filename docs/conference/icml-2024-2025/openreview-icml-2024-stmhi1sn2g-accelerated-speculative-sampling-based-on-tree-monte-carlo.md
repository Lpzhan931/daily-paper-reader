---
title: Accelerated Speculative Sampling Based on Tree Monte Carlo
title_zh: 基于树蒙特卡洛的加速投机采样
authors: "Zhengmian Hu, Heng Huang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=stMhi1Sn2G"
tags: ["query:llm"]
score: 9.0
evidence: 使用树蒙特卡洛方法加速投机采样，实现全局最优耦合
tldr: 投机采样虽能加速LLM推理，但增量最大耦合并非最优。本文提出树蒙特卡洛方法，在树空间上寻找全局最大耦合，从而加速生成并保持无偏性。实验证明在多种任务上比标准投机采样更快，为投机解码提供了新视角。
source: ICML-2024-Public
selection_source: conference_retrieval
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-stmhi1sn2g/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 447, \"height\": 288, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-stmhi1sn2g/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 846, \"height\": 507, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-stmhi1sn2g/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 829, \"height\": 505, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-stmhi1sn2g/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 660, \"height\": 434, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-stmhi1sn2g/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 848, \"height\": 1450, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-stmhi1sn2g/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 846, \"height\": 501, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-stmhi1sn2g/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1812, \"height\": 511, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-stmhi1sn2g/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1811, \"height\": 513, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-stmhi1sn2g/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1813, \"height\": 511, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-stmhi1sn2g/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1813, \"height\": 510, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-stmhi1sn2g/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1812, \"height\": 513, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-stmhi1sn2g/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1811, \"height\": 509, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-stmhi1sn2g/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1814, \"height\": 510, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-stmhi1sn2g/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1812, \"height\": 513, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-stmhi1sn2g/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1810, \"height\": 511, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-stmhi1sn2g/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1813, \"height\": 511, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-stmhi1sn2g/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1812, \"height\": 512, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-stmhi1sn2g/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1810, \"height\": 511, \"label\": \"Table\"}]"
motivation: 增量最大耦合不是最优，需要全局耦合以加速生成。
method: 提出树蒙特卡洛方法，在树空间上寻找全局最大耦合进行投机采样。
result: 在多种生成任务上比标准投机采样更快，且保持分布无偏。
conclusion: 树蒙特卡洛通过全局优化进一步提升投机采样效率。
---

## Abstract
Speculative Sampling (SpS) has been introduced to speed up inference of large language models (LLMs) by generating multiple tokens in a single forward pass under the guidance of a reference model, while preserving the original distribution. We observe that SpS can be derived through maximum coupling on the token distribution. However, we find that this approach is not optimal as it applies maximum coupling incrementally for each new token, rather than seeking a global maximum coupling that yields a faster algorithm, given the tree-space nature of LLM generative distributions. In this paper, we shift our focus from distributions on a token space to those on a tree space. We propose a novel class of Tree Monte Carlo (TMC) methods, demonstrating their unbiasedness and convergence. As a particular instance of TMC, our new algorithm, Accelerated Speculative Sampling (ASpS), outperforms traditional SpS by generating more tokens per step on average, achieving faster inference, while maintaining the original distribution.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：大型语言模型（LLM）推理速度慢，尤其是在自回归生成中，每次只生成一个token，导致严重延迟。现有加速方法——投机采样（Speculative Sampling, SpS）通过一个更快的参考模型生成多个候选token，再由目标模型并行计算概率并接受部分token，从而加速推理并保持原始分布无偏。
- **背景与动机**：SpS 本质上基于最大耦合（maximum coupling）在 token 空间上逐 token 进行最优匹配。但研究团队观察到，这种增量式最大耦合并非全局最优——当参考模型生成多个 token 时，输出空间是字符串空间（产品空间），而非单个 token 空间。因此，在字符串空间上的全局最大耦合无法通过逐 token 最大耦合的乘积实现。这促使论文从 token 空间转移到树空间（tree space），提出树蒙特卡洛（Tree Monte Carlo, TMC）方法，并以此构建加速投机采样（Accelerated Speculative Sampling, ASpS），实现更优的全局耦合，从而在保持无偏性的前提下生成更多 token，进一步加速推理。

## 2. 方法论
### 核心思想
- **树空间视角**：将 LLM 的生成过程建模为树结构，每个节点代表一个前缀，边代表 token，完整路径即为一个序列。树分布（tree distribution）定义在路径上，子树为条件分布。
- **子分布（Sub-distribution）**：引入一种偏序关系 P1 ⪯ P2，表示 P1 是 P2 的子分布，即所有路径概率按比例缩小的同时保持分支比例不变。该概念是实现树蒙特卡洛收敛的关键。
- **子采样器（Prefix Sub-sampler）**：给定一个前缀，子采样器的输出分布是该前缀下目标分布的一个子分布。子采样器在组合下封闭，且非退化的子采样器迭代收敛到叶单分布（leaf-only distribution，即目标分布）。
- **加速投机采样（ASpS）**：作为 TMC 的一个实例，ASpS 在给定参考模型采样的参考路径后，计算一个邻居分布（neighbor distribution），该分布仅在参考路径的“近邻”集合（S⪅σ 和 S≈σ）上有非零概率。ASpS 递归地定义耦合概率，与 SpS 的关键区别在于：SpS 只使用当前前缀下的概率质量 [P_SpS({σ}; σ)] 作为参考模型的可用质量，而 ASpS 使用整个路径的初始概率质量（即 Pref(a|σ)），从而在每一步都能利用更多概率进行耦合，实现更强的全局耦合。

### 关键技术细节（算法流程）
- **输入**：参考模型采样的 token 序列 `ref_token`，参考模型概率 `P_ref`（长度为 len_ref），目标模型概率 `P`（长度为 len_ref+1）。
- **输出**：最终接受的 token 序列。
- **步骤**：
  1. 初始化邻居概率矩阵 `P_N` 为全零，根节点概率 `P_N_ss = 1`。
  2. 逐个遍历参考 token（长度从 1 到 len_ref）：
     - 如果当前位置不是第一个 token，将上一位置对应的概率清零。
     - 计算 `C1 = max(0, P_ref - P_N_ss * P)`。
     - 计算 `C2 = C1[ref_token] / sum(C1)`。
     - 更新 `P_N` 中非当前分支的概率（按 C2/P_ref 缩放）。
     - 更新当前分支的概率：`P_N[当前位置, ref_token] = min(1, P_N_ss * P[当前位置, ref_token] / P_ref[当前位置, ref_token])`。
     - 更新 `P_N_ss` 为当前分支的概率。
  3. 采样 `(gen_len, last_token)` 来自 `P_N`。
  4. 根据 `gen_len` 和 `last_token` 构造最终接受的 token 序列。若全部接受，则额外采样一个 token。
- **复杂度**：O(len_ref × vocab_size)，仅涉及向量操作，远小于模型前向传播时间。

## 3. 实验设计
- **数据集/场景**：
  - 翻译任务：WMT16 数据集（英语-德语）。
  - 文本摘要任务：未明确指定但实验中有相关结果。
  - 开放式文本生成：使用多个模型组合在不同数据集上评估（如 open-ended text generation）。
- **Benchmarks**：与标准投机采样（SpS）进行对比，测量每个步骤平均接受 token 数（ATN）和每个 token 的推理时间（PTT），以及困惑度（PPL）变化。
- **对比方法**：仅对比 SpS 和 ASpS，未与其他加速方法（如 Medusa、Staged Speculative Decoding 等）进行全面比较。

## 4. 资源与算力
- **未明确说明**：论文未提及使用的 GPU 型号、数量、训练时长等具体算力资源。仅提到使用 Huggingface 库进行实现，并指出该库未优化推理速度，因此主要依赖 ATN 而非 wall-time 作为评价标准。

## 5. 实验数量与充分性
- **实验数量**：共进行了大量实验（参考附录 C 的多个表格），覆盖多种模型组合和任务：
  - 目标模型：LLaMa-7b, LLaMa-13b, LLaMa-2-7b, LLaMa-2-13b, Opt-13b, Opt-6.7b, GPT-Neo-2.7B, GPT-2-xl。
  - 参考模型：LLaMa-68m, Opt-125m, GPT-2。
  - 任务类型：翻译、摘要、开放式文本生成。
  - 参考 token 数量 n 从 1 到 10 分别测试。
- **充分性**：实验设计较为充分，覆盖了不同规模的模型、不同任务，并提供了统计误差（±值）。但缺少与其他最新加速方法的横向对比（如 Medusa、Staged Speculation），且只给出 ATN 提升百分比，未在优化后的硬件上测试 wall-time 加速比（作者承认 Huggingface 库的非优化性）。因此客观性有一定局限，但 ATN 作为与实现无关的指标是公平的。

## 6. 主要结论与发现
- **ASpS 优于 SpS**：当参考 token 数量 n ≥ 2 时，ASpS 在 ATN 上持续高于 SpS（提升幅度 0.9% ~ 14.3%，随 n 和模型组合变化）。当 n=1 时两者相等，符合理论预期（单 token 情况下 token 空间即为输出空间，SpS 已达最优）。
- **保持无偏性**：ASpS 被证明构成一个子采样器，因此迭代收敛到目标分布，困惑度变化在统计误差范围内（多数情况下 PPL 变化不显著），说明生成质量未受损。
- **全局耦合更优**：理论分析表明，ASpS 通过利用整个参考路径的概率质量，实现了比 SpS 更强的耦合，从而能接受更多 token。

## 7. 优点
- **理论创新**：首次提出树空间上的子分布和子采样器概念，并证明其收敛性和封闭性，为结构化采样提供新的数学框架。
- **算法简洁高效**：ASpS 仅需与 SpS 相同的输入，计算开销仅为 O(n×vocab_size) 的向量操作，几乎可忽略。
- **即插即用**：与参考模型无关，可与任何参考模型改进方案正交叠加。
- **实验覆盖较全**：在多种模型和任务上验证，且 ATN 指标与实现无关，结果可靠。

## 8. 不足与局限
- **实验对比不足**：未与其他流行的加速方法（如 Medusa、Jacobi 迭代解码、Staged Speculative Decoding）进行直接比较，也未在真实推理延迟（wall-time）上充分量化，主要依赖 ATN 这一代理指标。
- **实际硬件优化缺失**：作者承认使用 Huggingface 库非优化实现，无法给出真实加速比，可能让读者对实际加速效果存疑。
- **理论基础复杂**：树蒙特卡洛的概念（子分布、子采样器、邻居分布等）门槛较高，可能限制实际应用和复现。
- **应用限制**：参考模型需与目标模型共享相同的词表，且参考模型需足够快以弥补额外计算开销；在参考模型质量较差时，ASpS 的优势可能减弱。
- **实验规模较小**：仅使用开源中等规模模型（最大 13B），未在更大模型（如 70B、130B）上验证。

（完）
