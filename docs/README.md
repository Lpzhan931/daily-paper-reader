<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-04-11 ~ 2026-05-10
- 运行时间：2026-05-10 08:51:08 UTC
- 运行状态：成功
- 本次总论文数：41
- 精读区：0
- 速读区：41

### 今日简报（AI）
本期速览 41 篇前沿论文，深度聚焦大模型长文本推理中的 KV Cache 性能瓶颈。
重点推荐 CodeComp 与 IceCache，揭示了结构化压缩与语义化留存是实现高效智能体编程与长序列管理的核心趋势。
建议开发者优先关注 KV Cache 优化方案，以应对长上下文应用中的显存压力与推理延迟。
- 详情：[/20260411-20260510/README](/20260411-20260510/README)

### 精读区论文标签
- 本次无精读推荐。

### 速读区论文标签
1. [CodeComp: Structural KV Cache Compression for Agentic Coding](/20260411-20260510/2604.10235v1-codecomp-structural-kv-cache-compression-for-agentic-coding)  
   标签：评分：9.0/10、query:llm
   evidence：面向智能体代码任务的结构化 KV 缓存压缩
2. [IceCache: Memory-efficient KV-cache Management for Long-Sequence LLMs](/20260411-20260510/2604.10539v1-icecache-memory-efficient-kv-cache-management-for-long-sequence-llms)  
   标签：评分：9.0/10、query:llm
   evidence：使用语义令牌聚类进行高效的 KV 缓存管理
3. [Transactional Attention: Semantic Sponsorship for KV-Cache Retention](/20260411-20260510/2604.11288v1-transactional-attention-semantic-sponsorship-for-kv-cache-retention)  
   标签：评分：9.0/10、query:llm
   evidence：用于 KV 缓存保留的语义赞助机制
4. [Quantization Dominates Rank Reduction for KV-Cache Compression](/20260411-20260510/2604.11501v1-quantization-dominates-rank-reduction-for-kv-cache-compression)  
   标签：评分：9.0/10、query:kvcache-survey
   evidence：KV缓存压缩中量化与秩削减的对比研究
5. [KV Packet: Recomputation-Free Context-Independent KV Caching for LLMs](/20260411-20260510/2604.13226v1-kv-packet-recomputation-free-context-independent-kv-caching-for-llms)  
   标签：评分：9.0/10、query:kvcache-survey
   evidence：提出KV Packet实现无重计算且上下文无关的KV缓存复用。
6. [Graph-Guided Adaptive Channel Elimination for KV Cache Compression](/20260411-20260510/2604.16983v1-graph-guided-adaptive-channel-elimination-for-kv-cache-compression)  
   标签：评分：9.0/10、query:kvcache-survey
   evidence：使用自适应通道剪枝/消除的KV缓存压缩
7. [Towards Joint Quantization and Token Pruning of Vision-Language Models](/20260411-20260510/2604.17320v1-towards-joint-quantization-and-token-pruning-of-vision-language-models)  
   标签：评分：9.0/10、query:kvcache-survey
   evidence：针对多模态模型提出量化与标记剪枝的联合框架以降低KV缓存成本。
8. [MoE-nD: Per-Layer Mixture-of-Experts Routing for Multi-Axis KV Cache Compression](/20260411-20260510/2604.17695v1-moe-nd-per-layer-mixture-of-experts-routing-for-multi-axis-kv-cache-compression)  
   标签：评分：9.0/10、query:llm
   evidence：使用逐层混合专家路由进行多维 KV 缓存压缩
9. [DASH-KV: Accelerating Long-Context LLM Inference via Asymmetric KV Cache Hashing](/20260411-20260510/2604.19351v2-dash-kv-accelerating-long-context-llm-inference-via-asymmetric-kv-cache-hashing)  
   标签：评分：9.0/10、query:kvcache-survey
   evidence：DASH-KV利用非对称深度哈希进行KV缓存压缩和加速。
10. [DepthKV: Layer-Dependent KV Cache Pruning for Long-Context LLM Inference](/20260411-20260510/2604.24647v1-depthkv-layer-dependent-kv-cache-pruning-for-long-context-llm-inference)  
   标签：评分：9.0/10、query:kvcache-survey
   evidence：为长文本LLM引入了层依赖的KV缓存剪枝方法DepthKV。
11. [Rethinking KV Cache Eviction via a Unified Information-Theoretic Objective](/20260411-20260510/2604.25975v1-rethinking-kv-cache-eviction-via-a-unified-information-theoretic-objective)  
   标签：评分：9.0/10、query:llm
   evidence：基于信息瓶颈原理的 KV 缓存剔除
12. [HeadQ: Model-Visible Distortion and Score-Space Correction for KV-Cache Quantization](/20260411-20260510/2605.03562v2-headq-model-visible-distortion-and-score-space-correction-for-kv-cache-quantization)  
   标签：评分：9.0/10、query:kvcache-survey
   evidence：提出HeadQ方法，利用模型可见坐标和Logit修正进行KV缓存量化。
