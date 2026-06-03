---
title: Reward-Guided Speculative Decoding for Efficient LLM Reasoning
title_zh: 奖励引导投机解码以实现高效LLM推理
authors: "Baohao Liao, Yuhui Xu, Hanze Dong, Junnan Li, Christof Monz, Silvio Savarese, Doyen Sahoo, Caiming Xiong"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=AVeskAAETB"
tags: ["query:llm"]
score: 8.0
evidence: 面向大语言模型高效推理的投机解码
tldr: 本文针对大型语言模型推理效率问题，提出了奖励引导投机解码（RSD）框架。RSD结合轻量级草稿模型与强大目标模型，利用过程奖励模型评估中间步骤并动态决策，优化计算开销与输出质量的权衡。理论证明阈值混合策略达到最优平衡，实验验证了其有效性。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-aveskaaetb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1526, \"height\": 605, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-aveskaaetb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 730, \"height\": 255, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-aveskaaetb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1652, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-aveskaaetb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 806, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-aveskaaetb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 811, \"height\": 435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-aveskaaetb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 681, \"height\": 461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-aveskaaetb/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1736, \"height\": 740, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-aveskaaetb/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1568, \"height\": 420, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 854, \"height\": 638, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 872, \"height\": 382, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 806, \"height\": 290, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1700, \"height\": 1363, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 862, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 793, \"height\": 260, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1758, \"height\": 358, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 865, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1326, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1532, \"height\": 1583, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1664, \"height\": 359, \"label\": \"Table\"}]"
motivation: 现有投机解码方法追求无偏性，忽略了中间步骤的质量差异，导致计算资源浪费。
method: 提出RSD框架，结合草稿模型和目标模型，利用过程奖励模型评估中间步骤，动态决定是否调用目标模型。
result: 实验表明RSD在多种推理任务上显著提升效率，同时保持甚至改善输出质量。
conclusion: RSD通过引入奖励引导的决策机制，优化了投机解码的效率与质量权衡，具有广泛适用性。
---

## Abstract
We introduce Reward-Guided Speculative Decoding (RSD), a novel framework aimed at improving the efficiency of inference in large language models (LLMs). RSD synergistically combines a lightweight draft model with a more powerful target model, incorporating a controlled bias to prioritize high-reward outputs, in contrast to existing speculative decoding methods that enforce strict unbiasedness.
RSD employs a process reward model to evaluate intermediate decoding steps and dynamically decide whether to invoke the target model, optimizing the trade-off between computational cost and output quality. We theoretically demonstrate that a threshold-based mixture strategy achieves an optimal balance between resource utilization and performance. Extensive evaluations on challenging reasoning benchmarks, including Olympiad-level tasks, show that RSD delivers significant efficiency gains against decoding with the target model only (up to 4.4X fewer FLOPs), while achieving significant better accuracy than parallel decoding method on average (up to +3.5). These results highlight RSD as a robust and cost-effective approach for deploying LLMs in resource-intensive scenarios.

---

## 论文详细总结（自动生成）

好的，作为资深学术论文分析助手，我将遵循您的要求，对《Reward-Guided Speculative Decoding for Efficient LLM Reasoning》这篇论文进行详细、结构化、客观的中文总结。

### 论文总结：奖励引导投机解码以实现高效LLM推理

#### 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）的推理过程计算成本高昂，尤其是在处理复杂的多步推理任务（如数学、编程）时。现有的投机解码方法虽然旨在通过轻量级模型“草稿”和庞大模型“验证”来加速，但它们的核心约束是**严格的无偏性**，即必须保证最终输出的概率分布与目标模型完全一致。
- **研究动机**：这种无偏性要求导致了效率瓶颈。当“草稿”模型生成了一个质量很高（例如，推理步骤正确）但与“目标”模型的概率分布存在偏差的token时，传统方法会严格拒绝它，浪费了这个高质量输出。论文认为，**引入可控的偏差，优先采纳高奖励的输出，可以显著提升效率，甚至在某些情况下超越目标模型本身的性能**。
- **整体含义**：该论文旨在提出一种新的、更高效的推理框架，通过动态、智能地融合轻量级和重量级模型，在保证或提升输出质量的同时，大幅降低计算开销，使得LLM在资源受限或对延迟敏感的场景下更具实用性。

#### 2. 方法论

