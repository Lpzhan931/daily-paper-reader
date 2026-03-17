<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-03-17
- 运行时间：2026-03-17 20:12:41 UTC
- 运行状态：成功
- 本次总论文数：21
- 精读区：10
- 速读区：11

### 今日简报（AI）
今日深度复盘 21 篇 AI 论文，聚焦 KV Cache 压缩与高效调度等 10 项满分级硬核突破。
核心推荐：利用压缩 Key 预测稀疏注意力的 Self-Indexing 机制，以及仅靠乘法实现极简调度的 LMetric 方案。
建议优先研读大模型推理性能优化，特别是量化误差重构与自适应解码带来的效率提升。
- 详情：[/202603/17/README](/202603/17/README)

### 精读区论文标签
1. [Self-Indexing KVCache: Predicting Sparse Attention from Compressed Keys](/202603/17/2603.14224v1-self-indexing-kvcache-predicting-sparse-attention-from-compressed-keys)  
   标签：评分：10.0/10、query:llm
   evidence：用于稀疏注意力的自索引KV缓存
2. [LMetric: Simple is Better - Multiplication May Be All You Need for LLM Request Scheduling](/202603/17/2603.15202v1-lmetric-simple-is-better---multiplication-may-be-all-you-need-for-llm-request-scheduling)  
   标签：评分：10.0/10、query:llm
   evidence：优化LLM请求调度以提升吞吐量和KV缓存局部性
3. [DyLLM: Efficient Diffusion LLM Inference via Saliency-based Token Selection and Partial Attention](/202603/17/2603.08026v1-dyllm-efficient-diffusion-llm-inference-via-saliency-based-token-selection-and-partial-attention)  
   标签：评分：9.0/10、query:llm
   evidence：通过标记选择和部分注意力实现高效扩散LLM推理
4. [The Missing Memory Hierarchy: Demand Paging for LLM Context Windows](/202603/17/2603.09023v1-the-missing-memory-hierarchy-demand-paging-for-llm-context-windows)  
   标签：评分：9.0/10、query:llm
   evidence：针对LLM上下文窗口的需求分页系统，减少结构性浪费
5. [WVA: A Global Optimization Control Plane for llmd](/202603/17/2603.09730v1-wva-a-global-optimization-control-plane-for-llmd)  
   标签：评分：9.0/10、query:llm
   evidence：通过全局控制平面优化大模型推理的吞吐量和延迟
6. [Slow-Fast Inference: Training-Free Inference Acceleration via Within-Sentence Support Stability](/202603/17/2603.12038v1-slow-fast-inference-training-free-inference-acceleration-via-within-sentence-support-stability)  
   标签：评分：9.0/10、query:llm
   evidence：通过注意力稳定性实现的免训练推理加速
7. [IndexCache: Accelerating Sparse Attention via Cross-Layer Index Reuse](/202603/17/2603.12201v1-indexcache-accelerating-sparse-attention-via-cross-layer-index-reuse)  
   标签：评分：9.0/10、query:llm
   evidence：通过跨层索引复用加速稀疏注意力
8. [Dynamic Sparse Attention: Access Patterns and Architecture](/202603/17/2603.13430v1-dynamic-sparse-attention-access-patterns-and-architecture)  
   标签：评分：9.0/10、query:llm
   evidence：动态稀疏注意力与 KV 缓存局部性
9. [GradMem: Learning to Write Context into Memory with Test-Time Gradient Descent](/202603/17/2603.13875v1-gradmem-learning-to-write-context-into-memory-with-test-time-gradient-descent)  
   标签：评分：9.0/10、query:llm
   evidence：压缩内存作为大型KV缓存的替代方案
10. [SkipOPU: An FPGA-based Overlay Processor for Large Language Models with Dynamically Allocated Computation](/202603/17/2603.14785v1-skipopu-an-fpga-based-overlay-processor-for-large-language-models-with-dynamically-allocated-computation)  
   标签：评分：9.0/10、query:llm
   evidence：基于FPGA的动态LLM计算加速

### 速读区论文标签
1. [SERQ: Saliency-Aware Low-Rank Error Reconstruction for LLM Quantization](/202603/17/2603.08185v1-serq-saliency-aware-low-rank-error-reconstruction-for-llm-quantization)  
   标签：评分：8.0/10、query:llm
   evidence：用于高效部署的大语言模型量化技术
2. [Learning Adaptive LLM Decoding](/202603/17/2603.09065v1-learning-adaptive-llm-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：用于高效推理的自适应解码策略
3. [Learning Adaptive LLM Decoding](/202603/17/2603.09065v2-learning-adaptive-llm-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：基于计算资源条件的自适应LLM解码策略
4. [SPAR-K: Scheduled Periodic Alternating Early Exit for Spoken Language Models](/202603/17/2603.09215v1-spar-k-scheduled-periodic-alternating-early-exit-for-spoken-language-models)  
   标签：评分：8.0/10、query:llm
   evidence：早退框架加速语音语言模型推理
5. [Reject, Resample, Repeat: Understanding Parallel Reasoning in Language Model Inference](/202603/17/2603.07887v1-reject-resample-repeat-understanding-parallel-reasoning-in-language-model-inference)  
   标签：评分：7.0/10、query:llm
   evidence：并行推理中准确性与成本权衡的推理时方法
6. [NLE: Non-autoregressive LLM-based ASR by Transcript Editing](/202603/17/2603.08397v1-nle-non-autoregressive-llm-based-asr-by-transcript-editing)  
   标签：评分：7.0/10、query:llm
   evidence：基于LLM的非自回归并行预测语音识别
7. [Learning When to Sample: Confidence-Aware Self-Consistency for Efficient LLM Chain-of-Thought Reasoning](/202603/17/2603.08999v1-learning-when-to-sample-confidence-aware-self-consistency-for-efficient-llm-chain-of-thought-reasoning)  
   标签：评分：7.0/10、query:llm
   evidence：高效的大语言模型思维链推理
8. [Pooling Engram Conditional Memory in Large Language Models using CXL](/202603/17/2603.10087v1-pooling-engram-conditional-memory-in-large-language-models-using-cxl)  
   标签：评分：7.0/10、query:llm
   evidence：使用CXL为LLM内存组件提供可扩展存储
9. [Exclusive Self Attention](/202603/17/2603.09078v1-exclusive-self-attention)  
   标签：评分：6.0/10、query:llm
   evidence：改进自注意力机制以提升序列建模性能
10. [Distilling LLM Semantic Priors into Encoder-Only Multi-Talker ASR with Talker-Count Routing](/202603/17/2603.10587v1-distilling-llm-semantic-priors-into-encoder-only-multi-talker-asr-with-talker-count-routing)  
   标签：评分：6.0/10、query:llm
   evidence：在推理时保留快速的 CTC 风格解码
11. [Sema: A High-performance System for LLM-based Semantic Query Processing](/202603/17/2603.11622v1-sema-a-high-performance-system-for-llm-based-semantic-query-processing)  
   标签：评分：6.0/10、query:llm
   evidence：基于LLM的高性能查询处理系统


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
