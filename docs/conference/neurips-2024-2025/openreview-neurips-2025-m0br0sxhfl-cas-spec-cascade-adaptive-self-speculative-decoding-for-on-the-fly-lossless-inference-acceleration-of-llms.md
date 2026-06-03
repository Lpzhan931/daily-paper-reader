---
title: "CAS-Spec: Cascade Adaptive Self-Speculative Decoding for On-the-Fly Lossless Inference Acceleration of LLMs"
title_zh: CAS-Spec：级联自适应自投机解码用于LLM在线无损推理加速
authors: "Zhiyuan Ning, Jiawei Shao, Ruge Xu, Xinfei Guo, Jun Zhang, Chi Zhang, Xuelong Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=m0bR0sxhfL"
tags: ["query:llm"]
score: 8.0
evidence: 级联自适应自投机解码用于无损LLM推理加速
tldr: 本文提出CAS-Spec方法，通过动态可切换推理加速策略构建级联猜测模型，实现无需训练的在线自投机解码。该方法结合层级级联和自适应切换，在多种任务上取得比现有自投机方法更大的加速比，且不损失质量。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-m0br0sxhfl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1445, \"height\": 485, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-m0br0sxhfl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1396, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-m0br0sxhfl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 587, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-m0br0sxhfl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1187, \"height\": 928, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-m0br0sxhfl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1409, \"height\": 774, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-m0br0sxhfl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1386, \"height\": 377, \"label\": \"Table\"}]"
motivation: 现有自投机解码加速效果有限，而级联方法训练成本高。
method: 利用动态可切换推理加速策略构建级联猜测模型，无需专门训练。
result: 在多个基准上实现比现有自投机方法更高的加速比。
conclusion: 级联自适应自投机解码是一种实用且高效的无损加速方案。
---

## Abstract
Speculative decoding has become a widely adopted as an effective technique for lossless inference acceleration when deploying large language models (LLMs).
While on-the-fly self-speculative methods offer seamless integration and broad utility, they often fall short of the speed gains achieved by methods relying on specialized training.
Cascading a hierarchy of draft models promises further acceleration and flexibility, but the high cost of training multiple models has limited its practical application.
In this paper, we propose a novel Cascade Adaptive Self-Speculative Decoding (CAS-Spec) method which constructs speculative draft models by leveraging dynamically switchable inference acceleration (DSIA) strategies, including layer sparsity and activation quantization.
Furthermore, traditional vertical and horizontal cascade algorithms are inefficient when applied to self-speculative decoding methods.
We introduce a Dynamic Tree Cascade (DyTC) algorithm that adaptively routes the multi-level draft models and assigns the draft lengths, based on the heuristics of acceptance rates and latency prediction.
Our CAS-Spec method achieves state-of-the-art acceleration compared to existing on-the-fly speculative decoding methods, with an average speedup from $1.1\times$ to $2.3\times$ over autoregressive decoding across various LLMs and datasets.
DyTC improves the average speedup by $47$\% and $48$\% over cascade-based baseline and tree-based baseline algorithms, respectively.
CAS-Spec can be easily integrated into most existing LLMs and holds promising potential for further acceleration as self-speculative decoding techniques continue to evolve.

---

## 论文详细总结（自动生成）

# CAS-Spec: Cascade Adaptive Self-Speculative Decoding 论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）的自回归生成过程推理延迟高、计算成本大。投机解码（Speculative Decoding）通过小型“草案模型（draft model）”快速生成多个候选 token，再由目标模型并行验证，可无损加速。但现有方法面临两难：
  - 传统投机解码需要单独训练草案模型，带来额外训练开销和部署复杂度。
  - 自投机解码（Self-Speculative Decoding, SSD）利用目标模型自身（如跳过部分层、量化等）构建草案，无需训练，但加速效果有限，甚至不如简单的检索式方法（如 Prompt Lookup Decoding, PLD）。
  - 级联投机解码（Cascade Speculative Decoding）通过多个草案模型分层生成，可进一步提升加速，但训练多个草案模型的成本过高，限制了实际应用。

