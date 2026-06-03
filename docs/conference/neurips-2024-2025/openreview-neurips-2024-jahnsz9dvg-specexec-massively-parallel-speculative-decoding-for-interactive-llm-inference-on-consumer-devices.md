---
title: "SpecExec: Massively Parallel Speculative Decoding For Interactive LLM Inference on Consumer Devices"
title_zh: "SpecExec: 面向消费级设备交互式LLM推理的大规模并行投机解码"
authors: "Ruslan Svirschevski, Avner May, Zhuoming Chen, Beidi Chen, Zhihao Jia, Max Ryabinin"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=JAhNsZ9dvG"
tags: ["query:llm"]
score: 9.0
evidence: 大规模并行投机解码用于消费级设备LLM推理
tldr: 本文聚焦于在消费级设备上加速LLM推理，提出SpecExec方法。利用参数卸载使得单次批处理可同时处理数百个token，结合投机解码的并行验证，大幅降低推理延迟。实验表明，在消费级GPU上SpecExec实现了接近数据中心级别的加速，使大型模型能够在本地以交互速度运行。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-jahnsz9dvg/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1457, \"height\": 356, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jahnsz9dvg/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 231, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jahnsz9dvg/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1455, \"height\": 341, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jahnsz9dvg/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1454, \"height\": 343, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jahnsz9dvg/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1453, \"height\": 344, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jahnsz9dvg/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1216, \"height\": 1147, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jahnsz9dvg/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 879, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jahnsz9dvg/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1326, \"height\": 337, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jahnsz9dvg/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1453, \"height\": 427, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-jahnsz9dvg/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1427, \"height\": 866, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-jahnsz9dvg/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1429, \"height\": 555, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-jahnsz9dvg/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1445, \"height\": 596, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-jahnsz9dvg/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1167, \"height\": 284, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-jahnsz9dvg/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1379, \"height\": 336, \"label\": \"Table\"}]"
motivation: 消费级设备无法容纳大模型，参数卸载后批处理天然适合投机解码。
method: 提出SpecExec，利用参数卸载实现大规模批量token处理，结合并行验证。
result: 在消费级硬件上实现接近数据中心的加速效果。
conclusion: 投机解码可有效部署于资源受限设备，推动本地LLM应用。
---

## Abstract
As large language models gain widespread adoption, running them efficiently becomes a crucial task. Recent works on LLM inference use speculative decoding to achieve extreme speedups. However, most of these works implicitly design their algorithms for high-end datacenter hardware. In this work, we ask the opposite question: how fast can we run LLMs on consumer machines? Consumer GPUs can no longer fit the largest available models and must offload them to RAM or SSD. With parameter offloading, hundreds or thousands of tokens can be processed in batches within the same time as just one token, making it a natural fit for speculative decoding. We propose SpecExec (Speculative Execution), a simple parallel decoding method that can generate up to 20 tokens per target model iteration for popular LLM families.  SpecExec takes the most probable continuations from the draft model to build a "cache" tree for the target model, which then gets validated in a single pass. Using SpecExec, we demonstrate inference of 50B+ parameter LLMs on consumer GPUs with RAM offloading at 4--6 tokens per second with 4-bit quantization or 2--3 tokens per second with 16-bit weights. Our code is available at https://github.com/yandex-research/specexec .

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义
**研究动机**：消费级 GPU（如 RTX 3090、4090）无法容纳 50B+ 参数的大语言模型（LLM），必须通过参数卸载（offloading）将模型权重放在 CPU 内存或 SSD 中。每次推理时需从 RAM 加载全部参数到 GPU，导致带宽瓶颈（生成单个 token 需数秒）。现有投机解码方法（如 SpecInfer）在少量草稿 token 时有效，但在大规模草稿预算（数百至数千 token）下接受的 token 数量出现上界（约 10 个），无法充分利用卸载环境下的批处理能力。

**整体含义**：本文提出 SpecExec（Speculative Execution），通过利用卸载场景下批处理大量 token 的天然优势，结合新型投机解码机制，使消费级设备能够以交互速度（4–6 tok/s）运行 70B 量级的 LLM，降低对高端数据中心硬件的依赖，推动本地化、隐私友好的 LLM 部署。

## 2. 方法论
**核心思想**：采用草稿模型（draft model）**确定性地**构建一棵包含最可能连续 token 的缓存树（cache tree），然后目标模型（target model）在一次前向传播中并行验证整个树，并将验证后的概率存入缓存。后续采样时优先从缓存中读取概率，若缓存未命中则重新预计算。

**关键技术细节**：
- **草稿树构建**：将最优树搜索问题等价于单源最短路径（SSSP）问题，使用修改后的并行 Dijkstra 算法（Algorithm 2）**批量扩展**最有可能的 token，避免传统 beam search 的宽度–长度折衷。
- **验证与缓存**：草稿树中的每个节点（token）与之前缀一起构成键值对，目标模型一次前向计算所有节点的下一 token 概率，并存入缓存。
- **采样**：顺序采样时直接从缓存中取目标模型概率，保证与标准自回归采样**完全相同**的输出分布（种子一致性）。
- **卸载优化**：CUDA 流预取、层间并行加载、KV 缓存常驻 GPU。

**算法流程简述**：
1. **预计算阶段**：用草稿模型执行并行 SSSP 搜索，生成包含 K 个最可能 token 的树；用目标模型（卸载）前向传播该树，得到所有节点的概率，存入缓存。
2. **生成阶段**：从缓存中采样当前 token；若采样时前缀不在缓存中（缓存耗尽），则重新执行预计算。
3. 重复直至生成所需长度。

