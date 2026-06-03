---
title: "GRIFFIN: Effective Token Alignment for Faster Speculative Decoding"
title_zh: GRIFFIN：面向更快速投机解码的有效令牌对齐
authors: "Shijing Hu, Jingyang Li, Xingyu Xie, Zhihui Lu, Kim-chuan Toh, Pan Zhou"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=JwnAItQF9v"
tags: ["query:llm"]
score: 7.0
evidence: 通过令牌对齐改进LLM投机解码
tldr: 针对投机解码中训练与解码阶段的令牌错位问题，本文提出GRIFFIN框架，包含令牌对齐训练策略（损失掩码机制）和令牌对齐草稿模型（引入输入令牌校正特征）。在LLaMA、Vicuna等多个LLM上的实验表明，该方法有效缓解了错位，提升了推理速度。该工作专注于改进投机解码的核心对齐问题，适用于多种LLM。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-jwnaitqf9v/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1515, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jwnaitqf9v/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1277, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jwnaitqf9v/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1435, \"height\": 789, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-jwnaitqf9v/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1434, \"height\": 1217, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jwnaitqf9v/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1437, \"height\": 304, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jwnaitqf9v/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1435, \"height\": 319, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jwnaitqf9v/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1436, \"height\": 323, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jwnaitqf9v/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1435, \"height\": 272, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jwnaitqf9v/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1434, \"height\": 284, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jwnaitqf9v/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1436, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jwnaitqf9v/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1437, \"height\": 255, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jwnaitqf9v/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 735, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jwnaitqf9v/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1438, \"height\": 249, \"label\": \"Table\"}]"
motivation: 现有投机解码方法存在训练与解码阶段的令牌错位，限制了性能。
method: 设计损失掩码机制排除高错位令牌，并构建令牌对齐草稿模型校正特征不一致。
result: 在多个LLM上实现更快的推理速度，验证了对齐机制的有效性。
conclusion: GRIFFIN通过解决令牌错位问题，提升了投机解码的实用性和效率。
---

## Abstract
Speculative decoding accelerates inference in large language models (LLMs) by generating multiple draft tokens simultaneously. However, existing methods often struggle with token misalignment between the training and decoding phases, limiting their performance. To address this, we propose GRIFFIN, a novel framework that incorporates a token-alignable training strategy and a token-alignable draft model to mitigate misalignment.
The training strategy employs a loss masking mechanism to exclude highly misaligned tokens during training, preventing them from negatively impacting the draft model's optimization. The token-alignable draft model introduces input tokens to correct inconsistencies in generated features.
Experiments on LLaMA, Vicuna, Qwen and Mixtral models demonstrate that GRIFFIN achieves an average acceptance length improvement of over 8\% and a speedup ratio exceeding 7\%, outperforming current speculative decoding state-of-the-art methods. Our code and GRIFFIN's draft models will be released publicly in https://github.com/hsj576/GRIFFIN.

---

## 论文详细总结（自动生成）

# 论文《GRIFFIN: Effective Token Alignment for Faster Speculative Decoding》详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究背景**：大型语言模型（LLM）在推理时采用自回归解码，每步生成一个 token 需要一次完整前向传播，速度慢。投机解码（Speculative Decoding）通过轻量草稿模型并行生成多个候选 token，再交由目标 LLM 批量验证，从而加速推理。
- **核心问题**：现有方法（如 EAGLE、EAGLE2、HASS）在训练和推理阶段存在严重的**令牌错位（Token Misalignment）**：训练时草稿模型使用目标模型提供的真实特征和真实 token，而推理时只能使用自身生成的特征和前序草稿 token，导致特征错位和令牌错位，且误差随生成步长累积。HASS 部分缓解了特征错位，但忽略令牌错位，在多步训练中性能饱和甚至退化。
- **整体含义**：令牌错位是投机解码中未被充分认识的瓶颈，解决该问题可显著提升接受长度和加速比。论文提出 GRIFFIN 框架，通过令牌对齐训练和令牌对齐草稿模型系统性地缓解此问题，在多个 LLM 上取得 SOTA 加速效果。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：同时解决特征错位和令牌错位。一是通过**令牌对齐训练（Token-Alignable Training, TAT）** 在训练中引入损失掩码，只对与真实 token 在 top-k 预测中匹配的对齐 token 进行反向传播，避免高错位 token 破坏优化；二是设计**令牌对齐草稿模型（Token-Alignable Draft Model, TAD）**，包含两个新模块：
  - **Token-Guided Fusion（TGF）**：在特征融合中显式引入 token 嵌入，通过“嵌入融合→归一化与升维→非线性精化与残差”三步，使生成特征更接近目标模型分布。
  - **Token-Enhanced Head（TEH）**：双头设计，分别输出预测特征（用于 token 预测）和回归特征（用于后续前向传递），解耦 token 预测与特征生成的目标。

