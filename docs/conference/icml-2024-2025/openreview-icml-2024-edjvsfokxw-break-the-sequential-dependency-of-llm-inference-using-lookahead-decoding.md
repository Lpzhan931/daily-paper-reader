---
title: Break the Sequential Dependency of LLM Inference Using Lookahead Decoding
title_zh: 使用Lookahead解码打破大语言模型推理的顺序依赖
authors: "Yichao Fu, Peter Bailis, Ion Stoica, Hao Zhang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=eDjvSFOkXw"
tags: ["query:llm"]
score: 9.0
evidence: 并行解码加速大语言模型推理
tldr: 本文提出Lookahead解码，一种无需辅助模型或数据存储的精确并行解码算法。通过将每步log(FLOPs)转换为更少的总解码步数，显著降低了LLM推理延迟，并兼容FlashAttention等高效注意力机制，是一种通用的推理加速方法。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-edjvsfokxw/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 854, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-edjvsfokxw/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 855, \"height\": 649, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-edjvsfokxw/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 402, \"height\": 248, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-edjvsfokxw/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 849, \"height\": 445, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-edjvsfokxw/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1780, \"height\": 259, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-edjvsfokxw/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 847, \"height\": 900, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-edjvsfokxw/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 844, \"height\": 898, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-edjvsfokxw/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 866, \"height\": 231, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-edjvsfokxw/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 884, \"height\": 285, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-edjvsfokxw/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 835, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-edjvsfokxw/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 697, \"height\": 349, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-edjvsfokxw/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 851, \"height\": 230, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-edjvsfokxw/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1574, \"height\": 600, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-edjvsfokxw/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 723, \"height\": 116, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-edjvsfokxw/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1385, \"height\": 207, \"label\": \"Table\"}]"
motivation: 自回归解码受内存带宽限制，造成高延迟和并行计算资源浪费。
method: 通过并行预测多个未来token，每步生成多个候选，再通过验证保证精确性，从而减少解码步数。
result: 在多个模型和任务上，实现了2-3倍的加速，且不损失生成质量。
conclusion: Lookahead解码是一种高效、兼容现有系统的LLM推理加速方案。
---

## Abstract
Autoregressive decoding of large language models (LLMs) is memory bandwidth bounded, resulting in high latency and significant wastes of the parallel processing power of modern accelerators. Existing methods for accelerating LLM decoding often require a draft model (e.g., speculative decoding), which is nontrivial to obtain and unable to generalize. In this paper, we introduce Lookahead decoding, an exact, parallel decoding algorithm that accelerates LLM decoding without needing auxiliary models or data stores. It allows trading per-step log(FLOPs) to reduce the number of total decoding steps, is more parallelizable on single or multiple modern accelerators, and is compatible with concurrent memory-efficient attention (e.g., FlashAttention). Our implementation of Lookahead decoding can speed up autoregressive decoding by up to 1.8x on MT-bench and 4x with strong scaling on multiple GPUs in code completion tasks. Our code is avialable at https://github.com/hao-ai-lab/LookaheadDecoding

---

## 论文详细总结（自动生成）

# 论文总结：Break the Sequential Dependency of LLM Inference Using Lookahead Decoding

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）的自回归解码过程受内存带宽限制，导致高延迟，且严重浪费现代加速器（如GPU）的并行计算能力。
- **现有方法局限**：已有的加速方法（如投机解码）通常需要额外的草稿模型（draft model），而获取高质量的草稿模型十分困难，且训练好的模型不能跨模型和数据集泛化。
- **本文含义**：提出一种无需辅助模型或数据存储的精确并行解码算法——Lookahead Decoding，通过将每步少量额外计算（对数FLOPs）换取更少的解码步数，从而显著降低延迟，并兼容FlashAttention等高效注意力机制，是一种通用、可扩展的加速方案。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：将自回归解码等价地视为求解非线性系统的雅可比迭代过程（Jacobi decoding），该过程每步可并行生成多个token（但可能位置错误）。Lookahead Decoding利用这一特性，通过维护一个固定大小的2D窗口（序列轴×时间轴）来捕获历史轨迹，并从中生成多个不重叠的n-gram，再通过验证分支保证输出分布不变。
- **关键技术细节**：
  - **Lookahead分支**：参数W（前瞻未来位置数）和N（回溯历史步数）。每步基于前N-1步的轨迹，并行预测W个位置上的token，生成多个n-gram并缓存到n-gram池中。
  - **验证分支**：从n-gram池中搜索以当前最后输出token开头的候选n-gram（最多G个，通常G=W），并行的使用LLM验证这些n-gram，接受其中最长的前缀。支持贪心采样和随机采样，且不改变输出分布（有理论证明）。
  - **注意力掩码**：设计特定的注意力掩码（如图2(b)），使得lookahead和验证分支可以在同一前向步中合并计算，充分利用并行能力。
  - **集成FlashAttention**：将Lookahead Decoding的注意力模式硬编码到FlashAttention中，获得约20%额外加速。
  - **Lookahead并行（Lookahead Parallelism）**：将互不依赖的分支分配给不同GPU，每个GPU保持完整模型副本，避免通信，实现强扩展。
- **算法流程**（算法1）：每步先通过lookahead分支生成W个token，然后从n-gram池中取出最多G个候选，调用验证函数（贪心/采样）接受前缀，将新生成的n-gram加入池，并滑动窗口更新。

