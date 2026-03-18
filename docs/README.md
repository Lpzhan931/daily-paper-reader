<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-03-18
- 运行时间：2026-03-18 19:56:34 UTC
- 运行状态：成功
- 本次总论文数：22
- 精读区：11
- 速读区：11

### 今日简报（AI）
今日深度解析 22 篇 AI 论文，重点聚焦 KV 缓存压缩与扩散大模型（Diffusion LLM）的推理加速。
满分神作 VQKV 实现了高保真、高倍率的缓存压缩，ES-dLLM 则通过早停机制大幅优化了扩散模型的生成效率。
推荐优先研读 KV Cache 优化与 MoE 冗余削减方案，这是当前提升大模型长文本与多智能体性能的核心趋势。
- 详情：[/202603/18/README](/202603/18/README)

### 精读区论文标签
1. [VQKV: High-Fidelity and High-Ratio Cache Compression via Vector-Quantization](/202603/18/2603.16435v1-vqkv-high-fidelity-and-high-ratio-cache-compression-via-vector-quantization)  
   标签：评分：10.0/10、query:llm
   evidence：通过矢量量化进行KV缓存压缩
2. [ES-dLLM: Efficient Inference for Diffusion Large Language Models by Early-Skipping](/202603/18/2603.10088v1-es-dllm-efficient-inference-for-diffusion-large-language-models-by-early-skipping)  
   标签：评分：9.0/10、query:llm
   evidence：通过跳过标记实现扩散大语言模型的推理加速框架
3. [Serving Hybrid LLM Loads with SLO Guarantees Using CPU-GPU Attention Piggybacking](/202603/18/2603.12831v2-serving-hybrid-llm-loads-with-slo-guarantees-using-cpu-gpu-attention-piggybacking)  
   标签：评分：9.0/10、query:llm
   evidence：优化混合LLM负载的吞吐量和延迟
4. [Learning to Forget: Sleep-Inspired Memory Consolidation for Resolving Proactive Interference in Large Language Models](/202603/18/2603.14517v1-learning-to-forget-sleep-inspired-memory-consolidation-for-resolving-proactive-interference-in-large-language-models)  
   标签：评分：9.0/10、query:llm
   evidence：在KV缓存上实现学习型睡眠周期
5. [FlashHead: Efficient Drop-In Replacement for the Classification Head in Language Model Inference](/202603/18/2603.14591v1-flashhead-efficient-drop-in-replacement-for-the-classification-head-in-language-model-inference)  
   标签：评分：9.0/10、query:llm
   evidence：推理中分类层的高效替代方案
6. [MobileLLM-Flash: Latency-Guided On-Device LLM Design for Industry Scale](/202603/18/2603.15954v1-mobilellm-flash-latency-guided-on-device-llm-design-for-industry-scale)  
   标签：评分：9.0/10、query:llm
   evidence：端侧LLM设计，采用注意力跳过技术进行加速
7. [inference-fleet-sim: A Queueing-Theory-Grounded Fleet Capacity Planner for LLM Inference](/202603/18/2603.16054v1-inference-fleet-sim-a-queueing-theory-grounded-fleet-capacity-planner-for-llm-inference)  
   标签：评分：9.0/10、query:llm
   evidence：大模型推理延迟与吞吐量的集群容量规划器
8. [Efficient LLM Serving for Agentic Workflows: A Data Systems Perspective](/202603/18/2603.16104v1-efficient-llm-serving-for-agentic-workflows-a-data-systems-perspective)  
   标签：评分：9.0/10、query:llm
   evidence：针对智能体工作流的高效大模型服务
9. [Frequency Matters: Fast Model-Agnostic Data Curation for Pruning and Quantization](/202603/18/2603.16105v1-frequency-matters-fast-model-agnostic-data-curation-for-pruning-and-quantization)  
   标签：评分：9.0/10、query:llm
   evidence：用于剪枝和量化的数据筛选策略
10. [SpecSteer: Synergizing Local Context and Global Reasoning for Efficient Personalized Generation](/202603/18/2603.16219v1-specsteer-synergizing-local-context-and-global-reasoning-for-efficient-personalized-generation)  
   标签：评分：9.0/10、query:llm
   evidence：将投机采样用于分布式推理加速
