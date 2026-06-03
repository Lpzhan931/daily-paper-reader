---
title: "MoESD: Unveil Speculative Decoding's Potential for Accelerating Sparse MoE"
title_zh: MoESD：揭示投机解码加速稀疏MoE的潜力
authors: "Zongle Huang, Lei Zhu, ZongYuan Zhan, Ting Hu, Weikai Mao, Xianzhi Yu, Yongpan Liu, Tianyu Zhang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=FAeU7516MR"
tags: ["query:llm"]
score: 7.0
evidence: 稀疏MoE LLM的投机解码加速
tldr: 针对MoE大模型，本文首次证明在中等批量大小下，稀疏MoE模型比稠密模型从投机解码中获益更多。随着MoE稀疏化趋势，受益范围更广。通过定量分析，揭示了投机解码在MoE推理加速中的潜力。该工作扩展了投机解码的应用领域，为高效MoE推理提供了新方向。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1426, \"height\": 402, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1424, \"height\": 402, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 498, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1424, \"height\": 783, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1445, \"height\": 1427, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1432, \"height\": 716, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1456, \"height\": 368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1438, \"height\": 905, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1437, \"height\": 894, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1436, \"height\": 903, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1435, \"height\": 894, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1436, \"height\": 902, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1436, \"height\": 894, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1436, \"height\": 903, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1436, \"height\": 894, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1437, \"height\": 903, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1436, \"height\": 893, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1436, \"height\": 903, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1437, \"height\": 893, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1437, \"height\": 903, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1437, \"height\": 894, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1437, \"height\": 903, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1436, \"height\": 894, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1437, \"height\": 903, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1436, \"height\": 894, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1437, \"height\": 903, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1437, \"height\": 894, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-faeu7516mr/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1437, \"height\": 903, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-faeu7516mr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1440, \"height\": 342, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-faeu7516mr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1443, \"height\": 466, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-faeu7516mr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1426, \"height\": 1011, \"label\": \"Table\"}]"
motivation: 投机解码被认为仅对稠密模型有效，其在MoE上的潜力尚未被充分探索。
method: 理论分析和实验验证投机解码在MoE上的加速效果，并量化稀疏度与加速的关系。
result: 在中等批量下MoE受益更大，且稀疏度越高越有利于投机解码加速。
conclusion: 投机解码是加速稀疏MoE推理的有效手段，值得进一步研究。
---

## Abstract
Large Language Models (LLMs) have achieved remarkable success across many applications, with Mixture of Experts (MoE) models demonstrating great potential. Compared to traditional dense models, MoEs achieve better performance with less computation. Speculative decoding (SD) is a widely used technique to accelerate LLM inference without accuracy loss, but it has been considered efficient only for dense models. In this work, we first demonstrate that, under medium batch sizes, MoE surprisingly benefits more from SD than dense models. Furthermore, as MoE becomes sparser -- the prevailing trend in MoE designs -- the batch size range where SD acceleration is expected to be effective becomes broader. To quantitatively understand tradeoffs involved in SD, we develop a reliable modeling based on theoretical analyses. While current SD research primarily focuses on improving acceptance rates of algorithms, changes in workload and model architecture can still lead to degraded SD acceleration even with high acceptance rates. To address this limitation, we introduce a new metric 'target efficiency' that characterizes these effects, thus helping researchers identify system bottlenecks and understand SD acceleration more comprehensively. For scenarios like private serving, this work unveils a new perspective to speed up MoE inference, where existing solutions struggle. Experiments on different GPUs show up to 2.29x speedup for Qwen2-57B-A14B at medium batch sizes and validate our theoretical predictions.

---

## 论文详细总结（自动生成）

# 论文《MoESD: Unveil Speculative Decoding’s Potential for Accelerating Sparse MoE》中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：投机解码（Speculative Decoding, SD）被广泛用于无损加速大语言模型推理，但先前观点认为SD对混合专家模型（MoE）效果不佳，因为验证多token时会激活更多专家，导致内存访问增加、验证时间显著变长，因此SD被认为只对稠密模型有效。
- **核心问题**：探索在何种条件下SD能够有效加速MoE模型，并量化其加速潜力，挑战传统认知。
- **整体含义**：本文首次证明在中等批量大小下，MoE反而比稠密模型从SD中获益更多；且随着MoE稀疏化（每个token激活专家数减少），SD有效的批量范围变得更宽。这为MoE推理加速提供了新视角，尤其适用于私有化部署、延迟敏感或显存受限等场景。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
### 2.1 核心思想
- 关键洞察：当批量大小中等时，单个解码步已激活所有专家，验证多个草稿token不会增加额外专家参数加载成本；MoE越稀疏，每个专家每次参数加载处理的token数越少，算术单元利用率更低，从而为SD创造了更大的加速空间。

### 2.2 关键技术细节
- **目标效率（Target Efficiency）新指标**：定义为 `T_T(B,1)/T_T(B,γ)`，衡量目标模型在单token前向与多token前向的时间比，用于隔离算法因素，揭示系统瓶颈（如计算-bound vs 内存-bound）对SD加速的影响。
- **激活专家数量建模**：给定t个token，期望激活专家数 N(t)=E·[1-((E-K)/E)^t]，其中E为总专家数，K为每个token激活专家数。据此推导出“几乎满激活”的token阈值 `T_thres`。
- **每专家处理token数**：`T_exp(t;ρ)=ρt/(1-(1-ρ)^t)`，证明当 t>1 时，稀疏度ρ越小则 T_exp 越小，系统更倾向于内存-bound，SD验证阶段可利用空闲计算资源。

