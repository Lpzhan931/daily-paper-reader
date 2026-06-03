---
title: "Learning to Keep a Promise: Scaling Language Model Decoding Parallelism with Learned Asynchronous Decoding"
title_zh: 学习信守承诺：通过异步解码扩展语言模型解码并行性
authors: "Tian Jin, Ellie Y Cheng, Zachary Ankner, Nikunj Saunshi, Blake M Elias, Amir Yazdanbakhsh, Jonathan Ragan-Kelley, Suvinay Subramanian, Michael Carbin"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=ZfX43ZZRZR"
tags: ["query:llm"]
score: 7.0
evidence: 异步解码实现LLM并行生成
tldr: 传统自回归解码顺序生成，难以并行。本文提出学习型异步解码，通过识别输出中的语义独立部分，利用自定义标注语言Pasta-Lang让模型在推理时发起异步解码，配合解释器实现并行生成，从而提升LLM解码效率。方法无需预设结构，通用性强。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-zfx43zzrzr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1665, \"height\": 470, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zfx43zzrzr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1749, \"height\": 682, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zfx43zzrzr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1663, \"height\": 216, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zfx43zzrzr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1717, \"height\": 159, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zfx43zzrzr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 781, \"height\": 583, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zfx43zzrzr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1776, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zfx43zzrzr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 662, \"height\": 591, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zfx43zzrzr/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 596, \"height\": 601, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zfx43zzrzr/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1746, \"height\": 682, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zfx43zzrzr/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1754, \"height\": 215, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zfx43zzrzr/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 486, \"height\": 490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zfx43zzrzr/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 547, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zfx43zzrzr/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 547, \"height\": 489, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zfx43zzrzr/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 547, \"height\": 490, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-zfx43zzrzr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1760, \"height\": 192, \"label\": \"Table\"}]"
motivation: 自回归LLM解码顺序进行速度慢，现有并行方法需预定义结构，缺乏通用性。
method: 构建Pasta-Lang标注语言让模型指示异步点，并开发解释器动态执行异步解码。
result: 实验表明异步解码有效减少解码时间，且在多种任务上保持输出质量。
conclusion: 语义独立性的自动利用为LLM并行解码提供了新范式。
---

## Abstract
Decoding with autoregressive language models traditionally occurs sequentially, generating one token after another. Recent attempts to introduce parallelism require a pre-determined structure in the generated content to implement parallel generation, such as by pattern-matching on bullet points. In this work, we present a new technique to automate parallel generation by dynamically exploiting the semantic independence of generation outputs to implement asynchronous decoding. We introduce an annotation language Pasta-Lang for language models to initiate asynchronous decoding at inference time. We also develop an accompanying Pasta-Lang interpreter that performs on-the-fly asynchronous decoding, effectively implementing parallel generation and speeding up inference. We present an instruction-finetuning dataset with Pasta-Lang-annotated responses for teaching LLMs to annotate semantic independence with Pasta-Lang as well as the methodology for creating the dataset. Our evaluation shows using the interpreter with a Pasta-Lang-equipped model achieves significant speedup while maintaining the same generation quality.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义

- **研究动机**：自回归语言模型（LLM）解码本质上是顺序的，每生成一个 token 都需要依赖之前所有 token。这导致解码延迟高、硬件利用率低（推理时 MFU 通常低于 20%）。现有并行解码方法（如 Skeleton-of-Thought、APAR）依赖手工语法启发式（如正则表达式匹配列表、段落），这些方法缺乏可扩展性和鲁棒性，容易因格式偏差而失效。
- **整体目标**：提出一种**学习型异步解码系统 PASTA**，训练 LLM 自主识别输出中的语义独立块，并通过自定义标注语言 Pasta-Lang 在推理时动态发起并行解码，从而在不牺牲质量的前提下显著加速解码。

## 2. 方法论

- **核心思想**：教 LLM 在其响应中嵌入 Pasta-Lang 标签（如 `<promise/>`、`<sync/>`），这些标签标记出可以异步生成的语义独立片段。一个解释器在推理时实时解析这些标签，并行启动多个解码线程，并在同步点合并结果，实现非连续 token 块的并行生成。
- **关键技术细节**：
  - **Pasta-Lang 标注语言**：使用 XML 风格的标签。`<promise topic="..." tokens="..."/>` 标记一个将要异步生成的块（占位符）；`<async>...</async>` 包裹实际异步生成的内容；`<sync/>` 表示需要等待所有异步线程完成的地方。
  - **解释器设计**：维护一个交错的 KV-cache 布局，避免重复复制前缀，通过注意力掩码防止线程间提前干扰。同步时将异步生成的内容插入到对应 `<promise/>` 位置。
  - **两阶段微调流程**：
    1. **第一阶段（SFT）**：使用 Gemini 1.5 Flash 为 SlimOrca 数据集的响应自动添加 Pasta-Lang 标注（提供 7 个人工标注示例和语言描述），得到 Pasta-SFT 数据集；在此数据集上微调基础模型（Gemma 7B），得到 Pasta-SFT 模型。微调时修改注意力掩码（阻止 `<promise/>` 后的 token 看到 `<async>` 内容）、训练模型预测 `<async>` 块长度以分配位置 ID、设置预测目标跳过 `<promise/>` 占位符。
    2. **第二阶段（偏好优化）**：从 Pasta-SFT 模型采样 N=10 个带标注响应，使用得分 = speedup + λ × quality 进行排名（speedup 为理论加速比，quality 为基于 Gemini 1.5 Pro 的置信加权胜率）。用 BoNBoN 算法（结合 SFT 损失和 IPO 损失）优化模型，λ 控制质量-速度权衡。可多次迭代。