- **核心思想**：提出一个名为**奖励引导投机解码（RSD）** 的框架。RSD不是强制两个模型在每一步都达成一致，而是引入一个**过程奖励模型（PRM）** 来评估“草稿”模型每一步生成的质量。基于这个奖励分数，动态决定是接受草稿模型的输出，还是使用更昂贵的“目标”模型重新生成。

- **关键技术细节**：
    1.  **动态混合分布**：RSD不再追求与目标模型的概率分布 `PM` 完全一致，而是构建一个新的混合分布 `PRSD`：
        `PRSD(yi|zi) = w(yi|zi) * Pm(yi|zi) + ν * PM(yi|zi)`
        其中 `Pm` 是草稿模型分布，`PM` 是目标模型分布，`w` 是一个基于奖励 `r` 的动态权重函数，`ν` 是保证分布归一化的常数。
    2.  **权重函数 `w`**：函数 `w` 是奖励 `r` 的映射，用于决定多大程度依赖草稿模型。当奖励 `r` 越高（表示草稿输出质量好），`w` 越接近1，此时混合分布主要由草稿模型主导（高效）；反之，当奖励低时，`w` 接近0，混合分布转向目标模型 `PM`（高质量）。
    3.  **接受准则（Algorithm 2）**：给定一个奖励值 `r` 和阈值/权重函数 `ω(r)`，算法通过一个随机过程来决定是否接受草稿模型的输出。论文证明了在预算约束下，最优的权重函数是一个**二值阶跃函数**（Binary Step Function），即只有当奖励超过一个阈值 `δ` 时才接受草稿模型的输出。
    4.  **算法流程（Algorithm 1）**：
        1.  草稿模型生成一个候选步骤 `ŷi`。
        2.  使用PRM计算该步骤的奖励 `ri`。
        3.  应用接受准则 `Aω(ri)`：如果 `ri` 超过阈值 `δ`（或满足其他条件），则接受草稿步骤；否则，调用目标模型 `M` 生成一个高质量的新步骤。
    5.  **理论证明**：论文在命题2.2中证明了，如果权重函数 `ω(r)` 是奖励 `r` 的非递减函数，且目标模型的期望奖励不低于草稿模型，那么RSD的期望奖励将不低于草稿模型。命题2.3则证明了在给定采样预算下，最优的采样策略正是基于奖励阈值的二值阶跃函数。

#### 3. 实验设计

- **数据集/场景**：论文在多个具有挑战性的推理基准上进行了评估，涵盖数学、科学和综合知识领域：
    - **数学推理**：MATH500, GSM8K, Minerva Math, GaoKao-2023-En, OlympiadBench
    - **科学推理**：GPQA (Diamond)
    - **多任务**：MMLU (STEM)
- **基准对比方法**：
    - **目标模型单独使用（Target Model Only）**：性能天花板，但计算成本最高。
    - **草稿模型 alone**：成本最低，但性能差。
    - **多数投票（Majority Voting）** 和 **Best-of-N (BoN)**：典型的测试时扩展方法，通过大量采样来提升草稿模型性能。
    - **标准投机解码（Standard SD）**：追求无偏性，是RSD的直接对标方法。
    - **搜索方法**：包括与Beam Search和Process Best-of-N的比较。
- **模型配置**：论文测试了多种模型组合（草稿/目标/PRM），包括Qwen2.5-Math-Instruct, Qwen2.5-Instruct, Llama-3.1-Instruct系列，模型参数量从1B到72B不等。

#### 4. 资源与算力

- 论文中明确指出所有实验均在 **NVIDIA A100 GPU** 上运行。
- **未明确说明**：论文没有提供训练PRM所需的算力（因为是使用开源模型）或执行所有基准测试所需的总GPU小时数。因此，无法量化总计算成本。
- **相关数据**：论文在计算效率（FLOPs）分析中，遵循了“2N FLOPs/token”的标准近似，其中N是模型参数量。

#### 5. 实验数量与充分性

