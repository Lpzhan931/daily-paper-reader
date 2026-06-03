---
title: "Medusa: Simple LLM Inference Acceleration Framework with Multiple Decoding Heads"
title_zh: Medusa：基于多解码头的简单LLM推理加速框架
authors: "Tianle Cai, Yuhong Li, Zhengyang Geng, Hongwu Peng, Jason D. Lee, Deming Chen, Tri Dao"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=PEpbUobfJv"
tags: ["query:llm"]
score: 8.0
evidence: Medusa：多解码头加速LLM推理，无需独立草稿模型
tldr: LLM自回归解码每步需加载全模型参数，造成瓶颈。Medusa通过在模型上添加多个解码头来并行预测后续多个token，并采用树注意力机制构建候选序列，无需额外草稿模型。在多个模型和任务上测试，实现了2-3倍的推理加速，且生成质量几乎无损。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 812, \"height\": 671, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 810, \"height\": 534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1618, \"height\": 599, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1607, \"height\": 493, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 814, \"height\": 459, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1024, \"height\": 535, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1727, \"height\": 535, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 802, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1251, \"height\": 779, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1253, \"height\": 748, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1250, \"height\": 748, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1252, \"height\": 748, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1253, \"height\": 778, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1252, \"height\": 746, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1252, \"height\": 785, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1251, \"height\": 745, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1252, \"height\": 750, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1255, \"height\": 756, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1254, \"height\": 747, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1252, \"height\": 745, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1210, \"height\": 743, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 823, \"height\": 783, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 719, \"height\": 774, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-pepbuobfjv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 827, \"height\": 254, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pepbuobfjv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 819, \"height\": 149, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pepbuobfjv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 787, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pepbuobfjv/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1403, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pepbuobfjv/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1566, \"height\": 546, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pepbuobfjv/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1679, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pepbuobfjv/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1663, \"height\": 340, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pepbuobfjv/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1707, \"height\": 307, \"label\": \"Table\"}]"
motivation: 投机解码需单独维护草稿模型，增加复杂度。
method: 在LLM基础上添加并行解码头，利用树注意力生成候选并验证。
result: 在多种LLM上实现2-3倍加速，且生成质量与原始模型相当。
conclusion: Medusa提供了一种简单高效且无需额外模型的推理加速方案。
---

## Abstract
Large Language Models (LLMs) employ auto-regressive decoding that requires sequential computation, with each step reliant on the previous one's output. This creates a bottleneck as each step necessitates moving the full model parameters from High-Bandwidth Memory (HBM) to the accelerator's cache. While methods such as speculative decoding have been suggested to address this issue, their implementation is impeded by the challenges associated with acquiring and maintaining a separate draft model. In this paper, we present Medusa, an efficient method that augments LLM inference by adding extra decoding heads to predict multiple subsequent tokens in parallel. Using a tree-based attention mechanism, Medusa constructs multiple candidate continuations and verifies them simultaneously in each decoding step. By leveraging parallel processing, Medusa reduces the number of decoding steps required. We present two levels of fine-tuning procedures for Medusa to meet the needs of different use cases: Medusa-1: Medusa is directly fine-tuned on top of a frozen backbone LLM, enabling lossless inference acceleration. Medusa-2: Medusa is fine-tuned together with the backbone LLM, enabling better prediction accuracy of Medusa heads and higher speedup but needing a special training recipe that preserves the model's capabilities. Moreover, we propose several extensions that improve or expand the utility of Medusa, including a self-distillation to handle situations where no training data is available and a typical acceptance scheme to boost the acceptance rate while maintaining generation quality. We evaluate Medusa on models of various sizes and training procedures. Our experiments demonstrate that Medusa-1 can achieve over 2.2$\times$ speedup without compromising generation quality, while Medusa-2 further improves the speedup to 2.3-2.8$\times$.

---

## 论文详细总结（自动生成）

# 论文《Medusa：基于多解码头的简单LLM推理加速框架》中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）采用自回归解码，每步生成一个 token，需要将全部模型参数从高带宽内存（HBM）加载到加速器缓存，导致严重的内存带宽瓶颈，计算单元利用率低下。
- **现有方案的不足**：投机解码（Speculative Decoding）通过一个独立的小型草稿模型生成候选序列，再由原始模型验证，可以加速推理。但该方法需要单独训练和维护一个草稿模型，且在多模型分布式系统中集成复杂，增加了部署难度和资源开销。
- **本文目标**：提出一种简单、高效、无需额外草稿模型的 LLM 推理加速框架 Medusa，通过添加多解码头并行预测多个后续 token，结合树注意力机制并行验证候选序列，大幅减少解码步骤，同时保持生成质量。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 2.1 核心思想
- 在原始 LLM 的最后隐藏状态上添加多个**解码头（Medusa Heads）**，每个解码头预测未来固定偏移位置的 token（例如第 k 个头预测位置 t+k+1 的 token）。所有头的预测并行进行，通过**树注意力（Tree Attention）**构造多个候选连续序列，并在一次前向传播中同时验证，选择最长的可接受前缀作为本次解码输出。

