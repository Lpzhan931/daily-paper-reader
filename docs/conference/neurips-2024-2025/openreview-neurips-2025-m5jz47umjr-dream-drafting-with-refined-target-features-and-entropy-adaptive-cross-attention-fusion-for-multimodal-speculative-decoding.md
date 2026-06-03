---
title: "DREAM: Drafting with Refined Target Features and Entropy-Adaptive Cross-Attention Fusion for Multimodal Speculative Decoding"
title_zh: DREAM：基于精炼目标特征和熵自适应交叉注意力融合的多模态投机解码
authors: "Yunhai Hu, Tianhua Xia, Zining Liu, Rahul Raman, Xingyu Liu, BO BAO, Eric Sather, Vithursan Thangarasa, Sai Qian Zhang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=M5jz47umjR"
tags: ["query:vlm-spec"]
score: 10.0
evidence: 提出了面向视觉语言模型的投机解码框架
tldr: 针对视觉语言模型（VLM）投机解码未充分探索的问题，本文提出DREAM框架，通过交叉注意力机制将目标模型中间特征注入草稿模型提升对齐，基于注意力熵的自适应特征选择优化草稿训练，并采用视觉令牌压缩降低延迟。实验表明DREAM在VLM上实现了高效、准确且并行的多模态解码，显著加速推理。该工作填补了VLM投机解码的空白，为多模态推理加速提供了新方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-m5jz47umjr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 830, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-m5jz47umjr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 520, \"height\": 281, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-m5jz47umjr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1435, \"height\": 567, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-m5jz47umjr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1453, \"height\": 363, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-m5jz47umjr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 1773, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-m5jz47umjr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 939, \"height\": 435, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-m5jz47umjr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 945, \"height\": 424, \"label\": \"Table\"}]"
motivation: 现有投机解码方法主要针对LLM，而VLM中的多模态特性未被充分利用，直接迁移效果不佳。
method: 提出跨模态特征注入、熵引导的草稿训练和视觉令牌压缩三部分，构建VLM专用的投机解码框架。
result: 在多个VLM基准上实现显著加速，同时保持生成质量，验证了方法的有效性。
conclusion: DREAM展示了专门为VLM设计的投机解码可以大幅提升推理效率，拓展了投机解码的应用范围。
---

## Abstract
Speculative decoding (SD) has emerged as a powerful method for accelerating autoregressive generation in large language models (LLMs), yet its integration into vision-language models (VLMs) remains underexplored. We introduce DREAM, a novel speculative decoding framework tailored for VLMs that combines three key innovations: (1) a cross-attention-based mechanism to inject intermediate features from the target model into the draft model for improved alignment, (2) adaptive intermediate feature selection based on attention entropy to guide efficient draft model training, and (3) visual token compression to reduce draft model latency. DREAM enables efficient, accurate, and parallel multimodal decoding with significant throughput improvement. Experiments across a diverse set of recent popular VLMs, including LLaVA, Pixtral, SmolVLM and Gemma3, demonstrate up to 3.6x speedup over conventional decoding and significantly outperform prior SD baselines in both inference throughput and speculative draft acceptance length across a broad range of multimodal benchmarks.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：大规模语言模型（LLM）的推理速度受限于自回归生成过程。投机解码（Speculative Decoding, SD）通过轻量草稿模型快速生成候选令牌并由目标模型并行验证，可显著加速文本型LLM的推理。然而，将SD集成到视觉语言模型（VLM）中的研究尚不充分。VLM需要处理视觉与文本信息的深度融合，直接迁移文本型SD方法会破坏视觉表征的结构信息，导致对齐不佳。
- **动机**：提出一个专门为VLM设计的投机解码框架，解决多模态场景下草稿模型与目标模型的特征对齐、训练效率及推理延迟问题。
- **整体含义**：DREAM通过交叉注意力机制、自适应中间特征选择与视觉令牌压缩，首次系统性地优化了VLM的投机解码过程，在多个流行VLM上实现最高3.6倍加速，并显著优于现有SD基线。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
利用交叉注意力融合目标模型的中间特征到草稿模型，根据注意力熵动态选择最具信息量的中间层进行蒸馏，并压缩视觉令牌以降低草稿模型计算负载，从而实现高效、高质量的多模态投机解码。

### 关键技术细节

1. **交叉注意力机制**  
   - 以草稿模型当前解码层的输出特征 \(E^j\) 作为查询（Query），以目标模型最后一层特征 \(S^L\) 作为键（Key）和值（Value），计算交叉注意力：  
     \[
     Q = E^j W_Q,\quad K = S^L W_K,\quad V = S^L W_V
     \]
     \[
     F = \text{softmax}\left(\frac{QK^\top}{\sqrt{z}}\right) V
     \]
   - 融合后的特征 \(F\) 替代原第一层特征，输入后续解码块。  
   - 后续生成时，拼接已验证的目标特征与最新草稿特征作为新的K/V，支持树状并行解码。

2. **自适应中间特征选择**  
   - 对目标模型每一层计算平均注意力熵 \(AE(\ell) = -\frac{1}{n}\sum_{i,j} A_{\ell,i,j}\log A_{\ell,i,j}\)。  
   - 选择熵最低的层 \(\ell^* = \arg\min_\ell AE(\ell)\)，该层特征富含关键语义且稳定性高。  
   - 使用平滑L1损失将草稿模型第一层特征与目标模型选中层特征对齐：  
     \[
     \mathcal{L}_{\text{intermed}} = \text{smoothL1}(E^m, S^{\ell^*})
     \]

