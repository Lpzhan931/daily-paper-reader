---
title: "STree: Speculative Tree Decoding for Hybrid State Space Models"
title_zh: STree：面向混合状态空间模型的投机树解码
authors: "Yangchao Wu, Zongyue Qin, Alex Wong, Stefano Soatto"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=a95Vd41o1u"
tags: ["query:llm"]
score: 7.0
evidence: 面向状态空间模型的投机树解码，提升推理效率
tldr: 针对状态空间模型（SSM）缺乏高效的树验证方法的问题，提出首个可扩展的投机树解码算法，利用树结构同时验证多个候选序列，在保持生成质量的同时实现2-4倍加速。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-a95vd41o1u/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1105, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-a95vd41o1u/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1446, \"height\": 346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-a95vd41o1u/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 727, \"height\": 401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-a95vd41o1u/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 528, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-a95vd41o1u/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1402, \"height\": 399, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-a95vd41o1u/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1393, \"height\": 353, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-a95vd41o1u/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1241, \"height\": 227, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-a95vd41o1u/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 727, \"height\": 401, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-a95vd41o1u/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1281, \"height\": 493, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-a95vd41o1u/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1150, \"height\": 504, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-a95vd41o1u/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 889, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-a95vd41o1u/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1339, \"height\": 267, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-a95vd41o1u/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1065, \"height\": 267, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-a95vd41o1u/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1194, \"height\": 503, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-a95vd41o1u/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1398, \"height\": 159, \"label\": \"Table\"}]"
motivation: 现有SSM投机解码未利用树验证，效率受限。
method: 设计可扩展的树基投机解码算法，高效计算SSM的token树并并行验证。
result: 在多个SSM模型上实现2-4倍加速，且不损失生成质量。
conclusion: 树验证是提升SSM投机解码效率的关键，所提方法填补了空白。
---

## Abstract
Speculative decoding is a technique to leverage hardware concurrency in order to enable multiple steps of token generation in a single forward pass, thus improving the efficiency of large-scale autoregressive (AR) Transformer models. State-space models (SSMs) are already more efficient than AR Transformers, since their state summarizes all past data with no need to cache or re-process tokens in the sliding window context. However, their state can also comprise thousands of tokens; so, speculative decoding has recently been extended to SSMs. Existing approaches, however, do not leverage the tree-based verification methods, since current SSMs lack the means to compute a token tree efficiently. We propose the first scalable algorithm to perform tree-based speculative decoding in state-space models (SSMs) and hybrid architectures of SSMs and Transformer layers. We exploit the structure of accumulated state transition matrices to facilitate tree-based speculative decoding with minimal overhead relative to current SSM implementations. Along with the algorithm, we describe a hardware-aware implementation that improves naive application of AR Transformer tree-based speculative decoding methods to SSMs. Furthermore, we outperform vanilla speculative decoding with SSMs even with a baseline drafting model and tree structure on three different benchmarks, opening up opportunities for further speed up with SSM and hybrid model inference. Code can be find at: https://github.com/wyc1997/stree.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）
投机解码（Speculative Decoding）利用草稿模型快速生成多个候选token，再由目标模型并行验证，从而加速自回归推理。基于树的验证（tree-based verification）在Transformer上效果显著，但在状态空间模型（SSM）中难以实现，因为SSM的状态更新是因果的，缺乏像Transformer注意力机制那样的灵活性来指定树结构。现有SSM投机解码方法只能将树展开为多个独立序列，导致重复计算和内存膨胀。本文提出首个可扩展的SSM树解码算法**STree**，使SSM和混合架构（SSM+Transformer）也能高效利用树验证，显著提升推理速度。

## 2. 方法论：核心思想、关键技术细节、算法流程
- **核心思想**：利用SSM状态转移矩阵的对角化性质，通过**累积状态转移矩阵**（Accumulated State Transition Matrices）将树中所有节点的输出在一次前向传播中并行计算得出。
- **关键技术细节**：
  - 将前缀树节点打包成一个序列，并构建拓扑掩码矩阵 \(L \in \{0,1\}^{N\times N}\) 表示树的父-子关系。
  - 利用SSM参数 \(A_t\)（对角矩阵），定义 \(A_{\text{tree}} = L \cdot A_{\log}\)，其中 \(A_{\log}\) 是 \(\log(A_t)\) 的对角线向量堆叠成的矩阵。
  - 输出公式化简为：
    \[
    y_t = C_t \left( \exp\{(A_{\text{tree}})_t\} \circ x_0 + \sum_{s=1}^t L_{t,s} \exp\{(A_{\text{tree}})_t - (A_{\text{tree}})_s\} \circ (C_t B_s u_s) \right)
    \]
    其中 \(\circ\) 表示逐元素乘法。整个序列的输出可写成矩阵形式 \(y = M_x x_0 + M_u u\)。
  - 这种表示推广了Mamba2的矩阵变换形式，当 \(L\) 为因果注意力掩码时退化为标准SSM。
- **硬件感知实现**：
  - 设计**Tree Scan kernel**，避免实例化中间结果和SSM状态（保持于GPU共享内存）。
  - 使用**激活重放（Activation Replay）** 方法，在投机解码的每次迭代中只重新计算被拒绝部分的状态，避免存储所有状态。