- **整体含义**：本文旨在无需训练多个草案模型的前提下，利用目标模型自身的动态可切换推理加速策略（Dynamically Switchable Inference Acceleration, DSIA）构建级联草案模型，并通过自适应调度算法实现媲美甚至超越级联方法的加速效果。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- **CAS-Spec框架**：利用目标模型 \( M_t \) 本身的 DSIA 策略（如层稀疏、激活量化等）在线创建多个“虚拟”草案模型 \( \{M_{d1}, M_{d2}, ..., M_{dn}\} \)，并以一个极快的底层草案模型（如 PLD）作为最终阶段，形成层次化级联。所有草案模型无需额外训练。
- **Dynamic Tree Cascade (DyTC) 算法**：在生成过程中，动态选择草案模型、分配草案长度，并在 token 树结构中进行自适应路由，以最大化预期加速比。算法基于在线估计的接受率和延迟预测进行启发式优化。

### 关键技术细节
- **DSIA策略**：论文主要使用 **层稀疏（Layer Sparsity）** 作为案例（如跳过一半 Transformer 层），也可扩展至早期退出（Early-Exiting）、激活量化等。通过设置不同稀疏度（如 \( M_{d1} \) 稀疏度 0.4，\( M_{d2} \) 稀疏度 0.6）创建多个草案模型。
- **接受率（Acceptance Rate）α**：草案 token 被目标模型接受的概率。
- **成本系数（Cost Coefficient）c**：草案模型单步推理时间与目标模型单步推理时间的比值。
- **预期加速比（Expected Walltime Improvement Factor, EWIF）**：衡量给定草案配置下的理论加速倍数。论文推导了垂直级联（VC）和水平级联（HC）的 EWIF 公式，并据此建立“有效边界”（图1b、1c），判断中间草案模型是否能带来增益。
- **DyTC 算法流程**（Algorithm 1）：
  - 维护一个 token 树，每个叶节点有累积接受率 \( P_{acc} \)。
  - 每次选择累积接受率最高的叶节点进行扩展。
  - 调用 `FindBestConfigurationForStep`（Algorithm 2）在当前叶节点选出最优的草案模型配置 \( S^* \) 和草案长度 \( k^* \)，优化目标为：
    \[
    \max_{S, k} T_s(S, k) = \frac{\hat{\alpha}(1 - \hat{\alpha}^k)}{1 - \hat{\alpha}} + \hat{\alpha}^k \hat{\alpha}_{dn}}{\hat{c} k + \hat{c}_{dn}}
    \]
    其中 \( \hat{\alpha} \)、\( \hat{c} \) 为当前草案模型的在线估计值，\( \hat{\alpha}_{dn}, \hat{c}_{dn} \) 为底层草案模型参数。
  - 支持树并行：一次扩展多个兄弟节点，共享同一个草案长度。
- **在线估计更新**：接受率通过指数移动平均（EMA）更新，窗口大小 H=20，衰减因子 λ=0.7；延迟预测使用贝叶斯线性回归。

## 3. 实验设计

- **数据集 / 场景**：采用 Spec-Bench 基准，包含多轮对话（MT-Bench）、翻译（Trans）、摘要（Summary）、问答（QA）、数学推理（Math）、检索增强生成（RAG）等六个子任务，每个任务生成 1024 个新 token。
- **Benchmark**：以标准自回归解码的 wall time 为基准（Speedup = AR time / speculative decoding time）。
- **对比方法**：
  - 无需训练的方法：PLD、SWIFT、Lade、Lookahead。
  - 需要训练的方法：Kangaroo（双早期退出 + 适配器）、EAGLE/EAGLE2、Medusa、标准投机解码（使用更小的 Vicuna 68M 模型）。
- **模型**：Vicuna-7B-v1.3、Vicuna-13B-v1.3、Vicuna-33B-v1.3、Llama-2-7B（附录提及）。
- **硬件**：NVIDIA H100 80GB GPU。

## 4. 资源与算力

