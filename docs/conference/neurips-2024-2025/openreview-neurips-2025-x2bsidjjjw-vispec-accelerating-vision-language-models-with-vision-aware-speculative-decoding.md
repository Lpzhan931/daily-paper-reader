---
title: "ViSpec: Accelerating Vision-Language Models with Vision-Aware Speculative Decoding"
title_zh: ViSpec：基于视觉感知投机解码加速视觉语言模型
authors: "Jialiang Kang, Han Shu, Wenshuo Li, Yingjie Zhai, Xinghao Chen"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=x2BsIdJJJW"
tags: ["query:vlm-spec"]
score: 10.0
evidence: 面向VLM的视觉感知投机解码加速
tldr: 针对视觉语言模型（VLM）推理慢的问题，本文提出ViSpec框架，通过一个轻量级视觉适配器模块压缩图像令牌，使小型草稿模型能更好地处理视觉信息。该框架将投机解码思想引入VLM，实现了显著的推理加速（超过1.5倍）。实验验证了该方法在多种VLM任务上的有效性，为多模态模型的高效部署提供了关键技术。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-x2bsidjjjw/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1394, \"height\": 473, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-x2bsidjjjw/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1329, \"height\": 626, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-x2bsidjjjw/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 404, \"height\": 364, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-x2bsidjjjw/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 750, \"height\": 393, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-x2bsidjjjw/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1441, \"height\": 1173, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x2bsidjjjw/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1173, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x2bsidjjjw/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1369, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x2bsidjjjw/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 952, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x2bsidjjjw/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 481, \"height\": 347, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x2bsidjjjw/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1068, \"height\": 478, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x2bsidjjjw/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 697, \"height\": 282, \"label\": \"Table\"}]"
motivation: 现有投机解码在VLM上加速效果有限（<1.5倍），需要针对视觉信息的特性进行优化。
method: 提出ViSpec框架，包含轻量级视觉适配器压缩图像令牌，使草稿模型能有效利用视觉上下文。
result: 在多个VLM基准上取得超过1.5倍的加速比，且不损失生成质量。
conclusion: ViSpec填补了投机解码在VLM领域的空白，实现了显著的推理加速。
---

## Abstract
Speculative decoding is a widely adopted technique for accelerating inference in large language models (LLMs), yet its application to vision-language models (VLMs) remains underexplored, with existing methods achieving only modest speedups ($<1.5\times$). This gap is increasingly significant as multimodal capabilities become central to large-scale models. We hypothesize that large VLMs can effectively filter redundant image information layer by layer without compromising textual comprehension, whereas smaller draft models struggle to do so. To address this, we introduce Vision-Aware Speculative Decoding (ViSpec), a novel framework tailored for VLMs. ViSpec employs a lightweight vision adaptor module to compress image tokens into a compact representation, which is seamlessly integrated into the draft model's attention mechanism while preserving original image positional information. Additionally, we extract a global feature vector for each input image and augment all subsequent text tokens with this feature to enhance multimodal coherence. To overcome the scarcity of multimodal datasets with long assistant responses, we curate a specialized training dataset by repurposing existing datasets and generating extended outputs using the target VLM with modified prompts. Our training strategy mitigates the risk of the draft model exploiting direct access to the target model's hidden states, which could otherwise lead to shortcut learning when training solely on target model outputs. Extensive experiments validate ViSpec, achieving, to our knowledge, the first substantial speedup in VLM speculative decoding.

---

## 论文详细总结（自动生成）

# ViSpec: 基于视觉感知投机解码加速视觉语言模型——论文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **背景**：大型语言模型（LLM）的投机解码（Speculative Decoding）已被广泛用于加速推理，通过一个小型草稿模型快速生成候选 token 序列，再由目标模型并行验证。该方法在纯文本任务上可获得 3–4 倍的加速比。
- **问题**：将该技术扩展到视觉语言模型（VLM）时，现有方法仅能获得低于 1.5 倍的轻微加速，远未达到实际部署所需的显著提升。作者认为根本原因在于图像信息具有高度冗余性，而小型草稿模型缺乏足够的处理能力来有效过滤冗余的视觉信息并保持文本连贯性。
- **意义**：随着多模态能力成为大模型的核心，VLM 推理加速具有重要价值。本文旨在填补投机解码在 VLM 领域应用的空白，实现首个有意义的加速。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
ViSpec 让小型草稿模型通过轻量级视觉适配器压缩图像信息，并集成全局视觉特征，从而更准确地预测 token，提升投机解码的接受长度和加速比。

