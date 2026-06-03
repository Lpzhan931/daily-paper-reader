---
title: Attention-Level Speculation
title_zh: 注意力级投机并行
authors: "Jack Cai, Ammar Vora, Randolph Zhang, Mark O'Connor, Mark C. Jeffrey"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=4OszSYdsgO"
tags: ["query:llm"]
score: 9.0
evidence: 注意力级投机并行加速LLM推理
tldr: 针对大模型长上下文推理中注意力计算成为瓶颈的问题，本文提出注意力级投机并行（ALSpec），通过预测自注意力输出在独立设备上提前执行后续操作，实现注意力与非注意力计算重叠。在128K上下文长度下，注意力延迟降低5倍，端到端解码延迟降低1.65倍，且不损失质量。该方法为LLM推理加速提供了新的并行范式。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1769, \"height\": 552, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1526, \"height\": 294, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 706, \"height\": 567, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 867, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 837, \"height\": 1079, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 601, \"height\": 495, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1591, \"height\": 223, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1697, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 838, \"height\": 533, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1426, \"height\": 804, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1420, \"height\": 804, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1733, \"height\": 734, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1746, \"height\": 752, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1722, \"height\": 904, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1602, \"height\": 561, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 774, \"height\": 269, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1600, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 904, \"height\": 767, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 905, \"height\": 938, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 750, \"height\": 800, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 743, \"height\": 719, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 924, \"height\": 1011, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 900, \"height\": 954, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 750, \"height\": 582, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 742, \"height\": 555, \"label\": \"Table\"}]"
motivation: 传统张量/数据并行在扩展设备时收益递减，注意力计算成为瓶颈。
method: 预测自注意力输出，在额外设备上并行执行后续非注意力操作。
result: 128K上下文下注意力延迟降低5倍，端到端解码延迟降低1.65倍。
conclusion: ALSpec通过投机执行重叠计算，有效加速长上下文LLM推理。
---

## Abstract
As Large Language Models (LLMs) grow in size and context length, efficient inference strategies are essential to maintain low-latency token generation. Unfortunately, conventional tensor and data parallelism face diminishing returns when scaling across multiple devices. We propose a novel form—attention-level speculative parallelism (ALSpec)—that predicts self-attention outputs to execute subsequent operations early on separate devices. Our approach overlaps attention and non-attention computations, reducing the attention latency overhead at 128K context length by up to 5x and improving end-to-end decode latency by up to 1.65x, all without sacrificing quality. We establish the fundamental pillars for speculative execution and provide an execution paradigm that simplifies implementation. We show that existing attention-approximation methods perform well on simple information retrieval tasks, but they fail in advanced reasoning and math. Combined with speculative execution, we can approximate up to 90% of self-attention without harming model correctness. Demonstrated on Tenstorrent's NPU devices, we scale up LLM inference beyond current techniques, paving the way for faster inference in transformer models.

---

## 论文详细总结（自动生成）

### 1. 核心问题与整体含义（研究动机和背景）
- **问题**：大语言模型（LLM）推理时，随着模型规模和上下文长度增长，传统张量并行（TP）和数据并行（DP）在扩展设备数量时收益递减；自注意力（self-attention）计算在长上下文中成为主要瓶颈。
- **动机**：能否通过重叠注意力计算与其他操作（如前馈网络）来隐藏注意力延迟，同时不牺牲模型正确性？
- **含义**：提出一种新型投机并行范式——注意力级投机并行（ALSpec），通过预测注意力输出来提前执行后续操作，实现计算重叠，加速推理。

### 2. 方法论
- **核心思想**：在每个Transformer层中，用廉价近似（如注意力汇合，attention sink）计算推测注意力输出 ˜A_i，同时并计算精确注意力输出 A_i；验证两者差异（L2距离）是否小于阈值 λ·∥A_i∥。若通过，则接受推测结果并跳过后续注意力计算，实现注意力与前馈网络重叠。
- **关键技术细节**：
  - **预测器**：使用“注意力汇合”（仅关注前几个和最近滑动窗口的KV tokens），窗口大小S远小于上下文长度。
  - **验证机制**：基于Lipschitz连续性推导出最终输出偏差的上界，采用L2距离阈值 λ 决定是否接受推测。
  - **投机Flash Decode核**：修改Flash Decode的读取模式，先读取第一个和最后一个chunk，立即发送部分结果给接收设备，同时继续计算完整注意力，实现零额外开销的推测。
  - **静态图动态并发（SGDC）与优先级门控**：保持静态操作图，每个设备维护优先级向量，通过运行时条件跳过或执行操作，实现设备间的并发控制。
