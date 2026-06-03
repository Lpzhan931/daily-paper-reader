---
title: "SparseVLM: Visual Token Sparsification for Efficient Vision-Language Model Inference"
title_zh: "SparseVLM: 面向高效视觉-语言模型推理的视觉标记稀疏化"
authors: "Yuan Zhang, Chun-Kai Fan, Junpeng Ma, Wenzhao Zheng, Tao Huang, Kuan Cheng, Denis A Gudovskiy, Tomoyuki Okuno, Yohei Nakata, Kurt Keutzer, Shanghang Zhang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=80faIPZ67S"
tags: ["query:vlm-spec"]
score: 9.0
evidence: 视觉标记稀疏化加速VLM推理
tldr: 针对视觉语言模型推理中视觉标记计算开销大的问题，本文提出一种无需训练的标记稀疏化方法SparseVLM。该方法利用自注意力矩阵中文本标记与视觉标记的相关性来评估视觉标记重要性，并渐进式剪枝不相关标记。实验表明，该方法在保持性能的同时显著降低计算量，为VLM高效推理提供了轻量级方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-80faipz67s/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1651, \"height\": 662, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-80faipz67s/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1759, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-80faipz67s/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1763, \"height\": 621, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-80faipz67s/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1719, \"height\": 459, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-80faipz67s/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 867, \"height\": 564, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-80faipz67s/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1722, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-80faipz67s/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1739, \"height\": 833, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-80faipz67s/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1677, \"height\": 1093, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-80faipz67s/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1672, \"height\": 1080, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-80faipz67s/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1386, \"height\": 924, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-80faipz67s/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1527, \"height\": 2356, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-80faipz67s/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1791, \"height\": 1530, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-80faipz67s/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 875, \"height\": 363, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-80faipz67s/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 871, \"height\": 421, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-80faipz67s/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 823, \"height\": 411, \"label\": \"Table\"}]"
motivation: 视觉语言模型中视觉标记计算开销大，现有方法需额外训练数据或参数。
method: 利用文本-视觉标记自注意力相关性评分，无需训练地渐进剪枝不相关视觉标记。
result: 在多个VLM基准上保持性能的同时，显著减少计算量，无需额外参数或微调。
conclusion: SparseVLM是一种高效且无需训练的视觉标记优化机制，可加速VLM推理。
---

## Abstract
In vision-language models (VLMs), visual tokens usually consume a significant amount of computational overhead, despite their sparser information density compared to text tokens. To address this, most existing methods learn a network to prune redundant visual tokens and require additional training data. Differently, we propose an efficient training-free token optimization mechanism dubbed **SparseVLM** without extra parameters or fine-tuning costs. Concretely, given that visual tokens complement text tokens in VLMs for linguistic reasoning, we select visual-relevant text tokens to rate the significance of vision tokens within the self-attention matrix extracted from the VLMs. Then we progressively prune irrelevant tokens. To maximize sparsity while retaining essential information, we introduce a rank-based strategy to adaptively determine the sparsification ratio for each layer, alongside a token recycling method that compresses pruned tokens into more compact representations. Experimental results show that our SparseVLM improves the efficiency of various VLMs across a range of image and video understanding tasks. In particular, when LLaVA is equipped with SparseVLM, it achieves a 54\% reduction in FLOPs, lowers CUDA time by 37\%, and maintains an accuracy rate of 97\%. Our code is available at https://github.com/Gumpest/SparseVLMs.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：视觉-语言模型（VLM）中，视觉标记（visual tokens）的数量远多于文本标记，且视觉信息具有天然稀疏性，导致推理时产生巨大的计算和内存开销。现有加速方法通常需要训练额外的剪枝网络或修改模型结构，引入额外参数与数据，难以即插即用。
- **整体含义**：本文提出一种**无需训练的文本引导视觉标记稀疏化框架 SparseVLM**，通过复用 VLM 解码器中已有的自注意力矩阵，自适应地剪枝冗余视觉标记，同时利用标记回收机制减少信息损失，实现了高效、无额外开销的 VLM 推理加速。

### 2. 论文提出的方法论

- **核心思想**：利用文本标记对视觉标记的重要性评分，以文本为“评价者”指导视觉标记的剪枝，并根据注意力矩阵的秩自适应确定每层的剪枝率。
- **关键技术细节**：
  1. **视觉标记重要性估计**：从自注意力矩阵中提取文本-视觉交叉注意力部分 \(P \in \mathbb{R}^{L_t \times L_v}\)，对每列（即每个视觉标记）取所有文本行平均值得到显著性向量 \(\tilde{\mathbf{p}}\)。
  2. **相关文本标记选择（Rater Selection）**：并非所有文本标记都适合作为评价者。通过计算文本嵌入 \(H_q\) 与视觉嵌入 \(H_v\) 的点积 Softmax 得到视觉相关度 \(r\)，仅保留 \(r \geq \text{mean}(r)\) 的文本标记作为“评价者”，避免无关词（如介词、代词）的干扰。
  3. **自适应稀疏化比率**：对注意力矩阵 \(P\) 求秩（rank），定义每层应剪枝的视觉标记数量 \(N = \lambda \times (L_v - \text{rank}(P))\)，其中 \(\lambda\) 为缩放因子。高秩意味着信息冗余少，剪枝少；低秩则反之，实现逐层自适应。
  4. **视觉标记回收（Token Recycling）**：从待删除的视觉标记中保留重要性最高的 \(\tau\%\)，使用密度峰值聚类（kNN-based density peak）将它们聚合为若干类中心，再通过元素求和重构为更紧凑的令牌，从而减少信息损失。
