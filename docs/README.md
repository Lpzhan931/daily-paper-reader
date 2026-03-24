<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-03-24
- 运行时间：2026-03-24 19:55:23 UTC
- 运行状态：成功
- 本次总论文数：17
- 精读区：9
- 速读区：8

### 今日简报（AI）
今日深度解析 17 篇 AI 论文，重点攻克大模型推理效率瓶颈，两篇 10 分满分神作领衔 KV Cache 与自适应架构革新。
核心结论指出 KV Cache 优化与 AE-LLM 框架是实现长文本高效推理的关键，而云边端协同路由则为多设备部署提供了新思路。
建议开发者优先研读满分论文以掌握模型降本增效的底层逻辑，并关注 vLLM 语义路由等前沿工程实践。
- 详情：[/202603/24/README](/202603/24/README)

### 精读区论文标签
1. [KV Cache Optimization Strategies for Scalable and Efficient LLM Inference](/202603/24/2603.20397v1-kv-cache-optimization-strategies-for-scalable-and-efficient-llm-inference)  
   标签：评分：10.0/10、query:llm
   evidence：KV缓存优化技术的系统性综述
2. [AE-LLM: Adaptive Efficiency Optimization for Large Language Models](/202603/24/2603.20492v1-ae-llm-adaptive-efficiency-optimization-for-large-language-models)  
   标签：评分：10.0/10、query:llm
   evidence：自动选择和组合LLM效率优化技术的统一框架
3. [MKA: Memory-Keyed Attention for Efficient Long-Context Reasoning](/202603/24/2603.20586v1-mka-memory-keyed-attention-for-efficient-long-context-reasoning)  
   标签：评分：10.0/10、query:llm
   evidence：提出分层KV缓存管理和路由机制，用于高效长文本推理
4. [Beyond Token Eviction: Mixed-Dimension Budget Allocation for Efficient KV Cache Compression](/202603/24/2603.20616v1-beyond-token-eviction-mixed-dimension-budget-allocation-for-efficient-kv-cache-compression)  
   标签：评分：10.0/10、query:llm
   evidence：混合维度KV缓存压缩
5. [ParallelVLM: Lossless Video-LLM Acceleration with Visual Alignment Aware Parallel Speculative Decoding](/202603/24/2603.19610v2-parallelvlm-lossless-video-llm-acceleration-with-visual-alignment-aware-parallel-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：并行投机解码与视觉标记剪枝
6. [CALVO: Improve Serving Efficiency for LLM Inferences with Intense Network Demands](/202603/24/2603.21257v1-calvo-improve-serving-efficiency-for-llm-inferences-with-intense-network-demands)  
   标签：评分：9.0/10、query:llm
   evidence：分布式前缀缓存与KV缓存加载优化
7. [TIDE: Token-Informed Depth Execution for Per-Token Early Exit in LLM Inference](/202603/24/2603.21365v1-tide-token-informed-depth-execution-for-per-token-early-exit-in-llm-inference)  
   标签：评分：9.0/10、query:llm
   evidence：逐Token早退机制加速推理
8. [PRISM: Breaking the O(n) Memory Wall in Long-Context LLM Inference via O(1) Photonic Block Selection](/202603/24/2603.21576v1-prism-breaking-the-on-memory-wall-in-long-context-llm-inference-via-o1-photonic-block-selection)  
   标签：评分：9.0/10、query:llm
   evidence：用于KV缓存获取的O(1)光子块选择技术
9. [Chimera: Latency- and Performance-Aware Multi-agent Serving for Heterogeneous LLMs](/202603/24/2603.22206v1-chimera-latency--and-performance-aware-multi-agent-serving-for-heterogeneous-llms)  
   标签：评分：9.0/10、query:llm
   evidence：异构集群多智能体服务的预测性调度

### 速读区论文标签
1. [ResPrune: Text-Conditioned Subspace Reconstruction for Visual Token Pruning in Large Vision-Language Models](/202603/24/2603.21105v1-resprune-text-conditioned-subspace-reconstruction-for-visual-token-pruning-in-large-vision-language-models)  
   标签：评分：8.0/10、query:llm
   evidence：用于高效推理的视觉标记剪枝
2. [ConsRoute:Consistency-Aware Adaptive Query Routing for Cloud-Edge-Device Large Language Models](/202603/24/2603.21237v1-consrouteconsistency-aware-adaptive-query-routing-for-cloud-edge-device-large-language-models)  
   标签：评分：8.0/10、query:llm
   evidence：用于提高推理效率的自适应查询路由
3. [The Workload-Router-Pool Architecture for LLM Inference Optimization: A Vision Paper from the vLLM Semantic Router Project](/202603/24/2603.21354v1-the-workload-router-pool-architecture-for-llm-inference-optimization-a-vision-paper-from-the-vllm-semantic-router-project)  
   标签：评分：8.0/10、query:llm
   evidence：vLLM语义路由推理优化与集群配置
4. [Memori: A Persistent Memory Layer for Efficient, Context-Aware LLM Agents](/202603/24/2603.19935v1-memori-a-persistent-memory-layer-for-efficient-context-aware-llm-agents)  
   标签：评分：7.0/10、query:llm
   evidence：LLM智能体的高效上下文感知记忆层
5. [WWW.Serve: Interconnecting Global LLM Services through Decentralization](/202603/24/2603.20661v1-wwwserve-interconnecting-global-llm-services-through-decentralization)  
   标签：评分：7.0/10、query:llm
   evidence：互联LLM服务的去中心化框架
6. [Task-Specific Efficiency Analysis: When Small Language Models Outperform Large Language Models](/202603/24/2603.21389v1-task-specific-efficiency-analysis-when-small-language-models-outperform-large-language-models)  
   标签：评分：7.0/10、query:llm
   evidence：吞吐量与延迟的效率分析
7. [Dual-Space Knowledge Distillation with Key-Query Matching for Large Language Models with Vocabulary Mismatch](/202603/24/2603.22056v1-dual-space-knowledge-distillation-with-key-query-matching-for-large-language-models-with-vocabulary-mismatch)  
   标签：评分：7.0/10、query:llm
   evidence：通过知识蒸馏训练更小且高效的学生模型
8. [Nudging Hidden States: Training-Free Model Steering for Chain-of-Thought Reasoning in Large Audio-Language Models](/202603/24/2603.14636v1-nudging-hidden-states-training-free-model-steering-for-chain-of-thought-reasoning-in-large-audio-language-models)  
   标签：评分：6.0/10、query:llm
   evidence：推理阶段的模型引导以提升推理效率


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
