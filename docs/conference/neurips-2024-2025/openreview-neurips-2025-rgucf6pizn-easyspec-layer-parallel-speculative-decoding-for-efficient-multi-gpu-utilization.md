---
title: "EasySpec: Layer-Parallel Speculative Decoding for Efficient Multi-GPU Utilization"
title_zh: EasySpec：面向高效多GPU利用的层并行投机解码
authors: "Yize Wu, KE GAO, Ling Li, Yanjun Wu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=RGUcF6pIZN"
tags: ["query:llm"]
score: 8.0
evidence: 面向多GPU大语言模型推理的层并行投机解码策略
tldr: 针对多GPU系统中草稿模型与基座模型最佳张量并行大小不同导致GPU空闲的问题，提出EasySpec，采用层并行投机策略，将不同层分配到不同GPU上并行执行，显著提升GPU利用率和推理加速比。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-rgucf6pizn/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1430, \"height\": 1393, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rgucf6pizn/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1113, \"height\": 683, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rgucf6pizn/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 727, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rgucf6pizn/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1382, \"height\": 550, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rgucf6pizn/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1140, \"height\": 588, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-rgucf6pizn/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1260, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rgucf6pizn/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1396, \"height\": 1702, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rgucf6pizn/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1387, \"height\": 429, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rgucf6pizn/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 819, \"height\": 226, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rgucf6pizn/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1440, \"height\": 877, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rgucf6pizn/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1251, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rgucf6pizn/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 701, \"height\": 418, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rgucf6pizn/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 861, \"height\": 539, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rgucf6pizn/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1412, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rgucf6pizn/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1443, \"height\": 2039, \"label\": \"Table\"}]"
motivation: 多GPU投机解码中，草稿模型和基座模型的最优张量并行大小不同，导致GPU空闲和低效。
method: 打破传统的层顺序执行，提出层并行投机策略，将层分布到多个GPU上并行计算。
result: 有效减少GPU空闲时间，在多种LLM上实现显著加速。
conclusion: 层并行策略可有效提升多GPU投机解码的资源利用率和推理速度。
---

## Abstract
Speculative decoding is an effective and lossless method for Large Language Model (LLM) inference acceleration. It employs a smaller model to generate a draft token sequence, which is then verified by the original base model. In multi-GPU systems, inference latency can be further reduced through tensor parallelism (TP), while the optimal TP size of the draft model is typically smaller than that of the base model, leading to GPU idling during the drafting stage. We observe that such inefficiency stems from the sequential execution of layers, which is seemingly natural but actually unnecessary. Therefore, we propose EasySpec, a layer-parallel speculation strategy that optimizes the efficiency of multi-GPU utilization. EasySpec breaks the inter-layer data dependencies in the draft model, enabling multiple layers to run simultaneously across multiple devices as ``fuzzy'' speculation. After each drafting-and-verification iteration, the draft model’s key-value cache is calibrated in a single forward pass, preventing long-term fuzzy-error accumulation at minimal additional latency. EasySpec is a training-free and plug-in method. We evaluated EasySpec on several mainstream open-source LLMs, using smaller versions of models from the same series as drafters. The results demonstrate that EasySpec can achieve a peak speedup of 4.17x compared to vanilla decoding, while preserving the original distributions of the base LLMs. Specifically, the drafting stage can be accelerated by up to 1.62x with a maximum speculation accuracy drop of only 7\%. The code is available at https://github.com/Yize-Wu/EasySpec.

---

## 论文详细总结（自动生成）

# EasySpec: 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **背景**：投机解码（Speculative Decoding）利用小型草稿模型生成候选token序列，再由大型基座模型并行验证，从而加速LLM推理。在多GPU系统中，张量并行（Tensor Parallelism, TP）可进一步降低推理延迟。
- **问题**：草稿模型参数量小，最优TP大小通常小于基座模型（例如草稿模型单GPU最快，基座模型需8GPU），导致草稿阶段大部分GPU空闲，多GPU资源利用率低下。
- **根本原因**：传统层顺序执行（sequential layer execution）看似自然，但草稿结果无需精确（仅用于候选，最终输出由验证保证），因此严格按序是不必要的。利用近似推理可打破层间数据依赖，从而实现层并行。

## 2. 论文提出的方法论

### 核心思想
- **模糊投机（Fuzzy Speculation）**：打破层间数据依赖性，使多个注意力层在不同GPU上并行执行。关键观察：相邻层的隐藏状态余弦相似度极高（接近1），因此可用初始隐藏状态作为所有并行注意力层的输入进行近似计算。
- **奖励校准（Bonus Calibration）**：每次投试验证迭代后，将已接受的token序列与奖励token拼接，以常规顺序前向传播一次，更新KV cache为精确值，防止模糊误差长期累积。

