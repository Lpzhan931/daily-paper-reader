---
title: Tandem Transformers for Inference Efficient LLMs
title_zh: 用于高效推理的Tandem变压器
authors: "Aishwarya P S, Pranav Ajit Nair, Yashas Samaga B L, Toby James Boyd, Sanjiv Kumar, Prateek Jain, Praneeth Netrapalli"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=TN3fi7dwPo"
tags: ["query:llm"]
score: 8.0
evidence: 结合小自回归模型和大块模型的新型Transformer架构
tldr: 针对自回归LLM推理慢的问题，本文提出Tandem变压器架构：一个小的自回归模型通过注意力机制从大模型的丰富表征中获益，从而提升预测精度；同时大模型以块模式并行处理多个token。该设计无需额外训练，在多个数据集上实现了显著的加速比，且生成质量损失极小。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-tn3fi7dwpo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1330, \"height\": 619, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tn3fi7dwpo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1685, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tn3fi7dwpo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1640, \"height\": 436, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 856, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1424, \"height\": 447, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1704, \"height\": 410, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1300, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 854, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 854, \"height\": 172, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1422, \"height\": 447, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1040, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1777, \"height\": 360, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1430, \"height\": 475, \"label\": \"Table\"}]"
motivation: 投机解码依赖小模型但精度不足，并行解码未能充分利用大模型表征。
method: 设计双模型架构，小模型可访问大模型中间表示来提高预测准确率，大模型批量处理多个token。
result: 实验证明该方法在保持生成质量的同时，推理速度显著提升。
conclusion: 通过跨模型注意力增强，可有效结合小型和大型模型优势加速推理。
---

## Abstract
The autoregressive nature of conventional large language models (LLMs) inherently limits inference speed, as tokens are generated sequentially. While speculative (Leviathan et al., 2023) and parallel (Stern et al., 2018) decoding techniques attempt to mitigate this, they face limitations: either relying on less accurate smaller models for generation or failing to fully leverage the base LLM's representations. We introduce a novel architecture, Tandem transformers, to address these issues. This architecture uniquely combines (1) a small autoregressive model and (2) a large model operating in block mode (processing multiple tokens simultaneously). The small model's predictive accuracy is substantially enhanced by granting it attention to the large model's richer representations. On the PaLM2 pretraining dataset, a tandem of PaLM2-Bison and PaLM2-Gecko demonstrates a 3.3% improvement in next-token prediction accuracy over a standalone PaLM2-Gecko, offering a 1.16x speedup compared to a PaLM2-Otter model with comparable downstream performance. We further incorporate the Tandem model within the speculative decoding (SPEED) framework where the large model validates tokens from the small model. This ensures that the tandem of PaLM2-Bison and PaLM2-Gecko achieves substantial speedup (around 1.14x faster than using vanilla PaLM2-Gecko in SPEED) while maintaining identical downstream task accuracy.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **问题**：传统自回归大语言模型（LLM）推理速度受限于逐token生成，无法充分利用GPU/TPU的矩阵-矩阵乘法优势，导致高延迟。
- **背景**：现有尝试包括投机解码（依赖小模型但精度不足）和并行解码（未能充分利用大模型表示）。研究人员质疑：自然语言理解（NLU）和自然语言生成（NLG）是否必须由同一大型模型承担？能否将容量更多分配给NLU，而用较小模型完成生成？
- **意义**：提出一种新架构，旨在分离NLU与NLG容量，在不显著损失质量的前提下大幅提升推理效率。

### 2. 论文提出的方法论：核心思想、关键技术细节、算法流程（文字说明）
- **核心思想**：Tandem Transformers由一个大模型（ML，如PaLM2-Bison）和一个小模型（MS，如PaLM2-Gecko）组成。ML以块模式（非自回归）同时处理多个token，生成丰富表示；MS以自回归方式逐个生成token，但可**通过注意力机制访问ML对先前所有token的表示**（经投影层对齐维度），从而获得远超单独小模型的预测能力。
- **关键技术细节**：
  - **训练**：使用预训练好的ML（冻结）和MS，仅训练MS和投影层（线性层）。训练时按块长度γ=2划分序列，MS生成一个块内的γ个token时，K/V来自ML对之前所有块的表示（经投影），当前块内自己的token用自身自回归计算。
  - **损失**：可选交叉熵（CE）或加上蒸馏损失（Tandem-Distil，以ML logits为目标）。
  - **推理**：ML先处理查询/前缀，MS生成第一个响应块（γ个token），然后ML处理该块并更新表示，MS继续下一个块。可让ML额外预测下一个块的第一token（免费token）以进一步提升效率。
  - **Tandem + SPEED**：利用Tandem中的MS作为草稿模型生成块，ML验证。MS因能访问ML表示，草稿接受率更高，从而比标准SPEED更快。
  - **自适应块长度**：训练一个轻量MLP路由器，根据MS的熵、top-k概率等特征预测当前token是否会被ML接受，动态决定继续生成还是验证，进一步加速。
- **公式/算法流程**：文中给出了标准Transformer公式（1）和Tandem Transformer公式（2），说明了MS如何通过投影层从ML的某层表示获得输入，并在自回归生成时混合使用ML和自身的K/V。

