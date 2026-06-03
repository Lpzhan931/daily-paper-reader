---
title: "ASDSV: Multimodal Generation Made Efficient with Approximate Speculative Diffusion and Speculative Verification"
title_zh: ASDSV：利用近似投机扩散和投机验证实现高效多模态生成
authors: "Kaijun Zhou, Xingyu Yan, Xingda Wei, Xijun Li, Jinyu Gu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=IIGiVRKJYa"
tags: ["query:vlm-spec"]
score: 8.0
evidence: 面向多模态生成的近似投机扩散与投机验证方法
tldr: 受投机解码启发，提出近似投机扩散与投机验证方法（ASDSV），解决扩散模型推理慢的问题。通过近似验证降低连续高维输出验证开销，并在多模态生成任务上实现2-3倍加速，同时保持生成质量。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-iigivrkjya/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1423, \"height\": 805, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-iigivrkjya/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1357, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-iigivrkjya/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1431, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-iigivrkjya/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1413, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-iigivrkjya/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 666, \"height\": 266, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-iigivrkjya/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1427, \"height\": 498, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-iigivrkjya/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 663, \"height\": 267, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-iigivrkjya/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1426, \"height\": 397, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-iigivrkjya/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1424, \"height\": 598, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-iigivrkjya/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1433, \"height\": 862, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-iigivrkjya/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1445, \"height\": 1497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-iigivrkjya/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1445, \"height\": 2155, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-iigivrkjya/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 517, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-iigivrkjya/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 663, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-iigivrkjya/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 724, \"height\": 189, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-iigivrkjya/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 812, \"height\": 187, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-iigivrkjya/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1441, \"height\": 352, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-iigivrkjya/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1143, \"height\": 361, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-iigivrkjya/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 697, \"height\": 149, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-iigivrkjya/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 703, \"height\": 189, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-iigivrkjya/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1032, \"height\": 188, \"label\": \"Table\"}]"
motivation: 扩散模型迭代生成导致高推理延迟，需加速。
method: 将投机解码思想扩展到扩散模型，采用近似验证策略降低连续输出验证成本。
result: 在多模态生成任务上实现2-3倍加速，生成质量与原始扩散模型相当。
conclusion: 投机框架可有效加速扩散模型，为多模态生成提供高效方案。
---

## Abstract
Diffusion in transformer is central to advances in high-quality multimodal generation 
but suffer from high inference latency due to their iterative nature. 
Inspired by speculative decoding's success in accelerating large language models, 
we propose Approximate Speculative Diffusion with Speculative Verification (ASDSV), 
a novel method to enhance the efficiency of diffusion models. 
Adapting speculative execution to diffusion processes presents unique challenges. 

First, the substantial computational cost of verifying numerous speculative steps 
for continuous, high-dimensional outputs makes traditional full verification prohibitively expensive. 
Second, determining the optimal number of speculative steps $K$ 
involves a trade-off between potential acceleration and verification success rates. 

To address these, ASDSV introduces two key innovations: 
1) A speculative verification technique, which leverages the observed temporal correlation between draft and target model outputs, 
efficiently validates $K$ speculative steps by only checking the alignment of the initial and final states, significantly reducing verification overhead. 
2) A multi-stage speculative strategy that adjusts $K$ according to the denoising phase—employing smaller $K$ during volatile early stages 
and larger $K$ during more stable later stages to optimize the balance between speed and quality. 

We apply ASDSV to state-of-the-art diffusion transformers, 
including Flux.1-dev for image generation and Wan2.1 for video generation. 
Extensive experiments demonstrate that ASDSV achieves up to 1.77$\times$-3.01$\times$ speedup 
in model inference with a minimal 0.3\%-0.4\% drop in VBench score, 
showcasing its effectiveness in accelerating multimodal diffusion models without significant quality degradation. 
The code will be publicly available once the acceptance of the paper.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

扩散模型（特别是扩散Transformer）在高质量多模态生成（图像、视频）中取得了显著进展，但其推理延迟极高，主要原因在于需要数十到上百步的迭代去噪过程，且每一步计算量巨大。这严重阻碍了其在实时应用和大规模部署中的实用性。

受大型语言模型中投机解码（Speculative Decoding）成功的启发，作者尝试将投机执行范式引入扩散模型。然而，直接迁移面临两大独特挑战：
- **验证成本高昂**：扩散模型输出是连续、高维的图像/视频数据，验证所有投机步骤的计算开销远大于语言模型的离散token验证，限制了批量大小和分辨率。
- **投机步数K的平衡**：K值越大潜在加速越高，但草稿模型预测与目标模型偏差风险也越大，导致验证失败率上升。

