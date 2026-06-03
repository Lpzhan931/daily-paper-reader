---
title: Online Speculative Decoding
title_zh: 在线投机解码
authors: "Xiaoxuan Liu, Lanxiang Hu, Peter Bailis, Alvin Cheung, Zhijie Deng, Ion Stoica, Hao Zhang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=BPQHXwVNvl"
tags: ["query:llm"]
score: 8.0
evidence: 在线投机解码加速大模型推理
tldr: 传统投机解码中，小模型预测准确性受限于训练分布与查询分布的差异。本文提出在线投机解码，根据用户查询数据持续更新小模型，使其更好地适应当前分布，从而提升预测准确率和加速效果。原型实验验证了有效性。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-bpqhxwvnvl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 859, \"height\": 324, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bpqhxwvnvl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 679, \"height\": 218, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bpqhxwvnvl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1431, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bpqhxwvnvl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 804, \"height\": 321, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bpqhxwvnvl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1061, \"height\": 305, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bpqhxwvnvl/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1727, \"height\": 230, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bpqhxwvnvl/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 836, \"height\": 233, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bpqhxwvnvl/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 705, \"height\": 340, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bpqhxwvnvl/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 707, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bpqhxwvnvl/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1036, \"height\": 318, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bpqhxwvnvl/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 530, \"height\": 355, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-bpqhxwvnvl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 779, \"height\": 350, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bpqhxwvnvl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 852, \"height\": 194, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bpqhxwvnvl/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 859, \"height\": 188, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bpqhxwvnvl/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 694, \"height\": 152, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bpqhxwvnvl/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1246, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bpqhxwvnvl/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1643, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bpqhxwvnvl/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1761, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bpqhxwvnvl/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1062, \"height\": 422, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bpqhxwvnvl/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1749, \"height\": 165, \"label\": \"Table\"}]"
motivation: 投机解码中，小模型预测精度不足限制加速效果，尤其在能力差距大或输入分布变化时。
method: 在线更新小模型参数，使其适应实时查询分布，实现更准确的预测。
result: 原型系统显示，在线更新后小模型预测准确率提升，推理加速比增加。
conclusion: 在线自适应可有效弥合分布偏移，改善投机解码的加速性能。
---

## Abstract
Speculative decoding is a pivotal technique to accelerate the inference of large language models (LLMs) by employing a smaller draft model to predict the target model's outputs. However, its efficacy can be limited due to the low predictive accuracy of the draft model, particularly when faced with diverse text inputs and a significant capability gap between the draft and target models. We introduce online speculative decoding to address this challenge. The main idea is to continuously update the (multiple) draft model(s) on observed user query data. Adapting to query distribution mitigates the shifts between the training distribution of the draft model and the query distribution, enabling the draft model to more accurately predict the target model's outputs. We develop a prototype of online speculative decoding based on knowledge distillation and evaluate it using both synthetic and real query data. The results show a substantial increase in the token acceptance rate by 0.1 to 0.65, bringing 1.42x to 2.17x latency reduction. Our code is available at https://github.com/LiuXiaoxuanPKU/OSD.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：投机解码（Speculative Decoding）通过一个小型草稿模型（draft model）预测大模型（target model）的输出，以加速LLM推理。然而，草稿模型的预测准确率（token acceptance rate）往往较低，尤其是在面对多样化文本输入、或者草稿模型与目标模型能力差距较大时。传统方法假设草稿模型在部署后保持静态，无法适应在线查询分布的变化。
- **整体含义**：本文提出**在线投机解码（Online Speculative Decoding, OSD）**，旨在通过在服务过程中持续利用目标模型的校正信息更新草稿模型，使其动态适应当前查询分布，从而提高预测准确率，降低延迟。这不仅提升了推理效率，还降低了成本。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：将投机解码中的草稿模型视为学生，目标模型视为教师，利用知识蒸馏（Knowledge Distillation）框架在线更新草稿模型。在每次投机解码过程中，草稿模型提出多个候选token，目标模型并行验证并纠正错误。该纠正过程自然提供了教师分布信息（目标logits），用于蒸馏学生模型。
- **关键技术细节**：
  - **知识蒸馏距离度量**：采用多种散度：
    - 前向KL散度（Forward KL）
    - 反向KL散度（Reverse KL）
    - JSD散度（混合参数β）
  - **采样策略**：教师采样（teacher sampling）、学生采样（student sampling）、混合采样（mix sampling），样本直接代入损失函数，不通过采样梯度。
  - **算法流程（Algorithm 1）**：
    1. 用预热数据集预训练草稿模型。
    2. 对每个在线请求执行标准投机解码。
    3. 记录草稿模型预测错误的token位置及对应的目标logits（error index & target logits）。
    4. 将错误信息存入重放缓冲区（replay buffer）。
    5. 每间隔I个请求（本文固定I=8），用缓冲区数据更新草稿模型，优化公式(4)中的损失。
    6. 清空缓冲区，继续服务。
  - **多草稿模型路由**：将查询按语言或主题分类，为每个类别训练专用草稿模型，并在收到查询时路由到对应模型，进一步缩小分布范围，提高准确率。
