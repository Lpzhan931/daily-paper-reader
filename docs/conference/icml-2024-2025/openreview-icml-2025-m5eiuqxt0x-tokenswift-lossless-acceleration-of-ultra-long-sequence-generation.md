---
title: "TokenSwift: Lossless Acceleration of Ultra Long Sequence Generation"
title_zh: TokenSwift：超长序列生成的无损加速
authors: "Tong Wu, Junzhe Shen, Zixia Jia, Yuxuan Wang, Zilong Zheng"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=m5EIuQxt0x"
tags: ["query:llm"]
score: 8.0
evidence: 无损加速超长序列生成，解决KV缓存管理问题
tldr: 超长序列生成（高达100K tokens）因频繁模型重载、动态KV管理和重复生成而低效。TokenSwift框架通过优化这些瓶颈实现无损加速，实验显示显著提升生成速度且不损害模型质量，适用于超长上下文的推理加速。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-m5eiuqxt0x/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 849, \"height\": 430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m5eiuqxt0x/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1785, \"height\": 841, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m5eiuqxt0x/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 615, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m5eiuqxt0x/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 607, \"height\": 420, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m5eiuqxt0x/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 596, \"height\": 768, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m5eiuqxt0x/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1251, \"height\": 658, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m5eiuqxt0x/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1057, \"height\": 1224, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m5eiuqxt0x/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1425, \"height\": 682, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m5eiuqxt0x/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1417, \"height\": 657, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m5eiuqxt0x/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1419, \"height\": 647, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-m5eiuqxt0x/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 831, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m5eiuqxt0x/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 829, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m5eiuqxt0x/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1770, \"height\": 685, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m5eiuqxt0x/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1763, \"height\": 284, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m5eiuqxt0x/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 852, \"height\": 458, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m5eiuqxt0x/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 853, \"height\": 290, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m5eiuqxt0x/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 852, \"height\": 518, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m5eiuqxt0x/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 854, \"height\": 361, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m5eiuqxt0x/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 853, \"height\": 611, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m5eiuqxt0x/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1767, \"height\": 622, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m5eiuqxt0x/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1195, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m5eiuqxt0x/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 557, \"height\": 390, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m5eiuqxt0x/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 896, \"height\": 640, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m5eiuqxt0x/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1229, \"height\": 446, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m5eiuqxt0x/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1314, \"height\": 450, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m5eiuqxt0x/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1135, \"height\": 408, \"label\": \"Table\"}]"
motivation: 超长序列生成中频繁模型重载、动态KV管理和重复生成导致低效。
method: 提出TokenSwift框架，针对性优化模型重载、KV管理和消除重复生成。
result: 在超长序列生成任务上实现显著无损加速。
conclusion: TokenSwift有效解决超长序列生成效率问题，保持模型质量。
---

## Abstract
Generating ultra-long sequences with large language models (LLMs) has become increasingly crucial but remains a highly time-intensive task, particularly for sequences up to 100K tokens. While traditional speculative decoding methods exist, simply extending their generation limits fails to accelerate the process and can be detrimental. Through an in-depth analysis, we identify three major challenges hindering efficient generation: frequent model reloading, dynamic key-value (KV) management and repetitive generation. To address these issues, we introduce TokenSwift, a novel framework designed to substantially accelerate the generation process of ultra-long sequences while maintaining the target model’s inherent quality. Experimental results demonstrate that TokenSwift achieves over $3 \times$ speedup across models of varying scales (1.5B, 7B, 8B, 14B) and architectures (MHA, GQA). This acceleration translates to hours of time savings for ultra-long sequence generation, establishing TokenSwift as a scalable and effective solution at unprecedented lengths.

---

## 论文详细总结（自动生成）

### 论文核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）生成超长序列（例如 100K tokens）时极为耗时，例如 LLaMA3.1-8B 生成 100K tokens 需要约 5 小时。现有投机解码（Speculative Decoding，SD）方法主要针对短序列设计，直接扩展到超长序列会因 KV 缓存预算限制、频繁模型重载等问题而失败或收益甚微。
- **整体含义**：为了实现超长序列的无损加速，需要克服三大挑战：**频繁模型重载**（每次 token 生成需完整加载模型，I/O 瓶颈大于计算）、**动态 KV 缓存管理**（KV 对随序列增长，导致加载时间剧增）、**重复内容生成**（超长序列中模型易陷入重复循环，降低质量）。论文提出的 TokenSwift 框架旨在同时解决这些挑战，实现模型无关、训练开销极低的无损加速。