- **算法流程**（文字描述）：对每层，先执行前置操作，然后用注意力汇合计算推测输出，启动新线程执行后置操作；同时计算精确注意力；验证通过则提交推测结果并杀死精确线程，否则丢弃推测结果并重新执行后置操作。

### 3. 实验设计
- **数据集/场景**：涵盖问答（IFEval）、推理（GPQA COT、SWDE）、数学（GSM8K COT、MATH COT）、长上下文（HotpotQA、RepoBench-P）、MMLU PRO下的多个学科（经济学、商业、心理学等）。
- **基准测试**：使用LM Evaluation Harness框架，默认提示词和少样本模板。
- **对比方法**：
  - 基线：完整模型（无近似）。
  - 静态注意力汇合（所有层固定使用）。
  - 静态层选择：仅在高接受率的层固定使用注意力汇合。
  - 动态ALSpec（本文方法）。
- **指标**：相对准确率（与基线比较）、推测命中率（接受推测的层比例）。

### 4. 资源与算力
- 论文明确提到：性能实验在 **8个Tenstorrent N150芯片** 上执行，使用TT-Metalium框架进行核实现和测量。
- 正确性评估在 **NVIDIA A100或H100 GPU** 上运行模型（模拟推测行为）。
- 未提供具体训练时长或GPU卡数/小时数；仅给出推理阶段延迟测量。

### 5. 实验数量与充分性
- **实验组数**：在 Llama 3.1 8B 模型上对 λ ∈ {0.05,0.10,0.15,0.20,0.25} 共5个阈值，在10个以上数据集/任务上进行评估（包含QA、推理、数学、长上下文等），并给出每个λ下的准确率和推测命中率。
- **消融实验**：
  - 对比静态注意汇合、静态层选择 vs. 动态ALSpec。
  - 在 Llama 3.1 70B 模型上选取4个任务验证可扩展性。
  - “干草堆中找针”实验（16K上下文，10个随机密钥）展示不同λ下的找针成功数和接受层数。
- **充分性与公平性**：实验覆盖了多种任务类型，使用公开基准和规范化框架（LM Eval Harness），对比方法合理。但未在更广泛的模型家族（如Mistral、Qwen）或更长的上下文（>128K）上测试，存在一定局限。

### 6. 主要结论与发现
- ALSpec 在 λ=0.10 时，可在所有任务上实现与基线相当的准确率，且推测命中率普遍超过50%（如IFEval达90%，GPQA COT为65.7%，GSM8K COT为78.9%）。
- 在128K上下文长度下，注意力延迟降低最多5倍，端到端解码延迟降低最多1.65倍（87.5%命中率时）。
- 静态注意力汇合在高级推理和数学任务上明显下降，而动态ALSpec通过运行时验证避免了质量损失。
- 在Llama 70B（80层）上获得类似结果，说明方法可扩展到更深模型。

### 7. 优点
- **创新性**：首次提出注意力级投机并行，将投机执行从解码级扩展到层内注意力，可与张量并行、数据并行结合。
- **实用性**：无需修改模型架构或重新训练，仅需修改注意力核和运行时调度。
- **低开销**：投机Flash Decode核几乎零额外计算，SGDC机制使主机代码保持静态，实现简单。
- **可解释性**：提供Lipschitz连续性理论推导的误差界，验证机制有理论支持。
- **实验全面**：覆盖多种任务类型，并在两种规模模型上验证。

### 8. 不足与局限
- **实验局限性**：仅在Tenstorrent NPU上实测性能；GPU端仅做模拟估计（基于H100），未提供实际CUDA实现。
- **设备数量有限**：最大扩展到8设备，未测试更大规模集群（如16/32节点）下的效果。
- **任务覆盖**：未包含更极端的长上下文任务（如256K+）或更多模型架构（如混合专家模型）。
- **理论假设**：高概率误差界依赖于“推测误差无偏”假设，论文未严格证明该假设普遍成立。
- **超参数敏感**：λ阈值需人工设定，不同任务最优值可能不同，虽然λ=0.10广泛适用，但缺乏自适应调整方法。
- **应用限制**：当非注意力操作（如FF）大幅慢于注意力时，重叠收益较小；需要设备数量足够使推测路径与精确路径并行。

（完）
