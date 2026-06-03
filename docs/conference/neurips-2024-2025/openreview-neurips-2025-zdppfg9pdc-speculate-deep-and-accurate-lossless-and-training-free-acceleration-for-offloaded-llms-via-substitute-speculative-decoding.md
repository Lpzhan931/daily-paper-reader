---
title: "Speculate Deep and Accurate: Lossless and Training-Free Acceleration for Offloaded LLMs via Substitute Speculative Decoding"
title_zh: 深入且准确的投机：通过替代投机解码实现卸载大语言模型的无损免训练加速
authors: "Pei-Shuo Wang, Jian-Jia Chen, Chun-Che Yang, Chi-Chih Chang, Ning-Chi Huang, Mohamed S. Abdelfattah, Kai-Chiang Wu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=ZDpPfg9pDc"
tags: ["query:llm"]
score: 8.0
evidence: 面向内存交换大语言模型推理加速的投机解码方法
tldr: 针对模型卸载到CPU/GPU导致推理慢的问题，提出替代投机解码方法，利用草稿模型生成候选token，减少目标模型的前向传播次数，从而降低参数交换开销，实现无损加速，实验表明在有限GPU内存下加速显著。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-zdppfg9pdc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1363, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zdppfg9pdc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1439, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zdppfg9pdc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1443, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zdppfg9pdc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1432, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zdppfg9pdc/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1244, \"height\": 635, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zdppfg9pdc/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1243, \"height\": 679, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-zdppfg9pdc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1452, \"height\": 1056, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zdppfg9pdc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 732, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zdppfg9pdc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 503, \"height\": 286, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zdppfg9pdc/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 630, \"height\": 272, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zdppfg9pdc/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 772, \"height\": 197, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zdppfg9pdc/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1449, \"height\": 470, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zdppfg9pdc/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 569, \"height\": 155, \"label\": \"Table\"}]"
motivation: 大模型参数卸载到内存受限GPU时，权重传输延迟高，推理速度慢。
method: 利用草稿模型生成多个推测token，由目标模型并行验证，减少跨设备数据传输。
result: 在多种LLM和卸载场景下实现2-4倍加速，且不降低模型质量。
conclusion: 投机解码可有效缓解参数卸载的带宽瓶颈，实现高效的LLM边缘部署。
---

## Abstract
The immense model sizes of large language models (LLMs) challenge deployment on memory-limited consumer GPUs.
    Although model compression and parameter offloading are common strategies to address memory limitations, compression can degrade quality, and offloading maintains quality but suffers from slow inference.
    Speculative decoding presents a promising avenue to accelerate parameter offloading, utilizing a fast draft model to propose multiple draft tokens, which are then verified by the target LLM in parallel with a single forward pass. This method reduces the time-consuming data transfers in forward passes that involve offloaded weight transfers.
    Existing methods often rely on pretrained weights of the same family, but require additional training to align with custom-trained models. Moreover, approaches that involve draft model training usually yield only modest speedups. This limitation arises from insufficient alignment with the target model, preventing higher token acceptance lengths.
    To address these challenges and achieve greater speedups, we propose SubSpec, a plug-and-play method to accelerate parameter offloading that is lossless and training-free. SubSpec constructs a highly aligned draft model by generating low-bit quantized substitute layers from offloaded target LLM portions. Additionally, our method shares the remaining GPU-resident layers and the KV-Cache, further reducing memory overhead and enhance alignment.
    SubSpec achieves a high average acceptance length, delivering 9.1$\times$ speedup for Qwen2.5 7B on MT-Bench (8GB VRAM limit) and an average of 12.5$\times$ speedup for Qwen2.5 32B on popular generation benchmarks (24GB VRAM limit).

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）参数量巨大，难以在内存受限的消费级GPU（如8GB–24GB）上完全加载。常见的解决方案包括模型压缩（量化）和参数卸载（offloading）。压缩会降低模型质量（有损），而卸载虽能保持无损，但频繁的CPU–GPU数据传输导致推理速度极慢（仅1–2 tokens/s），无法满足实时交互需求。
- **研究背景**：投机解码（Speculative Decoding, SD）通过一个更小的草稿模型快速生成多个候选token，再由目标LLM并行验证，从而减少对目标模型的前向传播次数，降低参数卸载场景下的数据传输开销。然而，现有SD方法要么依赖同系列预训练小模型（需额外训练对齐），要么通过训练草稿模型但提升效果有限，主要原因是草稿模型与目标模型的对齐程度不足，导致平均接受长度（τ）较低（通常<7）。
- **整体含义**：本文旨在提出一种**无损、免训练、即插即用**的投机解码方法，在参数卸载场景下显著加速LLM推理，使大规模高质量模型能在消费级硬件上高效运行。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过构建与目标模型高度对齐的草稿模型，并利用深度树形投机解码，最大化平均接受长度，从而最小化昂贵的参数传输次数。草稿模型由两部分组成：
  1. **量化替代层**：对目标模型中被卸载到CPU的层，采用低比特（4-bit）量化后的轻量级替代层，完全驻留于GPU。
  2. **共享组件**：保留在GPU上的目标模型层（共享权重）以及共享的KV-Cache，既减少内存占用，又提升对齐精度。
