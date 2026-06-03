---
title: "When Linear Attention Meets Autoregressive Decoding: Towards More Effective and Efficient Linearized Large Language Models"
title_zh: 当线性注意力遇上自回归解码：迈向更高效且更有效的线性化大语言模型
authors: "Haoran You, Yichao Fu, Zheng Wang, Amir Yazdanbakhsh, Yingyan Celine Lin"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=7mFSaP6IiN"
tags: ["query:llm"]
score: 8.0
evidence: 结合线性注意力和投机解码提升LLM效率
tldr: 自回归LLM面临注意力二次复杂度和顺序解码两大瓶颈。本文首次系统研究线性注意力与投机解码的结合潜力，提出一种增强技术使线性化LLM更好地与投机解码协同工作，从而在保持性能的同时提升推理速度。实验验证了方法的有效性。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-7mfsap6iin/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 849, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-7mfsap6iin/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 861, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-7mfsap6iin/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 839, \"height\": 451, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-7mfsap6iin/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 778, \"height\": 652, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-7mfsap6iin/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 846, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-7mfsap6iin/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 850, \"height\": 598, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-7mfsap6iin/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 844, \"height\": 526, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-7mfsap6iin/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1777, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-7mfsap6iin/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 892, \"height\": 475, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-7mfsap6iin/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 853, \"height\": 326, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-7mfsap6iin/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 858, \"height\": 326, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-7mfsap6iin/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 851, \"height\": 328, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-7mfsap6iin/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1766, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-7mfsap6iin/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 856, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-7mfsap6iin/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 852, \"height\": 134, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-7mfsap6iin/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 855, \"height\": 171, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-7mfsap6iin/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 856, \"height\": 218, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-7mfsap6iin/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 850, \"height\": 150, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-7mfsap6iin/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1062, \"height\": 234, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-7mfsap6iin/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1250, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-7mfsap6iin/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 985, \"height\": 179, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-7mfsap6iin/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 987, \"height\": 359, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-7mfsap6iin/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1237, \"height\": 523, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-7mfsap6iin/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1060, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-7mfsap6iin/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1238, \"height\": 351, \"label\": \"Table\"}]"
motivation: 线性注意力和投机解码各自有潜力解决LLM效率问题，但二者的协同效果尚不明确。
method: 对现有线性注意力方法进行整合，并提出增强技术以适配投机解码。
result: 实验表明结合线性注意力和投机解码可取得显著加速，同时保持生成质量。
conclusion: 线性注意力和投机解码可互补，共同加速LLM推理。
---

## Abstract
Autoregressive Large Language Models (LLMs) have achieved impressive performance in language tasks but face two significant bottlenecks: (1) quadratic complexity in the attention module as the number of tokens increases, and (2) limited efficiency due to the sequential processing nature of autoregressive LLMs during generation. While linear attention and speculative decoding offer potential solutions, their applicability and synergistic potential for enhancing autoregressive LLMs remain uncertain. We conduct the first comprehensive study on the efficacy of existing linear attention methods for autoregressive LLMs, integrating them with speculative decoding. We introduce an augmentation technique for linear attention that ensures compatibility with speculative decoding, enabling more efficient training and serving of LLMs. Extensive experiments and ablation studies involving seven existing linear attention models and five encoder/decoder-based LLMs consistently validate the effectiveness of our augmented linearized LLMs. Notably, our approach achieves up to a 6.67 reduction in perplexity on the LLaMA model and up to a 2$\times$ speedup during generation compared to prior linear attention methods. Codes and models are available at https://github.com/GATECH-EIC/Linearized-LLM.

---

## 论文详细总结（自动生成）

# 中文论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- 自回归大语言模型（LLMs）在语言任务上表现出色，但面临两大效率瓶颈：
  - **瓶颈1**：注意力模块复杂度随输入序列长度呈二次增长，限制了长上下文处理能力。
  - **瓶颈2**：自回归解码的串行本质导致生成阶段并行度低，推理速度慢。
- 现有方法中，**线性注意力**（Linear Attention）旨在解决瓶颈1（将复杂度降至线性），**投机解码**（Speculative Decoding）旨在解决瓶颈2（通过草稿模型并行生成然后验证）。
- 然而，这些技术能否有效应用于自回归LLM，以及两者能否协同工作，此前缺乏系统性研究。
- 本文首次全面探索了线性注意力与投机解码的结合潜力，并针对现有线性注意力在自回归LLM中的失效问题提出了增强方法。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：对现有线性注意力进行局部增强，使其适配自回归解码的因果性，并设计兼容投机解码树形注意力的机制。
- **关键技术细节**：
  - **掩码深度可分离卷积（Masked DWConv）**：在注意力V分支中加入因果掩码的深度可分离卷积，增强局部特征提取，同时防止未来信息泄露（图5右分支）。解决了现有卷积增强（如DWConv）在自回归设置中导致信息泄漏的问题。
  - **分组线性注意力（Grouped Linear Attention）**：将输入序列划分为非重叠组，组内并行处理（使用softmax局部注意力），组间累积和（cumsum）进行跨组交互，提升效率（图5中分支）。
  - **与投机解码的兼容性设计**：投机解码中多个候选token同时生成，传统卷积和分组方案会错误捕获时序依赖。本文提出：
    - **展开卷积（Unfolded DWConv）**：将卷积表示为矩阵乘法（类似img2col），使得卷积核能够根据树形注意力掩码正确对齐时序依赖（图8b）。
    - **基于时间依赖的分组策略**：忽略每步候选数量，按实际时间步分组，确保每组内只访问已验证的前序token。