### 关键技术细节
- **层并行执行**：对于N个连续注意力层，将第一个隐藏状态作为所有层的输入，各层并行计算Attention输出，然后顺序计算MLP层（MLP层并行化误差过大，故保持顺序）。层并行策略：排除首尾层，剩余层以N为一组并行，最后不足一组时也尽量并行。
- **树注意力（Tree Attention）**：采用2D注意力掩码生成多个候选token序列（树结构），提高接受率。
- **算法流程**：
    1. 模糊投机：并行计算N个注意力层，顺序计算MLP层。
    2. 验证：基座模型验证候选序列，接受部分token。
    3. 奖励校准：将接受的token序列与奖励token拼接，以常规顺序前向传播草稿模型，更新KV cache。
- **公式/算法**（文字描述）：算法2展示了层并行模糊投机的伪代码，通过将多个注意力层输入设置为同一初始状态，消除依赖。

## 3. 实验设计

### 使用的模型与数据集
- **基座模型**：Llama-3-70B-Instruct, Qwen2-72B-Instruct, Llama-3.3-70B-Instruct, Qwen2-Math-72B-Instruct, Qwen2.5-Coder-32B-Instruct。
- **草稿模型**：同系列较小版本（0.5B/1.5B/3B/7B/8B等）。
- **数据集/任务**：
    - 语言理解：MMLU
    - 代码生成：HumanEval
    - 数学推理：MATH
    - 指令遵循：IFEval
    - 多语言推理：MGSM
    - 综合评测：Spec-Bench（包含MT、TL、SUM、QA、MR、RAG等子任务）
- **对比方法**：
    - 基线：TP（张量并行）、+SD（投机解码+TP）、+tree（树注意力）
    - 对比方法：EAGLE-2（训练单层草稿模型的方法）
- **指标**：token吞吐量（tokens/s）、每100 tokens运行时间（drafting/verification）、总加速比、接受率α。

## 4. 资源与算力

- **GPU配置**：8×A100 GPU（文中明确说明）。
- **TP设置**：草稿模型TP=1，基座模型TP=8（均为最优）。
- **训练时长**：无需训练（training-free），未报告训练时长；推理实验时间未量化。

## 5. 实验数量与充分性

- **实验数量**：
    - 主实验：Llama-3-70B和Qwen2-72B在6个数据集上，温度0和0.8，共12个设置。
    - 任务特定模型实验：Qwen2.5-Coder-32B在HumanEval，Qwen2-Math-72B在MATH。
    - 其他模型组合：如Qwen2-72B with 1.5B/0.5B drafter，Llama-3-70B with 3B/1B drafter等，多个数据集。
    - 与EAGLE-2对比：在Spec-Bench上6个子任务，报告吞吐量均值和方差。
    - 消融实验：树宽度（1/4/8/12）、层并行大小（1~5）、是否启用奖励校准，共约4×5×2=40种配置。
    - 近似精度分析：余弦相似度（表4）。
- **充分性**：实验覆盖主流模型和多种任务，对比方法合理（包括同领域最强方法EAGLE-2），消融实验全面，置信度较高。但仅在8×A100一种硬件配置上测试，可能缺乏跨平台验证。

## 6. 论文的主要结论与发现

- **加速效果**：EasySpec在Llama-3-70B和Qwen2-72B上相比vanilla解码最高达4.17x加速（Qwen2-72B, HE, temp=0.8），草稿阶段加速最高1.62x，接受率下降不超过7%。
- **与EAGLE-2对比**：在Spec-Bench上，使用同系列1B草稿模型的EasySpec吞吐量更高、方差更小（稳定性更强），表明同系列小模型天然具有良好对齐，且无需额外训练。
- **奖励校准有效性**：消融实验显示奖励校准显著提升接受率，尤其在低树宽度或高并行度时收益明显。
- **近似精度**：层并行后隐藏状态余弦相似度保持在0.8以上，查询和键相似度接近1，保证近似精度。

## 7. 优点

- **训练-free**：无需额外训练或微调，即插即用，易于集成到现有系统。
- **创新性**：首次针对多GPU环境下层顺序执行的低效问题提出层并行策略，利用近似推理突破依赖。
- **高效性**：模糊投机+奖励校准的组合在几乎不额外增加延迟的前提下有效消除误差累积。
- **鲁棒性**：在多个模型、多个数据集上稳定加速，且与EAGLE-2相比具有更好的泛化和稳定性。
- **可解释性**：从余弦相似度角度提供了近似精度的理论分析和实验验证。

## 8. 不足与局限

- **硬件依赖性**：实验仅在8×A100单一配置上进行，加速比可能随不同硬件（如GPU互联带宽、计算能力）变化。
- **MLP层不可并行**：MLP层必须顺序执行，否则误差过大，限制了并行度进一步提升。
- **层并行大小需要调参**：最优层并行大小因模型和任务而异，需手动选择（但文中给出了通用推荐值4）。
- **草稿模型选择限制**：最佳效果依赖于同系列较小版本模型，若不存在此类模型则需额外训练（但EasySpec不要求训练，可选用其他小模型）。
- **未涉及批处理场景**：实验均为单batch推理，未扩展到服务批处理（但这是未来工作方向）。

（完）