### 2.3 公式与算法流程（文字说明）
- **SD加速比公式**：
  `Speedup = (S·T_T(B,1)) / (R·[γ·T_D(B,1)+T_T(B,γ)+T_reject])`
  其中T_T、T_D分别为目标、草稿模型前向时间，γ为草稿长度，R为SD轮次，S为生成序列长度。
- **建模方法**：将目标模型前向时间分解为三个因素：(1) roofline模型效应（设计函数G(t;λ,s)）; (2) 活跃专家数N(t); (3) 专家负载T_exp。各因素通过线性组合（含偏置和系数）拟合GPU实测数据。草稿模型仅考虑roofline效应。使用最小二乘法确定参数，共10个可调参数。

## 3. 实验设计：使用了哪些数据集/场景，benchmark，对比了哪些方法
- **数据集**：HumanEval（代码生成）和 MT-Bench（对话任务），token化后提示长度分别为38~391和5~356。
- **场景**：不同批量大小（1~100）、不同草稿长度（γ=2,3,4）、不同温度（0.0和1.0）、不同稀疏度（通过修改K值模拟）、不同硬件平台。
- **对比方法**：
  - 同系列草稿：Qwen2-57B-A14B-Instruct 搭配 Qwen2-0.5B-Instruct（同族模型草图）。
  - 专用预测头：Mixtral-8x7B 搭配 Eagle（专用投机头）。
  - 稠密模型对比：Opt-30b 搭配 Opt-350m。
- **框架**：基于vLLM框架实现批处理投机解码、cuda graph优化，并记录各阶段时间。

## 4. 资源与算力
- **硬件平台**：2×A800、2×H800、4×A800、4×L40（NVIDIA GPU），具体算力未明确给出峰值或训练时长，仅说明实验在相应GPU上运行。
- **训练**：本文未涉及训练，仅进行推理加速评估。
- **未明确部分**：单次实验的具体耗时、总GPU使用时长未报告。

## 5. 实验数量与充分性
- **实验总量**：
  - 核心加速趋势实验：覆盖2种MoE模型、2个数据集、2种温度、3种草稿长度、多种批量（约19个），并分别在4种GPU配置上重复，总计上百组运行。
  - 稀疏度影响实验：对Qwen2模型修改K值（1,2,4,8,16,32）模拟不同稀疏度，结合2种草稿长度，共12个配置，各配置在19个批量下测试。
  - 建模拟合：使用21个精选测量点（从228个总测量中均匀采样），通过最小二乘法拟合10个参数，并与剩余实验点对比验证一致性。
  - 消融/对比：额外实验包括稠密vs MoE对比（图3）、不同GPU平台对比（表2）、不同草稿长度和温度的组合对比。
- **充分性**：实验覆盖了关键变量（批量、稀疏度、硬件、温度、数据集、草稿长度），验证了理论预测的趋势。但未进行长序列场景（KV-cache主导）的实验，也未测试其他MoE变体（如DeepSeek-V3）。实验均基于vLLM框架，可能受限于该框架的优化水平。

## 6. 论文的主要结论与发现
- **结论1**：在中等批量大小下，MoE从投机解码中获得的加速比高于稠密模型，且加速比随批量先增后减，峰值出现在中等批量。
- **结论2**：MoE越稀疏，SD有效的批量范围越宽（峰值对应的批量更大，加速比下降更缓慢）。
- **结论3**：新提出的“目标效率”指标与最终加速比趋势一致，能有效反映系统瓶颈，优于仅关注接受率的传统指标。
- **结论4**：所提出的建模方法（含10个参数）能与实际GPU测量结果在多种稀疏度和草稿长度下良好吻合（图4）。
- **量化加速**：在2×H800上，Qwen2-57B-A14B在HumanEval、γ=4、温度0.0时达到最高加速比2.29×（表2）。

## 7. 优点：方法或实验设计上的亮点
- **理论创新**：首次系统性揭示中等批量下稀疏MoE对SD更有利的规律，并给出严格的数学推导（专家激活数、每专家处理token数）。
- **新指标**：提出“目标效率”，将系统因素与算法因素解耦，使SD加速分析更透明，填补了现有研究只关注接受率的空白。
- **建模可解释**：基于roofline模型和活跃专家数的简单参数化模型，仅需少量测量即可拟合，且参数物理意义明确，能分解各因素贡献。
- **实验覆盖全面**：涵盖多种硬件、模型族、稀疏度、草稿长度和温度，并进行了统计显著性验证（附录A.1显示多次运行方差极小）。
- **实际价值**：指出中等批量在私有化部署、延迟敏感场景中的常见性，并讨论与offloading、专家并行等现有优化技术的兼容性。

## 8. 不足与局限
- **实验覆盖**：仅测试了Qwen2和Mixtral两个MoE模型，未覆盖更大规模（如DeepSeek-V3）或不同架构（如非transformer）的MoE；长序列场景（KV-cache占主导）未涉及，作者承认可参考MagicDec。
- **假设限制**：假设专家均匀激活（负载均衡），虽然当前先进MoE通过辅助损失实现，但极端不平衡情况未验证。
- **人为修改稀疏度**：通过修改config.json的K值模拟不同稀疏度，改变了模型结构，可能影响模型质量（文中通过σ归一化校正），但实际推理行为（如Attention占比）可能偏离真实稀疏MoE设计。
- **人工设计指标**：目标效率虽然有效，但依赖于具体实现（vLLM的cuda graph等），可泛化性需更多验证。
- **建模参数**：10个参数的拟合需要少量测量数据，但不同硬件和框架可能需要重新拟合，未提供跨平台通用参数集。
- **延迟与吞吐权衡**：论文主要关注加速比，未深入分析对首次token延迟（TTFT）和每output token时间（TPOT）的具体影响。

（完）
