<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-04-14
- 运行时间：2026-04-14 20:13:48 UTC
- 运行状态：成功
- 本次总论文数：23
- 精读区：12
- 速读区：11

### 今日简报（AI）
今日深度研读 23 篇前沿论文，重点攻克分布式边缘云推理优化与投机采样树扩展等 LLM 性能瓶颈。
满分佳作 ConfigSpec 与 SMART 揭示了通过配置优化与智能树扩展，能显著提升边缘云协作及投机采样的推理效率。
建议优先关注投机采样在复杂环境下的落地，并同步了解多轮对话与视频大模型的轻量化量化方案。
- 详情：[/202604/14/README](/202604/14/README)

### 精读区论文标签
1. [ConfigSpec: Profiling-Based Configuration Selection for Distributed Edge--Cloud Speculative LLM Serving](/202604/14/2604.09722v1-configspec-profiling-based-configuration-selection-for-distributed-edge--cloud-speculative-llm-serving)  
   标签：评分：10.0/10、query:llm
   evidence：分布式投机大模型服务的配置选择
2. [SMART: When is it Actually Worth Expanding a Speculative Tree?](/202604/14/2604.09731v1-smart-when-is-it-actually-worth-expanding-a-speculative-tree)  
   标签：评分：10.0/10、query:llm
   evidence：投机解码树构建的系统感知边际分析
3. [SpecMoE: A Fast and Efficient Mixture-of-Experts Inference via Self-Assisted Speculative Decoding](/202604/14/2604.10152v1-specmoe-a-fast-and-efficient-mixture-of-experts-inference-via-self-assisted-speculative-decoding)  
   标签：评分：10.0/10、query:llm
   evidence：针对MoE推理的自辅助投机解码
4. [IceCache: Memory-efficient KV-cache Management for Long-Sequence LLMs](/202604/14/2604.10539v1-icecache-memory-efficient-kv-cache-management-for-long-sequence-llms)  
   标签：评分：10.0/10、query:llm
   evidence：结合 PagedAttention 的高效 KV 缓存管理
5. [ZoomR: Memory Efficient Reasoning through Multi-Granularity Key Value Retrieval](/202604/14/2604.10898v1-zoomr-memory-efficient-reasoning-through-multi-granularity-key-value-retrieval)  
   标签：评分：10.0/10、query:llm
   evidence：针对长输出的动态KV缓存选择与压缩
6. [CASK: Core-Aware Selective KV Compression for Reasoning Traces](/202604/14/2604.10900v1-cask-core-aware-selective-kv-compression-for-reasoning-traces)  
   标签：评分：10.0/10、query:llm
   evidence：针对长文本推理链的KV缓存压缩
7. [Quantization Dominates Rank Reduction for KV-Cache Compression](/202604/14/2604.11501v1-quantization-dominates-rank-reduction-for-kv-cache-compression)  
   标签：评分：10.0/10、query:llm
   evidence：比较量化与秩削减的KV缓存压缩研究
8. [MoBiE: Efficient Inference of Mixture of Binary Experts under Post-Training Quantization](/202604/14/2604.06798v2-mobie-efficient-inference-of-mixture-of-binary-experts-under-post-training-quantization)  
   标签：评分：9.0/10、query:llm
   evidence：通过二值化和SVD实现MoE大模型的高效推理
9. [A-IO: Adaptive Inference Orchestration for Memory-Bound NPUs](/202604/14/2604.09752v1-a-io-adaptive-inference-orchestration-for-memory-bound-npus)  
   标签：评分：9.0/10、query:llm
   evidence：解决NPU上投机解码的内核同步开销问题
10. [LoopGuard: Breaking Self-Reinforcing Attention Loops via Dynamic KV Cache Intervention](/202604/14/2604.10044v1-loopguard-breaking-self-reinforcing-attention-loops-via-dynamic-kv-cache-intervention)  
   标签：评分：9.0/10、query:llm
   evidence：通过动态KV缓存干预打破重复循环
