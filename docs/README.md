<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-25
- 运行时间：2026-09-25 21:54:47 UTC
- 运行状态：成功
- 本次总论文数：17
- 精读区：6
- 速读区：11

### 今日简报（AI）
今天从17篇论文中精读6篇、速读11篇，重点锁定推测解码的效率与可控性。
最值得看的是两篇9.0分精读《To Copy or Not to Copy》和《WaveFront Decoding》，分别探索用模型内在信号控制复制、以及面向循环语言模型的并行自推测解码。
普通读者可优先扫读速读里的《On-Demand Attention》《TierKV》和《SpecQuant》，关注长上下文与端侧推理的落地思路。
- 详情：[/202609/25/README](/202609/25/README)

### 精读区论文标签
1. [To Copy or Not to Copy: Controlling Speculative Decoding via Intrinsic Model Signals](/202609/25/2609.20186v1-to-copy-or-not-to-copy-controlling-speculative-decoding-via-intrinsic-model-signals)  
   标签：评分：9.0/10、query:llm-sd
   evidence：用内在信号控制投机解码草稿策略
2. [WaveFront Decoding: Parallelized Self-Speculative Decoding for Looped Language Models](/202609/25/2609.23033v1-wavefront-decoding-parallelized-self-speculative-decoding-for-looped-language-models)  
   标签：评分：9.0/10、query:llm-sd
   evidence：面向循环语言模型的自投机解码
3. [H-Spec: Parallel Speculative Decoding Without a Drafter-Side KV Cache](/202609/25/2609.24197v1-h-spec-parallel-speculative-decoding-without-a-drafter-side-kv-cache)  
   标签：评分：9.0/10、query:llm-sd
   evidence：复用目标KV的并行投机解码与验证
4. [Adapting Tree-Structured Speculative Decoding to DeepSeek-V4 for Efficient Inference](/202609/25/2609.24698v1-adapting-tree-structured-speculative-decoding-to-deepseek-v4-for-efficient-inference)  
   标签：评分：9.0/10、query:llm-sd
   evidence：树结构投机解码与分支感知因果验证
5. [When Parallel Drafter Meets Parallel Speculative Decoding](/202609/25/2609.27396v1-when-parallel-drafter-meets-parallel-speculative-decoding)  
   标签：评分：9.0/10、query:llm-sd
   evidence：并行投机解码重叠起草与验证
6. [NebulaSD: Many-for-Many Speculative Decoding](/202609/25/2609.29364v1-nebulasd-many-for-many-speculative-decoding)  
   标签：评分：9.0/10、query:llm-sd
   evidence：面向LLM服务的多对多分布式投机解码系统

### 速读区论文标签
1. [On-Demand Attention: Language Models Know When to Recall](/202609/25/2609.20734v1-on-demand-attention-language-models-know-when-to-recall)  
   标签：评分：8.0/10、query:llm
   evidence：选择性全局注意力与KV缓存实现高效长上下文推理
2. [TierKV: Long-Context On-Device LLMs via Predictive Multi-Tier KV Caching](/202609/25/2609.21172v1-tierkv-long-context-on-device-llms-via-predictive-multi-tier-kv-caching)  
   标签：评分：8.0/10、query:llm
   evidence：面向端侧LLM高效推理的多级KV缓存优化
3. [SpecQuant: Speculative Decoding with Multi-Parent Quantization for Adaptive LLM Inference](/202609/25/2609.21704v1-specquant-speculative-decoding-with-multi-parent-quantization-for-adaptive-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：投机解码结合量化实现自适应大模型高效推理
4. [RheoSampling: Resolving the One-Hot Dilemma in Stochastic Dynamic-Tree Speculative Decoding](/202609/25/2609.21827v1-rheosampling-resolving-the-one-hot-dilemma-in-stochastic-dynamic-tree-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：基于树的投机解码加速大模型推理
5. [Elastic Threshold Attention: Learned Contextual Sparsity for Long-Context Decoding](/202609/25/2609.20888v1-elastic-threshold-attention-learned-contextual-sparsity-for-long-context-decoding)  
   标签：评分：7.0/10、query:llm
   evidence：KV缓存稀疏化与长上下文高效解码注意力
6. [VPRune: Efficient Training-free Pre-LLM Visual Token Pruning](/202609/25/2609.24485v1-vprune-efficient-training-free-pre-llm-visual-token-pruning)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：免训练视觉token剪枝降低LVLM推理成本
7. [Compressing Long Context into Answer-Aligned Memory Embeddings for LLM Inference](/202609/25/2609.25537v1-compressing-long-context-into-answer-aligned-memory-embeddings-for-llm-inference)  
   标签：评分：7.0/10、query:llm
   evidence：面向高效LLM推理的KV缓存压缩与两级KV缓存
8. [Flash-dLLM: IO-Aware KV Caching and Parallel Decoding for Fast, Memory-Efficient Diffusion LLMs](/202609/25/2609.26796v1-flash-dllm-io-aware-kv-caching-and-parallel-decoding-for-fast-memory-efficient-diffusion-llms)  
   标签：评分：7.0/10、query:llm
   evidence：KV缓存与并行解码实现快速显存高效LLM推理
9. [Understanding and Exploiting Diagonal Attention Sparsity in Autoregressive Image Generation](/202609/25/2609.19702v1-understanding-and-exploiting-diagonal-attention-sparsity-in-autoregressive-image-generation)  
   标签：评分：6.0/10、query:llm
   evidence：多模态自回归生成中的稀疏注意力与KV缓存效率
10. [Zarya: A Hybrid Autoregressive--Masked Diffusion Language Model with Flexible Training and Dual-Mode Inference](/202609/25/2609.19868v1-zarya-a-hybrid-autoregressive--masked-diffusion-language-model-with-flexible-training-and-dual-mode-inference)  
   标签：评分：6.0/10、query:llm
   evidence：混合自回归-扩散模型解决KV缓存复用与推理效率
11. [VPRune: Efficient Training-free Pre-LLM Visual Token Pruning](/202609/25/2609.24485v2-vprune-efficient-training-free-pre-llm-visual-token-pruning)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：免训练视觉词元剪枝降低大型视觉语言模型推理成本


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