- **算法流程**（文字说明）：
  1. 输入图像与文本指令，经视觉编码器和投影得到视觉令牌 \(H_v\)，文本令牌 \(H_q\)。
  2. 在进入 LLM 解码器前，先根据文本-视觉相似度选出文本评价者。
  3. 在每个 Transformer 层中，提取自注意力矩阵（兼容 FlashAttention 的双重前向技巧），计算视觉标记显著性及矩阵秩，确定该层剪枝数 \(N\)。
  4. 对重要性最低的 \(N\) 个视觉标记进行回收：取其中前 \(\tau\%\)，聚类重构为 \(C\) 个紧凑令牌，替换原有被剪令牌；其余直接丢弃。
  5. 保留的重要视觉标记与重构令牌一起参与后续计算。

### 3. 实验设计

- **数据集与场景**：
  - **图像理解**：GQA、MMBench、MME、POPE、ScienceQA、SEED-Bench、TextVQA、MMVet。
  - **视频理解**：TGIF-QA、MSVD-QA、MSRVTT-QA、ActivityNet-QA。
- **基准（Benchmark）**：对比各任务上的准确率（Acc.）和 GPT 评估分数（视频任务）。
- **对比方法**：
  - 图像任务：ToMe (ICLR'23)、FastV (ECCV'24)、PDrop (CVPR'25) 以及随机剪枝基线。
  - 视频任务：FastV。
  - 所有对比方法均保持相同的剩余视觉标记数量，公平比较。
- **模型框架**：LLaVA-1.5 (7B/13B)、Mini-Gemini (MGM)、Qwen2-VL、Video-LLaVA。

### 4. 资源与算力

- 文中明确说明：所有实验在**单张 NVIDIA A100-80G GPU** 上完成。软件环境为 Python 3.10、PyTorch 2.1.2、CUDA 11.8、transformers 4.31.0。
- **未提及训练时长**（因为 SparseVLM 无需额外训练，仅需要推理阶段的稀疏化处理），但给出了推理时的 CUDA 延迟和 FLOPs 数据（见表 1 等）。

### 5. 实验数量与充分性

- 实验覆盖**三个不同架构的 VLM**（LLaVA、Mini-Gemini、Qwen2-VL）和一个视频 VLM（Video-LLaVA），在**8个图像理解基准 + 4个视频理解基准**上测试。
- 进行了**多种稀疏化比率**（保留 192、128、64 个视觉标记）的对比，以及不同方法在相同延迟/FLOPs 下的性能比较。
- 包含**消融实验**：
  - 文本评价者选择的有效性（Figure 5）。
  - 标记回收（Token Recycling）的贡献（Table 4）。
- **客观性**：所有对比方法均保持相同的剩余令牌数，FLOPs 和延迟基于统一测量（单 A100），并报告了多次实验的平均表现。
- 结论：实验设计充分，公平性较好，覆盖了主流模型和任务。

### 6. 论文的主要结论与发现

- SparseVLM 在**无训练、无额外参数**的前提下，显著加速 VLM 推理，同时保留大部分原始精度。
  - LLaVA-7B：保留 192 令牌（压缩 66.7%）时，平均准确率下降仅 0.9%；保留 64 令牌（压缩 88.9%）时，下降 10.7%，但远超同类方法（如 FastV 下降 28.0%）。
  - 视频任务（Video-LLaVA）：保留 194 令牌（压缩 90.5%）时，平均准确率达 95.0% 的原始性能，而 FastV 仅为 80.3%。
- 文本引导的视觉稀疏化优于文本无关方法，自适应稀疏比率和标记回收均有正向贡献。
- **SparseVLM 兼容 FlashAttention**，可在不破坏其优化的情况下提取注意力矩阵。

### 7. 优点

- **训练免费**：完全无需微调或训练额外的网络，即插即用。
- **文本引导**：首次在无需训练的方法中利用文本内容指导视觉剪枝，精准保留与问题相关的视觉区域。
- **自适应稀疏化**：基于注意力矩阵的秩动态调整每层剪枝数，适应不同图像的信息密度。
- **标记回收**：将部分被剪令牌聚类重构，有效减少信息损失，在极端压缩场景下效果尤为显著。
- **易部署**：可作为插件模块应用于多种 VLM 架构（LLaVA、MGM、Qwen2-VL、Video-LLaVA），且兼容 FlashAttention。
- **全面评估**：在图像和视频两类任务、多种基准上验证了通用性和鲁棒性。

### 8. 不足与局限

- **信息损失风险**：虽然回收机制缓解了信息丢失，但在极高压缩率（如 88.9%）下，部分细粒度视觉细节仍可能丢失，影响依赖细节的任务（如 OCR、细粒度分类）的准确性。
- **依赖注意力矩阵质量**：方法的核心依赖于自注意力得分，若 VLM 未充分对齐视觉与文本模态，评估可能不够准确。
- **未讨论偏见问题**：论文指出“没有明显的社会影响”，但未评估模型在公平性、鲁棒性方面的潜在偏差，稀疏化可能加剧某些系统性偏差。
- **视频任务实验规模**：视频实验采用首个 1000 样本（与 FastV 一致），未有全量数据集测试，可能受采样偏差影响。
- **超参数依赖**：方法涉及 \(\lambda\)、\(\tau\)、\(\theta\) 等超参数，虽然在标准设置下表现良好，但未给出自动调优方案，跨场景可能需要手动调整。

（完）
