---
title: "Hawk: Leveraging Spatial Context for Faster Autoregressive Text-to-Image Generation"
title_zh: "Hawk: 利用空间上下文加速自回归文本到图像生成"
authors: "Zhi-Kai Chen, Jun-Peng Jiang, Han-Jia Ye, De-Chuan Zhan"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=NMQUvjAY5x"
tags: ["query:vlm-spec"]
score: 5.0
evidence: 投机解码用于图像生成，可迁移至VLM
tldr: 本文提出Hawk，将投机解码应用于自回归文本到图像生成以加速推理。针对图像生成中采样空间巨大且空间结构利用不足的问题，Hawk利用轻量级草稿模型和目标模型验证，有效提升了生成速度。实验表明，该方法在不牺牲图像质量的前提下显著降低延迟，为投机解码在视觉生成领域的应用开辟了新路径。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-nmquvjay5x/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 715, \"height\": 475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nmquvjay5x/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 676, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nmquvjay5x/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1449, \"height\": 846, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nmquvjay5x/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 717, \"height\": 446, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nmquvjay5x/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 707, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nmquvjay5x/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 765, \"height\": 543, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nmquvjay5x/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 731, \"height\": 775, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nmquvjay5x/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1446, \"height\": 1093, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nmquvjay5x/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1447, \"height\": 917, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-nmquvjay5x/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1452, \"height\": 554, \"label\": \"Table\"}]"
motivation: 自回归图像生成推理缓慢，投机解码在文本生成中成功但图像生成面临采样空间大和空间结构利用不足的挑战。
method: 提出Hawk，采用轻量级草稿模型进行快速推测，并结合图像的空间上下文进行验证。
result: 在图像生成任务上实现显著加速，同时保持生成质量。
conclusion: 投机解码可有效扩展至图像生成领域，为视觉模型推理加速提供新方法。
---

## Abstract
Autoregressive (AR) image generation models are capable of producing high-fidelity images but often suffer from slow inference due to their inherently sequential, token-by-token decoding process. Speculative decoding, which employs a lightweight draft model to approximate the output of a larger AR model, has shown promise in accelerating text generation without compromising quality. However, its application to image generation remains largely underexplored. The challenges stem from a significantly larger sampling space, which complicates the alignment between the draft and target model outputs, coupled with the inadequate use of the two-dimensional spatial structure inherent in images, thereby limiting the modeling of local dependencies. To overcome these challenges, we introduce Hawk, a new approach that harnesses the spatial structure of images to guide the speculative model toward more accurate and efficient predictions. Experimental results on multiple text-to-image benchmarks demonstrate a 1.71× speedup over standard AR models, while preserving both image fidelity and diversity.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：自回归（AR）图像生成模型虽然能生成高质量图像，但因其逐token的串行解码过程导致推理速度极慢，限制了实际部署。文本领域的投机解码（Speculative Decoding）已成功加速推理且不损失质量，但直接迁移到图像生成面临两大挑战：1）图像生成的采样空间远大于文本（词汇表大小通常大20-400倍），导致轻量草稿模型与目标模型难以对齐；2）图像具有二维空间结构（水平与垂直依赖），而文本投机解码忽视垂直空间信息，未能有效利用图像局部依赖性。
- **整体含义**：本文旨在将投机解码适配到图像生成领域，通过利用图像的空间上下文来加速推理同时保持生成保真度与多样性。

## 2. 方法论
- **核心思想**：提出 **Hawk** 框架，基于**空间投机解码（Spatial Speculative Decoding）**，显式利用图像二维空间结构（水平与垂直）来改进草稿模型与目标模型的对齐。通过引入**双向草稿头**（水平草稿头和垂直草稿头），分别沿水平和垂直方向生成候选token，然后合并成一个统一的空间采样池，最后利用树解码进行验证，实现多个token单步生成与验证，加速推理。
- **关键技术细节**：
  - **注意力下沉实验**：发现图像生成中，注意力不仅集中在推理相邻点（水平方向），还显著关注空间相邻点（如上一行像素），验证了垂直依赖的重要性。
  - **双向草稿头**：水平草稿头预测当前位置向右的token（如T+1, T+2...）；垂直草稿头预测当前位置向下跨越整行宽度的token（如T+Image_Width, T+2*Image_Width...）。垂直草稿结果缓存下来供后续行使用。
  - **空间采样池**：在每个推理位置，将水平草稿与缓存的垂直草稿合并，形成二维候选池。候选树通过采样池的笛卡尔积生成，增加候选多样性。
  - **验证与采样**：采用树结构化验证，依次验证每个深度上的候选。若某候选被接受则继续下一深度；若被拒绝，则根据目标分布与草稿分布的差异进行残差重采样（公式(6)-(7)），保证最终分布与原始模型一致。
