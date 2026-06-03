---
title: Streamline Without Sacrifice - Squeeze out Computation Redundancy in LMM
title_zh: 精简而不牺牲：消除大型多模态模型中的计算冗余
authors: "Penghao Wu, Lewei Lu, Ziwei Liu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=dEhemezhTu"
tags: ["query:vlm-spec"]
score: 7.0
evidence: 通过减少视觉token计算冗余来加速VLM推理
tldr: 大型多模态模型面临视觉token计算冗余导致的推理效率问题。本文提出ProxyV方法，通过引入代理视觉token，在不损失信息的前提下减轻对视觉token的大量操作（如自注意力、FFN），显著加速VLM推理。实验证明该方法有效减少计算开销，保持模型性能。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-dehemezhtu/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 857, \"height\": 519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dehemezhtu/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 855, \"height\": 557, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dehemezhtu/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1733, \"height\": 705, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dehemezhtu/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 854, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dehemezhtu/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1733, \"height\": 584, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-dehemezhtu/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 713, \"height\": 385, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dehemezhtu/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 832, \"height\": 385, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dehemezhtu/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 782, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dehemezhtu/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1322, \"height\": 1232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dehemezhtu/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1633, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dehemezhtu/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 831, \"height\": 304, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dehemezhtu/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1795, \"height\": 908, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dehemezhtu/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1419, \"height\": 723, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dehemezhtu/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1510, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dehemezhtu/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1442, \"height\": 1229, \"label\": \"Table\"}]"
motivation: 大型多模态模型因过多视觉token导致计算负担，现有方法多关注token级冗余，本文发现计算级冗余同样重要且可被消除。
method: 提出ProxyV，利用代理视觉token替代原始视觉token的繁重计算，保留关键信息同时降低计算量。
result: 实验表明ProxyV在多个多模态任务上保持性能的同时，显著减少推理计算开销。
conclusion: 计算级冗余是可以安全消除的，ProxyV为VLM高效推理提供了新思路。
---

## Abstract
Large multimodal models excel in multimodal tasks but face significant computational challenges due to excessive visual tokens. Unlike token reduction methods that focus on token-level redundancy, we identify and study the computation-level redundancy on vision tokens to ensure no information loss. Our key insight is that vision tokens from the pretrained vision encoder do not necessarily require all the heavy operations (e.g., self-attention, FFNs) in decoder-only LMMs and could be processed more lightly with proper designs. We designed a series of experiments to discover and progressively squeeze out the vision-related computation redundancy. Based on our findings, we propose ProxyV, a novel approach that utilizes proxy vision tokens to alleviate the computational burden on original vision tokens. ProxyV enhances efficiency without compromising performance and can even yield notable performance gains in scenarios with more moderate efficiency improvements. Furthermore, the flexibility of ProxyV is demonstrated through its combination with token reduction methods to boost efficiency further.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型多模态模型（LMM）如LLaVA系列在处理高分辨率图像、视频或多图像时，需要大量视觉token（通常数千个），导致自注意力计算量随序列长度平方增长，推理成本极高。现有方法主要通过**token级冗余**的视角进行剪枝或合并（如VisionZip、PyramidDrop），但这类操作不可避免地丢失细粒度信息，尤其在密集文档、精确视觉定位或多轮对话场景中。
- **研究动机**：作者发现**计算级冗余**同样存在——预训练视觉编码器输出的视觉token在进入大语言模型后，并不需要每一层都进行完整的自注意力与前馈网络（FFN）运算。通过合理设计，可以在**不丢失任何视觉信息**的前提下，大幅减少计算量。
- **整体含义**：本文旨在探索一种“不牺牲性能的加速”方案，从计算角度而非token数量角度优化，保留所有原始视觉token，同时显著提升推理效率。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：引入**代理视觉token（Proxy Vision Tokens）**——将原始视觉token下采样为一个小尺寸的“缩略图”版本，替代原始token参与LLM中的自注意力和FFN等繁重计算；代理token获得的语义信息再通过轻量级**引导更新模块（guided-update module）**传递回原始token，完成更新。这样原始token全程保留，且只经过轻量计算。
- **关键技术细节**：
  - **空间版本（Spatial ProxyV）**：
    - 假设原始token为N×N网格，以因子r下采样得到M×M代理token（M=N/r）。
    - 在LLM解码器层中，只有代理token和文本token参与自注意力（键、值包含代理、原始、文本token）和FFN，原始token不参与。
    - 代理token更新后，每个代理token通过**空间对应关系**（原始token的r×r区域对应一个代理token）利用轻量级两层MLP引导原始token更新。
    - 轻量级MLP参数：每层约14.68M（Vicuna-7B）或9.44M（简单替换方案）。
  - **非空间变体（Non-spatial ProxyV）**：
    - 不依赖2D空间结构，使用一组可学习的query embedding Q∈R^{m×d}，通过注意力机制从原始token中加权组合得到代理token（权重矩阵A∈R^{m×n}）。
    - 引导更新时，利用A的转置和softmax将代理token的信息“反投影”回每个原始token。
    - 优点：可与token reduction方法（如VisionZip）直接结合，进一步提升效率。
- **算法流程**：图像经过视觉编码器、投影后得到原始视觉token → 下采样生成代理token → 代理token与文本token一起通过LLM解码层（自注意+FFN）→ 代理token通过引导更新模块更新原始token → 后续层重复或仅原始token继续前向。

