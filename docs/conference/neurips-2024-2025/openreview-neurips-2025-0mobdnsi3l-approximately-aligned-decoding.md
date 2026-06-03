---
title: Approximately Aligned Decoding
title_zh: 近似对齐解码
authors: "Daniel Melcer, Sujan Kumar Gonugondla, Pramuditha Perera, Haifeng Qian, Wen-Hao Chiang, Yanjun Wang, Nihal Jain, Pranav Garg, Xiaofei Ma, Anoop Deoras"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=0mOBdNsI3L"
tags: ["query:llm"]
score: 4.0
evidence: 受投机解码启发的近似对齐解码，旨在提高计算效率
tldr: 本文提出近似对齐解码（AprAD），受投机解码算法启发，旨在平衡输出分布扭曲与计算效率。该方法可生成长序列满足困难约束的文本，同时比现有方法更少放大低概率输出，任务性能与不扭曲分布的方法相当。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-0mobdnsi3l/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 499, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0mobdnsi3l/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 517, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0mobdnsi3l/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 509, \"height\": 371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0mobdnsi3l/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 519, \"height\": 356, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0mobdnsi3l/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1401, \"height\": 482, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1454, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1453, \"height\": 444, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1408, \"height\": 518, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1441, \"height\": 836, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1151, \"height\": 260, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1413, \"height\": 408, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1419, \"height\": 411, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1446, \"height\": 905, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1217, \"height\": 236, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1457, \"height\": 407, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1426, \"height\": 119, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1423, \"height\": 121, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1419, \"height\": 121, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1418, \"height\": 125, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1414, \"height\": 120, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1417, \"height\": 121, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1410, \"height\": 123, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1405, \"height\": 117, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1414, \"height\": 123, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0mobdnsi3l/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1425, \"height\": 122, \"label\": \"Table\"}]"
motivation: 现有方法在拒绝LLM不良输出时计算开销大或扭曲分布。
method: 借鉴投机解码思想，通过近似对齐实现高效约束生成。
result: 任务性能与不扭曲分布的方法相当，且计算更高效。
conclusion: 近似对齐解码为约束生成提供了高效且低失真的解决方案。
---

## Abstract
It is common to reject undesired outputs of Large Language Models (LLMs); however, current methods to do so require an excessive amount of computation to re-sample after a rejection, or distort the distribution of outputs by constraining the output to highly improbable tokens.
We present a method, Approximately Aligned Decoding (AprAD), to balance the distortion of the output distribution with computational efficiency, inspired by algorithms from the speculative decoding literature.
AprAD allows for the generation of long sequences of text with difficult-to-satisfy constraints, while amplifying low probability outputs much less compared to existing methods.
We show through a series of experiments that the task-specific performance of AprAD is comparable to methods that do not distort the output distribution, while being much more computationally efficient.

---

## 论文详细总结（自动生成）

# 中文总结：Approximately Aligned Decoding (AprAD)

## 1. 论文的核心问题与整体含义
- **研究动机**：大型语言模型（LLM）生成文本时可能包含违反约束的内容（如语法错误、幻觉、敏感词等）。现有处理方法面临两难：拒绝采样（rejection sampling）计算开销大；而约束生成（constrained generation）会严重扭曲原始输出分布，将概率集中到低概率序列上。
- **核心问题**：如何在保持输出分布尽可能接近原始分布的同时，高效地生成满足复杂约束的长文本。
- **整体贡献**：提出 AprAD，一种无需额外训练、受投机解码（speculative decoding）启发的方法，在输出分布保真度与计算效率之间取得折中。

## 2. 论文提出的方法论
- **核心思想**：当生成过程中遇到错误序列时，不直接丢弃全部内容（如 ASAp），也不仅丢弃最后一个错误 token（如约束生成），而是利用投机采样算法（SpecSample）决定保留前缀的长度，使回溯行为自适应于误差的局部概率结构。
- **关键技术细节**：
  - 定义错误集合 B（满足前缀封闭性），目标是从重整化分布 \(\hat{P}_B\) 中采样。
  - 每次发现错误序列 \(x_{1:m}\) 后，将其加入 B 得到新分布 \(\hat{P}_{B \cup \{x\}}\)。
  - 调用 SpecSample(\(\hat{P}_{B \cup \{x\}}, \hat{P}_B, x_{1:m}\))，得到一个新前缀（可能短于原序列），随后继续从新分布生成。
  - SpecSample 中接受概率 \(r = (P(x_i)/S(x_i))^h\)，其中 \(h\) 是超参数（\(h=1\) 为原版 AprAD，\(h=0\) 退化为约束生成，\(h\to\infty\) 趋近 ASAp）。
- **算法流程**（文字说明）：
  1. 用当前分布 \(\hat{P}_B\) 自回归采样一个 token。
  2. 若完整序列仍在错误集外，则继续生成；若进入错误集，则：
     - 将该错误序列加入 B，更新分布。
     - 用 SpecSample 在更新前后的分布间选择保留的前缀。
     - 回退到该前缀位置，继续生成。
- **公式与说明**：无复杂公式，但给出概率放大界：每回溯一次，概率放大因子不超过 2（相比约束生成的无界放大）。

