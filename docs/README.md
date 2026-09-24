<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-24
- 运行时间：2026-09-24 22:42:12 UTC
- 运行状态：成功
- 本次总论文数：17
- 精读区：6
- 速读区：11

### 今日简报（AI）
今天扫完17篇论文（精读6、速读11），主线集中在投机解码：从长上下文异步批处理到用模型自身信号决定“抄不抄”。最值得看的是两篇8分精读《ASPIRE》和《To Copy or Not to Copy》，前者关注长上下文LLM推理加速，后者教你如何靠内在信号控制投机解码；速读里MoE专家共激活、无drafter侧KV缓存的H-Spec、以及适配DeepSeek-V4的树状投机解码同样值得扫一眼。普通读者可先抓住“投机解码如何省算力又不掉质量”这条线，再按需深入长上下文或MoE场景。
- 详情：[/202609/24/README](/202609/24/README)

### 精读区论文标签
1. [ASPIRE: Asynchronous Batched Self-Speculative Decoding for Long-Context LLM Inference](/202609/24/2609.17943v1-aspire-asynchronous-batched-self-speculative-decoding-for-long-context-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：面向长上下文LLM推理加速的自投机解码
2. [To Copy or Not to Copy: Controlling Speculative Decoding via Intrinsic Model Signals](/202609/24/2609.20186v1-to-copy-or-not-to-copy-controlling-speculative-decoding-via-intrinsic-model-signals)  
   标签：评分：8.0/10、query:llm-sd
   evidence：通过模型内在信号控制投机解码的草稿策略
3. [Elastic Threshold Attention: Learned Contextual Sparsity for Long-Context Decoding](/202609/24/2609.20888v1-elastic-threshold-attention-learned-contextual-sparsity-for-long-context-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：面向长上下文KV缓存解码的可学习上下文稀疏
4. [RheoSampling: Resolving the One-Hot Dilemma in Stochastic Dynamic-Tree Speculative Decoding](/202609/24/2609.21827v1-rheosampling-resolving-the-one-hot-dilemma-in-stochastic-dynamic-tree-speculative-decoding)  
   标签：评分：8.0/10、query:llm-sd
   evidence：随机动态树投机解码的接受率问题
5. [WaveFront Decoding: Parallelized Self-Speculative Decoding for Looped Language Models](/202609/24/2609.23033v1-wavefront-decoding-parallelized-self-speculative-decoding-for-looped-language-models)  
   标签：评分：8.0/10、query:llm-sd
   evidence：利用草稿预测的自投机解码以加速推理
6. [GDN Tree-Scan: Served Tree Verification for Recurrent-Hybrid Language Models](/202609/24/2609.23900v1-gdn-tree-scan-served-tree-verification-for-recurrent-hybrid-language-models)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：面向循环混合模型的树投机解码验证

### 速读区论文标签
1. [Efficient Mixture-of-Experts with Speculative Decoding via Expert Coactivation](/202609/24/2609.22471v1-efficient-mixture-of-experts-with-speculative-decoding-via-expert-coactivation)  
   标签：评分：8.0/10、query:llm
   evidence：面向MoE高效推理的投机解码
2. [H-Spec: Parallel Speculative Decoding Without a Drafter-Side KV Cache](/202609/24/2609.24197v1-h-spec-parallel-speculative-decoding-without-a-drafter-side-kv-cache)  
   标签：评分：8.0/10、query:llm-sd
   evidence：无需草稿侧KV缓存的并行投机解码
3. [Adapting Tree-Structured Speculative Decoding to DeepSeek-V4 for Efficient Inference](/202609/24/2609.24698v1-adapting-tree-structured-speculative-decoding-to-deepseek-v4-for-efficient-inference)  
   标签：评分：8.0/10、query:llm
   evidence：面向LLM高效推理的树结构投机解码
4. [SPECTRA: Adaptive Execution of Speculative Decoding on a Runtime-Reconfigurable Tiled Architecture](/202609/24/2609.24847v1-spectra-adaptive-execution-of-speculative-decoding-on-a-runtime-reconfigurable-tiled-architecture)  
   标签：评分：8.0/10、query:llm
   evidence：面向LLM投机解码的运行时重构硬件架构
5. [On-Demand Attention: Language Models Know When to Recall](/202609/24/2609.20734v1-on-demand-attention-language-models-know-when-to-recall)  
   标签：评分：7.0/10、query:llm
   evidence：面向长上下文高效推理的按需全局注意力与KV缓存
6. [RBS-Attention: Radius-Bounded Sparse Prefill for Long-Context Large Language Models](/202609/24/2609.20971v1-rbs-attention-radius-bounded-sparse-prefill-for-long-context-large-language-models)  
   标签：评分：7.0/10、query:llm
   evidence：面向长上下文LLM推理的高效稀疏预填充注意力
7. [SpecQuant: Speculative Decoding with Multi-Parent Quantization for Adaptive LLM Inference](/202609/24/2609.21704v1-specquant-speculative-decoding-with-multi-parent-quantization-for-adaptive-llm-inference)  
   标签：评分：7.0/10、query:llm
   evidence：将投机解码与多父量化结合以加速大模型自适应推理
8. [Watermarkable Multi-Draft Speculative Sampling via Poisson Processes](/202609/24/2609.21858v1-watermarkable-multi-draft-speculative-sampling-via-poisson-processes)  
   标签：评分：7.0/10、query:llm
   evidence：面向LLM推理效率的多草稿投机采样
9. [TierKV: Long-Context On-Device LLMs via Predictive Multi-Tier KV Caching](/202609/24/2609.21172v1-tierkv-long-context-on-device-llms-via-predictive-multi-tier-kv-caching)  
   标签：评分：6.0/10、query:llm
   evidence：端侧LLM推理的KV缓存优化
10. [Compressing Long Context into Answer-Aligned Memory Embeddings for LLM Inference](/202609/24/2609.25537v1-compressing-long-context-into-answer-aligned-memory-embeddings-for-llm-inference)  
   标签：评分：6.0/10、query:llm
   evidence：面向LLM高效推理的KV缓存与长上下文压缩
11. [Shallow to Deep: Aligning Token Pruning with Stage-wise Roles in LVLMs](/202609/24/2609.25635v1-shallow-to-deep-aligning-token-pruning-with-stage-wise-roles-in-lvlms)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：面向LVLM的视觉令牌剪枝以降低计算成本


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
