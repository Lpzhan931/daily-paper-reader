---
title: "SuffixDecoding: Extreme Speculative Decoding for Emerging AI Applications"
title_zh: "SuffixDecoding: 面向新兴AI应用的极端投机解码"
authors: "Gabriele Oliaro, Zhihao Jia, Daniel F Campos, Aurick Qiao"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=uwL0vbeEVn"
tags: ["query:llm"]
score: 8.0
evidence: 投机解码加速LLM推理，利用后缀树处理agent重复请求
tldr: 本文针对LLM agent中重复推理请求的特点，提出SuffixDecoding方法。通过构建高效的后缀树缓存长token序列，草稿模型能快速生成更长且更准确的草稿，大幅提升投机解码的加速比。实验表明，该方法在具身智能等场景下显著降低延迟，为新兴AI应用的推理优化提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-uwl0vbeevn/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1336, \"height\": 534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uwl0vbeevn/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 710, \"height\": 353, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uwl0vbeevn/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 710, \"height\": 375, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uwl0vbeevn/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1439, \"height\": 895, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uwl0vbeevn/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 866, \"height\": 298, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uwl0vbeevn/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1436, \"height\": 692, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uwl0vbeevn/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 707, \"height\": 588, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uwl0vbeevn/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 719, \"height\": 360, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uwl0vbeevn/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 718, \"height\": 464, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 304, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 227, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1447, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1448, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1447, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1450, \"height\": 501, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1449, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1450, \"height\": 488, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1449, \"height\": 500, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1448, \"height\": 497, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1448, \"height\": 276, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1447, \"height\": 276, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1447, \"height\": 249, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1447, \"height\": 275, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1447, \"height\": 274, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 645, \"height\": 452, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1506, \"height\": 333, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1073, \"height\": 275, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uwl0vbeevn/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1139, \"height\": 381, \"label\": \"Table\"}]"
motivation: 现有投机解码未充分利用LLM agent中重复请求的预测性，导致加速受限。
method: 提出SuffixDecoding，利用后缀树缓存历史序列，指导草稿模型生成长序列。
result: 在agent工作负载上实现突破性加速，延迟降低明显。
conclusion: 针对重复请求的投机解码优化可极大提升LLM服务效率。
---

## Abstract
Speculative decoding is widely adopted to reduce latency in large language model (LLM) inference by leveraging smaller draft models capable of handling diverse user tasks. However, emerging AI applications, such as LLM-based agents, present unique workload characteristics: instead of diverse independent requests, agentic frameworks typically submit repetitive inference requests, such as multi-agent pipelines performing similar subtasks or self-refinement loops iteratively enhancing outputs. These workloads result in long and highly predictable sequences, which current speculative decoding methods do not effectively exploit. To address this gap, we introduce \emph{SuffixDecoding}, a novel method that utilizes efficient suffix trees to cache long token sequences from prompts and previous outputs. By adaptively speculating more tokens when acceptance likelihood is high and fewer when it is low, SuffixDecoding effectively exploits opportunities for longer speculations while conserving computation when those opportunities are limited. Evaluations on agentic benchmarks, including SWE-Bench and Text-to-SQL, demonstrate that SuffixDecoding achieves speedups of up to 3.9$\times$, outperforming state-of-the-art methods -- 2.2$\times$ faster than model-based approaches like EAGLE-2/3 and 1.6$\times$ faster than model-free approaches such as Token Recycling. SuffixDecoding is open-sourced.

---

## 论文详细总结（自动生成）

# 论文《SuffixDecoding: Extreme Speculative Decoding for Emerging AI Applications》详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：大语言模型（LLM）推理延迟是主要瓶颈，投机解码（Speculative Decoding）通过轻量草稿模型预测多个token并由LLM并行验证来加速。然而现有方法（模型基或模型无关）**未充分挖掘新兴AI应用（如LLM agent）的重复性工作负载**——这些应用产生大量可预测的、长序列的重复输出（如多智能体流水线、自我修正循环）。模型基方法开销大且自适应差，模型无关方法（如Prompt Lookup Decoding）固定长度推测，缺乏灵活性。
- **动机**：需要一种既能**极快生成草稿**（无GPU开销）又能**根据预测置信度自适应推测长度**的方法，以最大化对重复序列的加速潜力。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
- **SuffixDecoding**：一种**模型无关**的投机解码方法，利用**后缀树（Suffix Tree）** 缓存历史token序列（当前请求的prompt/输出 + 之前所有请求的输出），快速匹配当前上下文的后缀模式，并基于频率统计构建推测树，由LLM并行验证。

