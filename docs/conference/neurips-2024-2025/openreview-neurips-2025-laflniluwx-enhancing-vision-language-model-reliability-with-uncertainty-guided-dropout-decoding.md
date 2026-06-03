---
title: Enhancing Vision-Language Model Reliability with Uncertainty-Guided Dropout Decoding
title_zh: 通过不确定性引导的Dropout解码增强视觉语言模型可靠性
authors: "Yixiong Fang, Ziran Yang, Zhaorun Chen, Zhuokai Zhao, Jiawei Zhou"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=LAflniLUwx"
tags: ["query:vlm-spec"]
score: 6.0
evidence: 视觉语言模型的推理时解码方法，提高可靠性
tldr: 本文针对大视觉语言模型（LVLM）中幻觉问题，提出Dropout Decoding推理时方法。通过将视觉token投影到文本空间并分解不确定性，聚焦认知不确定性，然后根据不确定性指导的dropout策略在解码时选择性遮蔽不可靠的视觉token。实验表明，该方法显著减少幻觉，提升输出可靠性，同时不损害任务性能。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-laflniluwx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 571, \"height\": 626, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-laflniluwx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1213, \"height\": 549, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-laflniluwx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1224, \"height\": 256, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-laflniluwx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 374, \"height\": 219, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-laflniluwx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 373, \"height\": 285, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-laflniluwx/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 372, \"height\": 284, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-laflniluwx/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 372, \"height\": 282, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-laflniluwx/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 258, \"height\": 401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-laflniluwx/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 373, \"height\": 257, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-laflniluwx/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 373, \"height\": 282, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-laflniluwx/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 415, \"height\": 283, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-laflniluwx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1268, \"height\": 580, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-laflniluwx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 589, \"height\": 131, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-laflniluwx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1015, \"height\": 157, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-laflniluwx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1033, \"height\": 180, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-laflniluwx/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1017, \"height\": 321, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-laflniluwx/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 859, \"height\": 344, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-laflniluwx/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 760, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-laflniluwx/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 686, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-laflniluwx/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 991, \"height\": 152, \"label\": \"Table\"}]"
motivation: LVLM常误解视觉输入导致幻觉，需要推理时干预。
method: 量化视觉token的认知不确定性，并在解码时依据不确定性进行dropout遮蔽。
result: 有效减少幻觉，提升VLM输出可靠性。
conclusion: 不确定性引导的解码策略可增强VLM的视觉语义对齐。
---

## Abstract
Large vision-language models (LVLMs) excel at multimodal tasks but are prone to misinterpreting visual inputs, often resulting in hallucinations and unreliable outputs. We present Dropout Decoding, a novel inference-time approach that quantifies the uncertainty of visual tokens and selectively masks uncertain tokens to improve decoding. Our method measures the uncertainty of each visual token by projecting it onto the text space and decomposing it into aleatoric and epistemic components. Specifically, we focus on epistemic uncertainty, which captures perception-related errors more effectively. Inspired by dropout regularization, we introduce uncertainty-guided token dropout, which applies the dropout principle to input visual tokens instead of model parameters, and during inference rather than training. By aggregating predictions from an ensemble of masked decoding contexts, we can robustly mitigate errors arising from visual token misinterpretations. Evaluations on benchmarks including CHAIR, THRONE, and MMBench demonstrate that Dropout Decoding significantly reduces object hallucinations (OH) and enhances both reliability and quality of LVLM outputs across diverse visual contexts.

---

## 论文详细总结（自动生成）

# 论文详细总结：《Enhancing Vision-Language Model Reliability with Uncertainty-Guided Dropout Decoding》

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：大型视觉语言模型（LVLMs，如 LLaVA、InstructBLIP）在多模态任务中表现出色，但在视觉输入理解上容易出错，常常产生**对象幻觉（Object Hallucination）**，即生成的内容包含图像中不存在或描述错误的物体，导致输出不可靠。
- **背景**：现有缓解幻觉的方法大多依赖训练阶段（如微调、额外监督信号），成本高、可扩展性差；推理阶段方法多基于注意力或 logits 的启发式设计，缺乏理论指导，且增加推理开销。
- **整体含义**：本文提出一种**推理时（inference-time）的不确定性引导的解码方法**，无需修改模型参数或额外训练，通过量化视觉 token 的认知不确定性并选择性丢弃高不确定性的 token，从而提升 LVLM 输出的可靠性与事实性。

## 2. 方法论：核心思想、关键技术细节与算法流程