13. [When Quantization Is Free: An int4 KV Cache That Outruns fp16 on Apple Silicon](/20260411-20260510/2605.05699v1-when-quantization-is-free-an-int4-kv-cache-that-outruns-fp16-on-apple-silicon)  
   标签：评分：9.0/10、query:kvcache-survey
   evidence：用于推理加速的 int4 KV 缓存量化
14. [ZoomR: Memory Efficient Reasoning through Multi-Granularity Key Value Retrieval](/20260411-20260510/2604.10898v1-zoomr-memory-efficient-reasoning-through-multi-granularity-key-value-retrieval)  
   标签：评分：8.0/10、query:llm
   evidence：针对长输出推理任务的KV缓存优化
15. [CASK: Core-Aware Selective KV Compression for Reasoning Traces](/20260411-20260510/2604.10900v1-cask-core-aware-selective-kv-compression-for-reasoning-traces)  
   标签：评分：8.0/10、query:llm
   evidence：针对推理轨迹的选择性 KV 压缩
16. [Latent-Condensed Transformer for Efficient Long Context Modeling](/20260411-20260510/2604.12452v1-latent-condensed-transformer-for-efficient-long-context-modeling)  
   标签：评分：8.0/10、query:llm
   evidence：在MLA潜空间内压缩上下文以实现高效建模
17. [Latent-Condensed Transformer for Efficient Long Context Modeling](/20260411-20260510/2604.12452v2-latent-condensed-transformer-for-efficient-long-context-modeling)  
   标签：评分：8.0/10、query:llm
   evidence：在MLA潜空间内压缩上下文以实现高效建模
18. [KV Packet: Recomputation-Free Context-Independent KV Caching for LLMs](/20260411-20260510/2604.13226v2-kv-packet-recomputation-free-context-independent-kv-caching-for-llms)  
   标签：评分：8.0/10、query:llm
   evidence：大语言模型中无需重计算且上下文无关的 KV 缓存