- **公式/算法**（文字说明）：
  - 理论加速比 = 基线响应总 token 数 / 异步响应中最长顺序解码序列长度。
  - 偏好优化损失函数：\(L = -\alpha \log p_\theta(y^+|x) + (1-\alpha)\left( \log\frac{p_\theta(y^+|x)}{p_\theta(y^-|x)} - \log\frac{p_{\theta_{\text{init}}}(y^+|x)}{p_{\theta_{\text{init}}}(y^-|x)} - \frac{1}{\beta} \right)^2\)，其中 \(y^+\), \(y^-\) 分别为最佳和最差响应。

## 3. 实验设计

- **数据集/场景**：使用 AlpacaEval 基准（805 个指令遵循提示）评估质量（长度控制胜率，LLM-as-judge：GPT-4 作为评估者）。训练数据为 SlimOrca 子集（约 87K 条）。
- **Benchmark**：将 PASTA 模型与以下方法对比：
  - Baseline-SFT（在去标注的 Pasta-SFT 数据集上微调的 Gemma 7B 顺序解码模型）
  - APAR（基于正则的异步解码，同样在 Pasta-SFT 上按官方方法实现）
  - SoT（Skeleton-of-Thought，提示式方法，应用于 Baseline-SFT 和更强模型 Gemma-IT）
- **对比指标**：实际加速比（墙钟时间比）、理论加速比、理论并行度、GPT-4 LC 胜率。

## 4. 资源与算力

- 论文中未明确说明训练使用的 GPU 数量、总训练时长、总能耗等详细信息。
- 仅提及推理评估在 **H100 GPU** 上进行，使用 batch size 1，greedy decoding，并通过 torch.compile 优化（最大自动调优模式），每个请求解码两次以排除编译开销。
- 基础模型为 **Gemma 7B**，训练超参数：batch size 8，学习率线性衰减从 1e-5 到 0，训练 4 个 epoch。硬件和训练资源配置未进一步展开。

## 5. 实验数量与充分性

- **主要实验**：在 AlpacaEval 上评估了多个 PASTA 变体（不同 λ 值 1,2,4,8,∞）、基线、APAR、SoT，共约 10 组以上结果。每组均计算加速比和胜率。
- **消融实验**：
  - 偏好优化迭代次数的影响（初始、10% R1、100% R1、10% R2、60% R2）。
  - 位置嵌入策略比较（固定长度、预测长度 Pred-1X/Pred-10X、Oracle 基线）。
  - 不同效率指标（理论加速比、算术/调和平均、理论并行度）对优化效果的影响。
- **充分性评价**：
  - 实验设计较为全面，覆盖了核心变量（质量-速度权衡、训练迭代、位置编码、评分函数）。
  - 对比方法也覆盖了现有代表性异步解码方法。
  - 不足：仅在一个基准（AlpacaEval）上评估，缺乏跨多样任务（如推理、代码、翻译等）或更大规模模型（如 70B+）的验证。评估使用 GPT-4 作为裁判，可能存在对特定风格/长度的偏差；但引入了长度控制（LC）胜率以减轻偏差。

## 6. 主要结论与发现

- PASTA 在质量-速度权衡上帕累托优于所有现有异步解码方法（APAR、SoT）。
- 几何平均实际加速比范围为 **1.21× 到 1.93×**，对应胜率变化为 **+2.2% 到 -7.1%**（相对于基线）。
- 质量权重 λ 可有效控制权衡：λ 越小（如 1）获得更高加速但质量下降更多；λ=∞ 获得质量提升（52.3% 胜率）并仍有 1.21× 加速。
- 偏好优化迭代次数持续提升帕累托前沿，未在 2 轮后出现饱和，显示出扩展性。
- 预测长度（Pred-10X）的位置嵌入策略接近 Oracle 水平，是最佳实践。
- 理论加速比与实际加速比接近，说明解释器实现高效。
- SoT 在基础模型上无加速（需强指令跟随能力），在更强模型上加速但质量下降更大。

## 7. 优点

- **学习型方法替代手工规则**：自动化识别语义独立性，不依赖特定语法结构，灵活性和可扩展性更强。
- **两阶段微调可扩展**：从少量人工演示启动，通过 LLM 自动标注和偏好优化不断改进，能直接利用更多训练计算提升效果。
- **高效解释器设计**：交错的 KV-cache 布局避免了前缀复制和内存浪费，降低了异步解码开销。
- **帕累托控制**：通过 λ 和迭代次数可灵活权衡速度与质量，实用性强。
- **直接优化延迟目标**：将加速比纳入偏好优化目标，思路新颖，优于单纯优化质量或并行度。

## 8. 不足与局限

- **依赖外部 LLM 生成标注**：初始 Pasta-SFT 数据集由 Gemini 1.5 Flash 自动标注，可能引入噪音和标注不一致；该模型的知识和偏见可能影响最终模型行为。
- **单一基准评估**：仅在 AlpacaEval（指令跟随场景）上评估，未在推理、翻译、代码生成等任务上验证，泛化能力未充分证明。
- **模型规模有限**：仅使用 Gemma 7B 进行实验，更大规模模型（如 70B+）上的效果未知；异步解码的并行效率可能随模型增大而改善。
- **仅 greedy 解码**：只评估了贪婪解码，未探讨采样或束搜索下的加速与质量平衡。
- **位置 ID 估计误差**：训练预测长度无法完美匹配真实长度，可能引入位置偏移误差，影响模型生成稳定性（尤其长序列）。
- **应用限制**：PASTA 要求模型在微调时学习标注，无法直接应用于未经过训练的预训练模型；异步解码的实时协调增加了推理系统复杂性。

（完）