## 3. 实验设计
**使用数据集/场景**：
- **对话数据集**：OpenAssistant (OAsst)、MTBench
- **文章数据集**：WikiText-2、C4
- 场景涵盖 Chat/Instruct 模型（Llama-2-70B-chat、Llama-3-70B、Mixtral 8x7B）和基础模型（Llama-2-70B）。

**对比方法**：
- **SpecInfer**：支持多序列/树状草稿的投机解码基线。
- **顺序推理**（无投机）：测量同一硬件上的原始推理速度。

**Benchmark 指标**：
- 生成速度（tokens/s）
- 加速比（相对于顺序推理）
- 每步生成 token 数（Generations per step）
- 覆盖率：草稿模型 top-k token 在目标模型中的累计概率。

**消融实验**：
- 不同草稿模型大小（JackFram-160M、TinyLlama-1.1B、Llama-2-7B/13B）
- 不同 draft budget（8–4096 token）
- 不同温度与 top-p 设置（t=0.6, p=0.9 与 greedy）
- 不同 GPU 型号（A100、RTX 4090/3090/2080Ti/4060）
- 量化版本（GPTQ 4-bit vs FP16）
- 额外惩罚分析（禁止包含“r”的 token）

## 4. 资源与算力
**硬件配置**：
- **数据中心 GPU**：NVIDIA A100（80GB VRAM，但模拟消费级场景，不常驻任何层，仅用于卸载基准测量）
- **消费级 GPU**：RTX 4090、RTX 3090、RTX 4060、RTX 2080Ti
- 连接方式：PCIe 3.0/4.0 x16
- **主机内存**：至少 140GB（FP16）或 64GB（4-bit）用于存放模型
- **推理时间**：实验仅推理，无训练。每次预计算约耗时数秒，取决于 draft budget 和 GPU。

**模型**：
- 目标模型：Llama-2-70B / Llama-3-70B / Mixtral 8x7B（均含 Chat 版）
- 草稿模型：Llama-2-7B（主要）、TinyLlama-1.1B、ShearedLlama-1.3B、JackFram-160M
- 量化工具：GPTQ（4-bit）

## 5. 实验数量与充分性
**实验数量**：
- **主速度实验**：覆盖 4 个数据集（OAsst、MTBench、WikiText-2、C4）、3 种目标模型、2 种量化等级、6 种 GPU 型号、2 种对比方法（SpecInfer 和顺序推理），共约 30+ 组独立速度测量。
- **接受率实验**：测试不同 draft budget（8–4096）下的每步生成 token 数，包含 Chat/基础模型、不同温度。
- **覆盖率分析**：5 种草稿模型在 512 个对话样本上的累计概率曲线。
- **消融实验**：草稿模型大小、预算规模、量化影响、惩罚效应等。

**充分性评价**：
- **客观性**：所有方法保证相同的输出分布，对比公平；基线 SpecInfer 使用公开算法实现。
- **局限性**：论文明确说明**没有提供误差棒**，仅报告平均值；未在不同随机种子下重复多次。部分实验（如 RTX 4060、2080Ti）仅测试一种配置。另外，对于非卸载（in-memory）场景，仅提供少量数据（附录 G），结论较弱。

## 6. 主要结论与发现
1. **消费级设备可实现交互速度**：在 RTX 4090 上运行 Llama-2-70B 4-bit 达到 5.66 tok/s，加速比 8.3×；FP16 版本在 A100（模拟卸载）达 3.12 tok/s，加速比 18.7×。
2. **大规模草稿预算有效**：SpecExec 在 2048 草稿 token 下可生成 20+ 个 token/步，而 SpecInfer 饱和于 ≈10 个。
3. **目标模型概率分布集中**：top-4 token 覆盖 90–98% 概率，使确定性树搜索高效。
4. **算法保证等价性**：SpecExec 与标准采样完全一致（种子级别确定性），优于投机解码的概率性保证。
5. **跨硬件稳健**：从 A100 到 RTX 2080Ti 均能获得显著加速。

## 7. 优点
- **方法简洁高效**：直接缓存目标模型概率，无需复杂的拒绝采样机制，保证输出分布严格一致。
- **可扩展性好**：大规模草稿预算下性能持续提升，克服了现有方法的上界问题。
- **硬件通用性强**：适配从高端数据中心 GPU 到老旧消费级 GPU，且不依赖特定量化方案。
- **实用导向**：代码开源、配置详尽，可直接用于本地部署。

## 8. 不足与局限
- **实验统计不足**：未报告误差棒，无法评估结果波动性，尤其在低预算或小数据集下。
- **草稿模型依赖**：性能高度依赖草稿模型质量（7B 草稿明显优于 1B 以下），而 7B 草稿本身需 13GB+ VRAM，可能超出部分消费级 GPU 的显存容量。
- **非卸载场景弱**：在无卸载的推理中加速比仅约 2×（附录 G），优势不突出。
- **惩罚约束下的鲁棒性有限**：强 token 惩罚（如禁止包含“r”）导致接受率下降（附录 H）。
- **资源需求仍较高**：FP16 版本需 140GB+ RAM，4-bit 版本需 64GB+，限制了部分低配设备的使用。
- **不覆盖所有生成参数**：仅测试固定温度（0.6 / 0）和 top-p（0.9），未系统评估超参数影响。

（完）
