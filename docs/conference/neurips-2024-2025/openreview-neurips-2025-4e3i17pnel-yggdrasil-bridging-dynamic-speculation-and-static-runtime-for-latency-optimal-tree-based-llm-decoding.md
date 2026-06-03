---
title: "Yggdrasil: Bridging Dynamic Speculation and Static Runtime  for Latency-Optimal Tree-Based LLM Decoding"
title_zh: Yggdrasil：连接动态推测与静态运行时的延迟最优树状LLM解码
authors: "Yue Guan, Changming Yu, Shihan Fang, Weiming Hu, Zaifeng Pan, Zheng Wang, Zihan Liu, Yangjie Zhou, Yufei Ding, Minyi Guo, Jingwen Leng"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=4E3I17pNEl"
tags: ["query:llm"]
score: 7.0
evidence: 面向LLM的延迟最优树状投机解码系统
tldr: 针对投机解码中动态推测与静态运行时失配导致性能次优的问题，本文提出Yggdrasil系统，通过等增长树结构兼容静态图、延迟感知目标优化草稿选择、阶段式调度降低开销。支持未修改的LLM，在多种硬件上实现最高3.98倍加速。该方法将系统级优化与投机解码结合，为LLM服务提供了高效的加速方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 664, \"height\": 277, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 724, \"height\": 314, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 726, \"height\": 305, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 382, \"height\": 257, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 345, \"height\": 251, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 601, \"height\": 263, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 751, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 511, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1453, \"height\": 297, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1421, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 707, \"height\": 216, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 739, \"height\": 215, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 706, \"height\": 220, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 611, \"height\": 232, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 649, \"height\": 186, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 676, \"height\": 192, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-4e3i17pnel/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 655, \"height\": 268, \"label\": \"Table\"}]"
motivation: 现有投机解码系统因动态推测与静态运行时假设不匹配，性能未达最优。
method: 引入等增长树结构、延迟感知优化目标与阶段调度，实现系统级联合设计。
result: 在多种硬件上获得最高3.98倍加速，显著优于现有基线。
conclusion: Yggdrasil通过协同设计解决了系统级瓶颈，提升了树状投机解码的实用性和性能。
---

## Abstract
Speculative decoding improves LLM inference by generating and verifying multiple tokens in parallel, but existing systems suffer from suboptimal performance due to a mismatch between dynamic speculation and static runtime assumptions. We present Yggdrasil, a co-designed system that enables latency-optimal speculative decoding through context-aware tree drafting and compiler-friendly execution. Yggdrasil introduces an equal-growth tree structure for static graph compatibility, a latency-aware optimization objective for draft selection, and stage-based scheduling to reduce overhead. Yggdrasil supports unmodified LLMs and achieves up to $3.98\times$ speedup over state-of-the-art baselines across multiple hardware setups.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

**问题：** 现有投机解码（Speculative Decoding）系统在LLM推理加速中性能次优，根本原因在于**动态草稿算法**与**静态编译时运行时假设**之间不匹配。动态树结构导致算子形状可变，无法充分利用深度学习编译器的图融合、内核调优和内存规划等静态优化；同时现有方法以平均接受长度（AAL）为优化目标，忽略了非均匀验证开销和CPU-GPU协调成本。

**背景：** 投机解码通过并行生成和验证多个候选token来提高吞吐，但现有系统（如SpecInfer、Sequoia、vLLM-Spec）要么牺牲编译优化支持动态性，要么牺牲动态性兼容编译优化，导致端到端延迟次优。

**整体含义：** 本文提出**Yggdrasil**系统，通过**算法-运行时协同设计**，在保持动态上下文感知能力的同时兼容静态图编译优化，实现延迟最优的树状投机解码。

## 2. 论文提出的方法论

### 核心思想
Yggdrasil基于三个核心技术：
1. 延迟感知优化目标
2. 等增长树结构（Equal-Growth Tree, EGT）
3. 阶段式调度运行时

### 关键技术细节

#### 2.1 延迟感知优化目标
传统方法以AAL近似速度up，但忽略了草稿开销和验证延迟特性。本文提出更准确的加速比公式：

\[
\text{Speedup} = \frac{\text{AAL}(W_{\text{draft}}, D_{\text{draft}}, W_{\text{verify}}) \cdot T_{\text{verifier}}(1)}{\sum D_{\text{draft}} T_{\text{drafter}}(W_{\text{draft}}) + T_{\text{verifier}}(W_{\text{verify}})}
\]

其中 \(W_{\text{draft}}\) 为草稿宽度，\(D_{\text{draft}}\) 为草稿深度，\(W_{\text{verify}}\) 为验证宽度。该目标直接反映实际系统延迟。

#### 2.2 等增长树（EGT）
EGT将树结构搜索分解为三个贪心子决策：
- **草稿深度预测**：使用轻量级多头深度预测器（两层MLP编码器+多个预测头），基于目标模型最后一层token嵌入预测期望接受长度，从而提前实例化所有草稿图，消除逐token控制流。
- **草稿宽度选择**：在预测深度下，选择使加速比目标最大化的宽度，贪心地在树中添加叶子，优先选择路径期望AAL增益最大的位置。
- **验证宽度剪枝**：草稿完成后，通过动态规划求解最大价值子树问题，选取满足验证预算的子树以最大化加速比。

