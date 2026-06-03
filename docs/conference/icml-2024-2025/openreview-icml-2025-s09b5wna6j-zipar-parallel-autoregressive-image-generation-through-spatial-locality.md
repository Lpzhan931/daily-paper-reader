---
title: "ZipAR: Parallel Autoregressive Image Generation through Spatial Locality"
title_zh: "ZipAR: 通过空间局部性实现并行自回归图像生成"
authors: "Yefei He, Feng Chen, Yuanyu He, Shaoxuan He, Hong Zhou, Kaipeng Zhang, Bohan Zhuang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=S09B5wNa6J"
tags: ["query:vlm-spec"]
score: 6.0
evidence: 基于投机解码思想的并行自回归图像生成加速
tldr: 针对自回归图像生成速度慢的问题，本文提出ZipAR，利用图像空间局部性，在行方向解码的同时并行解码列方向相邻标记，并通过类似投机解码的自适应窗口拒绝采样保证上下文对齐。该方法无需训练即可显著加速图像生成，展示了投机解码思想在视觉领域的迁移潜力。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-s09b5wna6j/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1592, \"height\": 988, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-s09b5wna6j/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1751, \"height\": 1130, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-s09b5wna6j/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1595, \"height\": 537, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-s09b5wna6j/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1586, \"height\": 475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-s09b5wna6j/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 780, \"height\": 636, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-s09b5wna6j/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 791, \"height\": 660, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-s09b5wna6j/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1411, \"height\": 418, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-s09b5wna6j/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1297, \"height\": 461, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s09b5wna6j/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1467, \"height\": 650, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s09b5wna6j/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1386, \"height\": 536, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s09b5wna6j/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 633, \"height\": 343, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s09b5wna6j/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 551, \"height\": 385, \"label\": \"Table\"}]"
motivation: 自回归图像生成逐像素解码速度慢，利用图像局部性可并行化。
method: 基于空间局部性，在行解码基础上并行解码列相邻标记，采用自适应窗口拒绝采样。
result: 在多个图像生成模型上实现显著的加速比，无需额外训练。
conclusion: ZipAR是一种即插即用的并行解码框架，可高效加速自回归视觉生成。
---

## Abstract
In this paper, we propose ZipAR, a training-free, plug-and-play parallel decoding framework for accelerating autoregressive (AR) visual generation. The motivation stems from the observation that images exhibit local structures, and spatially distant regions tend to have minimal interdependence. Given a partially decoded set of visual tokens, in addition to the original next-token prediction scheme in the row dimension, the tokens corresponding to spatially adjacent regions in the column dimension can be decoded in parallel. To ensure alignment with the contextual requirements of each token, we employ an adaptive local window assignment scheme with rejection sampling analogous to speculative decoding. By decoding multiple tokens in a single forward pass, the number of forward passes required to generate an image is significantly reduced, resulting in a substantial improvement in generation efficiency. Experiments demonstrate that ZipAR can reduce the number of model forward passes by up to 91% on the Emu3-Gen model without requiring any additional retraining.

---

## 论文详细总结（自动生成）

# 论文总结：ZipAR: Parallel Autoregressive Image Generation through Spatial Locality

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：自回归（AR）图像生成模型（如Emu3、LlamaGen等）采用逐token的自回归解码（next-token prediction），生成高分辨率图像需要数千次前向传播，导致推理速度极慢，成为部署障碍。
- **背景**：尽管大型语言模型中的并行解码方法（如Medusa、Jacobi解码、投机解码）已被提出，但这些方法要么需要额外训练（如辅助头或草稿模型），要么未利用视觉内容的独特属性（如空间局部性）。现有AR视觉模型通常按光栅顺序（raster order）逐行生成，导致相邻行的起始token与前一行的末尾token在序列上相邻但空间上相距甚远，而空间上相邻的token（如同一列的上下行）却必须等待整个前一行解码完才能生成，效率低下。
- **整体含义**：本文提出ZipAR，一种**无需训练、即插即用**的并行解码框架，利用视觉内容的**空间局部性**，在保持图像质量的同时大幅减少前向传播次数，提升AR视觉生成的效率。

## 2. 方法论：核心思想、关键技术细节、公式或算法流程