- **公式**（文字描述）：
  - 蒸馏损失 ℓ(θ) = (1/n_B) Σ_D(p(·|x)∥q_θ(·|x))，其中D为散度。
  - 实际估计时，通过采样序列y，计算∑ D(p(y|x,y_<j)∥q_θ(y|x,y_<j))。

## 3. 实验设计：数据集、场景、基准、对比方法
- **数据集**：
  - 四个领域数据集：Text-to-SQL（Spider）、数学推理（Gsm8k）、Python代码生成（Code-search-Python）、金融问答（Alpaca-finance）。
  - 真实世界数据集：LMSYS-Chat-1M，抽取10K条Vicuna模型对话记录。
- **场景**：
  - 离线评估：用全部训练数据蒸馏草稿模型，测试token接受率。
  - 在线评估：模拟服务流，逐步处理请求并在线更新草稿模型，追踪实时接受率。
  - 分布偏移仿真：合并不同数据集模拟突变和渐变。
  - 真实工作负载：LMSYS聊天数据集，按语言和主题分类。
- **模型对**：
  - 目标：Vicuna-7B，草稿：LLaMA-160M
  - 目标：FLAN-T5-XL（3B），草稿：T5-Small（80M）
  - 此外还有（TinyLLaMA-1.1B 草稿，Vicuna-33B 目标）用于延迟测量。
- **对比方法**：
  - 原始未蒸馏草稿模型（Original）
  - 基于教师标签微调（FT）
  - 各种蒸馏变体（TF, SF, MixF）
  - 离线用10%数据蒸馏的静态草稿模型（作为基线）
  - 与Medusa-v1对比（标准投机解码 vs Medusa+OSD）
  - 单草稿模型 vs 多专用草稿模型

## 4. 资源与算力
- **明确说明**：
  - 延迟测量在单张A100-80G GPU上进行，batch size=1。
  - 使用llama.cpp框架实现投机解码。
  - 在线更新草稿模型的计算量分析表明：对于(160M, 7B)对，更新一次约0.12秒；对于(1.1B, 33B)对，约0.67秒，而目标模型推理一次需数秒，因此更新开销可忽略。
  - 文中分析了Arena集群的算力利用率极低（<1%），并指出更新草稿模型仅占极小部分。
- **未明确说明**：
  - 离线蒸馏训练的具体GPU数量和总时长（仅提及训练2个epoch，但未报告具体硬件和耗时）。
  - 在线更新时使用的硬件配置（推断与A100-80G相同，但未明确）。