### 关键技术细节
1. **双后缀树结构**：
   - **全局后缀树**：存储所有之前请求的输出（可离线构建或在服务过程中累积）。
   - **逐请求后缀树**：存储当前正在进行的请求的prompt和已生成token，支持在线更新。
   - 两棵树独立维护，避免多请求同步开销。

2. **模式匹配与推测树生成**：
   - 给定当前token序列的后缀（长度为`p`），在后缀树中定位对应节点`Np`。
   - 从`Np`开始**贪心扩展**，每次选择使`D(N)`最大的子节点加入推测树，直至达到`MAX_SPEC`大小。  
     - `C(N)`：节点N在参考语料中的出现次数（估计条件概率）。  
     - `D(N)`：节点N被验证接受的概率，递归定义为`D(Parent(N)) * C(N)`（根节点`D=1`）。
   - 同时考虑全局树和逐请求树，对不同`p`值生成多个候选推测树，选择**总分最高的**（`SCORE(T)=∑D(N)`）。

3. **自适应推测长度**：
   - 观察发现**接受token数量与模式匹配长度`p`正相关**，因此设置`MAX_SPEC = α·p`，其中α为**最大推测因子**（实验建议α∈[1,4]）。模式匹配长时推测更多token，短时保守推测，避免浪费验证计算。

4. **混合推测**：
   - 可集成模型基推测方法（如EAGLE-3）：当`SCORE`低于阈值τ时回退到模型基推测，实现“两全其美”。τ设为回退方法平均接受token数时效果最佳。

5. **算法流程**（算法1）：
   - 对每个解码步骤，遍历两个后缀树及不同`p`，调用`MatchPattern`和`ExpandSpeculationTree`，选出最优推测树，由LLM一次前向传播验证。

## 3. 实验设计：数据集、场景、对比方法

### 数据集/场景
| 类别 | 具体数据集/应用 | 特点 |
|------|----------------|------|
| **Agentic工作负载** | SWE-Bench（OpenHands agent解决GitHub问题） | 长序列、高重复（agent迭代修改代码） |
| | AgenticSQL（专有多智能体SQL生成流水线，含Classify/Extract/Enrich/SQL1-3/Combine等子任务） | 结构化输出、高度重复模式 |
| **非Agentic（对比）** | Spec-Bench（13类任务，含MT-Bench 8项、open-ended问答等） | 开放域、多样性高 |
| **额外消融** | WildChat（开放域聊天）、Magicoder（代码聊天）、SpiderSQL | 检测分布偏移、可扩展性 |

### 对比方法
- **模型基**：EAGLE, EAGLE-2, EAGLE-3（SOTA）
- **模型无关**：Prompt Lookup Decoding (PLD), Token Recycling
- **基线**：Vanilla（无推测解码）
- **SuffixDecoding变体**：linear（线性推测链）和tree（树状推测）；Hybrid（+EAGLE-3回退）

### 评估指标
- **平均每步接受token数**（Mean Accepted Tokens）
- **加速比**（Speedup over Vanilla = 每输出token墙钟时间比值）
- **端到端任务完成时间**（仅SWE-Bench，含prefill、生成、代码执行）

## 4. 资源与算力

- **硬件**：单台AWS p5.48xlarge实例，配备 **8× NVIDIA H100 80G GPU**，2TB主存。
- **实验模式**：单batch size=1推理（Spec-Bench模式）；端到端SWE-Bench使用4卡tensor parallelism + prefix caching，并发8个任务。
- **训练/更新**：后缀树在CPU上构建，无需GPU训练，更新和查询均在μs级别（见表2：~4μs更新/token，~12μs查询/推测token）。
- **未说明**：训练草稿模型（无），因此无GPU训练时长；推理实验为单次执行，未报告多次重复。

## 5. 实验数量与充分性