- **关键技术细节**：
  - **多步训练**：训练时逐步让草稿模型依赖自身生成的特征和 token（而非真实值），模拟推理行为。第一步（n=1）无错位，使用标准损失。第 n 步（n≥2）引入累积对齐掩码 \(m_t = \prod_{i=t-n+1}^{t-1} \bar{m}_i\)，其中 \(\bar{m}_i\) 指示 ground-truth token 是否在 draft token 的 top-k 中。损失函数为 \(L^{(n)}_M = \frac{1}{\sum m_t} \sum m_t \cdot \ell(\bar{x}_t, x_t, \bar{F}_t, F_t)\)。
  - **TGF 模块**：输入特征 \(F\) 和 token 嵌入 \(x\)，经 MLP 融合得 \(h\)；对 \(h\) 和 \(x\) 分别层归一化后拼接，用 Up Projector 升维至 4d；经 SiLU 激活后 Down Projector 降维回 d，与 \(h\) 残差连接。
  - **TEH 模块**：借鉴 FSPAD 的双头结构，分离预测特征 \(\bar{F}^P_{t+1}\) 和回归特征 \(\bar{F}^R_{t+1}\)。

- **算法流程**（文字说明）：训练阶段，每步用当前草稿模型生成 n 个 draft 特征和 token，计算每个 token 是否在 top-k 对齐，生成掩码，仅对齐位置参与损失计算；推理阶段，草稿模型使用 TGF 和 TEH 结构，配合动态草稿树（EAGLE-2 风格）生成候选序列，目标模型单次验证接受。

## 3. 实验设计

- **数据集与场景**：
  - 对话：MT-Bench（多轮对话）
  - 代码生成：HumanEval
  - 数学推理：GSM8K
  - 训练数据：ShareGPT 数据集
- **Benchmark**：以标准自回归解码为基线（加速比 1.00×），评估指标为**加速比（Speedup Ratio, SR）** 和**接受长度（Acceptance Length, τ）**。温度设为 T=0 和 T=1。
- **对比方法**：
  - 无训练的方法：SPS、PLD、Lookahead
  - 基于草稿模型的方法：Medusa、EAGLE、EAGLE-2、EAGLE-3、FSPAD、HASS
- **测试模型**：LLaMA2-Chat 7B/13B、LLaMA3-Instruct 8B/70B、Vicuna-1.5 7B、Qwen2-Instruct 7B、Mixtral-8x7B-Instruct-v0.1
- **主要实验结果**：GRIFFIN 在所有模型和数据集上均取得最高 SR 和 τ。例如 LLaMA2-7B 上平均加速比 3.28×（T=0），比 EAGLE-2 高约 18%，比 HASS 高约 7%；接受长度 5.44（T=0），比 HASS 高约 8%。在 Mixtral-8x7B 上加速比仍比 HASS 高 6.6%。
- **消融实验**：
  - 移除 TAT 或 TAD 均显著下降，两者同时移除下降最大。
  - 比较不同 top-k 值（1,3,5,10），k=3 最佳。
  - 比较训练步数 n=1~5，n=3 后性能小幅提升，n=5 接近饱和。
  - TGF 消融：将二次融合的输入替换为 F（特征）或 h（融合特征），均低于用 x（token 嵌入），证明 token 引导是关键。
  - TAD 组件消融：移除 TEH 或 TGF，性能均下降，TGF 影响更大。
  - 还对 TGF 扩张维度、模型大小、吞吐量（vLLM 集成实验）等进行对比。

## 4. 资源与算力

- **实验设备**：除 LLaMA3-70B 和 Mixtral-8x7B 需 2 张 A100-80G GPU 外，其余模型使用单张 NVIDIA A100 80G GPU。
- **训练开销**：
  - GRIFFIN 采用与 HASS 相同的三步训练策略。对 7B/13B/70B 模型，HASS 约需 130/220/500 A100 GPU 小时；GRIFFIN 约需 150/250/600 A100 GPU 小时，略高但可接受。
  - 草稿模型仅训练一次，推理阶段贡献更大。GRIFFIN 相比 HASS 在推理加速上提升约 8%，额外训练成本值得。