### 核心思想
- 基于观察：AR模型中注意力分数主要分配给同列的上一行附近的token（图3证明）。因此，无需等待整行解码完毕，只要当前行已生成足够的邻近token（由**局部窗口大小**定义），就可以并行开始下一行token的解码。
- 通过**跨行并行**（inter-row parallel decoding），在单次前向传播中解码多个token，减少总步数。

### 关键技术细节

#### 2.1 并行解码条件
- 定义局部窗口大小 $s$。对于位于第 $i$ 行、第 $j$ 列的token $x_{i,j}$，当上一行中同一列附近 $s$ 个token（即 $x_{i-1, j}, x_{i-1, j+1}, \ldots, x_{i-1, j+s-1}$）全部已被解码时，$x_{i,j}$ 即可开始生成。
- 公式化条件：
\[
C(i,j) = 
\begin{cases}
1 & \text{如果 } \{x_{i-1,k} \mid j \le k < j+s\} \subseteq \mathcal{D} \\
0 & \text{否则}
\end{cases}
\]
其中 $\mathcal{D}$ 为已解码的token集合。

#### 2.2 起始token处理
- 对于每个新行的第一个token $x_{i,0}$，需要上一行的最后一个token作为输入。ZipAR提供两种方案：
  - 若模型支持**行尾标记**（end-of-row token，如Lumina-mGPT），预先插入这些固定标记作为占位符。
  - 否则，临时用已解码的最近邻token（如上一行的同列token）赋值给缺失的末尾token。

#### 2.3 自适应窗口大小分配
- 固定窗口大小 $s$ 是超参数，不同token所需上下文不同（图5显示注意力分布差异大）。为平衡效率与质量，提出**自适应窗口 + 类似投机解码的拒绝采样**：
  - 给定最小窗口 $s_{\min}$，生成 $x_{i, s_{\min}-1}$ 后尝试开始下一行第一个token $x_{i+1,0}$。
  - 不直接接受该token，而是在下一前向步中，用稍大窗口 $s_{\min}+1$ 重新预测同一个位置，并计算两个预测分布 $p(x|x_{0,0},...,x_{i,k})$ 和 $p(x|x_{0,0},...,x_{i,k-1})$ 的比率。
  - 若随机采样值 $r \sim U[0,1]$ 满足：
\[
\tilde{C}(i+1,0) = 
\begin{cases}
1 & \text{if } r < \min\left(1, \frac{p(x|x_{0,0},...,x_{i,k})}{p(x|x_{0,0},...,x_{i,k-1})}\right) \\
0 & \text{otherwise}
\end{cases}
\]
则接受，并继续生成该行的后续token；否则拒绝当前token并从调整后的分布中重新采样（公式3），并继续扩大窗口直到满足或上一行完全解码。

#### 2.4 整体流程（图4示意）
- 设定最小窗口 $s$，从第一行开始光栅顺序解码。当满足C(i,j)=1时，下一行的对应token可并行生成。随着多行同时解码，一次前向传播可产出多个token，总步数减少。

## 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

### 数据集与场景
- **类条件图像生成**：ImageNet 256×256（生成384×384后resize到256×256），评估FID。
- **文本引导图像生成**：MS-COCO验证集，评估CLIP Score、VQAScore、HPSv2、ImageReward、Aesthetic Score。也采用Parti数据集的部分提示。
- 可视化样本：使用Emu3-Gen（图1）、Lumina-mGPT-7B（图7）的定性展示。

### 对比方法
- **基线**：原始自回归模型（NTP，next-token prediction）。
- **并行解码方法**：
  - SJD（Speculative Jacobi Decoding，Teng et al., 2024）——已有工作，适用于自回归图像生成。
  - 消融中对比固定窗口 vs 自适应窗口。
- 未与其他投机解码（如Medusa、标准Jacobi）直接比较（但指出ZipAR与这些方法正交）。

### Benchmark指标
- FID（Frechet Inception Distance）；CLIP Score；VQAScore；HPSv2；ImageReward；Aesthetic Score；前向步数（Step）及延迟（Latency）。

## 4. 资源与算力

