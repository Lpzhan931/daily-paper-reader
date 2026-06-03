---
title: Cascade Speculative Drafting for Even Faster LLM Inference
title_zh: 级联投机草稿：实现更快的LLM推理
authors: "Ziyi Chen, Xiaocong Yang, Jiacheng Lin, Chenkai Sun, Kevin Chang, Jie Huang"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=lZY9u0ijP7"
tags: ["query:llm"]
score: 8.0
evidence: 级联投机草稿用于更快LLM推理
tldr: 本文提出级联投机草稿（CS Drafting）算法，通过层级草稿生成和重要性感知的token生成来克服传统投机解码中草稿过程缓慢且均匀分配计算的问题。该方法显著降低了目标模型调用次数，进一步加速LLM推理。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-lzy9u0ijp7/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1434, \"height\": 625, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-lzy9u0ijp7/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1308, \"height\": 488, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-lzy9u0ijp7/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 1487, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-lzy9u0ijp7/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 790, \"height\": 359, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-lzy9u0ijp7/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1292, \"height\": 595, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-lzy9u0ijp7/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1402, \"height\": 299, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-lzy9u0ijp7/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 458, \"height\": 226, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-lzy9u0ijp7/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1383, \"height\": 1159, \"label\": \"Table\"}]"
motivation: 投机解码的草稿过程低效，且对所有token分配相同计算。
method: 引入级联草稿结构，结合重要性感知的token生成。
result: 在多个基准上比标准投机解码获得更高加速比。
conclusion: 级联草稿策略能有效提升投机解码的效率。
---

## Abstract
Introduced to enhance the efficiency of large language model (LLM) inference, speculative decoding operates by having a smaller model generate a draft. A larger target model then reviews this draft to align with its output, and any acceptance by the target model results in a reduction of the number of the target model runs, ultimately improving efficiency. However, the drafting process in speculative decoding includes slow autoregressive generation and allocates equal time to generating tokens, irrespective of their importance. These inefficiencies collectively contribute to the suboptimal performance of speculative decoding. To further improve LLM inference, we introduce Cascade Speculative Drafting (CS Drafting), a speculative execution algorithm that incorporates two types of cascades. The *Vertical Cascade* eliminates autoregressive generation from neural models, while the *Horizontal Cascade* optimizes time allocation in drafting for improved efficiency. Combining both cascades, CS Drafting achieves greater speedup compared to the baselines in our experiments, while preserving the same output distribution as the target model. Our code is publicly available at https://github.com/lfsszd/CS-Drafting.

---

## 论文详细总结（自动生成）

### 论文核心问题与整体含义（研究动机和背景）

- **动机**：大型语言模型（LLM）推理延迟严重，尤其在长文本生成中。投机解码（Speculative Decoding）通过小模型生成草稿、大模型并行审查来加速，但草稿过程仍使用低效的自回归生成，且对所有token分配相同的计算时间，导致效率不佳。
- **背景**：投机解码中，草稿模型生成靠后token的接受概率指数下降（仅当所有前序token被接受时才被审查），这些“不重要”的token却消耗了同等计算资源。因此，核心问题是**如何在保持输出分布不变的前提下，进一步提高投机解码的加速比**。

### 方法论：核心思想、关键技术细节

- **核心思想**：引入两类级联——**垂直级联（Vertical Cascade）**和**水平级联（Horizontal Cascade）**，消除神经模型的自回归生成并优化token级计算分配。
- **垂直级联**：草稿模型不再自回归生成，而是由更小的模型（递归直至统计语言模型）为其生成草稿，草稿模型仅作为“审查者”。  
  - 例如：目标模型→审查草稿模型Md1；Md1→审查更小的Md2；Md2→审查统计模型MaG。  
  - 利用**宽容度（lenience）**加速草稿模型间的审查，但不应用于目标模型审查阶段，从而保证最终输出分布与原目标模型一致。
- **水平级联**：在单个投机步骤中，不同位置的token由不同大小的草稿模型生成。  
  - 靠前token（被接受概率高）使用较大的草稿模型；靠后token（被接受概率低）使用较小的草稿模型，甚至直接用统计语言模型。  
  - 公式：EWIF（期望壁时间改进因子）为 \(\frac{\sum_{i=0}^k \prod_{j=1}^i \alpha_j}{1 + \sum_{i=1}^k c_i}\)，其中 \(\alpha_j\) 为第j个token的接受概率，\(c_i\) 为生成第i个token的模型相对成本。
