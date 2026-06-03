---
title: "Grounding Language with Vision: A Conditional Mutual Information Calibrated Decoding Strategy for Reducing Hallucinations in LVLMs"
title_zh: 语言与视觉对齐：基于条件互信息校准的解码策略减少LVLM幻觉
authors: "Hao Fang, Changle Zhou, Jiawei Kong, Kuofeng Gao, Bin Chen, Tao Liang, Guojun Ma, Shu-Tao Xia"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=W5HnIf2jla"
tags: ["query:vlm-spec"]
score: 5.0
evidence: 减少LVLM幻觉的解码策略，与VLM推理相关
tldr: 本文针对LVLM中过度依赖语言先验导致幻觉的问题，提出条件互信息（C-PMI）校准的解码策略。通过自适应增强生成文本与输入图像之间的互依性，减少对语言先验的依赖。与仅关注文本采样的方法不同，该方法联合建模视觉和文本贡献，实验证明能有效抑制幻觉，提升多模态生成质量。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-w5hnif2jla/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1434, \"height\": 401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-w5hnif2jla/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1424, \"height\": 614, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-w5hnif2jla/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1436, \"height\": 1168, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-w5hnif2jla/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 494, \"height\": 328, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-w5hnif2jla/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 938, \"height\": 322, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-w5hnif2jla/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 653, \"height\": 442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-w5hnif2jla/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 650, \"height\": 428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-w5hnif2jla/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1368, \"height\": 432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-w5hnif2jla/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1364, \"height\": 1708, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-w5hnif2jla/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1442, \"height\": 1941, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-w5hnif2jla/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1457, \"height\": 1370, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-w5hnif2jla/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 149, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-w5hnif2jla/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1456, \"height\": 640, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-w5hnif2jla/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1345, \"height\": 315, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-w5hnif2jla/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1115, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-w5hnif2jla/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1029, \"height\": 416, \"label\": \"Table\"}]"
motivation: LVLM过度依赖语言先验而忽略视觉信息导致幻觉。
method: 提出C-PMI校准解码，增强文本与图像的互信息。
result: 显著减少幻觉，提高多模态生成可靠性。
conclusion: 互信息校准可有效纠正LVLM中的模态不平衡。
---

## Abstract
Large Vision-Language Models (LVLMs) are susceptible to hallucinations, where generated responses seem semantically plausible yet exhibit little or no relevance to the input image. Previous studies reveal that this issue primarily stems from LVLMs' over-reliance on language priors while disregarding the visual information during decoding. To alleviate this issue, we introduce a novel Conditional Pointwise Mutual Information (C-PMI) calibrated decoding strategy, which adaptively strengthens the mutual dependency between generated texts and input images to mitigate hallucinations. Unlike existing methods solely focusing on text token sampling, we propose to jointly model the contributions of visual and textual tokens to C-PMI, formulating hallucination mitigation as a bi-level optimization problem aimed at maximizing mutual information. To solve it, we design a token purification mechanism that dynamically regulates the decoding process by sampling text tokens remaining maximally relevant to the given image, while simultaneously refining image tokens most pertinent to the generated response. Extensive experiments across various benchmarks reveal that the proposed method significantly reduces hallucinations in LVLMs while preserving decoding efficiency.

---

## 论文详细总结（自动生成）

# 论文详细总结：Grounding Language with Vision: A Conditional Mutual Information Calibrated Decoding Strategy for Reducing Hallucinations in LVLMs

## 1. 核心问题与整体含义（研究动机与背景）

- **问题**：大型视觉-语言模型（LVLMs）在生成文本时经常出现“幻觉”——输出语义流畅但与输入图像内容无关或错误（例如描绘不存在的物体、错误描述属性或关系）。这严重限制了LVLMs在医疗诊断、金融等高风险场景中的应用。
- **原因**：已有研究表明，幻觉主要由LVLMs在自回归解码过程中过度依赖语言先验（language priors），而对视觉信息的关注不足导致。具体表现为，尽管图像token在输入中占多数，但其累积注意力分数远低于文本token（见图1a）。
- **研究动机**：从信息论视角出发，通过增强生成文本与输入图像之间的互依性（mutual dependency）来从根本上减少幻觉。现有解码策略多为经验性设计，缺乏理论支撑，且未能显式量化和控制动态互相关性。

## 2. 方法论：核心思想、关键技术细节与算法流程

### 2.1 核心思想

- 以**条件点互信息（Conditional Pointwise Mutual Information, C-PMI）**为理论基础，将幻觉缓解重新表述为最大化图像与文本之间的互信息问题。
- 将该问题分解为两个互补子任务（文本侧和视觉侧），形成**双层优化（bi-level optimization）**框架，通过交替优化文本token分布和视觉token集合来最大化C-PMI。

### 2.2 关键技术细节

#### （1）校准分布采样（文本侧）
- 基于C-PMI公式，构建校准后的token分布：
  \[
  y_t \sim p_c(\cdot|v,x,y_{<t}) = \text{softmax}\left[(1+\lambda) f_\theta(\cdot|v,x,y_{<t}) - \lambda f_\theta(\cdot|x,y_{<t})\right]
  \]
  其中 \(\lambda\) 为超参数（默认0.5），用于控制对视觉信息的依赖强度。该分布优先选择与图像更相关的token，抑制仅依赖语言的幻觉token。
- 结合自适应token截断机制，进一步缩小采样空间以提高生成质量。