### 关键技术细节
1. **图像嵌入压缩（Image Embedding Compression）**
   - 采用轻量级的 Q-Former 式视觉适配器（Vision Adaptor），由一个小型 Transformer 编码器和一组固定可学习的查询向量组成。
   - 输入图像的特征作为 Key/Value，查询向量作为 Query，通过注意力机制将大量图像 token 压缩成少量紧凑的视觉嵌入（实验中取 1 个）。
   - 这些压缩后的 token 保留原始图像的位置信息，并融入草稿模型的注意力机制。

2. **全局视觉特征注入（Global Visual Feature Injection）**
   - 从视觉适配器的输出中提取一个全局视觉特征向量 \( g \)。
   - 对草稿模型每个文本位置的隐藏状态 \( f_t \) 进行增强：\( f_t^{\text{aug}} = f_t + W_g g \)，其中 \( W_g \) 为可学习投影矩阵。
   - 该机制使草稿模型在长文本生成过程中始终能访问全局视觉上下文，缓解“中间丢失”（Lost in the Middle）问题。

3. **训练策略与数据集生成**
   - 面临多模态长回复数据集稀缺的问题。作者通过修改已有数据集的提示词（如“请用至少 1000 字回答”），让目标 VLM 生成长回复，构建合成训练数据。
   - 训练时采用多 token 预测（multi-token prediction）和温度采样，破坏草稿模型与目标模型隐藏状态之间的一一对应关系，防止投机捷径学习。
   - 损失函数为交叉熵：\( \mathcal{L} = \text{CrossEntropy}(p_i, \hat{p}_i) \)，其中 \( p_i \) 为目标模型概率，\( \hat{p}_i \) 为草稿模型概率。

4. **推理机制**
   - 使用 EAGLE-2 的上下文感知动态草稿树（30 个候选 token，树深度 3，扩展节点数 8）来生成候选序列，然后进行严格投机解码验证，保证生成质量无损。

## 3. 实验设计

### 数据集/场景
- **训练数据集**：
  - 文本基础：ShareGPT 数据集（68,000 个对话）。
  - 多模态基础：LLaVA Visual Instruct Pretrain LCS 数据集（68,000 个样本）。
  - 多模态长回复：通过修改上述数据集提示词，使用目标 VLM 生成长回复。
- **评测任务**：8 个多模态基准数据集
  - ScienceQA (SQA)、MM-Vet、MME、TextVQA、COCO Captions、VizWiz、GQA、SEED-Bench。
  - 覆盖视觉问答、图像描述、多模态评估等多种场景。

### Benchmark
- 对比方法：Medusa、EAGLE-2（均适配为 VLM 版本）。
- 评估指标：平均接受长度 \( \tau \)、加速比（Speedup Ratio，相对于标准自回归解码）。

### 对比方法
- 四个目标 VLM：
  - LLaVA-v1.6-Vicuna-7B
  - LLaVA-v1.6-Vicuna-13B
  - Qwen2.5-VL-3B-Instruct
  - Qwen2.5-VL-7B-Instruct

## 4. 资源与算力

- **硬件环境**：所有推理实验单 GPU 运行；草稿模型训练使用 8 块 GPU（具体型号未说明）。
- **训练超参数**：学习率 3e-5（Medusa/EAGLE-2）、3e-6（ViSpec），批大小 8，优化器 AdamW，训练 20 个 epoch，1 个 epoch 预热 + 线性学习率衰减，最大序列长度 2048。
- **训练数据规模**：文本 68k + 多模态 68k（含生成的长回复）。
- 未提供精确的训练时长或 GPU 型号等细节。

