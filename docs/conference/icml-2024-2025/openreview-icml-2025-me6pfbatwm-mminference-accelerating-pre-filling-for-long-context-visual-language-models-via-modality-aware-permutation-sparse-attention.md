---
title: "MMInference: Accelerating Pre-filling for Long-Context Visual Language Models via Modality-Aware Permutation Sparse Attention"
title_zh: MMInference：通过模态感知排列稀疏注意力加速长上下文视觉语言模型的预填充
authors: "Yucheng Li, Huiqiang Jiang, Chengruidong Zhang, Qianhui Wu, Xufang Luo, Surin Ahn, Amir H. Abdi, Dongsheng Li, Jianfeng Gao, Yuqing Yang, Lili Qiu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=me6PfbATWM"
tags: ["query:vlm-spec"]
score: 8.0
evidence: 加速长上下文视觉语言模型的预填充阶段
tldr: 本文提出MMInference，一种动态稀疏注意力方法，针对长上下文多模态输入的预填充阶段进行加速。通过分析视频输入的时空局部性和不同模态的稀疏分布，设计模态感知的排列稀疏注意力，大幅降低计算复杂度，在保持精度的前提下显著缩短了预填充时间。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 657, \"height\": 774, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1711, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1729, \"height\": 1269, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1347, \"height\": 839, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 858, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 859, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 865, \"height\": 395, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 868, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1653, \"height\": 452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 859, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 821, \"height\": 473, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1083, \"height\": 592, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1349, \"height\": 1024, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1375, \"height\": 501, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1373, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 895, \"height\": 462, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 799, \"height\": 450, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 901, \"height\": 450, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 893, \"height\": 496, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 889, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 895, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 895, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1154, \"height\": 573, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 894, \"height\": 463, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 880, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1042, \"height\": 629, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1686, \"height\": 1799, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-me6pfbatwm/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1690, \"height\": 887, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-me6pfbatwm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1756, \"height\": 986, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-me6pfbatwm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 747, \"height\": 853, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-me6pfbatwm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1597, \"height\": 217, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-me6pfbatwm/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1323, \"height\": 351, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-me6pfbatwm/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 906, \"height\": 1180, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-me6pfbatwm/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1711, \"height\": 1232, \"label\": \"Table\"}]"
motivation: 长上下文VLM在预填充阶段面临二次注意力计算复杂度，成为部署瓶颈。
method: 利用视频的时空稀疏性和模态差异性，设计模态感知的排列稀疏注意力，只计算重要位置的注意力。
result: 在长视频理解等任务上，预填充速度提升数倍，且性能损失极小。
conclusion: 稀疏注意力能有效加速长上下文VLM的预填充阶段。
---

## Abstract
The integration of long-context capabilities with visual understanding unlocks unprecedented potential for Vision Language Models (VLMs). However, the quadratic attention complexity during the pre-filling phase remains a significant obstacle to real-world deployment. To overcome this limitation, we introduce MMInference (Multimodality Million tokens Inference), a dynamic sparse attention method that accelerates the prefilling stage for long-context multi-modal inputs. First, our analysis reveals that the temporal and spatial locality of video input leads to a unique sparse pattern, the Grid pattern. Simultaneously, VLMs exhibit markedly different sparse distributions across different modalities. We introduce a permutation-based method to leverage the unique Grid pattern and handle modality boundary issues. By offline search the optimal sparse patterns for each head, MMInference constructs the sparse distribution dynamically based on the input. We also provide optimized GPU kernels for efficient sparse computations. Notably, MMInference integrates seamlessly into existing VLM pipelines without any model modifications or fine-tuning. Experiments on multi-modal benchmarks-including Video QA, Captioning, VisionNIAH, and Mixed-Modality NIAH-with state-of-the-art long-context VLMs (LongVila, LlavaVideo, VideoChat-Flash, Qwen2.5-VL) show that MMInference accelerates the pre-filling stage by up to 8.3x at 1M tokens while maintaining accuracy. Our code is available at https://ama.ms/MMInference.

---

## 论文详细总结（自动生成）

# MMInference 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：长上下文视觉语言模型（VLM）在预填充阶段（pre-filling）面临注意力机制的二次复杂度问题，导致首令牌延迟（Time-to-First-Token）极高，严重阻碍了其在真实场景（如机器人、自动驾驶、医疗）中的部署。例如，处理128k token的视频输入时，注意力计算占总延迟的绝大部分。
- **背景**：现有稀疏注意力方法（如MInference）主要针对纯文本LLM设计，未能利用VLM中多模态输入的独特稀疏模式，尤其是在混合模态（视频+文本）场景下，存在模态边界问题导致性能下降。

## 2. 论文提出的方法论

### 核心思想
利用视频输入的时空局部性（形成Grid模式）以及模态间稀疏分布的差异性，设计模态感知的排列稀疏注意力，实现高效动态稀疏计算。通过离线搜索为每个注意力头找到最优稀疏模式，在线动态构建稀疏索引，并使用优化的GPU内核加速。

### 关键技术细节
- **Grid Head**：针对视频帧产生的网格状注意力模式（均匀分布的水平和垂直线），通过在线估计注意力矩阵确定网格步长和相位，然后对Q、K、V进行排列（permutation），将稀疏的网格元素集中为连续块，从而允许密集的块级计算（通过FlashAttention），大幅减少计算量。
- **模态边界处理**：
  - **Q-Boundary**：在查询维度上出现模态边界。通过按模态类型对Q进行排列，然后对每个模态内的查询独立应用稀疏注意力，利用模态内连续性。
  - **2D-Boundary**：在查询和键两个维度都有模态边界。对Q、K、V均按模态排列，然后遍历模态对（如视觉到文本）分别计算稀疏注意力，并正确构建注意力掩码。