- **算力使用**：论文未给出具体的训练 GPU 数量和训练时长。CAS-Spec 本身**无需训练**（training-free），仅需在线推理阶段执行动态切换，计算开销很低。对比的 Kangaroo 方法需要训练适配器，但论文仅引用了其公开权重（仅提供 7B 和 13B），未给出训练资源。
- **实验运行**：所有实验在单张 NVIDIA H100 80GB 上完成，具体每项实验耗时未报告。

## 5. 实验数量与充分性

- **实验数量**：
  - **主实验（表1）**：在 3 种模型（7B、13B、33B）×6 个子任务 + MT-Bench 共 7 个指标上对比 CAS-Spec 与 PLD、SWIFT、Lade、Kangaroo 等，共 3×7=21 组数据。
  - **消融实验（图3）**：在 Vicuna-7B 上，比较不同级联策略（LS、VC、HC、VC+HC、Tr、Tr+VC、DyTC）的加速比。
  - **与训练方法的比较（附录表2）**：在 Vicuna-7B 上对比了 PLD、SWIFT、CAS-Spec、标准投机解码、Medusa、EAGLE、EAGLE2。
  - **理论分析模拟（图1b、1c）**：数值仿真验证有效边界。
- **充分性与公平性**：
  - 覆盖了多种模型规模和任务类型，对比方法涵盖无需训练和需要训练的代表性方法。
  - 所有实验均为**无损解码**（输出与自回归解码一致）。
  - 未报告误差棒或统计显著性测试，但结果趋势一致且稳定。
  - 消融实验充分验证了 DyTC 算法相比传统级联和树算法的优势。

## 6. 论文的主要结论与发现

- **CAS-Spec 在无训练投机解码方法中达到 SOTA**：在 Vicuna-7B/13B/33B 上，CAS-Spec 取得 1.1×～2.3× 的加速比，全面优于 PLD、SWIFT、Lade 等无训练方法。
- **DyTC 算法显著提升加速效果**：相比传统垂直+水平级联（VS+HC）基线，平均加速比提升 47%；相比 SWIFT 的树算法基线，提升 48%。
- **级联构建的有效性**：通过 DSIA 策略（如层稀疏）构建的多个草案模型可以在合适的调度下超过单个强检索模型（PLD）的性能。
- **动态自适应是关键**：DyTC 根据实时接受率和延迟预测进行路由和长度分配，比静态策略更优。
- **与训练方法的差距**：CAS-Spec 仍落后于 EAGLE/EAGLE2 等需要大量训练的方法，但差距小于其他无训练方法。

## 7. 优点

- **完全无需训练**：利用目标模型自身的 DSIA 策略即时创建草案模型，避免了额外训练数据和计算成本，易于部署。
- **无损加速**：验证过程保证生成结果与原始模型完全一致。
- **动态自适应**：DyTC 算法在线调整草案选择和长度，适应不同生成上下文和硬件特性。
- **通用性强**：可集成到大多数现有 LLM 中，支持多种 DSIA 策略（层稀疏、量化、早期退出等）。
- **理论指导实践**：通过推导 EWIF 和有效边界，为级联设计提供了理论依据。
- **实验充分**：在多种模型和任务上进行了系统对比，消融实验和与训练方法的比较完整。

## 8. 不足与局限

- **依赖 DSIA 策略质量**：CAS-Spec 的加速效果受限于所选 DSIA 策略的效率和接受率。当前主要验证了层稀疏，其他策略（如量化、激活稀疏）仅讨论未实验。
- **在线估计开销**：DyTC 需要维护接受率估计和延迟预测，虽轻量但仍有额外运行时开销，且需要短时预热才能达到最佳性能。
- **批量大小敏感**：动态调度的优势在 batch size 较大时会减弱（文中明确指出）。
- **兼容性有限**：无法与依赖目标模型隐藏状态的 SOTA 方法（如 EAGLE-3、Medusa）结合，因为这些方法要求使用未修改的隐藏状态。
- **未与所有最新方法对比**：例如未与 TriForce、MagicDec 等针对长上下文的方法比较（仅在附录提及）。
- **未提供误差/置信区间**：结果仅报告单一数值，未进行多次实验或统计波动分析。
- **硬件局限**：实验仅在高端 GPU H100 上运行，未评估在低端硬件或边缘设备上的表现。

（完）