### 2.1 核心思想
- **灵感来源**：传统 Dropout 正则化应用于模型参数，本文将其逆向应用于**输入视觉 token**，且仅在**推理阶段**进行。
- **关键概念**：将每个视觉 token 通过 LLM 解码器投影到文本词汇空间，得到“视觉-文本分布”，进而分解不确定性为**偶然不确定性（aleatoric）**和**认知不确定性（epistemic）**。其中认知不确定性更能捕捉模型感知错误，作为丢弃 token 的依据。

### 2.2 关键技术细节

1. **文本空间投影**：
   - 对第 \(i\) 个视觉 token \(x^v_i\)，计算其经过 LLM 解码器顶层后的隐藏表示 \(h^v_i\)，再通过 softmax 映射到词汇表得到投影分布 \(q^{\text{proj}}_i = \text{softmax}(W_V h^v_i)\)。
   - 对所有视觉 token 的投影分布取平均得到平均分布 \(\bar{q}^{\text{proj}}\)。

2. **不确定性量化**：
   - **认知不确定性**（用于指导 dropout）：  
     \[
     U_{\text{epi}}(i) = D_{\text{KL}}(q^{\text{proj}}_i \parallel \bar{q}^{\text{proj}})
     \]
   - 高认知不确定性表示该 token 的信息与整体视觉内容显著不同，容易导致幻觉。

3. **不确定性引导的 Token Dropout**：
   - 构造 dropout 概率：  
     \[
     P^{(k)}_{\text{dropout}}(x^v_i) = \gamma^{(k)} \frac{U_{\text{epi}}(i) - U_{\min}}{U_{\max} - U_{\min}} + \delta^{(k)}
     \]
   - 采样 \(K\) 个独立的二进制掩码 \(M^{(k)}\)，每个掩码独立决定是否丢弃该 visual token（丢弃概率即 \(P^{(k)}_{\text{dropout}}\)）。
   - **可选步骤：初步前向传递**：先生成一个初步预测 token \(y^{\text{init}}_j\)，保留与该 token 相关的视觉 token（即 \(y^{\text{init}}_j\) 出现在该 token 投影分布 top-k 中），这些 token 不被 dropout。

4. **集成解码**：
   - 对 \(K\) 个 dropout 掩码分别进行前向传播，得到 \(K\) 个候选预测 \(y_j^{(k)}\)。
   - 通过**多数投票**确定最终 token \(y_j\)；平局时选择丢弃 token 最少的候选（保留信息最多）。

### 2.3 算法流程（文字描述）
```
1. 输入：视觉 token x_v，文本 token x_t，掩码数量 K，生成长度 L
2. 解码前：计算每个视觉 token 的投影分布 q^proj_i，平均分布 q_bar，认知不确定性 U_epi(i)
3. 对于每个生成位置 j=1..L：
   a. (可选) 生成初步 token y_init_j，得到相关 token 集合 S_j
   b. 根据 U_epi(i) 计算 K 个 dropout 概率，采样 K 个掩码 M^(k)（保留 S_j 中的 token）
   c. 并行前向传播得到 K 个候选 y_j^(k)
   d. 多数投票选出最终 y_j
4. 返回生成序列 y
```

## 3. 实验设计

### 3.1 数据集与基准（Benchmark）
- **CHAIR**：MSCOCO 图像描述任务，评估对象幻觉（CHAIR_S 句子级、CHAIR_I 对象级）。
- **THRONE**：更全面的幻觉评估，包括精度（P_all）、召回（R_all）、F1_all、F0.5_all 等。
- **MMBench**：综合多模态能力评估（选择题）。
- **数据来源**：MSCOCO 2014 测试集，随机采样 500 张图片，3 种随机种子报告均值和标准差。

### 3.2 对比方法
- **原始模型**（Greedy 解码）
- **Beam Search**
- **OPERA**（基于注意力惩罚的推理修正）
- **VCD**（视觉对比解码：对比原始与扭曲图像）
- **本文方法**：Dropout Decoding（含/不含初步前向传递）

### 3.3 基础 LVLMs
- LLaVA-1.5（576 个视觉 token）
- InstructBLIP（32 个视觉 token，高信息密度）
- LLaVA-NEXT（约 2000 个视觉 token）

### 3.4 主要结果
- **Table 1（CHAIR+THRONE）**：在所有三个模型上，Dropout Decoding 在 CHAIR_S、CHAIR_I、F1_all、F0.5_all、P_all 等指标上**一致优于或持平**所有基线，尤其 InstructBLIP 上 CHAIR_I 下降 16%。
- **Table 2（MMBench）**：在 LLaVA-1.5 上 Dropout Decoding 取得最高分 74.01，优于 VCD（72.35）和 OPERA（73.86）；LLaVA-NEXT 上略低于 greedy（74.31 vs 74.57）但优于其他。