- **公式/算法流程**：
  - 设定当前推断位置T，水平投机深度n，垂直投机深度VSD。
  - 第一步：使用Dual Direction Drafting Heads分别生成水平草稿分布 $P_{horiz}(x_{T+n}|x_{\le T})$ 和垂直草稿分布（缓存）。
  - 第二步：从缓存中检索对应位置的垂直草稿（公式(3)），与水平草稿合并成空间采样池（公式(5)）。
  - 第三步：从各候选位置的采样池中生成树形候选序列。
  - 第四步：目标模型并行验证候选，更新接受/拒绝，按公式(7)调整分布。

## 3. 实验设计
- **数据集/场景**：
  - 使用 **COCO 2017** 和 **Flickr30K** 的验证集，各采样500个样本作为测试集。
  - 训练集：从LAION aesthetic训练集中采样6000张图像微调草稿头。
- **基准模型**：Lumina-mGPT（768×768图像生成），使用top-k=2000采样，温度1.0，分类器无引导尺度3.0。
- **对比方法**：
  - Vanilla AR（标准自回归解码）
  - Medusa（仅水平草稿头）
  - Hawk with Vertical Draft Heads（仅垂直草稿头）
  - LANTERN++（集成到Medusa框架中的多草稿方法）
  - Hawk with Spatial Draft Heads（水平和垂直草稿头组合，即本文完整方法）
- **评估指标**：
  - 加速比（原推理时间/加速后推理时间）
  - 平均接受长度
  - FID（越低越好）
  - CLIP Score（越高越好）

## 4. 资源与算力
- 文中明确说明：所有实验在 **单张RTX 3090 GPU** 上完成。
- 训练草稿头使用6000张图像，采用AdamW优化器，学习率2e-5，权重衰减0.1，beta=(0.9,0.95)，训练耗时 **8-12小时**收敛。
- 推理加速实验在相同RTX 3090上进行。

## 5. 实验数量与充分性
- **定量实验**：在两个数据集（COCO2017, Flickr30K）上对比了五种方法，报告了加速比、接受长度、FID、CLIP Score（表1）。
- **定性实验**：展示了四组不同提示词生成的图像对比（图3），视觉质量无明显退化。
- **消融分析**：
  - 对比水平草稿头与垂直草稿头的训练损失与性能衰减率（图4），发现垂直头在相同距离下衰减更小。
  - 对比水平和垂直头在不同区域（如细节区域）的KL散度（图5），验证垂直头在边缘、轮廓等区域提供互补信息。
  - 理论分析多采样空间对残差概率的影响（图6），表明双方向设计降低拒绝概率。
- **充分性评价**：实验覆盖了主流数据集、多种对比方法、消融分析以及理论验证，较充分。但未报告多次运行的误差棒（论文解释LLM领域通常不报告），统计显著性不明确。整体客观性较好，对比方法在相同框架下实现公平比较。

## 6. 主要结论与发现
- Hawk方法在COCO2017上达到 **1.71×加速**，在Flickr30K上达到 **1.69×加速**，同时FID和CLIP Score与原始模型基本持平，证明加速不牺牲质量。
- 垂直草稿头虽然投机距离远，但利用空间相邻信息，训练损失比相同欧氏距离的水平头更低，说明垂直方向提供了有效信号。
- 在生成细节丰富区域（如大象眼睛、鼻子等），水平和垂直头分布的KL差异增大，表明双向空间采样池能更好地覆盖目标模型的多种可能输出，提高接受率。
- 双向草稿头相比单方向可进一步降低残差重采样概率，理论上可取得更大加速。

## 7. 优点
- **创新性**：首次将投机解码与图像二维空间结构结合，利用垂直草稿头扩展采样空间，想法新颖。
- **方法论扎实**：通过注意力下沉实验验证空间依赖的存在性，并给出理论证明保证分布一致性。
- **实验设计合理**：在多数据集上与多种基线（包括最新LANTERN++）对比，同时进行消融分析。
- **效率与质量权衡良好**：在不放宽验证阈值的情况下实现加速，避免了LANTERN++因放宽阈值导致质量下降的问题。
- **轻量级**：草稿头参数仅占基础模型<1%，内存开销约134MB（FP16），训练仅需8-12小时。

## 8. 不足与局限
- **实验覆盖有限**：仅在一个模型（Lumina-mGPT）和两个数据集（COCO, Flickr30K）上验证，未在更大的AR图像生成模型（如DALL-E、Chameleon）或其他分辨率设置下测试，泛化性待验证。
- **缺少误差分析**：未提供多次运行的统计误差或置信区间，实验稳定性无法量化。
- **基线选择较弱**：论文承认Medusa并非最先进的投机解码方法，未来可集成Eagle、Hydra等更优基线，当前加速比可能低估潜力。
- **训练数据规模小**：仅用6000张图像微调，可能无法充分覆盖复杂场景，影响草稿头泛化能力。
- **内存与计算开销**：垂直草稿头需要额外缓存（大小约IW×VSD×(VSD+1)/2），在大图像或深投机深度下可能增加显存压力。
- **应用限制**：当前方法仅适用于遵循光栅扫描顺序的AR图像生成模型，对非光栅顺序或多尺度生成可能不直接适用。

（完）