- **整体架构**（图5）包含三个分支：局部注意力（左）、分组累积和（中）、掩码DWConv（右），三者结合构成增强线性注意力。

## 3. 实验设计：数据集、场景、对比方法
- **模型**：
  - 小规模：FLASH（110M参数，从零训练）、GPT-2（~500M）、T5（~900M）。
  - 大规模：LLaMA-2-7B、LLaMA-2-13B（微调）。
- **任务与数据集**：
  - 语言建模：Wiki40B（FLASH训练）、PG-19（LLaMA评估）、RedPajama（LLaMA微调）。
  - 文本分类：GLUE基准（SST2、WNLI、QNLI、MNLI、RTE、MRPC、QQP）。
  - 零样本/少样本下游任务：BBH、PIQA、MMLU、COPA、ARCC、AGNews。
  - 生成速度：MT-Bench（结合投机解码测试吞吐量）。
- **对比方法（基线）**：
  - 7种线性注意力：FLASH-Local、FLASH-Global、Linformer、Performer、TransNormer、YOSO、ReLU。
  - 原始softmax注意力作为上界。
  - 投机解码基线：Medusa。
- **评估指标**：分类准确率、困惑度、推理延迟、内存占用、吞吐量（tokens/s）。

## 4. 资源与算力
- 文中明确提到的GPU型号：A5000（用于BERT profiling）、A100（24K? 实际为A100-80G用于LLaMA推理和训练）。
- **训练资源配置**：
  - FLASH从零训练：110M参数，序列长度1024，批大小256，训练步骤100K步（enwik8或Wiki40B），使用AdamW优化器。未明确GPU数量，推测单卡。
  - LLaMA-2微调：1K步，批大小64，峰值学习率2e-5，使用AdamW。训练在1个A100-80G上完成（？文中未明说，但从上下文推测使用单卡）。
- **推理资源**：LLaMA-2-7B/13B推理在单张A100-80G上测试，对比原始注意力内存和延迟。
- 总体而言，算力细节部分明确（GPU型号、步数、批大小），但具体训练时长未给出，可认为资源使用中等规模。

## 5. 实验数量与充分性
- **实验数量**：大量实验（正文+附录共17页），包括：
  - 7种线性注意力在3类LLM上的GLUE性能对比（Tables 1-3）。
  - 提出的增强方法在5种模型上的评估：语言建模（Table 15）、文本分类（Table 14）、下游任务准确率（Table 7）。
  - 推理延迟和内存对比（Tables 4-5）。
  - 与投机解码结合的吞吐量对比（Table 8）。
  - 消融实验：各组件贡献（Tables 12-13、图6）。
  - 扩展到更多线性注意力方法（Table 16）、更长序列（Section 5.3）。
- **充分性与公平性**：
  - 覆盖了多种模型规模（110M~13B）、多种任务（分类、语言建模、推理效率），对比基线全面。
  - 消融实验验证了掩码DWConv、分组策略、局部注意力的单独贡献。
  - 实验设置规范（如遵循LongLora、Medusa的设置），结果报告客观（包括OOM情况）。
  - 不足：主要验证了7B/13B规模，未在更大模型（如30B+）上测试；部分实验（如FLASH from scratch）使用了相对较小的110M模型，可能低估了在实际大模型上的挑战。

## 6. 论文的主要结论与发现
- 现有线性注意力方法在encoder-based LLM（如BERT）上表现较好，但在decoder-based/encoder-decoder LLM（GPT-2、T5）上性能显著下降，且直接结合投机解码效果差。
- 提出的增强线性注意力（掩码DWConv + 分组线性注意力）有效提升了自回归LLM的性能：
  - 在LLaMA-2-7B/13B上困惑度降低最多6.67。
  - 推理延迟降低可达56%，内存节省36%，支持序列长度从8K扩展到32K。
  - 与投机解码结合后生成速度提升约2倍。
- 增强方法可推广到多种线性注意力（RFA、Performer、Linformer），平均准确率提升5%~8%。

## 7. 优点：方法或实验设计上的亮点
- **创新性**：首次系统研究线性注意力与投机解码的协同问题，提出实用的兼容性解决方案（展开卷积、时间依赖分组）。
- **技术贡献**：掩码DWConv简洁有效地解决了信息泄露问题；分组线性注意力提升了训练并行性。
- **实验全面性**：覆盖主流线性注意力方法和多种LLM架构，包含大规模模型（13B）和真实场景任务（MT-Bench），消融分析深入。
- **效率与效果兼顾**：在降低计算复杂度的同时，通过增强保持甚至提升模型质量（部分任务准确率超过原始softmax）。
- **开源**：代码和模型已公开，有利于复现和后续研究。

## 8. 不足与局限
- **规模限制**：最大实验模型为13B，未在更大模型（如70B、130B）上验证，线性注意力的优势在超长序列和大模型上可能更明显，但结论的泛化性需进一步确认。
- **任务覆盖**：主要使用GLUE和语言建模基准，缺乏对复杂长上下文任务（如长文档问答、代码生成）的评估，而这些正是线性注意力的目标场景。
- **投机解码集成开销**：虽然整体加速明显，但展开卷积和分组策略会引入额外计算，论文未详细量化这部分开销。
- **对比公平性**：与原始softmax注意力的延迟对比中，未使用同等优化的flash attention内核（但线性注意力本身具有常数cache优势）。
- **训练效率**：论文主要强调推理加速，训练阶段（从零训练FLASH）虽提到速度提升，但未提供详细训练时间数据。
- **超参数敏感**：α平衡参数（局部vs全局）需要调优，不同模型可能需调整。

（完）
