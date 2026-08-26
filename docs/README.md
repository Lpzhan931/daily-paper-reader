<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-26
- 运行时间：2026-08-26 22:03:26 UTC
- 运行状态：成功
- 本次总论文数：10
- 精读区：6
- 速读区：4

### 今日简报（AI）
今日推荐聚焦高效推理：AgentSpec 实现LLM智能体批量推断的投机解码，VisCache 提出视觉KV缓存剪枝，双双拿下9.0高分。

最值得关注的是投机解码与KV缓存压缩两大方向，分别显著加速LLM智能体推理和视觉大模型长序列处理，兼顾吞吐与显存效率。

后续可优先精读这两篇高分论文，再顺带宽泛浏览稀疏化采样、长上下文生成与视频token压缩等工作，以建立系统认识。
- 详情：[/202608/26/README](/202608/26/README)

### 精读区论文标签
1. [AgentSpec: Speculative Decoding for Batch Inference of LLM Agents](/202608/26/2608.24004v1-agentspec-speculative-decoding-for-batch-inference-of-llm-agents)  
   标签：评分：9.0/10、query:llm
   evidence：用于LLM智能体批量推理的投机解码算法。
2. [VisCache: Visual KV Cache Pruning for Efficient Vision Large Language Model Inference](/202608/26/2608.24063v1-viscache-visual-kv-cache-pruning-for-efficient-vision-large-language-model-inference)  
   标签：评分：9.0/10、query:vlm-spec
   evidence：通过视觉KV缓存剪枝实现高效视觉大语言模型推理
3. [MoNe: Modular Neural Memory for Efficient Long Context Inference](/202608/26/2608.17616v1-mone-modular-neural-memory-for-efficient-long-context-inference)  
   标签：评分：8.0/10、query:llm
   evidence：面向预训练Transformer的高效长上下文推理模块化神经记忆方法。
4. [LiLiCorr: Lightweight Likelihood Correlation of Parallel Drafts for Speculative Decoding](/202608/26/2608.20530v1-lilicorr-lightweight-likelihood-correlation-of-parallel-drafts-for-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：改进投机解码中的草稿连贯性以加速大模型推理
5. [NeuroPrefetcher: Storage-Aware Sparse LLM Inference via Delta Prefetching](/202608/26/2608.22643v1-neuroprefetcher-storage-aware-sparse-llm-inference-via-delta-prefetching)  
   标签：评分：8.0/10、query:llm
   evidence：面向存储感知的稀疏大模型推理，利用增量预取加速超内存场景下的解码
6. [HAP: Head-Adaptive Visual Token Pruning via Cross-Modal Alignment](/202608/26/2608.23921v1-hap-head-adaptive-visual-token-pruning-via-cross-modal-alignment)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：面向VLM的视觉标记剪枝以降低prefill开销

### 速读区论文标签
1. [Reservoir of Importance: Learning Semi-Structured Sparsity with Differentiable Subset Sampling](/202608/26/2608.23048v1-reservoir-of-importance-learning-semi-structured-sparsity-with-differentiable-subset-sampling)  
   标签：评分：8.0/10、query:llm
   evidence：面向大语言模型加速的半结构化N:M稀疏性剪枝
2. [ProxyFormer: A Dual-Stream Proxy Architecture for Ultra-Long Context and High-Resolution Generation](/202608/26/2608.23463v1-proxyformer-a-dual-stream-proxy-architecture-for-ultra-long-context-and-high-resolution-generation)  
   标签：评分：8.0/10、query:llm
   evidence：双流代理架构降低注意力与KV缓存开销
3. [Aggregating Visual Information with Optimal Transport for VideoLM Token Compression](/202608/26/2608.20473v2-aggregating-visual-information-with-optimal-transport-for-videolm-token-compression)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：视频语言模型的Token压缩以减轻解码负担
4. [Learning to Look Again: Loss-Gap Supervision for Free-form Crop Routing in Vision-Language Models](/202608/26/2608.21762v1-learning-to-look-again-loss-gap-supervision-for-free-form-crop-routing-in-vision-language-models)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：面向VLM的选择性重读以避免无差别计算


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