## 4. 资源与算力（文中说明）

- **硬件**：4×A800 80GB GPU（用于 vLLM 效率测试）；也使用 Huggingface Transformers（单 GPU 内存 14.02 GB → 15.31 GB）。
- **训练**：方法无需训练，仅推理。
- **推理开销**：
  - 不含初步前向传递时：吞吐量从 37.0 tok/s 降至 34.1 tok/s（-7.8%）；wall-time 增加 8.9%。
  - 含初步前向传递时：吞吐量下降 45.7%，wall-time 增加 84.4%。
  - 不确定性计算成本：LLaVA-1.5 下每个输入仅 73.30 ms。
- **GPU 内存**：利用 vLLM 和 KV 缓存后，额外内存开销极小（几乎不变）。

## 5. 实验数量与充分性

- **主实验**：在 3 个模型 × 3 个数据集（CHAIR、THRONE、MMBench）上系统评估，每个结果包含 3 个随机种子的标准差。
- **消融实验**：
  1. 并行掩码数量 \(K\) 的影响（图 3，发现 \(K=3\) 最优）。
  2. 初步前向传递的必要性（Table 1 中对比含/不含，含时效果更好但耗时）。
  3. 不确定性引导 vs 随机掩码（Table 4，随机掩码在 CHAIR 上看似更好但 BLEU 下降、THRONE 出错，且导致重复生成）。
  4. 高置信度 token 掩码（Table 5，替换为丢弃低不确定性 token，结果接近 greedy，说明丢弃高不确定性 token 才有效）。
  5. 计算效率分析（Table 3）。
- **充分性评价**：实验设计较为全面，覆盖了幻觉评估的两个主流基准（CHAIR、THRONE）和一个通用能力基准（MMBench），并在三个代表性 LVLM 上验证。消融研究针对核心设计选择进行了验证。但缺少在更多细分任务（如 VQA、视觉推理）上的评估，且仅使用单一图像描述提示（“Describe the image.”），未测试多种指令。

## 6. 主要结论与发现

- **Dropout Decoding 显著减少对象幻觉**，在 CHAIR 和 THRONE 指标上超越现有推理时方法（VCD、OPERA），且不牺牲召回率（保留相关物体）。
- **认知不确定性是有效的指引信号**，高不确定性 token 往往对应图像中信息丰富但易误导的区域，丢弃它们可减少幻觉。
- **集成多个 dropout 掩码的多数投票**能稳定生成，避免单一掩码的随机性导致质量下降。
- **初步前向传递**可以进一步提升性能，但会带来较大计算开销；对于视觉 token 较多的模型（LLaVA），可省略而不显著降低效果；对于 token 少的模型（InstructBLIP）则建议保留。

## 7. 优点

1. **无需额外训练或模型修改**：纯粹推理时方法，适用于任何预训练 LVLM。
2. **理论动机明确**：基于不确定性分解（偶然/认知），从信息论角度解释视觉 token 的不确定性，而非纯启发式设计。
3. **集成策略稳健**：通过多掩码投票，既降低了幻觉风险，又保持了生成稳定。
4. **灵活可控**：通过超参数 \(\gamma, \delta\) 可调节丢弃强度，适应不同模型和任务。
5. **兼顾效率与性能**：在可接受的计算开销内取得显著提升，尤其在无初步前向传递时，仅增加约 7% 的推理时间。

## 8. 不足与局限

1. **计算开销**：含初步前向传递时增加近一倍时间（+84.4%），虽可选但影响实用性。
2. **依赖投影质量**：认知不确定性估计基于视觉 token 到文本空间的投影（logit lens），该投影可能受视觉-文本对齐质量影响，在弱对齐模型上效果可能打折。
3. **任务覆盖有限**：只评估了图像描述（CHAIR、THRONE）和选择题（MMBench），未在 VQA、视觉对话、开放生成等更多任务上验证泛化性。
4. **超参数敏感**：\(K, \gamma, \delta\) 等需调参，虽提供默认值，但迁移到新模型或任务时可能需重新调整。
5. **潜在偏差风险**：以多数投票决定 token，可能导致少数珍贵但正确的信息被淹没（若多数掩码错误），不过实验结果显示 F1 和召回率并未下降。
6. **未测试更大规模模型**：实验中仅用 7B-13B 级别模型，未在 70B+ 量级的 LVLM 上验证可扩展性。

（完）