## 5. 实验数量与充分性

- **主要实验**：表 1 在 4 个目标 VLM × 8 个数据集 × 2 种温度（0 和 1）下进行，共 64 组对比（每个方法在每个设置下均报告了 \(\tau\) 和加速比）。实验覆盖了不同的模型规模、温度设置和多样任务，对比公平（采用相同草稿树结构、相同接受条件）。
- **消融实验**：
  - 表 2：不同压缩图像嵌入数量（1/4/16/64）对性能的影响。
  - 表 3：逐步添加三个组件（图像嵌入压缩、全局视觉注入、数据集生成）的增益。
  - 表 4：视觉适配器开销分析（参数量、GFLOPs、延迟）。
  - 表 5：输出长度与加速比关系。
- **额外实验**：附录 B 中补充了高分辨率数据集（HR-Bench 4K、MME-RealWorld）和视频数据集（MSVD-QA、MVBench）的验证。
- **充分性评估**：实验较为充分，涵盖多种模型、任务、温度设置，且进行了组件消融和扩展场景验证。但未报告多次运行的标准差或统计显著性，所有实验固定随机种子，结论的稳定性依赖于单一运行结果。

## 6. 主要结论与发现

- ViSpec 在所有实验设置下均显著优于 Medusa 和 EAGLE-2，实现了最高的平均接受长度和加速比。
  - 例如 LLaVA-1.6 7B 在温度 0 时，平均加速比 2.58×（TextVQA 上最高 2.90×），而 EAGLE-2 为 1.62×，Medusa 为 1.42×。
  - 在温度 1 下，ViSpec 仍保持优势，平均加速比 2.14×（LLaVA-1.6 7B）。
- 各组件均有效：图像嵌入压缩提升加速比约 30%，全局视觉注入再提升 7%，数据集生成再提升约 30%，三者协同实现显著加速。
- 草稿模型压缩图像嵌入数量为 1 时已达到最优速度，增加数量反而因计算开销降低加速比。
- 较长输出序列可获得更高加速比，但 ViSpec 在短输出上也稳定提供加速。

## 7. 优点

- **方法创新**：首次将投机解码有效应用于 VLM 并实现大幅加速，提出双重视觉集成机制（压缩嵌入 + 全局特征注入），解决了小型草稿模型处理冗余视觉信息的瓶颈。
- **数据集生成策略**：巧妙利用现有数据集和 VLM 自身生成长回复，克服了长多模态数据稀缺的问题，且训练时通过采样和 multi-token 预测避免投机捷径。
- **实验设计全面**：在多个主流 VLM 和 8 个数据集上验证，包含温度 0 和 1 两种设置，有组件消融、参数影响、开销分析等。附录还扩展到高分辨率和视频任务，展示泛化性。
- **保持生成质量**：采用严格投机解码，保证与目标模型输出分布一致，无需额外质量验证。

## 8. 不足与局限

- **绝对加速比低于纯文本 SOTA**：尽管 ViSpec 在 VLM 上取得首个显著加速，但绝对加速比（最高约 3.22×）仍低于纯文本 LLM 的 3–4×，表明 VLM 投机解码仍受限于图像预填充和视觉处理开销。
- **未报告实验统计变异性**：论文固定随机种子，未提供误差条或多次运行结果，无法评估结果的可信度。
- **训练资源细节不足**：未说明具体 GPU 型号、训练时长，使可复现性受限。
- **领域覆盖有限**：主要评测图像+文本任务，视频任务仅做初步测试（无视频特定训练），高分辨率数据集上加速比受预填充时间影响而下降。
- **部署实际性**：草稿模型需针对每个目标 VLM 单独训练，且依赖目标 VLM 生成长回复，可能引入额外训练成本。
- **通用性假设**：方法假设图像冗余性可通过压缩解决，但对于高度复杂或非常规图像（如医学影像），压缩可能丢失关键信息，文中未讨论。

（完）