- **Max-Gram（MaG）**：一种高效的统计语言模型，通过贪婪匹配输入中的最长子串来生成token，无匹配时退化为bigram（基于Wikipedia）。GPU友好实现，成本可忽略。
- **算法流程**：结合水平与垂直级联的递归算法，输入为超参数矩阵 \(K_{nn}\)（控制每层生成token数上限），统计模型作为递归基。

### 实验设计

- **数据集与场景**：
  - **GSM8K**（数学推理）和**MMLU**（多任务理解），均采用零样本思维链（zero-shot chain-of-thought）设置。
- **基准方法**：
  - 标准投机解码（S Decoding）使用单一草稿模型；
  - **Medusa**（多解码头加速）及其与树注意力的结合；
  - 自回归生成（基线）。
- **评估指标**：
  - **标准化壁时间改进（SWI）**：假设模型运行时间与参数量或已有延迟数据成正比，保证可复现性。
  - **实际壁时间**：tokens/s，基于单张NVIDIA A40 GPU测量。
- **对比方法**：CS Drafting与不同层数的级联（2层：神经模型+MaG；3层：两个神经模型+MaG）对比；另与S Decoding、Medusa对比。

### 资源与算力

- 文中明确所有壁时间实验在**单张NVIDIA A40 GPU**上进行。未提及训练时长，因为方法无需额外训练，直接使用预训练模型进行零样本推理。标准化SWI假设基于参数量或先前工作的延迟数据，不依赖特定硬件。

### 实验数量与充分性

- **实验组数**：在FLAN-T5系列（目标模型XXL，草稿模型BASE/SMALL）上，对两种数据集各报告了7种设置（含自回归、S Decoding两种草稿、CS Drafting三种组合），总计14组；在Vicuna-7B上报告了5种设置（含自回归、S Decoding、CS Drafting、Medusa、CS Drafting+树注意力）。
- **消融实验**：移除水平级联（性能下降约2.6 tokens/s）；超参数 \(K_{00}\) 的敏感性测试（仅轻微下降）。
- **充分性评价**：实验覆盖了encoder-decoder和decoder-only两种架构，包含主流数据集和多种基线，消融和超参数分析完备。**公平客观**：均采用零样本、温度0（贪婪解码），并与先前工作设置一致；同时提供标准化和实际两种指标以消除硬件偏差。

### 主要结论与发现

- CS Drafting在GSM8K上最高比S Decoding**额外加速44%**，在MMLU上**额外加速81%**（按标准化SWI）。
- 单层CS Drafting（一个神经模型+MaG）已优于最佳S Decoding（例如MMLU上加速70%），且无额外部署开销。
- 结合树注意力后，CS Drafting+Tree Attention在Vicuna-7B上超过Medusa（63.81 vs 61.87 tokens/s）。
- 水平级联的消融证实其贡献显著；统计语言模型MaG几乎零成本，且能有效提升草稿效率。
- 理论分析（EWIF生成函数）支撑了垂直级联在统计模型成本可忽略时总能提升性能。

### 优点

- **保持输出分布不变**：目标模型审查阶段不使用宽容度，严格保证等价性。
- **无需微调或额外训练**：完全利用预训练模型，实用性强。
- **理论分析严谨**：用生成函数推导EWIF，证明了两种级联的有效性。
- **可组合性**：能与树注意力等其他加速技术无缝结合。
- **鲁棒性**：超参数 \(K_{00}\) 在较大范围内性能稳定，降低调参成本。

### 不足与局限

- **硬件依赖性**：实际壁时间结果基于单张A40，不同硬件可能略有差异（作者通过标准化SWI缓解）。
- **统计模型局限性**：MaG基于Wikipedia bigram，对于专业领域词汇或罕见模式匹配可能较差，需验证泛化性。
- **超参数调优**：虽然简单设置已接近最优，但追求最佳性能仍需调整\(K_{nn}\)矩阵；论文未提供自动调优方法。
- **实验覆盖**：未在更大规模模型（如70B+）或更多样化任务（编程、对话）上验证；仅测试了数学推理和知识问答两类。
- **对比基线数量有限**：未与Staged Speculative Decoding（Spector & Re, 2023）等方法直接对比，但垂直级联与之有相似之处。

（完）