- **实验数量**：论文进行了大量实验，包括：
    - **主实验结果**：在7个基准数据集上，对8种不同的模型/方法配置进行对比（Table 2）。
    - **计算效率分析**：FLOPs vs. Accuracy对比（Figure 4）。
    - **与搜索方法对比**：在3个基准上与Beam Search和Process Best-of-N比较（Table 3）。
    - **消融实验**：
        - **阈值 `δ` 的影响**：在MATH500上分析不同阈值的表现（Figure 5）。
        - **权重函数的选择**：对比了表1中列出的5种不同权重函数的性能（Figure 6）。
        - **奖励模型的鲁棒性**：使用不同的PRM（Skywork, Qwen2.5-Math-PRM）进行测试（Table 5）。
        - **模型合并**：将PRM与目标或草稿模型合并，以减少模型数量（Table 4）。
        - **通用领域任务**：在AlpacaEval上使用ORM代替PRM进行测试（Table 6）。
        - **推理复杂度分析**：根据MATH500中问题的难度级别（Level 1-5）分析RSD表现（Figure B.1）。
- **充分性与公平性**：
    - 实验设计是**相当充分和系统**的，覆盖了方法论的核心组件（阈值、权重函数、奖励模型）并进行了消融。
    - 对比基线**非常全面**，包括标准SD、BoN、多数投票、搜索方法，以及不同大小的模型组合。
    - 公平性体现在对所有方法使用了**统一的后端（vLLM）**，并尝试控制一些超参数（如温度）。论文也注意到了SD在现实中的不完美无偏性（由于浮点误差）。

#### 6. 主要结论与发现

1.  **效率显著提升**：相比单独使用目标模型，RSD能实现 **最高4.4倍** 的FLOPs下降。相比BoN等采样方法，RSD在相当或更低的计算成本下取得了更好的准确率。
2.  **准确率更优**：RSD在几乎所有测试场景下，平均准确率都显著优于标准SD（平均提升高达+3.5）。在一些基准（如GPQA）上，RSD甚至**超越**了单独使用更强大的目标模型。
3.  **自动计算分配**：RSD通过阈值 `δ` 实现了计算资源的智能分配：对于简单问题，大多数步骤由草稿模型生成并被接受（低成本）；对于复杂问题，目标模型参与的必要步骤更多（高成本）。这解决了传统SD对所有问题“一刀切”地使用双模型的问题。
4.  **鲁棒性**：RSD对于不同类型的PRM是鲁棒的。即使使用通用的ORM代替PRM，RSD仍然优于草稿模型，表明方法在不同任务上具有泛化能力。
5.  **可扩展性**：RSD可以与标准SD结合使用，并且可以通过模型合并来减少部署时的服务模型数量。

#### 7. 优点

- **理论创新**：首次将过程奖励模型系统地引入投机解码框架，并理论推导出最优混合策略是阈值函数，为方法提供了坚实的数学基础。
- **视角转变**：从追求“无偏性”转向追求“高质量输出”，这是一种更实用、更符合推理任务需求的范式转变。
- **显著的实际效果**：在多个权威基准上，RSD都实现了“又快又好”的结果，展示了很强的工程实用价值。
- **全面的实验分析**：实验设计非常完善，不仅证明了方法的有效性，还深入分析了阈值、权重函数、PRM选择等各个组件的影响，以及对不同难度问题的行为差异。
- **理论严谨性**：提供了完备的定理证明，如命题2.2证明奖励不会低于草稿模型，命题2.3证明阈值函数的最优性。

#### 8. 不足与局限

- **依赖PRM质量**：RSD的性能强烈依赖于PRM的质量。虽然论文验证了对不同开源PRM的鲁棒性，但如果PRM本身对推理步骤的评估存在偏差或噪声，可能会引入错误。例如，如果PRM将错误的推理步骤给予了高分，RSD会错误地接受它。
- **基于步骤的粒度**：RSD将模型生成定义为“推理步骤”（以`\n\n`分隔），这与大多数投机解码基于“token”的粒度不同。虽然这更符合推理任务，但该方法对于非自然以步骤形式进行的生成任务（如纯文本创作）的适用性有待进一步探索。论文自己也提到，尚缺乏通用领域的PRM。
- **通用领域PRM的缺失**：论文指出，目前缺乏通用的过程奖励模型，限制了RSD在更广泛领域的应用。虽然实验中使用ORM进行替代，但ORM是评估最终结果而非中间步骤，可能不是最优选择。
- **缺乏对超大模型的验证**：最大的模型组合是目标模型为72B，对于更大的模型（如175B或更大），由于资源限制，论文未进行验证，其效率提升能否稳定保持尚待考察。

（完）