## 3. 实验设计
- **数据集与场景**：
  - **合成模拟**：3 个 token（A/B/C），等概率，标记不同错误子集（共 7 种配置），生成 10000 条长度为 3 的序列，计算 KL 散度和生成比率。
  - **唇语任务（Lipogram）**：使用 Mistral-7B-Instruct-v0.2，要求生成 200 token 文本，避免使用特定元音。共 25 个提示（5 个任务 × 5 个元音），人工评分（质量 1-5，约束意图 1-3）。
  - **代码幻觉避免（BigCodeBench v0.1）**：使用 StarCoder2 7B 和 15B，温度 0.8，top-p 0.95，每任务 5 次生成。检测器基于 Pyright 识别 API 幻觉。评估 pass@1、pass@5、无 NameError 率、生成比率。
- **Benchmark**：BigCodeBench（1140 个编程任务，面向实际库调用）。
- **对比方法**：无约束生成（unconstrained）、约束生成（constrained）、ASAp（Adaptive Sampling with Approximate Expected Futures）、AprAD（本文）。

## 4. 资源与算力
- **明确说明**：附录 G 指出，BigCodeBench 实验（1140 任务 × 4 方法 × 2 模型 × 5 次 ≈ 45600 次生成，输出约 10^7–10^8 token）在 AWS p4d.24xlarge 实例上运行了约 1–2 天。
- 唇语任务和模拟实验算力需求远小于上述，模拟实验运行在普通笔记本电脑上（数分钟至秒级）。
- 推理时间未精确追踪，因并行运行带来高方差；主要使用“生成比率”（generation ratio）而非 wall-clock time 作为效率指标。

## 5. 实验数量与充分性
- **实验数量**：
  - 合成模拟：7 种错误集，每种 10000 样本，统计 KL 散度和比率。
  - 唇语：25 个 prompt × 4 方法 = 100 个输出，由 4 名独立评分者盲评。
  - BigCodeBench：全量 1140 任务，但主要报告输出有差异的子集（15B 模型 233 任务，7B 模型 304 任务），并额外给出全量结果。
- **充分性与公平性**：
  - 覆盖了合成、文本生成、代码生成三种场景，对比了最相关的三类基线（无约束、约束生成、ASAp）。
  - 使用相同随机种子，确保输出差异仅由约束触发引起。
  - 人工评估采用盲评，评分者独立，并预填充违反约束的案例。
  - 生成比率作为计算开销的代理指标，避免了环境差异的干扰。
  - 不足：缺少对超参数 \(h\) 的系统消融实验（仅提及概念）；未与后验估计类方法（如 FUDGE、Ctrl-G、SMC Steering）直接对比。

## 6. 论文的主要结论与发现
- AprAD 在输出分布保真度（KL 散度）上显著优于约束生成，接近 ASAp；在计算效率（生成比率）上远优于 ASAp，接近约束生成。
- 在唇语任务中，AprAD 的输出质量和约束意图得分接近无约束生成，远优于 ASA (因 ASA 在 2000 次模型调用内只能生成极短文本) 和约束生成（后者常通过省略字母、使用非标准字符等违规方式满足约束）。
- 在 BigCodeBench 中，AprAD 的 pass@1 和 name error 避免率与 ASAp 相当，生成比率仅 1.06–1.08（ASAp 为 1.47–1.56，约束生成约为 1.00–1.02），实现了较好的折中。
- 结论：AprAD 是一种有效、通用、无需额外训练的方法，适用于错误密度高的约束生成场景。

## 7. 优点
- **无需额外训练或微调**：直接使用原始 LLM，无额外训练开销。
- **实现简单**：基于投机解码算法的前缀选择逻辑，易集成到现有推理流程。
- **概率放大可控**：每回溯一步的放大因子有界（≤2），避免约束生成的无界放大。
- **可调超参数**：通过 \(h\) 可精细控制分布保真度与计算效率的折中。
- **实验设计稳健**：覆盖合成、自由文本和代码三个领域，包含人工评估和客观指标，对比方法全面。

## 8. 不足与局限
- **仍存在一定概率放大**：由于仅在遇到错误时才回溯，部分非错误序列的概率被略微提升（如附录 B、C 分析）。
- **依赖错误检测器的准确性**：代码任务中检测器倾向于假阴性（漏报），可能高估约束遵循效果；唇语任务中简单子串匹配无法处理同音异形等技巧。
- **未探索超参数 \(h\) 的敏感性与最优设定**：仅在理论层面提出，未进行实验验证。
- **未与后验估计类方法直接比较**：这些方法在可训练判别器或 HMM 可建模的任务上可能有优势，论文仅在讨论中定性对比。
- **生成比率作为效率指标存在局限**：未报告实际推理时间，因环境差异导致无法直接比较绝对速度。
- **在极端密集错误集上效率可能下降**：当大部分前缀都是错误时，AprAD 可能仍需多次回溯，作者提及可结合 \(h\) 参数极端调整为约束生成。
- **可重复性**：论文声称代码将开源，但未提供完整代码（仅附 GitHub 链接），且部分实现细节（如 Trie 结构的浮点误差处理）需依赖附录。

（完）