## 5. 实验数量与充分性
- **实验数量**：论文包含**大量实验**，覆盖以下方面：
  - **离线蒸馏对比**（表1）：4个数据集 × 2个模型对 × 5种蒸馏方法（Original, FT, TF, SF, MixF）共40组结果。
  - **在线学习曲线**（图3）：4个数据集 × 2个模型对，每50条记录平均α，共8个子图。
  - **分布偏移**（图4）：组合数据集，与不同比例离线蒸馏对比。
  - **真实工作负载**（图5）：按语言5类、按主题5类，跟踪α。
  - **单 vs 多草稿模型对比**（图6）：每个主题下两种模式的α对比。
  - **延迟测量**（表2、表3）：不同α、不同模型对、不同数据集下的实际速度提升。
  - **与Medusa对比**（表4）：Spider和Arena数据集。
  - **定性分析**（图7、表6）：高频token的精确率和召回率改进。
  - **采样策略与距离度量消融**：虽未全部展示，但文中提及尝试了前向KL、反向KL、JSD，并报告了teacher sampling最佳。
  - **额外实验**（附录中）：不同分布偏移程度（图11）、数据混合遗忘（图9）、生成长度影响（表8）等。
- **充分性与公平性评价**：
  - 实验**充分**：覆盖了多个数据集、模型对、蒸馏变体、在线/离线设置、真实场景，并进行了消融和对比。
  - **公平性**：对比基线包括原始模型、标签微调、离线上限；在线更新与离线“全额访问”对比表明OSD可接近甚至超过。但部分对比（如与Medusa）中，OSD+标准投机解码在某些数据集上不如Medusa本质，作者对此有讨论。
  - 不足：消融实验不够系统（如最优距离度量未全面对比，仅称forward KL更好）；超参数（I=8）未调优；只测试了两个具体模型对，泛化性有限。

## 6. 论文的主要结论与发现
- **主要结论**：
  - 知识蒸馏（特别是教师采样+前向KL）显著提高草稿模型的token接受率，从原始值提升0.1-0.65。
  - 在线自适应（OSD）能在处理少量请求后迅速提升α，并追赶甚至超越离线蒸馏上限。
  - 在真实工作负载下，按语言/主题定制多个草稿模型可进一步改善α 0.1-0.2。
  - OSD带来的速度提升达1.42×-2.17×（Vicuna-7B组合），且计算与内存开销可忽略。
  - OSD可与其他投机解码变体（如Medusa）结合，进一步提升性能。

## 7. 优点：方法或实验设计上的亮点
- **方法创新**：首次提出在线更新草稿模型以适应查询分布，打破了静态假设，使投机解码更贴合实际部署。
- **结合知识蒸馏**：利用投机解码过程中天然产生的教师-学生分布对齐，无需额外标注。
- **多草稿模型路由**：针对不同子域训练专用模型，进一步缩小分布差异，提升准确率。
- **系统考量**：深入分析了FLOPs、内存带宽、延迟等资源开销，证明在线更新可行且高效。
- **实验全面**：覆盖合成与真实数据、多种模型规模、离线/在线/分布偏移多种场景，并与Medusa对比，验证了通用性。
- **开源代码**：提供完整代码，促进复现和后续研究。

## 8. 不足与局限
- **模型对覆盖有限**：仅测试了(160M,7B)和(80M,3B)两组，未验证更大模型（如33B目标+1.1B草稿）的在线自适应效果（延迟测量用到但未做在线学习实验）。
- **超参数未充分调优**：更新间隔I固定为8，未探索不同更新频率的影响；缓冲区清空策略简单，未考虑更好重放策略。
- **蒸馏方法消融不足**：仅报告了前向KL最好，但未呈现反向KL、JSD的完整对比数据。
- **多草稿路由未优化**：路由策略简单（基于语言/主题标签），未研究最优模型数量、分类模型开销、以及动态更新多个模型时的同步问题。
- **灾难性遗忘问题**：文中仅通过混合数据集实验初步验证了知识保持，但未系统评估持续学习中的遗忘风险。
- **实验环境限制**：延迟测量使用llama.cpp和自定义实现，可能未能代表工业级生产系统的实际性能。
- **现实部署复杂性**：在线更新需要同步机制、资源争用处理等，论文未深入讨论工程细节。
- **公平性**：与Medusa对比时，OSD+标准投机解码在Arena数据集上不如原版Medusa，作者虽承认但未充分解释。

（完）
