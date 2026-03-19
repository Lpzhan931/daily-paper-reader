<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-03-19
- 运行时间：2026-03-19 19:47:15 UTC
- 运行状态：成功
- 本次总论文数：20
- 精读区：9
- 速读区：11

### 今日简报（AI）
今日深度解析 20 篇大模型推理前沿论文，重点攻克多阶段流调度与存储瓶颈。
满分研究展示了跨 SSD 的 KVCache 协同卸载与多阶段调度技术，能显著提升长文本服务效率。
建议关注 Mamba-Transformer 混合架构及多智能体服务框架，探索更高效的系统级部署方案。
- 详情：[/202603/19/README](/202603/19/README)

### 精读区论文标签
1. [Multi-stage Flow Scheduling for LLM Serving](/202603/19/2603.17456v1-multi-stage-flow-scheduling-for-llm-serving)  
   标签：评分：10.0/10、query:llm
   evidence：多阶段流调度优化大模型服务的首字延迟
2. [Swarm: Co-Activation Aware KVCache Offloading Across Multiple SSDs](/202603/19/2603.17803v1-swarm-co-activation-aware-kvcache-offloading-across-multiple-ssds)  
   标签：评分：10.0/10、query:llm
   evidence：利用协同激活相关性将KV缓存卸载到SSD
3. [Efficient Training-Free Multi-Token Prediction via Embedding-Space Probing](/202603/19/2603.17942v1-efficient-training-free-multi-token-prediction-via-embedding-space-probing)  
   标签：评分：10.0/10、query:llm
   evidence：无需训练的多标记预测与投机标记树
4. [ASAP: Attention-Shift-Aware Pruning for Efficient LVLM Inference](/202603/19/2603.14549v2-asap-attention-shift-aware-pruning-for-efficient-lvlm-inference)  
   标签：评分：9.0/10、query:llm
   evidence：针对视觉语言模型的注意力偏移感知剪枝
5. [LEXI: Lossless Exponent Coding for Efficient Inter-Chiplet Communication in Hybrid LLMs](/202603/19/2603.15589v1-lexi-lossless-exponent-coding-for-efficient-inter-chiplet-communication-in-hybrid-llms)  
   标签：评分：9.0/10、query:llm
   evidence：激活值与缓存的无损压缩
6. [Mostly Text, Smart Visuals: Asymmetric Text-Visual Pruning for Large Vision-Language Models](/202603/19/2603.16001v1-mostly-text-smart-visuals-asymmetric-text-visual-pruning-for-large-vision-language-models)  
   标签：评分：9.0/10、query:llm
   evidence：针对大型视觉语言模型的非对称文本-视觉剪枝技术
7. [ZipServ: Fast and Memory-Efficient LLM Inference with Hardware-Aware Lossless Compression](/202603/19/2603.17435v1-zipserv-fast-and-memory-efficient-llm-inference-with-hardware-aware-lossless-compression)  
   标签：评分：9.0/10、query:llm
   evidence：针对大模型推理的硬件感知无损压缩
8. [RAMP: Reinforcement Adaptive Mixed Precision Quantization for Efficient On Device LLM Inference](/202603/19/2603.17891v1-ramp-reinforcement-adaptive-mixed-precision-quantization-for-efficient-on-device-llm-inference)  
   标签：评分：9.0/10、query:llm
   evidence：用于高效推理的强化学习自适应混合精度量化
9. [CARE: Covariance-Aware and Rank-Enhanced Decomposition for Enabling Multi-Head Latent Attention](/202603/19/2603.17946v1-care-covariance-aware-and-rank-enhanced-decomposition-for-enabling-multi-head-latent-attention)  
   标签：评分：9.0/10、query:llm
   evidence：在不增加KV缓存成本的情况下提高表达能力

### 速读区论文标签
1. [Orla: A Library for Serving LLM-Based Multi-Agent Systems](/202603/19/2603.13605v1-orla-a-library-for-serving-llm-based-multi-agent-systems)  
   标签：评分：8.0/10、query:llm
   evidence：跨后端协调大模型推理的服务层
2. [Flash-Unified: A Training-Free and Task-Aware Acceleration Framework for Native Unified Models](/202603/19/2603.15271v1-flash-unified-a-training-free-and-task-aware-acceleration-framework-for-native-unified-models)  
   标签：评分：8.0/10、query:llm
   evidence：针对原生统一模型的任务感知加速框架
3. [DUET: Disaggregated Hybrid Mamba-Transformer LLMs with Prefill and Decode-Specific Packages](/202603/19/2603.15530v1-duet-disaggregated-hybrid-mamba-transformer-llms-with-prefill-and-decode-specific-packages)  
   标签：评分：8.0/10、query:llm
   evidence：针对混合模型预填充和解码阶段的解耦加速器
4. [Efficient Reasoning on the Edge](/202603/19/2603.16867v1-efficient-reasoning-on-the-edge)  
   标签：评分：8.0/10、query:llm
   evidence：优化边缘部署中的KV缓存占用和Token成本
5. [ExPosST: Explicit Positioning with Adaptive Masking for LLM-Based Simultaneous Machine Translation](/202603/19/2603.14903v1-exposst-explicit-positioning-with-adaptive-masking-for-llm-based-simultaneous-machine-translation)  
   标签：评分：7.0/10、query:llm
   evidence：通过KV缓存实现高效解码
6. [Attention Residuals](/202603/19/2603.15031v1-attention-residuals)  
   标签：评分：7.0/10、query:llm
   evidence：通过注意力残差进行选择性聚合并减少内存占用
7. [DOS: Dependency-Oriented Sampler for Masked Diffusion Language Models](/202603/19/2603.15340v1-dos-dependency-oriented-sampler-for-masked-diffusion-language-models)  
   标签：评分：7.0/10、query:llm
   evidence：掩码扩散语言模型的高效并行解码
8. [100x Cost & Latency Reduction: Performance Analysis of AI Query Approximation using Lightweight Proxy Models](/202603/19/2603.15970v2-100x-cost--latency-reduction-performance-analysis-of-ai-query-approximation-using-lightweight-proxy-models)  
   标签：评分：7.0/10、query:llm
   evidence：通过代理模型实现高效推理
9. [On the Computational Hardness of Transformers](/202603/19/2603.11332v1-on-the-computational-hardness-of-transformers)  
   标签：评分：6.0/10、query:llm
   evidence：注意力机制的计算复杂度与效率研究
10. [Outcome-Aware Tool Selection for Semantic Routers: Latency-Constrained Learning Without LLM Inference](/202603/19/2603.13426v1-outcome-aware-tool-selection-for-semantic-routers-latency-constrained-learning-without-llm-inference)  
   标签：评分：6.0/10、query:llm
   evidence：LLM推理网关中受延迟限制的工具选择
11. [Retrieval-Feedback-Driven Distillation and Preference Alignment for Efficient LLM-based Query Expansion](/202603/19/2603.13776v1-retrieval-feedback-driven-distillation-and-preference-alignment-for-efficient-llm-based-query-expansion)  
   标签：评分：6.0/10、query:llm
   evidence：通过蒸馏实现高效的大模型查询扩展


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