- **关键技术细节**：
  - **草稿模型构建**：使用数据无关的快速量化方法（如HQQ）生成4-bit替代层；共享GPU层和KV-Cache，使草稿模型与目标模型在共享部分完全一致，极大提升对齐度。
  - **深度上下文感知动态草稿树**：采用树形投机解码，通过迭代生成多个分支token，构建深度为D的树（实验中D可达48）。在每次迭代中，所有叶子节点输入草稿模型，选出累计概率最高的top-k token作为新叶子节点。
  - **草稿概率锐化**：针对贪心解码场景，对草稿模型输出应用低温（如0.2）进行概率锐化，抑制“假阳性”路径（即低概率分支因后续高概率token累积而错误胜出），从而提升平均接受长度。
  - **异步数据传输**：在目标模型验证阶段，将GPU计算与下一层参数的CPU预取重叠，隐藏数据传输延迟。
  - **分块预填充**：对长输入序列进行分块处理（如每块256 tokens），逐步构建KV-Cache，避免峰值内存过高导致GPU驻留层数减少。
- **公式（文字说明）**：论文推导了投机解码的加速比公式：加速比 = τ / (D·t_draft/t_target + γ)，其中τ为平均接受长度，D为草稿深度，t_draft和t_target分别为草稿和目标模型单次前向传播延迟，γ为验证的相对成本。在卸载场景下，t_target因数据传输而很大，因此提升τ是关键，允许使用较大但对齐更好的草稿模型。

## 3. 实验设计：数据集、基准、对比方法

- **数据集/场景**：使用5个代表性生成任务：
  - MT-Bench（多轮对话）
  - HumanEval（代码生成）
  - GSM8K（数学推理）
  - Alpaca（指令跟随）
  - CNN/Daily Mail（摘要生成）
- **基准（benchmark）**：在贪心解码（温度=0）和随机解码（温度=0.6）两种设置下进行评测，主要指标为吞吐量（tokens/s）和平均接受长度τ。
- **对比方法**：
  - 基线：无投机解码的原始卸载推理（None）。
  - EAGLE-2（使用预训练草稿头，需训练对齐）。
  - 同系列小模型作为草稿模型（如Qwen2.5 1.5B、Llama3.2 1B等）。
  - SpecExec（附录中对比，但未在主表列出）。
- **硬件**：单张RTX 4090 GPU（24GB显存），通过程序限制为8GB、12GB、24GB以模拟不同消费级设备。
- **参数设置**：替代层量化位宽4-bit，分组大小64；草稿树top-k=6，草稿深度D通过网格搜索确定（SubSpec为48，预训练小模型为32）；所有方法使用相同的动态草稿树算法，且均采用torch.compile优化。

## 4. 资源与算力

- 论文明确说明实验使用单张RTX 4090 GPU、Intel i7-13700K CPU、PCIe 4.0 x16总线、128GB DDR5 RAM。
- **训练成本**：SubSpec无需训练，量化过程仅需数分钟（对7B–70B模型），属于免训练方法。
- **未明确说明**：未给出每次实验的运行总时长，但提及基线（无SD）因速度慢仅用5个样本，而SD方法各用20个样本。