#### （2）视觉token净化（视觉侧）
- 设计一个轻量级**视觉token净化器（Visual Token Purifier）**，由少量Transformer块和MLP组成，学习在当前文本上下文下保留哪些图像token最有利于C-PMI最大化。
- 净化器输入为图像token、指令token和已生成文本token的拼接，输出每个图像token的保留概率（二分类），通过Gumbel-Softmax实现可微采样。
- 训练损失包含三项：C-PMI损失、注意力得分损失（利用LVLM某一层注意力得分衡量token重要性）、保留比例正则项（控制保留比例 \(\gamma\)，LLaVA默认80%）。
- 双优化过程的交替执行：每步先利用校准分布采样文本token，再通过净化器筛选图像token。

### 2.3 算法流程简述

1. 初始化：给定图像 \(v\)、指令 \(x\)，LVLM生成视觉token和文本token序列。
2. 每步解码 \(t\)：
   - **内层子问题（文本）**：根据式(5)计算校准分布，采样下一个token \(y_t\)。
   - **外层子问题（视觉）**：使用训练好的视觉token净化器，结合当前文本上下文，过滤冗余视觉token，得到精炼后的 \(v^*\)。
3. 重复直到生成结束，同时利用特征引导机制（VTI）增强稳定性。

## 3. 实验设计

### 3.1 数据集与基准（Benchmarks）

| 基准名称 | 用途 | 数据来源 |
|---------|------|---------|
| CHAIR | 物体幻觉评估（句子/实例级别） | MSCOCO验证集500张图像 |
| GPT-4o辅助评估 | 细粒度幻觉（属性、关系、位置等） | Visual Genome 200张图像 |
| POPE | 物体幻觉问答（随机/流行/对抗三种负采样） | MSCOCO |
| MME | 多模态综合能力（感知/认知10个子任务） | 官方MME数据集 |
| MMBench | 感知与推理（20个任务维度，≥3000道选择题） | 官方MMBench数据集 |

### 3.2 对比方法

- **标准策略**：Sampling（Top-p=1）、Greedy。
- **解码缓解方法**：VCD、ICD、VTI、SID、HALC、OPERA、VASparse（部分基于beam search）。
- **模型**：LLaVA-1.5 (7B)、InstructBLIP (7B)、Shikra (7B)、LLaVA-Next (8B)，共4个代表性LVLM。

### 3.3 训练与实现细节

- 视觉token净化器训练数据：ShareGPT4V（来自MSCOCO图像-问答对），LLaVA系列用2000样本，InstructBLIP和Shikra用4000样本。
- 超参数：\(\alpha=100\)，\(\beta=500\)，\(\lambda=0.5\)，保留比例 \(\gamma\)（LLaVA:80%，InstructBLIP:90%），净化起始层 \(i=2\)（LLaVA等）或 \(i=4\)（InstructBLIP）。
- 输出最大新token数：512。

## 4. 资源与算力

- **论文未明确说明**具体的GPU型号、数量或总训练时长。
- 仅提及视觉token净化器非常轻量（参数不到LVLM的1%），且训练仅需少量数据（2000-4000样本）和5个epoch，学习率 \(1\times 10^{-6}\)，推测算力需求不高。
- 推理阶段，由于净化器轻量和视觉token减少，整体计算开销基本不变（甚至略有降低，见表5、6）。

## 5. 实验数量与充分性

- **实验众多**：共在5个基准上、4个模型上进行，对比了9种SOTA方法，覆盖物体幻觉、细粒度幻觉、通用多模态能力、推理速度。
- **消融实验充分**：
  - 验证两种核心组件（校准分布采样 vs. 视觉token净化）各自贡献（图6）。
  - 超参数分析：\(\lambda\)（图5b）、\(\alpha\)（图5a）、保留比例 \(\gamma\)（图7）。
  - 学习变体 vs. 手工变体（表7）：验证学习净化器的高效性。
- **公平性**：作者指出beam search方法（HALC、OPERA、VASparse）因保留更宽候选路径可能不公平，但CMI-VLD仍优于它们。所有方法采用相同的评估设置。
- **结论**：实验充分、客观，结果具有统计显著性。

## 6. 主要结论与发现

- CMI-VLD **显著降低LVLM幻觉**，在所有基准上一致优于竞争方法，且在多个LVLM上鲁棒。
  - CHAIR: LLaVA-1.5上CS从52.2降至30.2，CI从15.8降至9.3。
  - POPE: LLaVA-Next上对抗F1从77.16%提升至82.14%。
  - MME/MMBench: 整体能力也有提升（例如MME从1465提升至1481）。
- 通过最大化C-PMI，动态加强了视觉与文本的互依性，有效抑制了语言先验的主导。
- 推理效率保持，几乎无额外开销（图4）。

## 7. 优点

- **理论严谨**：从信息论角度出发，提出C-PMI优化框架，将现有对比解码方法视为特例。
- **双层优化视角新颖**：联合优化文本和视觉token，突破单纯调整文本分布的限制。
- **高效实用**：视觉token净化器轻量，推理时通过减少冗余token反而提升速度；与特征引导（VTI）兼容。
- **实验全面**：覆盖多种幻觉类型、通用能力、效率，在多模型上验证泛化能力。
- **开源代码**：提供可复现代码。

## 8. 不足与局限

- **额外训练开销**：视觉净化器需要额外训练（尽管数据量小，但仍需调参）。
- **保留比例敏感**：\(\gamma\) 需要针对不同模型手动调整，且论文采用固定比例，而最优比例可能随解码步骤变化。
- **长文本场景效率下降**：当生成非常长的文本时，视觉token减少带来的效率优势可能不显著。
- **通用能力提升有限**：在MME/MMBench上虽有提升但幅度不大，表明CMI-VLD主要针对幻觉，对整体多模态能力提升有限。
- **未消歧义**：实验未涉及多轮对话或更复杂的视觉推理任务。
- **安全性分析缺失**：未讨论该方法可能被逆向用于生成误导性内容。

（完）