### 论文方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：TokenSwift 是一种自投机解码（self-speculative decoding）框架，将目标模型自身同时作为草稿模型和验证模型。通过多头并行草稿生成、token 复用、动态 KV 缓存管理以及上下文惩罚采样，显著减少模型重载次数、降低 KV 缓存开销、抑制重复生成，从而加速超长序列生成。
- **关键技术细节**：
  - **多 token 自草稿生成**：借鉴 Medusa 思路，在 LLM 最后一层后添加 γ 个额外线性层（文中 γ=3），通过残差连接（hᵢ = fᵢ(hᵢ₋₁) + hᵢ₋₁）依次生成多个隐藏表示，再经 LM Head 输出 γ+1 个 logits。这样一次前向传递即可得到多个候选 token。
  - **Token 复用（Token Reutilization）**：维护一个 n-gram 频率表（n=4），从已生成序列中提取高频 n-gram。在每次草稿阶段，以第一个候选 token 为起始，检索 top-k 个最频繁的 n-gram 作为额外草稿候选。随着生成长度增加，n-gram 池变大，复用率提高。
  - **树注意力（Tree-based Attention）**：利用简单的 3 叉树结构（配置 [1,3,3,3]）组织所有候选 token，在验证阶段并行计算目标模型的 logits，保证一次前向即可验证多个候选。
  - **动态 KV 缓存管理**：在草稿阶段，固定保留前 |S| 个 KV 对（S 为初始缓存大小），其余位置按重要性分数排序，只保留前 |B| - |S| 个最重要的 KV 对（|B| 为预算上限）。重要性分数基于 QKᵀ 的点积，针对 GQA 架构，将每个 K 对应的 Q 组进行聚合。当新 token 生成超出预算时，从草稿缓存中替换最不重要的 KV 对；若替换超过 |S| 位置，则重新计算所有 token 的重要性并重建缓存。
  - **上下文惩罚（Contextual Penalty）**：在采样时，对最近 W 个 token（文中 W=1024）的 logits 施加惩罚系数 θ（θ > 1，文中 θ=1.2），降低这些 token 被再次选中的概率，从而抑制局部重复。公式中 I(l) = θ 若 l ∈ W，否则 1.0，然后 softmax 得到惩罚后的概率。
  - **随机 n-gram 选择**：当多个候选 n-gram 通过验证（与目标 token 精确匹配）时，随机选择一个作为输出，增加多样性。
- **算法流程**（文字描述）：
  1. 预填充目标模型，得到完整 KV 缓存 C_full。
  2. 初始化部分 KV 缓存 C_p：保留前 |S| 对，再从剩余中选取 top (|B|-|S|) 个重要 KV 对。
  3. 循环直到生成足够 token：
     - 若剩余未更新 token 数超过 |B|-|S|，则动态更新 C_p。
     - 使用部分缓存 C_p 进行多头并行草稿生成（经上下文惩罚），得到概率 p_≤3。
     - 利用解码树 T 构造 g 组候选 draft token。
     - 复用 n-gram：检索 top-k 个以 argmax p₀ 为起始的 4-gram 作为额外候选。
     - 将所有候选（共 k+g 组）送入目标模型（使用完整缓存 C_full）并行验证，得到目标概率 q_i。
     - 从 q_i 采样得到目标 token。
     - 随机选择最长有效匹配的 draft 片段作为输出（验证为 lossless）。
     - 更新 n-gram 频率表、完整 KV 缓存和部分 KV 缓存。

### 实验设计

- **数据集**：PG-19（长序列书籍语料库），测试集用于推理，训练集（前 8K token 的部分）用于训练线性层。
- **基准模型（Baseline）**：
  - **TriForce***：原始 TriForce 的改进版，采用动态 KV 更新（原版静态更新无法加速 100K 生成）。
  - **Medusa***：基于 Medusa 训练食谱，并采用 TokenSwift 的验证方法，保证无损。
  - **Autoregressive (AR)**：标准自回归生成，作为速度基准。
  - 注意：MagicDec 在 batch size=1 时对 GQA 模型无加速，故未作为 baseline。
- **评估指标**：
  - **接受率（Acceptance Rate α）**：所有草稿 token 中被接受的比例（式 4）。
  - **加速比（Speedup ̂）**：AR 延迟与 TokenSwift 延迟的比值（式 5）。
  - **多样性（Distinct-n）**：n-gram 的多样性，值越高重复越少。
- **对比方法**：TriForce*、Medusa* 与 TokenSwift 在不同生成长度（20K/40K/60K/80K/100K）和不同前缀长度（2K/4K/8K）下比较。

### 资源与算力

- **GPU 型号**：NVIDIA A100-SXM4-80GB（单卡推理，4 卡训练）。
- **训练**：仅训练 3 个额外线性层，LLM 参数冻结。训练步数：LLaMA3.1-8B 和 YaRN-LLaMA2 使用 200 步（梯度累积 10，每 GPU batch size 3）；Qwen2.5 系列使用 600 步（每 GPU batch size 1）。学习率：LLaMA3.1-8B 为 5e-3，其余为 1e-3。无需大量调参。
- **训练数据**：来自 PG-19 训练集中长度超过 8K 的样本的第一 8K token。
- **推理**：单张 A100 80GB 进行超长序列生成。