针对上述挑战，论文提出**ASDSV（Approximate Speculative Diffusion with Speculative Verification）**，旨在显著降低扩散模型推理延迟，同时保持接近原始模型的生成质量。

## 2. 论文提出的方法论

### 核心思想
利用扩散过程中草稿模型（轻量级模型）与目标模型（全尺寸模型）之间输出变化的强时序相关性，设计一种**近似投机验证**机制：仅验证投机序列的头尾两步，而非全部K步，从而大幅降低验证计算量。同时，根据去噪阶段动力学特性，采用**多阶段投机策略**，在不同阶段使用不同的K值，以平衡加速比和质量。

### 关键技术细节

- **观察基础**：实验发现，在去噪过程中（尤其是初期N步之后），草稿模型与目标模型相邻步输出差异（L1 loss）的变化趋势高度相似，即 $\|D_i - D_{i-1}\|_1 \approx \|T_i - T_{i-1}\|_1$。这意味着如果头尾输出对齐，中间步也大概率对齐。

- **投机验证规则**：
  1. 草稿模型连续运行K步，产生候选输出 $D_{N+1}, ..., D_{N+K}$。
  2. 目标模型仅对第一步和最后一步进行推理，得到 $T_{N+1}$ 和 $T_{N+K}$。
  3. 若 $\text{L1\_loss}(D_{N+1}, T_{N+1}) \le \delta$ 且 $\text{L1\_loss}(D_{N+K}, T_{N+K}) \le \delta$，则接受所有K步候选；否则拒绝并从 $T_{N+2}$ 开始重新生成。

- **流水线优化**：将当前轮的最后一步验证与下一轮的第一步生成打包成批量推理，进一步减少目标模型调用次数。

- **多阶段投机策略**：
  - **Stage-0**（初始N步）：由目标模型单独运行，建立生成基础。
  - **Stage-1**（早期去噪）：使用较小的K（如2或3），保持高验证成功率，避免误差累积。
  - **Stage-2**（后期去噪）：使用较大的K（如9），最大化加速比。
  
- **加速比理论上限公式**：  
  设总步数为 $T$，草稿模型单步时间 $T_{M_q}$，目标模型单步时间 $T_{M_p}$，成本系数 $c = T_{M_q}/T_{M_p}$，Stage-1和Stage-2分别完成 $\alpha_1$ 和 $\alpha_2$ 轮投机（假设全部成功）。  
  $$ \text{Speedup} = \frac{N + \alpha_1 \gamma_1 + \alpha_2 \gamma_2}{N + 1 + \alpha_1(c\gamma_1 + 1) + \alpha_2(c\gamma_2 + 1)} $$  
  实际加速因验证失败而低于上限，但论文通过保守设置K和阈值δ维持低失败率。

## 3. 实验设计

### 模型与场景
- **图像生成**：Flux.1-dev（12B参数）作为目标模型，Flux-SVD（量化版）作为草稿模型。分辨率512×512。
- **视频生成**：Wan2.1（14B参数）作为目标模型，Wan2.1-1.3B作为草稿模型。分辨率832×480，帧数81（主要实验）。

### 数据集与评估指标
- **图像**：COCO Captions 2014（生成10k张图）。指标：FID（与原始模型输出对比）、CLIP score、LPIPS、PSNR、Inception Score（IS）。
- **视频**：VBench数据集（生成2k个视频）。指标：VBench score（视频质量）、LPIPS、PSNR、SSIM（与原始模型输出对比）。
- **效率**：FLOPs、推理延迟（秒），加速比。

### 对比方法
- **TeaCache**：基于缓存的加速方法（fast/slow两种变体）。
- **Sparse VideoGen**：架构优化方法（视频生成，sparsity 0.10/0.20）。
- **草稿模型直接生成**（Flux-lite, Flux-SVD等蒸馏/量化模型）。
- **改进型草稿模型基线**（将Stage-0后的步骤全部由草稿模型生成）。

### ASDSV变体
- **ASDSV-slow**：更保守，Stage-1使用小K，启用验证，追求高质量。
- **ASDSV-fast**：跳过验证，假设始终接受，使用固定大K，追求高速度。
- **ASDSV-medium**（消融中）：中间配置。

### 实现细节
- 总去噪步数：50步。
- 阈值δ：图像0.02，视频0.2。
- 初始N：图像8%～15%步数，视频10%～15%步数。
- γ1：图像3，视频2；γ2：均为9。
- 单卡NVIDIA A800 GPU，PyTorch 2.6.0，CUDA 12.4。