EGT保证了静态算子形状，兼容编译时图优化。

#### 2.3 阶段式调度
针对投机解码中CPU-GPU协调开销，提出两种提前执行策略：
- **提前尾草稿（Ahead-of-Time Tail Draft）**：不再条件性地草稿最后一个token，而是提前为整个候选序列草稿，接受后直接复用结果，消除条件分支。
- **提前头草稿（Ahead-of-Time Head Draft）**：在上一轮奖励草稿后立即发出头草稿，与验证阶段重叠。

通过离线profile指导的网格搜索，在依赖图中找到最优执行计划。

## 3. 实验设计

### 数据集/场景
- **语言建模数据集**：C4、Wikipedia、CNNDaily
- **采样温度**：0 和 0.6

### Benchmark
- **目标模型**：Llama-2-7B、Llama-2-13B
- **草稿模型**：Llama-68M、Llama-160M
- 主要指标：**每token延迟（TPOT）**

### 对比方法
- SpecInfer（算法中心）
- Sequoia（静态树）
- vLLM-Spec（系统优化）
- 同时对比了序列投机解码、N-way树等基线

### 实验场景
- **GPU设备**：NVIDIA A100 (80G) 和 A40
- **环境**：CUDA 11.7 + TorchInductor编译器

## 4. 资源与算力

论文中明确说明实验使用**NVIDIA A100 (80G)** 和 **A40** GPU，CPU为Intel(R) Xeon(R) E5-2620 v3 @ 2.40GHz。未报告训练深度预测器所需的精确GPU数量和训练时长，仅提到使用校准数据集离线训练，未提及整体算力消耗的定量数据。

## 5. 实验数量与充分性

### 实验组数及覆盖
- **端到端性能对比**：4种模型组合（7B-68M, 7B-160M, 13B-68M, 13B-160M）在3个数据集（C4, Wikitext, CNN）上测试，共12个组合，含A100和A40两种硬件。
- **树结构对比**：在Wikitext上对比不同验证数下AAL和加速比。
- **优化分解**：逐步应用5个优化（O1～O5）并报告加速比。
- **灵敏度分析**：EGT参数（宽度、深度、验证数）、优化目标（加速 vs AAL）、采样温度等。
- **消融实验**：固定深度 vs 深度预测器、速度up目标 vs AAL目标。

### 充分性与公平性
- 实验覆盖多种模型规模、硬件、数据集，结果具有统计显著性（静态平均值）。
- 与SOTA基线（SpecInfer, Sequoia, vLLM-Spec）对比，基线实现来自原论文或开源代码。
- 所有方法在相同硬件和编译器条件下测试，确保公平。
- 但未报告误差条或置信区间，统计显著性声明不够严谨。

## 6. 论文的主要结论与发现

- Yggdrasil在A100上最高实现**3.98x加速**，在A40上实现**2.76x加速**，优于所有基线。
- 树结构对比：EGT动态调整宽度始终优于Sequoia静态树，验证了上下文感知的重要性。
- 优化分解显示：图编译优化贡献最大（2.775倍），阶段调度额外贡献1.21倍，深度预测器贡献1.10倍。
- 延迟感知目标比AAL目标额外提升8%性能。
- 低温度采样下性能更优（草稿与目标模型更一致），但Yggdrasil在所有温度下均优于Sequoia（平均1.49x）。

## 7. 优点

- **算法-运行时协同设计**：首次系统性地将投机解码的动态算法与编译优化结合，解决长期存在的冲突。
- **延迟感知优化目标**：从系统角度建模，避免AAL代理偏差。
- **等增长树**：兼顾动态性和编译友好性，设计巧妙。
- **阶段调度**：针对投机解码特有的CPU-GPU协调开销提出创新性提前执行策略。
- **支持未修改模型**：无需修改模型架构，通用性强。
- **广泛的实验验证**：涵盖多种模型、数据集、硬件，与多个SOTA对比，结果令人信服。

## 8. 不足与局限

- **未考虑批处理场景**：实验仅在单请求独占GPU的延迟优化设置下进行，不适用于批量在线服务（吞吐导向）。论文承认此局限，并指出联合批调度是未来方向。
- **缺少统计分析**：未报告误差条或置信区间，可能影响结论的统计显著性。
- **深度预测器训练细节不足**：未报告训练数据量、训练时间、超参数等，可复现性受限。
- **未评估更大模型**：目标模型最大为13B，草稿模型最大160M，未测试更大规模（如70B/340M）的效果。
- **未考虑内存/能耗**：优化目标仅为延迟，未评估加速带来的额外资源消耗或能耗。
- **仅限语言模型**：未在多模态或其他架构上验证。
- **代码未开源**：论文声称接受后开源，当前不可复现。

（完）