## 5. 实验数量与充分性

- **实验数量**：主实验覆盖5个数据集 × 3种目标模型大小（7B/8B、14B、32B） × 2种解码温度 × 多个对比方法，共约60+组实验结果。此外，包含以下补充实验：
  - 消融实验（表2）：逐步添加共享KV-Cache、概率锐化、异步传输，观察贡献。
  - 推理模型评测（附录表6）：在DeepSeek-R1蒸馏模型和QWQ上测试，覆盖AIME、MATH、GPQA、LiveCodeBench。
  - 量化目标模型场景（附录表7）：对比fp16与int8目标模型下的性能。
  - SpecExec参数扫描（附录表4）。
  - 草稿温度影响分析（附录表5）。
- **充分性**：实验设计较为充分，覆盖多种模型族（Qwen、Llama）、多种任务、两种解码策略。消融实验验证了各组件贡献。但**缺乏与更多近期方法（如Sequoia、Medusa、Dovetail）的直接对比**，仅在附录中提及SpecExec并进行了单独测试（但未在统一设置下对比）。另外，**未提供误差线或统计显著性检验**（论文明确说明“too time-consuming”），可能影响结果可靠性。

## 6. 论文的主要结论与发现

- SubSpec在所有测试场景下均取得最高吞吐量：对Qwen2.5 7B在8GB限制下平均约25 tokens/s（10×加速），对32B模型在24GB限制下平均约6.5 tokens/s（12.5×加速）。
- 平均接受长度τ稳定在28–30之间，远高于其他草稿模型（通常τ<14），证实了高度对齐的草稿模型能有效降低验证次数。
- 在随机解码（温度0.6）下，加速比下降约60%，但仍保持5.8×–7.8×加速，证明了方法的鲁棒性。
- 消融实验显示，共享KV-Cache、概率锐化、异步传输分别贡献7%–13%的吞吐量提升，联合使用可达9.15×加速。
- SubSpec在推理模型（DeepSeek-R1、QWQ）上同样取得10×以上加速。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：首次提出利用低比特量化替代层与共享GPU驻留组件构建高度对齐的草稿模型，实现**无损、免训练、即插即用**的投机解码加速，解决了现有方法需微调或对齐效果差的问题。
- **理论分析**：通过公式推导和实证验证，明确了卸载场景下对齐度和草稿深度比草稿速度更重要，为方法设计提供了理论基础。
- **工程优化**：异步数据传输、分块预填充、概率锐化等技术均针对实际硬件瓶颈设计，实验证明有效。
- **实验全面性**：覆盖多种模型大小、任务类型、解码策略，并包含推理模型和量化目标模型的扩展实验。
- **高效性**：量化过程仅需数分钟，且无需训练数据，易于部署。

## 8. 不足与局限

- **最小GPU内存要求较高**：SubSpec要求草稿模型完全驻留GPU，包括量化替代层。对于7B目标模型，约需7.1GB显存，导致可保留的GPU目标模型层数少于某些替代方法（如EAGLE-2），但最终吞吐仍更高。
- **量化粒度未深入探索**：仅测试了4-bit量化，未尝试2-bit或3-bit以进一步降低显存占用，可能错失更优的显存–对齐权衡。
- **架构适应范围有限**：主要适用于密集Transformer架构，未在MoE（混合专家）模型上验证，可能需要额外适配。
- **对比方法不全**：未与近期代表性方法（如Sequoia、Medusa、Dovetail）在统一框架下进行定量比较，仅与EAGLE-2和同系列小模型对比，说服力可进一步加强。
- **缺乏误差分析**：未报告多次运行的方差或置信区间，尽管论文声称标准差很低（0.101 tokens/s），但未在全部实验提供。
- **随机解码性能下降**：当目标模型使用随机采样时，加速比显著降低（约60%），说明方法对概率分布变化敏感，可能在多样化生成场景中效果受限。

（完）