- 文中明确说明：**所有实验在Nvidia A100 GPU上使用PyTorch框架进行**。
- 未具体说明使用的GPU数量、每个实验的运行时间或训练时长（因为ZipAR是训练-free方法，仅需推理）。
- 可推断：对于类条件生成（50K图像），可能需要多卡但未提及。

## 5. 实验数量与充分性

- **主要实验组**：
  1. **类条件生成（ImageNet）**：在LlamaGen-L和LlamaGen-XL上测试，对比NTP、SJD和ZipAR不同窗口大小（ZipAR-16/14/12等）。结果见表1。
  2. **文本引导生成（MS-COCO）**：在LlamaGen-XL-512、Lumina-mGPT-768、Lumina-mGPT-1024上测试，对比NTP、SJD和ZipAR不同窗口大小。结果见表2（多指标）和表3（CLIP Score+延迟）。
  3. **Emu3-Gen**：定性展示（图1），给出步数减少百分比（最高91%）。
  4. **消融实验**：
     - 自适应窗口 vs 固定窗口（图6），在LlamaGen-L上对比不同步数下的FID。
     - 超参数敏感性：不同分类器引导尺度（表4）、不同采样温度（表5）对ZipAR-16的影响。
- **充分性评价**：实验覆盖了主流的AR视觉生成模型（LlamaGen、Lumina-mGPT、Emu3），包含类条件和文本引导两大场景，指标多样。消融实验验证了自适应窗口的优势，并检验了超参数鲁棒性。整体实验设计较为充分、客观。未进行用户研究或大规模泛化测试（如视频生成），但针对论文目标已足够。

## 6. 论文的主要结论与发现

- **主要结论**：ZipAR能有效利用空间局部性并行解码跨行token，在**无需任何额外训练**的情况下，将AR视觉生成的前向步骤减少最高**91%**（Emu3-Gen），同时保持可比的图像质量（FID、CLIP Score等指标几乎不变或轻度波动）。
- **关键发现**：
  - 图像中注意力存在强烈的列方向局部性（同列上一行），而非序列相邻性。
  - 自适应窗口分配比固定窗口更优（相同步数下FID更低）。
  - ZipAR对采样超参数（温度、CFG尺度）不敏感，可在保持原最优参数下使用。
  - 加速效果随图像分辨率增加更显著（高分辨率下更多行可并行）。

## 7. 优点：方法或实验设计上有哪些亮点

- **方法亮点**：
  - **无需训练**：即插即用，直接用于现有AR视觉模型，降低部署成本。
  - **空间局部性创新**：首次将投机解码思想与视觉二维空间结构结合，优于传统序列级并行方法。
  - **自适应窗口+拒绝采样**：动态平衡上下文充分性与加速比，避免手工调参。
  - **兼容性**：与Medusa、Jacobi等序列级并行方法正交，可叠加使用。
- **实验亮点**：
  - 覆盖多个模型（不同架构、尺寸）和任务（类条件、文生图），指标全面。
  - 对比方法包括已有的SJD，且进行了公平的步数-质量权衡分析。
  - 消融实验清晰验证自适应窗口的有效性，并测试超参数鲁棒性。

## 8. 不足与局限

- **实验覆盖**：
  - 未在更大尺度视觉生成模型（如Video AR模型、更高分辨率如1024×1024的LlamaGen等）上测试，但已包含768和1024的Lumina-mGPT。
  - 未与其他无训练并行方法（如标准Jacobi迭代、Medusa）直接对比，仅与SJD比较，而SJD本身也是基于Jacob的，但可认为ZipAR在视觉模型上更高效。
  - 缺少真实用户时延测试（仅模拟batch=1）。
- **偏差风险**：
  - 方法依赖光栅顺序，对非光栅顺序的AR模型（如随机顺序）可能不直接适用。
  - 若图像内容需要长程依赖（如全局场景布局），过小的窗口可能导致质量下降（尽管自适应窗口缓解）。
  - 拒绝采样可能引入额外的随机性，但理论上保持分布一致。
- **应用限制**：
  - 需要模型能处理行尾标记或插入占位符，部分模型需特殊处理。
  - 加速比受图像大小与模型架构影响：特征图过小（如4×4）可能并行机会少。

（完）
