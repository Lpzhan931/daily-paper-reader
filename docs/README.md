<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-05-12
- 运行时间：2026-05-12 21:00:30 UTC
- 运行状态：成功
- 本次总论文数：15
- 精读区：6
- 速读区：9

### 今日简报（AI）
今日深度解析 15 篇 AI 论文，核心聚焦大模型推理中的 KV Cache 极致压缩与内存架构革新。
重点推荐 ReST-KV 的鲁棒缓存剔除方案，以及通过语义感知内存层级打破 HBM 限制、优化推理效率的新路径。
建议关注长文本处理与边缘端 DeepSeek 推理优化，掌握降低大模型显存门槛与能耗的关键技术。
- 详情：[/202605/12/README](/202605/12/README)

### 精读区论文标签
1. [ReST-KV: Robust KV Cache Eviction with Layer-wise Output Reconstruction and Spatial-Temporal Smoothing](/202605/12/2605.08840v1-rest-kv-robust-kv-cache-eviction-with-layer-wise-output-reconstruction-and-spatial-temporal-smoothing)  
   标签：评分：9.0/10、query:llm
   evidence：基于输出重构的鲁棒KV Cache剔除
2. [Not All Thoughts Need HBM: Semantics-Aware Memory Hierarchy for LLM Reasoning](/202605/12/2605.09490v1-not-all-thoughts-need-hbm-semantics-aware-memory-hierarchy-for-llm-reasoning)  
   标签：评分：9.0/10、query:llm
   evidence：用于KV Cache管理的语义感知内存层级
3. [Sparse Attention as a Range Searching Problem: Towards an Inference-Efficient Index for KV Cache](/202605/12/2605.06763v2-sparse-attention-as-a-range-searching-problem-towards-an-inference-efficient-index-for-kv-cache)  
   标签：评分：8.0/10、query:llm
   evidence：使用稀疏注意力的推理高效 KV Cache 索引
4. [When Does Value-Aware KV Eviction Help? A Fixed-Contract Diagnostic for Non-Monotone Cache Compression](/202605/12/2605.08234v1-when-does-value-aware-kv-eviction-help-a-fixed-contract-diagnostic-for-non-monotone-cache-compression)  
   标签：评分：8.0/10、query:kvcache-survey
   evidence：非单调KV缓存压缩与剔除的诊断分析
5. [RDKV: Rate-Distortion Bit Allocation for Joint Eviction and Quantization of the KV Cache](/202605/12/2605.08317v1-rdkv-rate-distortion-bit-allocation-for-joint-eviction-and-quantization-of-the-kv-cache)  
   标签：评分：8.0/10、query:kvcache-survey
   evidence：KV Cache 的联合剔除与量化
6. [Make Each Token Count: Towards Improving Long-Context Performance with KV Cache Eviction](/202605/12/2605.09649v1-make-each-token-count-towards-improving-long-context-performance-with-kv-cache-eviction)  
   标签：评分：8.0/10、query:llm
   evidence：基于全局保留的长上下文推理 KV 剔除

### 速读区论文标签
1. [Forcing-KV: Hybrid KV Cache Compression for Efficient Autoregressive Video Diffusion Models](/202605/12/2605.09681v1-forcing-kv-hybrid-kv-cache-compression-for-efficient-autoregressive-video-diffusion-models)  
   标签：评分：8.0/10、query:llm
   evidence：视频扩散模型的混合KV Cache压缩
2. [Compute Where it Counts: Self Optimizing Language Models](/202605/12/2605.10875v1-compute-where-it-counts-self-optimizing-language-models)  
   标签：评分：8.0/10、query:llm
   evidence：LLM推理效率的动态预算分配
3. [DSPE: An Energy-Efficient Edge Processor for DeepSeek Inference with MerkleTree-based Incremental Pruning, Multi-Stage Boothing Lookup and Dynamic Adaptive Posit Processing](/202605/12/2605.08615v1-dspe-an-energy-efficient-edge-processor-for-deepseek-inference-with-merkletree-based-incremental-pruning-multi-stage-boothing-lookup-and-dynamic-adaptive-posit-processing)  
   标签：评分：7.0/10、query:llm
   evidence：针对DeepSeek推理的能效边缘处理器，采用剪枝技术
4. [LAQuant: A Simple Overhead-free Large Reasoning Model Quantization by Layer-wise Lookahead Loss](/202605/12/2605.08755v1-laquant-a-simple-overhead-free-large-reasoning-model-quantization-by-layer-wise-lookahead-loss)  
   标签：评分：7.0/10、query:llm
   evidence：量化过程中的 KV Cache 保真度维持
5. [Fitting Is Not Enough: Smoothness in Extremely Quantized LLMs](/202605/12/2605.08894v1-fitting-is-not-enough-smoothness-in-extremely-quantized-llms)  
   标签：评分：7.0/10、query:llm-ef
   evidence：极低比特量化LLM中的平滑度退化分析
6. [Non-Monotonic Latency in Apple MPS Decoding: KV Cache Interactions and Execution Regimes](/202605/12/2605.08913v1-non-monotonic-latency-in-apple-mps-decoding-kv-cache-interactions-and-execution-regimes)  
   标签：评分：7.0/10、query:llm
   evidence：分析Apple MPS上的KV缓存交互与执行机制
7. [KV-RM: Regularizing KV-Cache Movement for Static-Graph LLM Serving](/202605/12/2605.09735v1-kv-rm-regularizing-kv-cache-movement-for-static-graph-llm-serving)  
   标签：评分：7.0/10、query:llm
   evidence：静态图服务中的 KV Cache 移动正则化
8. [Key-Value Means](/202605/12/2605.09877v1-key-value-means)  
   标签：评分：7.0/10、query:llm
   evidence：用于管理增长状态的新型注意力块循环机制
9. [AAAC: Activation-Aware Adaptive Codebooks for 4-bit LLM Weight Quantization](/202605/12/2605.08692v1-aaac-activation-aware-adaptive-codebooks-for-4-bit-llm-weight-quantization)  
   标签：评分：6.0/10、query:llm-ef
   evidence：用于大模型权重量化的激活感知自适应码本


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