### 实验数量与充分性

- **主要实验**：在 YaRN-LLaMA2-7B-128k（MHA）和 LLaMA3.1-8B（GQA）上测试了 5 种生成长度（20K～100K）和 3 种前缀长度（2048/4096/8192），共约 5×3×2=30 组主实验，每组重复 5 次取平均和标准差。结果呈现在 Table 3。
- **扩展实验**：在 Qwen2.5-1.5B/7B/14B 三种不同规模模型上测试（Table 4），显示速度优势随模型规模增大而增大。
- **消融实验**：
  - Token 复用（k=20 与 k=0 对比，Figure 3）
  - KV 更新策略（Full Cache / Partial Cache / Dynamic Partial Cache，Table 5）
  - 上下文惩罚（不同采样方法 top-p/min-p/η-sampling 下有无惩罚，Table 6）
  - 树结构配置（Table 7）
  - n-gram 候选数量 k（Figure 4）
  - 惩罚值 θ（Table 8）
  - 温度（Table 9）
  - 前缀长度（Table 14）
  - 惩罚窗口 W（Table 15, 16）
  - 采样方法（Table 13）
- **充分性评价**：实验设计较为全面，覆盖了不同模型架构（MHA、GQA）、不同模型规模（1.5B～14B）、不同生成长度和前缀长度，并且消融实验深入探讨了各个关键组件的影响。但需要注意：所有实验仅在 PG-19 数据集上进行，未涉及其他领域（如代码、对话等），泛化性有限。对比了 TriForce* 和 Medusa* 两种改进版方法，但未与最新单点方法（如 Sequoia、EAGLE-2）直接比较。此外，实验仅使用 batch size=1，未评估批次推理场景下的表现。

### 论文主要结论与发现

1. TokenSwift 在生成 100K tokens 时，在 LLaMA3.1-8B 上实现了 3× 以上的加速（从 5 小时缩短至 90 分钟，Figure 1）。
2. 加速效果随着生成长度增加而更加明显（接受率随 n-gram 池扩大而提高）。
3. 对模型规模具有鲁棒性：更大模型（如 14B）加速比更高（最高达 3.34×），节省时间可达 5.54 小时。
4. 上下文惩罚显著提升生成多样性（Distinct-n 从 0.12 提升至 0.69），只牺牲约 8% 的速度。
5. 动态 KV 缓存管理在平衡接受率和计算开销方面优于全缓存和静态部分缓存。
6. TokenSwift 与多种采样方法（top-p、min-p、η-sampling）兼容，且实现无损（与目标模型输出分布一致）。

### 优点

- **创新点**：首次将自投机解码、n-gram 复用、动态 KV 缓存和上下文惩罚系统性结合，专门针对超长序列生成进行优化。
- **效率**：仅需训练少量线性层（无额外 LLM 训练），推理时无需多模型切换，减少 I/O 瓶颈。
- **鲁棒性**：在多个模型规模、架构和前缀长度下表现一致，且随序列变长加速比提升。
- **实用性**：生成 100K 序列时间从数小时降至几十分钟，显著提升实际部署可行性。
- **可扩展性**：方法模型无关，可应用于未来更大模型。

### 不足与局限

- **实验范围有限**：仅使用 PG-19（书籍文本）数据集，未在代码、对话、科学文献等多样化场景验证。
- **基线对比不充分**：未与最新投机解码方法（如 Sequoia、EAGLE-2、Speculative Decoding with Draft Model）直接比较，仅采用了改进版 TriForce* 和 Medusa*（均基于开源代码调整）。
- **仅 batch size=1**：未探索高吞吐服务场景，与 MagicDec 的对比缺失，且 MagicDec 在 batch>1 时可能更优。
- **重复抑制依赖超参数**：上下文惩罚的 θ 和 W 需手动设定（文中 θ=1.2, W=1024），未见自适应调整策略。
- **n-gram 复用可能引入偏差**：高频 n-gram 可能来自训练数据分布，若生成内容与训练数据差异大，则复用效率可能下降。
- **验证假设未量化**：论文声称“lossless”但仅在验证时通过精确匹配保证分布一致，未进行显著性检验或理论证明（附录 A 给出了一般 SD 的无损证明，但未专门证明 TokenSwift 的变体是否严格保持分布）。实际上，由于随机 n-gram 选择和上下文惩罚改变了采样分布，严格意义上并非“lossless”与原模型分布一致，而是“保持目标模型内在质量”。论文也明确“保持目标模型的内在质量”，故这一点可接受。
- **KV 缓存更新策略可能限制最坏情况**：若序列长度极长且注意力模式变化剧烈，频繁重计算重要性可能导致额外开销，论文未分析极端情况。

（完）