11. [FleetOpt: Analytical Fleet Provisioning for LLM Inference with Compress-and-Route as Implementation Mechanism](/202603/18/2603.16514v1-fleetopt-analytical-fleet-provisioning-for-llm-inference-with-compress-and-route-as-implementation-mechanism)  
   标签：评分：9.0/10、query:llm
   evidence：通过管理空闲KV缓存槽位优化GPU容量

### 速读区论文标签
1. [LightMoE: Reducing Mixture-of-Experts Redundancy through Expert Replacing](/202603/18/2603.12645v1-lightmoe-reducing-mixture-of-experts-redundancy-through-expert-replacing)  
   标签：评分：8.0/10、query:llm
   evidence：MoE大模型压缩中的专家替换技术
2. [Efficient and Interpretable Multi-Agent LLM Routing via Ant Colony Optimization](/202603/18/2603.12933v1-efficient-and-interpretable-multi-agent-llm-routing-via-ant-colony-optimization)  
   标签：评分：8.0/10、query:llm
   evidence：高效的多智能体路由以降低LLM推理成本和延迟
3. [Dependency-Aware Parallel Decoding via Attention for Diffusion LLMs](/202603/18/2603.12996v1-dependency-aware-parallel-decoding-via-attention-for-diffusion-llms)  
   标签：评分：8.0/10、query:llm
   evidence：通过注意力机制实现扩散LLM的并行解码
4. [CAMD: Coverage-Aware Multimodal Decoding for Efficient Reasoning of Multimodal Large Language Models](/202603/18/2603.14745v1-camd-coverage-aware-multimodal-decoding-for-efficient-reasoning-of-multimodal-large-language-models)  
   标签：评分：8.0/10、query:llm
   evidence：多模态大语言模型的高效解码
5. [Optimal Expert-Attention Allocation in Mixture-of-Experts: A Scalable Law for Dynamic Model Design](/202603/18/2603.10379v1-optimal-expert-attention-allocation-in-mixture-of-experts-a-scalable-law-for-dynamic-model-design)  
   标签：评分：7.0/10、query:llm
   evidence：MoE模型中专家与注意力的最优计算分配以实现高效扩展
6. [Leech Lattice Vector Quantization for Efficient LLM Compression](/202603/18/2603.11021v1-leech-lattice-vector-quantization-for-efficient-llm-compression)  
   标签：评分：7.0/10、query:llm
   evidence：用于高效大模型压缩的向量量化
7. [Summarize Before You Speak with ARACH: A Training-Free Inference-Time Plug-In for Enhancing LLMs via Global Attention Reallocation](/202603/18/2603.11067v1-summarize-before-you-speak-with-arach-a-training-free-inference-time-plug-in-for-enhancing-llms-via-global-attention-reallocation)  
   标签：评分：7.0/10、query:llm
   evidence：LLM免训练推理时插件
8. [Spend Less, Reason Better: Budget-Aware Value Tree Search for LLM Agents](/202603/18/2603.12634v1-spend-less-reason-better-budget-aware-value-tree-search-for-llm-agents)  
   标签：评分：7.0/10、query:llm
   evidence：大模型智能体的预算感知推理框架
9. [Duration Aware Scheduling for ASR Serving Under Workload Drift](/202603/18/2603.11273v1-duration-aware-scheduling-for-asr-serving-under-workload-drift)  
   标签：评分：6.0/10、query:llm
   evidence：集成到vLLM中的语音识别服务调度
10. [On the Nature of Attention Sink that Shapes Decoding Strategy in MLLMs](/202603/18/2603.14337v1-on-the-nature-of-attention-sink-that-shapes-decoding-strategy-in-mllms)  
   标签：评分：6.0/10、query:llm
   evidence：基于注意力汇聚点的推理策略
11. [Compute Allocation for Reasoning-Intensive Retrieval Agents](/202603/18/2603.14635v1-compute-allocation-for-reasoning-intensive-retrieval-agents)  
   标签：评分：6.0/10、query:llm
   evidence：检索流水线中的计算分配以管理推理成本


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