## 4. 资源与算力

论文明确说明：“We measure the latency per sample on a single NVIDIA A800 GPU using Pytorch 2.6.0 and CUDA 12.4。” 所有推理实验均在单张A800上完成，无多卡分布式训练或推理。未提及训练成本（方法无额外训练）。因此，算力条件为单A800 GPU，相对适中。

## 5. 实验数量与充分性

论文进行了多组实验，覆盖以下方面：

| 实验类型 | 内容 | 数量/规模 |
|---------|------|-----------|
| 主要对比 | 图像/视频生成效率与质量（表1、2） | 图像10k张，视频2k个 |
| 与草稿模型对比 | 直接使用蒸馏/量化模型（表5、6） | 图像10k张，视频2k个 |
| 验证策略消融 | fast/medium/slow三种配置 | 视频生成，定性+定量 |
| 分辨率/长度扩展 | 不同帧数、分辨率（图7） | 4个场景 |
| γ1、γ2、δ消融 | Wan2.1模型，暴力搜索与迭代调整（表3、4） | 每个设置200个视频 |
| 多种子稳定性 | 3个不同种子，2000图/500视频（表7、8） | 统计标准差 |
| 多阶段策略对比 | 不同warmup策略（图9） | 定性比较 |
| FID对真实图像 | COCO Captions（表9） | 10k张 |

**评价**：实验设计全面，覆盖了效率、质量、消融、稳定性、扩展性等多个维度。对比方法包括当前主流加速方法（TeaCache、Sparse VideoGen），且设置了合理的公平对比（保持原始模型输出为ground truth）。实验规模足够，统计量报告较完整（除未提供误差棒外）。因此，实验充分且客观。

## 6. 论文的主要结论与发现

1. **ASDSV在图像和视频生成上均能实现显著加速**：ASDSV-fast在Wan2.1上达到3.01×加速，ASDSV-slow达到1.77×加速，同时VBench分数仅下降0.3%–0.4%，质量保持性优于TeaCache和Sparse VideoGen。

2. **近似投机验证有效**：通过仅验证头尾两步，大幅降低验证计算量，且基于时序相关性的假设成立，验证失败率可控。

3. **多阶段策略优于固定K**：Stage-1小K避免早期误差，Stage-2大K实现高加速，整体质量-速度平衡最佳。

4. **ASDSV优于直接使用草稿模型**：对比蒸馏/量化后的直接生成，ASDSV在相似度指标（FID、LPIPS、PSNR）上显著更优，且加速比不损失。

5. **对分辨率与视频长度稳健**：在480P/720P、41/141帧等多种设置下均保持1.7–3.0×加速，说明方法泛化性好。

## 7. 优点

- **创新性**：首次将投机解码扩展到高分辨率图像/视频扩散模型，并针对连续输出设计近似验证，避免了传统全验证的高额开销。
- **实用性**：利用社区已有的轻量级变体作为草稿模型（如Wan2.1-1.3B、Flux-SVD），无需额外训练，即插即用。
- **质量保持**：在加速2–3倍的同时，VBench等参考指标下降极小，视觉对比显示与原始模型几乎无异，优于缓存类和架构优化类方法。
- **设计合理**：观察到时序相关性现象并加以利用；多阶段策略契合扩散过程动力学，理论加速公式推导清晰。
- **实验全面**：覆盖多种模态、分辨率、帧数，并与多个强基线进行公平对比，消融实验细致。

## 8. 不足与局限

- **依赖草稿模型效率**：成本系数c（草稿/目标单步时间比）在实验中为0.60（图像）和0.19（视频），远大于语言模型（<0.05）。若目标模型本身已高度优化或草稿模型不够快，加速收益有限。论文也指出“optimization of optimal draft model is orthogonal”。
- **验证失败处理简单**：当前策略是丢弃所有后续K步并重新生成，未利用部分有效信息。作者提到可引入二分查找等更智能的恢复策略，但未实现。
- **硬件敏感性**：ASDSV-fast的FLOPs最低但延迟并非最小，因为量化草稿模型在A800上未达到理想加速，暗示对硬件（如支持低精度计算的GPU）依赖。
- **未与并行化方法结合**：论文提到分布式并行（如PipeFusion、DistriFusion）正交，未探索集成，可能错失进一步加速潜力。
- **实验误差棒缺失**：主要结果未报告标准差或置信区间，一定程度上影响统计显著性结论。
- **不考虑社会影响细节**：仅简要提及环境效益，未深入讨论潜在的公平性、偏见等问题，但作为加速方法合理。

（完）