### 实验组数
- **主实验**（图4）：3个benchmark × 7~10种方法，结果以条形图加数值显示。
- **消融实验**：
  - 全局 vs 逐请求后缀树（图7，7个子任务）
  - 自适应 vs 固定推测长度（图2b，模拟）
  - 分布偏移（图9，WildChat→SpiderSQL，在线适应）
  - 混合阈值敏感性（附录表3、表4）
  - 不同后缀树规模对速度的影响（图8，WildChat/Magicoder）
  - 内存/时间扩展（附录表2）
- **端到端实验**（图6）：SWE-Bench Verified上比较SuffixDecoding与PLD，按不同仓库分解。

### 充分性与公平性
- **充分**：覆盖了agentic和非agentic两类场景，包含模型基和模型无关基线，有多项消融验证设计选择。
- **公平**：所有方法在同一硬件/软件栈（vLLM）上测试；EAGLE-2/3因长上下文限制无法在SWE-Bench运行（已标注）；使用标准Spec-Bench框架。
- **局限**：未报告多个随机种子的误差棒（论文称未报告误差棒）；未比较其他agent专用加速方法（如ALTO, Dynasor）——但后者与推测解码正交。

## 6. 主要结论与发现

- **在Agentic负载上SuffixDecoding显著加速**：
  - AgenticSQL：平均加速**5.3×**（vs Vanilla），比EAGLE-2/3快**2.8×**，比Token Recycling快**1.9×**。
  - SWE-Bench：平均加速**2.5×**（vs Vanilla），比PLD快**1.7×**（EAGLE无法运行）。
  - 端到端SWE-Bench解码时间降低**1.8–4.5×**，总任务时间降低与之成比例。
- **混合模式取得最佳平衡**：在Spec-Bench（非agentic）上Hybrid（Suffix+EAGLE-3）加速**2.5×**，超越单独EAGLE-3（2.4×）和Token Recycling（2.2×）。
- **自适应推测长度提升效率**：`MAX_SPEC=α·p`比固定长度获得更好的加速-接受率权衡。
- **双后缀树互补**：全局树对结构化任务（如Extract/Enrich）效果好，逐请求树对重复利用上下文（Combine）效果好。
- **可在线适应分布偏移**：从WildChat切换到SpiderSQL，仅需500个新样例即可与离线训练性能相当。

## 7. 优点

- **模型无关、零额外GPU开销**：草稿生成仅CPU操作（后缀树查找），极快（~20μs/token），不消耗GPU算力。
- **自适应推测长度**：根据模式匹配长度动态调整推测token数，避免浪费验证计算。
- **双树设计**：同时利用全局历史输出和当前请求上下文，覆盖多种重复模式来源。
- **可混合模型基方法**：在开放域任务中通过回退机制结合模型基推测，实现“两全其美”。
- **易于集成**：已集成到vLLM，支持生产部署；支持批处理（附录C讨论与TurboSpec/AdaServe兼容）。
- **内存可扩展**：CPU内存（2TB）足够缓存数周的生成token（约31天），支持LRU驱逐。
- **结构化任务特别高效**：如JSON布尔值分支、多SQL候选等，可一次推测数十个token。

## 8. 不足与局限

- **对非重复/开放域任务局限性大**：单独SuffixDecoding在Spec-Bench上仅1.7×加速，远弱于EAGLE-3（2.4×）——需要混合回退机制。
- **依赖历史数据质量**：如果历史输出与当前任务分布偏差大，性能会下降（但实验显示能迅速在线适应）。
- **未报告多次运行方差**：论文未给出误差棒或置信区间，结果稳定性未知。
- **未与特定agent加速方法直接比较**：如ALTO（流水线调度）、Dynasor（早期终止）是正交优化，但可组合使用。
- **仅测试自回归模型（Llama-3.1-8B）**：未验证其他架构（如MoE、encoder-decoder）的通用性。
- **模拟验证假设贪心采样**：实际生产可能使用随机采样，尽管方法原理上兼容（推测树验证阶段处理不同采样策略）。
- **未讨论安全/伦理影响**：加速本身无直接危害，但加速agent可能放大错误或恶意使用风险，论文未提及。

（完）