### 2.2 关键技术细节
- **Medusa Head 结构**：每个头为单层前馈网络 + 残差连接：  
  `p_t^(k) = softmax(W2^(k) · (SiLU(W1^(k)·h_t) + h_t))`  
  其中 W2^(k) 初始化为原始语言模型头的参数，W1^(k) 初始为零，确保初始预测与原始模型一致。
- **树注意力机制**：将多个候选 token 序列组织成树结构（每个候选对应一条从根到叶子的路径），通过修改因果注意力掩码，使得每个 token 只能访问其前缀 token，从而一次性处理所有候选，无需增大 batch size。候选数量为各头 top-s_k 预测的笛卡尔积。
- **训练策略**：
  - **Medusa-1**：冻结主干 LLM，仅训练 Medusa Heads，使用加权交叉熵损失（权重 λ_k = 0.8^k）。
  - **Medusa-2**：联合训练 Medusa Heads 和主干 LLM，采用三项关键策略：
    1. **组合损失**：保留原始 LLM 的交叉熵损失（λ_0 权重）。
    2. **差异化学习率**：Medusa Heads 的学习率是主干模型的 4 倍。
    3. **头部预热（Heads Warmup）**：先单独训练 Heads，再联合训练，避免初期大梯度扭曲主干参数。
- **典型接受方案（Typical Acceptance）**：替代投机解码中的拒绝采样，根据原始模型预测概率和熵设置阈值，接受“典型” token（概率大于 min(ϵ, δ·exp(-H))），保证至少接受第一个 token（贪心解码），提高接受率且保持生成质量。
- **自蒸馏（Self-Distillation）**：当无可用训练数据时，使用原始模型自身生成训练集，并通过 LoRA 微调主干，将蒸馏损失（KL 散度）加入训练，避免质量下降。
- **优化树结构**：根据校准数据集统计各头各 top 预测的准确率，贪心选择贡献最大的节点加入树，最大化期望接受长度，在固定节点预算下提升加速效果。

## 3. 实验设计：数据集、场景、基准和对比方法

### 3.1 数据集与场景
- **训练数据**：
  - Vicuna-7B/13B：使用 ShareGPT 数据集（约 60k 样本，序列长度 4096）。
  - Vicuna-33B、Zephyr-7B：使用自蒸馏方法，种子数据集为 ShareGPT 和 UltraChat，生成约 100k 样本（序列长度 2048）。
- **评估基准**：MT-Bench（多轮对话基准），包含 8 个类别（人文、推理、角色扮演、写作、STEM、数学、编程、提取）。部分消融实验使用 Writing 和 Roleplay 类别。额外在 AlpacaEval 上验证。

### 3.2 对比方法
- 基线：默认 Huggingface 实现（无加速）。
- 投机解码（Speculative Decoding）：使用开源草稿模型（Llama-68M, Llama-160M, Tiny-Llama, Tiny-Vicuna）对 Vicuna-7B/13B/33B 进行对比。
- 消融实验：对比 Medusa-1 vs Medusa-2、有无树注意力、不同树配置、典型接受 vs 拒绝采样 vs 贪心采样、不同典型接受阈值。

## 4. 资源与算力

- **文中明确说明**：
  - Medusa-1 在 Vicuna-7B 上：单张 NVIDIA A100 PCIe GPU，训练 5 小时（60k ShareGPT 样本）。
  - Medusa-2 联合训练：使用 QLoRA（4-bit 量化主干），Global batch size=64，峰值学习率 5e-4（主干）和 2e-3（Heads），预热 40 步，在单卡或多卡（未明确说明 GPU 数量）上完成。
  - 自蒸馏训练：使用 LoRA（未量化），序列长度 2048，batch size=128，峰值学习率 1e-4（主干），预热 20 步。
  - 投机解码：使用开源草稿模型，利用 torch.compile() 加速，但未报告具体训练成本（论文指出预训练草稿模型需 275 A100 GPU 小时，如 SpecInfer）。
- **硬件型号**：主要为 NVIDIA A100-80GB-PCIe，部分消融实验还使用了 A40、A6000 进行算子级 roofline 分析。

## 5. 实验数量与充分性