- **模型大小**：GRIFFIN 草稿模型参数约为 0.41B（7B 目标）、0.42B（8B）、0.65B（13B）、2.07B（70B），0.45B（Mixtral-8x7B），比 EAGLE-2/HASS 大约 0.17B~1.08B，但与 FSPAD 相近。

## 5. 实验数量与充分性

- **实验数量**：论文包含 10 张表格（主表 1 + 消融表 2-10），涉及 8 个模型、3 个数据集、2 个温度、多种 baseline、多种消融（TAT、TAD、top-k、训练步数、TGF 结构、扩张维度、吞吐量等），共约 20 余组对比实验。
- **充分性**：实验覆盖了主流的 LLM 系列和多种任务类型，消融实验较全面，验证了各组件必要性。对比 baseline 包括最新方法（EAGLE-3、HASS、FSPAD）。但对大型模型（如 70B、MoE）只做了部分数据集测试。对更大 batch size 的吞吐量实验限于链长 2 的串行推测（vLLM 限制），未完全体现树结构优势。整体实验设计客观公平，使用相同训练数据和超参数，代码将开源。
- **公平性**：对于未公开草稿模型参数的方法（如 HASS 在 Vicuna/Qwen/Mixtral 上、FSPAD、EAGLE-3），作者自行训练并尽量匹配原始设置。训练数据统一使用 ShareGPT，避免数据偏差。

## 6. 主要结论与发现

1. **令牌错位是限制投机解码性能的关键因素**，现有方法对此关注不足。
2. **GRIFFIN 的令牌对齐训练（TAT）和令牌对齐草稿模型（TAD）能有效缓解令牌错位**，使接受长度和加速比超过 SOTA。
3. **Token-Guided Fusion 模块中显式使用 token 嵌入比只使用特征更有效**，这是 TGF 优于其他融合方式的原因。
4. **多步训练对性能增益边际递减**，但 GRIFFIN 在 n=3 后仍能缓慢提升，优于 HASS 的饱和现象。
5. **GRIFFIN 在不同架构（LLaMA、Vicuna、Qwen、Mixtral）和温度下均表现稳定**，体现了通用性。
6. **特征级损失（ℓ1 距离）对稳定训练仍重要**，去除后加速比下降约 10-15%（附录 I 对比 EAGLE-3）。

## 7. 优点

- **问题定义新颖**：首次明确揭示并专门解决投机解码中的令牌错位问题，区别于以往仅关注特征错位的工作。
- **方法设计精巧**：
  - TAT 采用 top-k 对齐掩码和累积对齐掩码，模拟推理行为，且不破坏预计算特征。
  - TGF 通过 token 引导融合，显式利用 token 信息纠正特征不一致，结构轻量但效果显著。
- **实验充分且公平**：覆盖多种模型、任务、温度，消融实验验证各组件贡献，对比 baseline 包括最新 SOTA（EAGLE-3、HASS 等），训练条件一致。
- **实用性强**：草稿模型仅需一次训练，推理加速明显，代码将开源，易于复现和应用。
- **扩展性好**：在 MoE 架构（Mixtral）上仍有稳定加速，且可在 vLLM 等框架中集成。

## 8. 不足与局限

- **训练开销略高**：相比 EAGLE-2，GRIFFIN 的三步训练需要更多 GPU 小时（约 15% 额外时间），但推理加速收益可弥补。
- **草稿模型参数增大**：GRIFFIN 草稿模型比 EAGLE-2/HASS 大约 0.17B~1.08B 参数，可能对内存受限部署带来挑战。
- **多步训练收益递减**：训练步数 n=4 和 5 时提升很小，可能存在最优步数选择问题。
- **MoE 模型加速受限**：在 Mixtral-8x7B 上所有投机解码方法加速比均较低（约 2.5×），GRIFFIN 虽优于 HASS，但仍低于非 MoE 模型，MoE 架构下的验证开销是限制因素。
- **实验覆盖局限**：
  - 未测试更大模型（如 130B+）或更小模型（如 1B 量级）。
  - 吞吐量实验中 vLLM 集成不支持树结构，仅用串行推测链长 2，未充分体现树结构优势。
  - 未在真实服务场景（多用户并发）下测试延迟分布。
- **偏差风险**：训练仅在 ShareGPT 数据集上，可能使草稿模型偏向对话风格，对其他领域（如科学推理、长文档）泛化性未验证。
- **理论分析不足**：未提供令牌错位的理论界或收敛性分析，主要为经验验证。

（完）