- **Modality-Aware Sparse Attention Search Algorithm**：离线搜索，分三步：1) 模态内搜索（使用A-shape、Vertical-Slash、Grid模式）；2) 跨模态搜索（所有模态对）；3) 模态间搜索（结合前两步结果）。在固定FLOPs预算下选择召回率最高的模式。
- **GPU Kernel优化**：基于Triton和FlashAttention实现块稀疏加载与密集计算，使用FlashDecoding模式稀疏化查询加载，FlashAttention-2模式稀疏化键加载。不显式排列张量，而是在内核中动态加载和写入。

### 算法流程（文字说明）
- Grid Head：用最后64个查询估计注意力矩阵 → 在线搜索网格步长和相位 → 排列Q、K、V → 稀疏块注意力。
- Q-Boundary Head：按模态排列Q → 循环处理每个模态的查询 → 对每个模态调用模态内稀疏注意力。
- 2D-Boundary Head：排列Q、K、V → 双重循环遍历模态对 → 为每个模态对构建注意力掩码并调用稀疏注意力。

## 3. 实验设计

### 使用的数据集/场景
- **长视频理解任务**：ActNet-QA, EgoSchema, Next-QA, PerceptionTest, VideoDC, VideoMME（涵盖视频问答、字幕生成，帧数范围110~256，token数约20k~66k）。
- **Video Needle in a Haystack (V-NIAH)**：长视频检索任务，帧数最多6000帧（约1.1M tokens），评估模型在大规模上下文中的检索能力。
- **Mixed-Modality Needle in a Haystack (MM-NIAH)**：新提出的任务，在视频中插入25%的文本段（混合模态），帧数最多4500帧（约1.1M tokens），测试混合模态检索能力。

### 对比方法
- **稀疏注意力基线**：SparseTransformer (Fixed/Strided), A-shape, Tri-shape, Vertical-Slash (MInference), MInference。
- **视觉token压缩方法**：VisionZip。
- **全注意力基线**：FlashAttention-2。

### 模型
LongVILA-7B-1M, Llava-Video-7B, VideoChat-Flash, Qwen2.5-VL-7B-Instruct。

## 4. 资源与算力

论文在实验部分提到：“Latency experiments are performed on a single NVIDIA A100 using bfloat16”。未明确说明训练（搜索）时长，但提到搜索时间约15分钟（在单个A100上，使用egoschema任务的一个样本，不足25k tokens）。未提及多卡训练或具体GPU数量。

## 5. 实验数量与充分性

- **多维度覆盖**：在6个长视频理解数据集上评估，额外有V-NIAH和MM-NIAH两个长上下文检索任务，涵盖问答、字幕生成、检索等。
- **消融实验**：在MM-NIAH上对比了有无模态间处理（w/ Inter vs w/o Inter）的效果。
- **对比充分**：与5种稀疏注意力方法、1种token压缩方法以及全注意力进行比较，公平性较好（FLOPs对齐，如Tri-shape采用相近FLOPs配置）。
- **扩展性验证**：在VideoChat-Flash（已使用视觉token压缩）上验证了兼容性。
- **普遍性**：在四种不同架构的VLM上均进行了测试。

总体实验较为充分，覆盖了常见视频理解任务和长上下文检索，消融实验验证了模态间处理的有效性，对比基线全面。

## 6. 论文的主要结论与发现

- MMInference在保持全注意力精度（性能损失极小，如Llava-Video上平均差异<1%）的情况下，将预填充阶段加速最高8.3倍（针对1M tokens，相比FlashAttention-2），相比MInference加速1.7倍。
- Grid模式在视觉输入中优势明显，比Vertical-Slash模式稀疏性更好，GPU延迟更低（1M tokens时Grid延迟358ms）。
- 模态边界处理(Q-Boundary/2D-Boundary)对混合模态输入至关重要，忽略会导致性能显著下降（如MM-NIAH中MInference的召回率从96.7%降至88%）。
- 稀疏索引在相同模态内可以跨模态边界外推，但不同模态间不能直接共享。

## 7. 优点

- **系统-算法协同设计**：从底层GPU kernel优化到上层稀疏模式搜索，实现端到端加速。
- **无需模型修改或微调**：即插即用，兼容现有VLM pipeline。
- **新颖的排列技术**：将不规则稀疏网格转化为连续块，利用硬件张量核心高效计算，解决了以往稀疏注意力中不规则内存访问问题。
- **全面考虑模态边界**：不仅提出了Grid模式，还分类处理了四种模态边界类型，适用于混合模态输入。
- **低开销**：在线近似注意力矩阵时仅用最后64个查询，索引构建开销极小。

## 8. 不足与局限

- **实验覆盖方面**：主要基于7B参数的VLM评估，未在更大规模模型（如13B/70B）上验证；仅测试了视觉-文本混合模态，未涵盖音频或图像-文本混合模态（但论文提及在Audio LM中观察到类似边界现象）。
- **应用限制**：Grid模式假设视频帧是均匀采样的（固定帧间隔），对于非均匀采样或动态分辨率的输入可能适应性有限（论文在Qwen2.5-VL上进行了初步可视化，但未深入分析）。
- **偏差风险**：离线搜索仅使用单一任务（EgoSchema）的一个样本，可能存在领域偏差，虽然论文声称泛化良好，但未大规模验证。
- **资源消耗**：虽然推理速度快，但离线搜索仍需约15分钟和一定手动调整搜索空间，对于新模型可能需要重复搜索。
- **理论分析**：稀疏注意力可能导致信息丢失，尤其是对于需要细粒度跨模态对齐的任务（如细粒度动作识别），论文仅在整体指标上验证，未深入分析失败场景。

（完）