- **实验数量**：涵盖了多种模型（Vicuna-7B/13B/33B、Zephyr-7B，共计 4 个），每个模型都在 MT-Bench 上评测了 8 个类别，并报告了整体速度、加速比、质量（GPT-4 评分）。另在 AlpacaEval 上进行了补充验证。
- **消融实验**：
  - 树注意力节点数对加速比和速度的影响（0~250 候选 token，密集 vs 稀疏树）。
  - 典型接受阈值（ϵ 从 0.01 到 0.25）对加速比和评分的 trade-off。
  - Medusa-1 vs Medusa-2 vs 直接联合微调（对比质量与加速比）。
  - 各技术贡献累积表（表 3：从基础 Medusa 头到优化树再到 Medusa-2，逐次显示加速比提升）。
  - Roofline 模型分析：在不同 GPU、不同 batch size、不同序列长度下，分析 Medusa 如何提升操作强度（Operational Intensity）和 FLOP/s。
  - 投机解码对比：在三个 Vicuna 模型上搜索最佳草稿模型和 γ 参数。
- **充分性与公平性**：
  - 实验设计较为全面，覆盖了不同规模、不同训练方式（公开数据、自蒸馏）的模型。
  - 对比投机构解码时，使用了多种开源草稿模型并调优了 γ 参数，尽量公平。
  - 采用 GPT-4 作为评判员评估生成质量，减少主观偏差。
  - 主要局限性：所有实验默认 batch size=1（本地个人使用场景），未深入探讨多 batch 场景（但指出可推广）。另外，自蒸馏训练可能导致与原始模型分布有偏差，需通过知识蒸馏损失弥补。

## 6. 论文的主要结论与发现

- Medusa 可在不损失生成质量的前提下，实现 **2.3–2.8 倍** 的端到端推理加速（Medusa-2 比 Medusa-1 更高）。
- Medusa-1（冻结主干）简单高效，单卡即可训练，速度提升约 2.2 倍；Medusa-2（联合训练）进一步提升 Head 预测准确率，加速比达到 2.83 倍。
- 树注意力机制是关键：通过构造多个候选并并行验证，显著提高每次解码步骤可接受的 token 数（加速率 3+）。优化稀疏树结构比密集树更高效，在更少节点下达到相近或更好的加速比。
- 典型接受方案在保持生成质量（接近随机采样）的同时，比拒绝采样获得更高加速比，且温度越高效果越明显。
- 自蒸馏方法有效解决了无训练数据场景，在 Vicuna-33B 和 Zephyr-7B 上取得良好加速（2.35x 和 2.66x），质量轻微下降或持平。
- Medusa 在编程和提取类别上加速比最高（3.29x 和 3.62x），显示其对结构化输出的优势。

## 7. 优点：方法或实验设计的亮点

1. **无需草稿模型**：避免了独立训练和维护一个小模型，系统集成简单，适合分布式环境。
2. **参数效率极高**：Medusa Heads 仅为一层前馈网络，参数量极小，训练迅速。
3. **训练友好**：Medusa-1 可在单张消费级 GPU 上量化训练，Medusa-2 也支持 LoRA/QLoRA，资源需求低。
4. **树注意力创新**：将候选组织成树，通过注意力掩码实现并行验证，避免 batch 扩展带来的额外开销。
5. **典型接受方案**：基于信息论准则，兼顾效率和质量，无需严格匹配原始分布。
6. **自蒸馏管道**：解决模型不可知训练数据的问题，利用原始模型生成数据并结合 KL 蒸馏，保持生成质量。
7. **实验分析深入**：提供了详细的 roofline 建模，从硬件角度解释了 Medusa 如何将内存带宽受限操作转变为计算受限操作，指导了最优候选 token 数量的选择。
8. **比较全面**：与投机解码进行了系统化对比，覆盖了不同草稿模型和参数。

## 8. 不足与局限

1. **实验场景局限**：所有实验在 batch size=1 下进行，未全面验证多 batch 下效果（论文声称可推广，但未提供结果）。
2. **模型覆盖有限**：主要测试了 Vicuna 系列和 Zephyr（基于 Llama 架构），对其他架构（如 GPT、PaLM、T5）的泛化性未知。
3. **自蒸馏质量权衡**：对于 Vicuna-33B，加速比（2.35x）低于其他模型（2.83x），且质量略有下降（+0.05），表明自蒸馏可能面临分布不匹配问题。
4. **典型接受方案缺乏理论保证**：与拒绝采样不同，典型接受无法保证输出分布与原始模型完全一致，虽然实际质量相近，但在严格要求分布匹配的场景（如科学研究）中可能不够稳妥。
5. **树优化依赖校准数据集**：优化稀疏树需要额外的校准数据计算各头准确率，若校准集分布与目标分布不同，可能影响效果。
6. **长序列性能退化**：roofline 分析显示，当序列长度增加或 batch size 增大时，加速比下降，主要是因为注意力计算开销增长。论文未深入探讨如何缓解。
7. **对模型规模的依赖**：实验表明 Medusa 在 7B 和 13B 上效果最好，33B 上加速比略低，可能随模型增大而收益减少（参数量增大导致内存带宽压力更大，Heads 预测准确率下降）。

（完）