3. **视觉令牌压缩**  
   - 计算目标模型最后一层各令牌的注意力重要性得分（基于注意力矩阵中该令牌对所有其他令牌的注意力权重之和）。  
   - 保留视觉部分中得分最高的部分令牌（如75%），按子采样比率 \(r\) 压缩，大幅减少草稿模型处理的令牌数。

4. **损失函数**  
   包含三项：
   - 特征损失 \(\mathcal{L}_{\text{feat}} = \text{smoothL1}(E^L, S^L)\) 对齐最终层特征。
   - 中间层损失 \(\mathcal{L}_{\text{intermed}}\) 对齐选中的中间层特征。
   - KL散度损失 \(\mathcal{L}_{\text{KL}} = \text{KL}(\text{softmax}(D), \text{softmax}(T))\) 对齐令牌输出分布。  
   总损失：\(\mathcal{L}_{\text{final}} = \lambda_{\text{feat}}\mathcal{L}_{\text{feat}} + \lambda_{\text{intermed}}\mathcal{L}_{\text{intermed}} + \lambda_{\text{KL}}\mathcal{L}_{\text{KL}}\)，实验中设 \(\lambda_{\text{feat}}=\lambda_{\text{intermed}}=0.2\)，\(\lambda_{\text{KL}}=1.0\)。

## 3. 实验设计

### 数据集与基准
- **VLM模型**：LLaVA-v1.6-Vicuna-7B/13B、SmolVLM-2B、Pixtral-12B、Gemma3-12B。
- **多模态任务基准**：MMT-Bench、SEED-Bench-2、ScienceQA、OCRBench、ChartQA、MathVista。
- **对比方法**：SPD、Kangaroo、Medusa、Hydra、EAGLE、EAGLE-2，均为文本型SD方法适配至VLM。
- **评估指标**：
  - 加速比 \(S = t_{\text{AR}} / t_{\text{method}}\)
  - 平均接受令牌长度 \(\tau\)

### 训练设置
- 训练数据集：LLaVA mix665k中的55,000样本 + 每个评估数据集随机抽取1,000样本。
- 优化器：AdamW (\(\beta_1=0.9\), \(\beta_2=0.95\))，学习率 \(3\times10^{-5}\)，梯度裁剪0.5，迭代68,000次。
- 草稿模型结构：初始解码块 + 交叉注意力块 + 最终解码块，参数规模分别为0.65B、0.98B、0.9B、0.28B、0.9B。
- 树结构：\(k=4\)个子节点，深度6，最大草稿长度32令牌。

## 4. 资源与算力

- **训练**：2张NVIDIA A100 80GB GPU，batch size=4，68,000次迭代。
- **评估**：所有模型在单张NVIDIA A100 80GB GPU上运行，KV缓存启用。
- 文中未明确报告总训练时长，但基于迭代次数和硬件可推算。

## 5. 实验数量与充分性

- **主实验**（Table 1）：在5种VLM、6个基准、2种温度（T=0和T=1）下对比6种基线，全面报告加速比和接受长度。
- **消融实验**：
  - 草稿模型架构（Table 2）：移除不同组件、增加交叉注意力块、改变EAGLE-2深度。
  - 中间特征选择策略（图4a）：无中间监督、静态选择25%/50%/75%层 vs 动态熵选择。
  - 树解码 vs 链解码（图4b）。
  - 视觉令牌压缩率（图4c/Table 3）：100%、75%、50%、25%。
  - 损失权重（图4d）：\(\lambda_{\text{feat}}/\lambda_{\text{intermed}}\)从0.05到0.4。
  - 不同温度下的鲁棒性（Table 1包含T=1结果）。
- **充分性与公平性**：所有方法使用相同数据集、训练轮次、学习率、batch size、硬件环境；随机种子固定并报告三次运行平均值；代码开源可复现。

## 6. 主要结论与发现

- DREAM在所有任务和模型上一致取得最高加速比和最长的接受令牌长度，最高达3.6倍加速（LLaVA-13B, MMT-Bench），相比EAGLE-2额外提升20-40%。
- 交叉注意力块是性能提升的关键（移除后性能下降最大），自适应熵选择优于静态层选择。
- 75%视觉令牌压缩率在速度与精度之间取得最佳平衡；过度压缩（50%以下）导致接受长度大幅下降。
- 较大模型（如LLaVA-13B, Pixtral-12B）从DREAM获益更多，因为解码瓶颈更严重。
- 长文本问答任务（如MMT-Bench, ScienceQA）受益最大；精细OCR任务（如MathVista）挑战较大。
- 高温设置（T=1）下性能有所下降，但DREAM仍优于所有基线。

## 7. 优点

- **方法创新性**：首次将交叉注意力、自适应中间特征蒸馏与视觉令牌压缩系统性地结合到VLM投机解码中，解决了多模态特征对齐问题。
- **实验全面性**：覆盖多种模型规模（2B-13B）、多任务、多温度，消融实验充分验证每个组件贡献。
- **公平性**：基线方法均使用相同训练数据和超参数，代码开源，可复现。
- **有效性**：在多个基准上取得显著且一致的加速，验证了方法的通用性和鲁棒性。

## 8. 不足与局限

- **硬件局限**：仅评估NVIDIA A100 GPU，未在CPU、TPU或其他加速器上测试，泛化性未知。
- **评估覆盖**：部分基准（如OCRBench、MathVista）上性能提升有限，表明对细粒度视觉理解任务仍有改进空间。
- **应用风险**：可能被滥用于生成有害的多模态内容，论文虽提及需注意但未提供具体防护措施。
- **训练成本**：需要额外训练草稿模型（2-4天单GPU），且依赖于目标模型中间特征的预计算，对资源要求较高。
- **温度影响**：采样温度升高时加速和接受长度下降，对需要高随机性的场景效果减弱。

（完）