## 3. 实验设计

- **使用数据集/场景**：
  - **聊天/指令**：MT-Bench（多轮对话，独特token多）
  - **数学推理**：GSM8K（前1000题）
  - **代码生成**：HumanEval（补全和填充），MBPP（指令式代码生成），ClassEval（类级代码生成）
  - **摘要**：CNN/Daily Mail、XSum（用于采样质量验证）
- **基准测试**：主要对比HuggingFace贪心搜索实现，以及集成FlashAttention后的更强基线。还对比了投机解码（草稿模型为TinyLLaMA 1B、Vicuna 7B）、Medusa、并行雅可比解码（PJ、PGJ）等。
- **评估指标**：吞吐量（tokens/s）、压缩比（S，自回归步数/Lookahead步数）、Rouge分数（采样）、MT-Bench分数。

## 4. 资源与算力

- **GPU型号**：NVIDIA A100 80GB（S1）和NVIDIA A100 40GB（DGX节点，8卡，NVLink，S2）。
- **模型与部署**：
  - 7B、13B、34B模型在单卡A100上部署，70B模型用2张A100通过Pipeline Parallelism（Accelerate）。
  - 分布式对比中，使用了Tensor Parallelism（DeepSpeed）和Pipeline Parallelism（Accelerate）作为基线。
- **训练/推理细节**：所有模型均使用FP16精度，batch size为1（除非特别说明）。没有提及训练时长，所有实验均为推理加速评估。

## 5. 实验数量与充分性

- **实验数量**：
  - 端到端性能（图5）：在7B/13B/70B模型上测试了4种数据集（MT-Bench、GSM8K、MBPP、HumanEval补全/填充），共约12个实验点。
  - FlashAttention与多GPU扩展（图6、7）：在7B和13B模型上，对MT-Bench、HumanEval、ClassEval三种数据集，分别测试了1、4、8 GPU下与TP、PP、LP的对比，包含FlashAttention启用与否，每个配置均有数据，实验点丰富。
  - 生成质量（表2）：在两个摘要数据集上，对比了贪心和采样下的Rouge分数和速度。
  - 消融实验（表3）：在MT-Bench上对比了不同W、N、G组合以及是否使用Prompt作为参考，共9个配置。
  - 与多种方法对比（附录表6）：在Vicuna-7B/13B上与SD、Medusa、PJ、PGJ等对比。
- **充分性与公平性**：实验覆盖了多种模型尺寸、任务类型、硬件配置，且对比了主流加速方法（投机解码、Medusa等）。消融实验系统分析了关键参数影响。生成质量验证了贪心和采样下与原始输出的一致性。总体实验设计较充分，对比公平。

## 6. 主要结论与发现

- Lookahead Decoding在无草稿模型条件下，实现1.4x-2.3x加速（单GPU），结合FlashAttention和Lookahead Parallelism后可达1.8x（MT-Bench 7B）至4x（ClassEval 8 GPU）。
- 算法具有可扩展的缩放律：随着每步FLOPs（≈log(W+G)*(N-1)）指数增加，解码步数线性减少，即trade-off次步计算与总步数。
- 在多GPU强扩展场景下，Lookahead Parallelism显著优于Tensor Parallelism和Pipeline Parallelism（后者反而导致减速），几乎无通信开销。
- 生成质量保持不变：贪心采样下输出与原始模型在数值误差内一致；随机采样下Rouge分数几乎相同。
- 与投机解码相比，无需训练草稿模型，泛化性强；与雅可比解码相比，显著提升有效token生成率。

## 7. 优点

- **方法创新性**：无需草稿模型或数据存储，直接从LLM自身前几步轨迹中生成n-gram并验证，是“免费午餐”。
- **理论支撑**：给出了缩放律分析，并与投机解码统一建模，证明了lookahead可线性减少解码步数。
- **兼容性**：可无缝集成FlashAttention等高效注意力机制，且支持多种采样方式，不改变输出分布。
- **分布式友好**：提出的Lookahead Parallelism利用多GPU并行性，通信几乎为零，实现强扩展。
- **实验全面**：覆盖多种模型（7B~70B）、多种任务（聊天、数学、代码、摘要）、多种配置（单GPU、多GPU、FlashAttention），消融充分。

## 8. 不足与局限

- **计算开销**：Lookahead Decoding需要额外FLOPs（每步约增加几十倍），在计算受限环境（如高并发batch服务、低端GPU）下可能造成减速。实验也显示在RTX 3090上加速比低于A100。
- **参数调优**：W、N、G需要根据模型和任务手动调节，无自动化策略（论文给出了推荐值，但未讨论自适应方案）。
- **通用性验证不足**：主要基于LLaMA-2和CodeLlama系列，未在其他架构（如GPT、Mistral）上验证，且batch size固定为1，实际服务场景可能有不同表现。
- **长序列性能未充分考察**：实验最大序列长度约2048，更长序列下注意力计算成本可能影响加速效果。
- **采样验证的理论证明**虽已给出，但附录中证明较长，实际实现复杂，且需要存储n-gram候选，内存消耗可能随生成过程增长。
- **与投机解码的对比**：文中对比的投机解码草稿模型（TinyLLaMA 1B、Vicuna 7B）并非最优选择，可能未完全公平反映投机解码的上限。

（完）