11. [RouterWise: Joint Resource Allocation and Routing for Latency-Aware Multi-Model LLM Serving](/202604/14/2604.10907v1-routerwise-joint-resource-allocation-and-routing-for-latency-aware-multi-model-llm-serving)  
   标签：评分：9.0/10、query:llm
   evidence：针对延迟敏感型大模型推理的联合资源分配与路由
12. [Flow-Controlled Scheduling for LLM Inference with Provable Stability Guarantees](/202604/14/2604.11001v1-flow-controlled-scheduling-for-llm-inference-with-provable-stability-guarantees)  
   标签：评分：9.0/10、query:llm
   evidence：通过流量控制调度优化大模型服务的吞吐量与稳定性

### 速读区论文标签
1. [MT-OSC: Path for LLMs that Get Lost in Multi-Turn Conversation](/202604/14/2604.08782v1-mt-osc-path-for-llms-that-get-lost-in-multi-turn-conversation)  
   标签：评分：8.0/10、query:llm
   evidence：多轮对话推理中的高效上下文压缩
2. [Tango: Taming Visual Signals for Efficient Video Large Language Models](/202604/14/2604.09547v2-tango-taming-visual-signals-for-efficient-video-large-language-models)  
   标签：评分：8.0/10、query:llm
   evidence：针对高效视频LLM的Token剪枝
3. [ReSpinQuant: Efficient Layer-Wise LLM Quantization via Subspace Residual Rotation Approximation](/202604/14/2604.11080v1-respinquant-efficient-layer-wise-llm-quantization-via-subspace-residual-rotation-approximation)  
   标签：评分：8.0/10、query:llm
   evidence：高效的逐层LLM量化框架
4. [Decoupled Similarity for Task-Aware Token Pruning in Large Vision-Language Models](/202604/14/2604.11240v1-decoupled-similarity-for-task-aware-token-pruning-in-large-vision-language-models)  
   标签：评分：8.0/10、query:llm
   evidence：视觉语言模型中的任务感知令牌剪枝
5. [EdgeCIM: A Hardware-Software Co-Design for CIM-Based Acceleration of Small Language Models](/202604/14/2604.11512v1-edgecim-a-hardware-software-co-design-for-cim-based-acceleration-of-small-language-models)  
   标签：评分：8.0/10、query:llm
   evidence：基于存内计算的大模型加速软硬件协同设计
6. [MemCoT: Test-Time Scaling through Memory-Driven Chain-of-Thought](/202604/14/2604.08216v2-memcot-test-time-scaling-through-memory-driven-chain-of-thought)  
   标签：评分：7.0/10、query:llm
   evidence：长上下文推理的测试时内存扩展
7. [Agentic Compilation: Mitigating the LLM Rerun Crisis for Minimized-Inference-Cost Web Automation](/202604/14/2604.09718v1-agentic-compilation-mitigating-the-llm-rerun-crisis-for-minimized-inference-cost-web-automation)  
   标签：评分：7.0/10、query:llm
   evidence：最小化Web自动化智能体的推理成本
8. [Efficient Matrix Implementation for Rotary Position Embedding](/202604/14/2604.09742v1-efficient-matrix-implementation-for-rotary-position-embedding)  
   标签：评分：7.0/10、query:llm
   evidence：注意力机制中RoPE的高效矩阵实现
9. [POINTS-Long: Adaptive Dual-Mode Visual Reasoning in MLLMs](/202604/14/2604.11627v1-points-long-adaptive-dual-mode-visual-reasoning-in-mllms)  
   标签：评分：7.0/10、query:llm
   evidence：动态视觉Token缩放实现高效推理
10. [Dynamic Ranked List Truncation for Reranking Pipelines via LLM-generated Reference-Documents](/202604/14/2604.09492v1-dynamic-ranked-list-truncation-for-reranking-pipelines-via-llm-generated-reference-documents)  
   标签：评分：6.0/10、query:llm
   evidence：通过排序列表截断实现高效重排序
11. [SinkTrack: Attention Sink based Context Anchoring for Large Language Models](/202604/14/2604.10027v1-sinktrack-attention-sink-based-context-anchoring-for-large-language-models)  
   标签：评分：6.0/10、query:llm
   evidence：基于注意力汇聚的上下文锚定


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