- **算法流程**：
  1. 利用草稿模型从最后的接受token出发，生成一个前缀树（含多个分支）。
  2. 通过激活重放计算目标模型在该token处的正确状态。
  3. 使用Tree Scan kernel一次前向传播得到树中所有token的输出。
  4. 根据目标模型输出与草稿token的匹配情况，接受部分token，拒绝剩余token，并进入下一轮迭代。

## 3. 实验设计
- **数据集/场景**：MT-Bench（对话）、HumanEval（代码生成）、GSM-8K（数学推理）。
- **基准模型**：
  - 目标模型：Mamba2-2.7B、MambaInLlama-8B（50% Transformer + 50% SSM），以及不同Transformer比例的Mamba2-Llama3变体。
  - 草稿模型：从目标模型蒸馏的小型2层SSM（多个检查点）。
- **对比方法**：
  - 自回归（Autoregressive）
  - Vanilla Speculative Decoding（无树验证，使用Fused Selective Scan FSS处理单序列）
  - FSS + 展开树（将树展开为多个序列）
  - Chunk Scan（针对长序列优化，不适用于短序列投机解码）
- **树结构**：静态树（如宽度3、深度4构型）、束搜索树（动态生成）。
- **评估指标**：生成速度（tokens/sec）、平均接受长度（\(\tau\)）、内存占用（GB）。

## 4. 资源与算力
- 所有主实验在**单张Nvidia RTX 3090 GPU**上运行（24GB显存）。
- 附录中补充了**H100 GPU**上的实验结果以验证硬件通用性。
- 论文未提及具体训练时长、卡数或总计算量。蒸馏过程提到使用了48000步/264000步的检查点，但未说明蒸馏所需资源。

## 5. 实验数量与充分性
共包含**6大类实验**，每类下有多组对比：
1. **前向传播开销对比**（Figure 3）：不同树深度（4/5/6层）下STree vs FSS vs Chunk Scan的耗时和状态数。
2. **生成速度与内存对比**（Table 2）：不同树大小（M=2~5, N=4/8/16）下STree vs FSS展开树的吞吐和显存。
3. **端到端生成对比**（Table 3）：3个数据集 × 2种温度（0和1），STree vs Vanilla SD。
4. **消融实验**：
   - 温度影响（Figure 4b,4c）
   - 采样算法（多步投机采样 vs 朴素采样）
   - 静态树结构（5种构型）
   - Transformer比例（50%/25%/0%）
   - 蒸馏步数（12000/48000/264000步）
5. **模型规模扩展**（Table 1）：Mamba2模型2.3B~23B下的延迟对比。
6. **H100与动态树补充**（附录Table 7,8）。

**公平性评价**：对比方法均使用相同的草稿模型、相同的树结构（静态或动态），且运行于同一硬件。接受长度作为内部指标，速度作为最终指标，解释充分。消融实验覆盖了主要变量，结论可靠。

## 6. 主要结论与发现
- **STree是首个可扩展的SSM树解码算法**，能直接解码打包的树序列，避免反复计算，显著优于展开树方法（速度提升最高1.49×，内存降低至0.57×）。
- **在端到端投机解码中**，使用基本草稿模型和静态树，STree在三个基准上均超越Vanilla SD，高温度下优势更明显（如MT-Bench温度1时：STree 54.08 vs Vanilla SD 49.24 tokens/sec）。
- **模型越大，Tree优势越明显**：STree相对于自回归的开销随模型增大而减小（2.04× → 1.26×）。
- **Transformer比例越高，每单位接受长度带来的加速越大**（Speed-up/τ从0.63增至0.66）。
- **接受长度是核心杠杆**：蒸馏更好的草稿模型（更长训练步数）能直接提升生成速度。

## 7. 优点
- **方法创新**：首次为SSM和混合模型设计树解码算法，填补了领域空白。
- **硬件友好**：Tree Scan kernel避免中间状态实例化，内存效率高，易于集成到现有SSM实现。
- **实验充分**：从多个维度（树大小、温度、树结构、模型比例、蒸馏进度）进行了消融和对比，结论扎实。
- **代码开源**：提供https://github.com/wyc1997/stree，便于复现和扩展。
- **分析透彻**：给出了接受长度与模型运行时之间的权衡公式，帮助选择是否使用树解码以及树的大小。

## 8. 不足与局限
- **短序列开销**：在输入长度很小时（如4层满二叉树），STree与FSS速度接近，未体现优势；分析指出需要接受长度有足够提升才能获益。
- **模型规模验证有限**：仅验证到8B（MambaInLlama），更大规模的实验（如13B/23B）仅做了延迟测量，未进行端到端生成测试，结果的可推广性有待验证。
- **草稿模型和树结构依赖**：实验中使用的草稿模型较简单，静态树也非最优；性能上限依赖于更先进的草稿策略和树构建方法（如Sequoia动态规划）。
- **未讨论资源消耗**：蒸馏过程的计算成本未量化，可能影响实用选择。
- **仅涉及贪婪/随机采样**：未扩展到beam search或其他复杂解码策略。
- **局限性明确声明**：论文在最后一节讨论了这些局限，并指出未来工作方向。

（完）