### 3. 实验设计：数据集、场景、Benchmark、对比方法

- **数据集与基准**：
  - **细粒度视觉理解（fine-grained）**：DocVQA、ChartQA、InfoVQA、TextVQA、OCRBench（评价平均得分Score_fine）。
  - **通用多模态基准**：MMBench、SEED-Bench、RefCOCO、MMStar、GQA、MME、MMMU、POPE、ScienceQA、AI2D、RealWorldQA。
  - **文档解析任务**：使用DocStruct4M数据集继续训练，在CCpdf验证集上评测BLEU和编辑距离。
  - **视觉定位**：RefCOCO（testA+testB）。
- **对比方法**：VisionZip（token reduction before LLM）、PyramidDrop（progressive pruning inside LLM）、以及多种消融变体（仅屏蔽注意力、跳过FFN、简单替换MLP等）。
- **场景设置**：采用2-stage训练（预训练1.2M captioning数据1 epoch，指令微调779K数据1 epoch），图像采用AnyRes策略（最多5个网格，每个网格336×336→24×24 tokens），LLM backbone包括Vicuna1.5-7B/13B、LLama3-8B、Qwen2-7B、Phi3-3B、InternLM2.5-7B。

### 4. 资源与算力

- **文中明确提及**：所有FLOPs和时间测量在**单块H100 GPU**上完成，使用eager attention实现，固定配置为5个图像网格（2880 tokens）+ 50个文本token，主要测量**prefilling阶段**。
- **训练算力未详细说明**：未给出使用的GPU数量、训练总时长等具体信息。推测在常见LLaVA训练配置（如8×A100）下可复现，但论文未提及。

### 5. 实验数量与充分性

- **实验数量**：超过15组主要实验，包括：
  - 探索性实验（不同LLM下attention masking曲线，图2）。
  - 消融实验（跳过注意力、跳过FFN、替换MLP vs ProxyV，表1-3）。
  - 主实验（6种不同LLM backbone，各两种配置，表4）。
  - 与token reduction方法对比（表5，包含通用基准和文档解析任务）。
  - 非空间变体及组合实验（表6）。
  - 附录中提供完整细粒度分数和通用基准分数（表7-10）。
- **充分性与公平性**：
  - 覆盖了多种主流LLM和多种任务类型（细粒度、通用、定位、文档解析）。
  - 对比方法使用相同的训练数据和微调策略，并调整参数使效率相近，比较公平。
  - 消融实验逐步验证各组件贡献，逻辑清晰。
  - 局限性：未在更大规模模型（如13B以上除Vicuna-13B外仅此一个）或更多样的高分辨率策略上进行验证；对于视频或多图像场景未直接测试。

### 6. 论文的主要结论与发现

- **计算级冗余确实存在**：在LLM的中后期层，视觉token之间的自注意力可以完全屏蔽而不影响性能（图2），且不同LLM冗余程度不同。
- **同时跳过自注意力和FFN**：仅通过轻量级MLP替换原始操作可显著降低FLOPs（40%~80%），但可能导致性能下降；增加视觉专用参数带来的增益可部分抵消损失（表2）。
- **ProxyV能有效权衡**：从中层（如第12层）开始应用ProxyV，可达到101%的相对性能（在细粒度基准上甚至略有提升），同时FLOPs减少46%、时间减少41%；从第16层开始则性能提升至102.4%，效率提升略小（表3、4）。
- **与token reduction互补**：非空间变体可与VisionZip结合，在性能基本不变情况下进一步降低62% FLOPs（表6）。
- **视觉专用模块促进模态对齐**：通过MIR度量发现，引入轻量级视觉MLP可改善文本与视觉token的对齐（MIR从3.62降至3.10），解释了性能提升的原因。

### 7. 优点

- **创新视角**：首次系统研究LMM中的计算级冗余，区别于主流的token级剪枝，从根本上避免了信息丢失。
- **设计精巧**：代理token方案在保留原始token的前提下大幅降低计算，引导更新模块参数轻量且有效。
- **灵活可扩展**：非空间变体解除空间依赖，能无缝兼容现有的token reduction方法，形成双层面加速。
- **实验扎实**：覆盖多种LLM、多类任务，并提供了详尽的消融和对比，结论可靠。

### 8. 不足与局限

- **未深入分析冗余差异**：仅指出不同LLM冗余模式不同，但未给出统一理论解释或自适应选择策略。
- **非空间变体仍有参数开销**：虽然效率提升，但需要额外的可学习query和注意力计算，对于极长序列可能影响延迟。
- **文档解析任务性能略降**：ProxyV在CCpdf上BLEU略低于基线（0.7923 vs 0.7991），虽然远好于token reduction方法，但说明仍有微小信息损失（可能源于引导更新模块的近似性）。
- **场景覆盖有限**：实验主要基于静态图像（最多5个网格），未在视频或多图像长上下文场景中验证，这些场景可能带来不同的冗余模式。
- **训练资源未透明**：未报告完整训练所需的GPU数量和时间，不利于复现和能耗评估。
- **潜在偏差**：仅使用LLaVA-Next风格的架构，未在交叉注意力架构或其他投影方式上验证，结论普适性待进一步检验。

（完）