### 3. 实验设计：数据集、场景、Benchmark与对比方法
- **数据集**：
  - 预训练评估：PaLM2预训练数据上的准确率和交叉熵。
  - 下游任务：SuperGLUE、TyDiQA（含金passage）、生成任务集（Gen-tasks，含SQuADv2、Natural Questions、TriviaQA、WebQuestions、Lambada）、MBPP、WMT22（x→en翻译）。
  - 延迟评测：CNN/DailyMail、Reddit Posts摘要、1 Billion Word Benchmark (LM1B) 的1000条提示。
- **场景**：单样本（1-shot）评估；延迟评估包括num-samples=1和4。
- **对比方法**：
  - 基线模型：PaLM2-Gecko、PaLM2-Gecko-Distil（蒸馏版）、PaLM2-Otter、PaLM2-Bison。
  - SPEED框架内对比：PaLM2-Gecko-Distil作为草稿 vs Tandem-Distil作为草稿。
  - 此外测试了更小的二次模型（PaLM2-XXXS）以及自适应块长度变体。
- **评价指标**：准确率、交叉熵、下游任务得分、延迟加速比（相对于PaLM2-Bison或基线）。

### 4. 资源与算力
- 文中未明确说明训练使用的GPU/TPU具体型号、数量及训练时长。
- 所有延迟评估在**TPUv5e**上执行（Cloud TPU v5e）。
- 训练和评估基于PaLM2预训练模型，使用Google的内部基础设施（推测为TPU v4或v5），但细节未公开。

### 5. 实验数量与充分性
- **实验数量**：较为充分，包含以下主要实验组：
  - 预训练指标对比（表1）：Tandem-CE、Tandem-Distil vs 基线的准确率和CE，以及相对准确率和TV距离。
  - SPEED框架延迟对比（表2、表7）：多数据集（Reddit、CNN/DM、LM1B）、多种num-samples（1和4）、多种γ配置。
  - 独立模型评估（表3、表9、表10）：五个下游任务（生成任务、MBPP、WMT22、TyDiQA、SuperGLUE）及每个子任务详细得分。
  - 自适应块长度效果（表5、表8、表6）：额外加速比及运行次数分析。
  - 更小二次模型实验（表4）：使用PaLM2-XXXS作为MS的对比。
- **公平性与客观性**：对比了多种基线，包括无蒸馏、蒸馏、不同大小模型；SPEED框架下保证了输出质量与主模型一致，公平比较加速比；消融了自适应块长度；结果清晰显示Tandem在多项指标上优于蒸馏版小模型，且几乎持平于更大模型（Otter），加速显著。
- **不足**：未在更多模型家族（如LLaMA、GPT）上验证，仅基于PaLM2系列；缺乏对训练效率（重新训练时间）的报道。

### 6. 论文的主要结论与发现
- Tandem架构显著提升小模型预测精度：Tandem-Distil在预训练数据上准确率58.61%（vs Gecko 55.06%），相对TV距离从0.391降至0.141。
- 作为独立模型，Tandem（Bison+Gecko）性能接近PaLM2-Otter，而推理速度**快1.16倍**（Speedup vs PaLM2-Otter 2.75× vs 2.36×，相对于Bison）。
- 在SPEED框架中，Tandem-Distil草稿接受率比蒸馏Gecko高约11.24%，带来**1.11~1.17倍相对加速**（相对基准SPEED）。
- 自适应块长度进一步优化：在LM1B上，Tandem+SPEED+AG相较于Tandem+SPEED有1.093倍加速（相对于Bison达2.853倍）。
- 更小的二次模型（PaLM2-XXXS）配合Tandem可获得更大加速（如LM1B上Tandem-Distil加速3.04× vs 2.445×）。
- 证明了**NLU与NLG可有效解耦**，大模型容量集中于较早序列，小模型负责生成，同时维持高质量。

### 7. 优点：方法或实验设计上的亮点
- **创新性架构**：首次将“大模型块模式+小模型自回归+跨模型注意力”结合，实现容量分离。
- **即插即用**：可基于预训练模型直接初始化，仅需微调小模型和投影层，训练成本低。
- **兼容性**：可无缝融入SPEED框架，且支持自适应块长度等改进。
- **实验全面**：涵盖多个数据集、多种设置（不同num-samples、batch-size、γ）、对比多种基线（包括蒸馏、不同大小模型）；既验证独立模型也验证SPEED场景。
- **结果清晰**：在保证质量（SPEED下输出与主模型相同）的同时大幅加速，实际部署价值高。

### 8. 不足与局限
- **模型泛化性**：仅基于PaLM2系列，未在其他主流LLM（如GPT、LLaMA）上验证，可能受架构影响。
- **训练细节不透明**：未披露具体训练步数、学习率、计算资源成本，难以复现。
- **块长度选择**：训练时固定γ=2，推理时可用其他γ，但未讨论γ对最佳性能的影响规律。
- **自适应块长度方法**：路由器MLP仅基于少量特征，且阈值τ固定为0.8，可能不是最优；未考虑多样本/大batch场景下的挑战。
- **应用限制**：需要双模型部署，增加了内存占用（尽管小模型很小）；仅针对推理加速，未考虑训练效率。

（完）