19. [YOCO++: Enhancing YOCO with KV Residual Connections for Efficient LLM Inference](/20260411-20260510/2604.13556v1-yoco-enhancing-yoco-with-kv-residual-connections-for-efficient-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：用于大模型高效推理的跨层KV压缩
20. [Reducing Peak Memory Usage for Modern Multimodal Large Language Model Pipelines](/20260411-20260510/2604.16734v1-reducing-peak-memory-usage-for-modern-multimodal-large-language-model-pipelines)  
   标签：评分：8.0/10、query:llm
   evidence：多模态大模型KV缓存压缩以降低峰值显存
21. [HieraSparse: Hierarchical Semi-Structured Sparse KV Attention](/20260411-20260510/2604.16864v1-hierasparse-hierarchical-semi-structured-sparse-kv-attention)  
   标签：评分：8.0/10、query:llm
   evidence：分层KV缓存压缩框架及加速算子
22. [Open-TQ-Metal: Fused Compressed-Domain Attention for Long-Context LLM Inference on Apple Silicon](/20260411-20260510/2604.16957v1-open-tq-metal-fused-compressed-domain-attention-for-long-context-llm-inference-on-apple-silicon)  
   标签：评分：8.0/10、query:llm
   evidence：融合压缩域注意力与 int4 KV 缓存量化
23. [River-LLM: Large Language Model Seamless Exit Based on KV Share](/20260411-20260510/2604.18396v1-river-llm-large-language-model-seamless-exit-based-on-kv-share)  
   标签：评分：8.0/10、query:llm
   evidence：基于KV共享的早期退出推理加速
24. [SAW-INT4: System-Aware 4-Bit KV-Cache Quantization for Real-World LLM Serving](/20260411-20260510/2604.19157v1-saw-int4-system-aware-4-bit-kv-cache-quantization-for-real-world-llm-serving)  
   标签：评分：8.0/10、query:llm
   evidence：面向实际部署的系统感知 4-bit KV 缓存量化
25. [DASH-KV: Accelerating Long-Context LLM Inference via Asymmetric KV Cache Hashing](/20260411-20260510/2604.19351v1-dash-kv-accelerating-long-context-llm-inference-via-asymmetric-kv-cache-hashing)  
   标签：评分：8.0/10、query:llm
   evidence：通过 KV 缓存哈希加速长文本大语言模型推理
26. [Forget, Then Recall: Learnable Compression and Selective Unfolding via Gist Sparse Attention](/20260411-20260510/2604.20920v1-forget-then-recall-learnable-compression-and-selective-unfolding-via-gist-sparse-attention)  
   标签：评分：8.0/10、query:llm
   evidence：通过可学习的要点标记和稀疏注意力进行KV缓存压缩
27. [SparKV: Overhead-Aware KV Cache Loading for Efficient On-Device LLM Inference](/20260411-20260510/2604.21231v1-sparkv-overhead-aware-kv-cache-loading-for-efficient-on-device-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：针对端侧大模型推理的自适应 KV 缓存加载
28. [Sub-Token Routing in LoRA for Adaptation and Query-Aware KV Compression](/20260411-20260510/2604.21335v1-sub-token-routing-in-lora-for-adaptation-and-query-aware-kv-compression)  
   标签：评分：8.0/10、query:llm
   evidence：用于查询感知 KV 压缩的子 Token 路由
29. [Salca: A Sparsity-Aware Hardware Accelerator for Efficient Long-Context Attention Decoding](/20260411-20260510/2604.24820v1-salca-a-sparsity-aware-hardware-accelerator-for-efficient-long-context-attention-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：针对长文本 KV 缓存和稀疏注意力的硬件加速器
30. [PolyKV: A Shared Asymmetrically-Compressed KV Cache Pool for Multi-Agent LLM Inference](/20260411-20260510/2604.24971v1-polykv-a-shared-asymmetrically-compressed-kv-cache-pool-for-multi-agent-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：多智能体推理中的共享非对称压缩 KV 缓存池
31. [Make Your LVLM KV Cache More Lightweight](/20260411-20260510/2605.00789v1-make-your-lvlm-kv-cache-more-lightweight)  
   标签：评分：8.0/10、query:llm
   evidence：通过视觉标记压缩实现轻量化LVLM KV缓存
32. [SplitZip: Ultra Fast Lossless KV Compression for Disaggregated LLM Serving](/20260411-20260510/2605.01708v1-splitzip-ultra-fast-lossless-kv-compression-for-disaggregated-llm-serving)  
   标签：评分：8.0/10、query:llm
   evidence：针对解耦式大模型服务的无损 KV 压缩
33. [Stochastic Sparse Attention for Memory-Bound Inference](/20260411-20260510/2605.01910v1-stochastic-sparse-attention-for-memory-bound-inference)  
   标签：评分：8.0/10、query:llm
   evidence：稀疏化 Value 缓存访问以解决内存受限的推理问题
34. [WindowQuant: Mixed-Precision KV Cache Quantization based on Window-Level Similarity for VLMs Inference Optimization](/20260411-20260510/2605.02262v1-windowquant-mixed-precision-kv-cache-quantization-based-on-window-level-similarity-for-vlms-inference-optimization)  
   标签：评分：8.0/10、query:llm
   evidence：针对视觉语言模型的混合精度 KV 缓存量化
35. [HeadQ: Model-Visible Distortion and Score-Space Correction for KV-Cache Quantization](/20260411-20260510/2605.03562v1-headq-model-visible-distortion-and-score-space-correction-for-kv-cache-quantization)  
   标签：评分：8.0/10、query:llm
   evidence：KV 缓存量化的模型可见失真度量
36. [AdapShot: Adaptive Many-Shot In-Context Learning with Semantic-Aware KV Cache Reuse](/20260411-20260510/2605.03644v1-adapshot-adaptive-many-shot-in-context-learning-with-semantic-aware-kv-cache-reuse)  
   标签：评分：8.0/10、query:llm
   evidence：多样本ICL高效推理中的KV缓存复用
37. [QKVShare: Quantized KV-Cache Handoff for Multi-Agent On-Device LLMs](/20260411-20260510/2605.03884v1-qkvshare-quantized-kv-cache-handoff-for-multi-agent-on-device-llms)  
   标签：评分：8.0/10、query:kvcache-survey
   evidence：端侧多智能体大语言模型的量化 KV 缓存移交
38. [A Queueing-Theoretic Framework for Stability Analysis of LLM Inference with KV Cache Memory Constraints](/20260411-20260510/2605.04595v1-a-queueing-theoretic-framework-for-stability-analysis-of-llm-inference-with-kv-cache-memory-constraints)  
   标签：评分：8.0/10、query:llm
   evidence：利用排队论分析了KV缓存内存限制下的LLM推理稳定性。
39. [Irminsul: MLA-Native Position-Independent Caching for Agentic LLM Serving](/20260411-20260510/2605.05696v1-irminsul-mla-native-position-independent-caching-for-agentic-llm-serving)  
   标签：评分：8.0/10、query:llm
   evidence：面向大模型服务的MLA原生位置无关缓存
40. [Requests of a Feather Must Flock Together: Batch Size vs. Prefix Homogeneity in LLM Inference](/20260411-20260510/2605.06046v1-requests-of-a-feather-must-flock-together-batch-size-vs-prefix-homogeneity-in-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：通过前缀同质化批处理优化KV缓存访问的局部性。
41. [Efficient Serving for Dynamic Agent Workflows with Prediction-based KV-Cache Management](/20260411-20260510/2605.06472v1-efficient-serving-for-dynamic-agent-workflows-with-prediction-based-kv-cache-management)  
   标签：评分：8.0/10、query:llm
   evidence：基于预测的动态智能体工作流KV缓存管理


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
