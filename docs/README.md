<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-26
- 运行时间：2026-09-26 21:58:52 UTC
- 运行状态：成功
- 本次总论文数：16
- 精读区：6
- 速读区：10

### 今日简报（AI）
今日16篇中精读6篇、速读10篇，主线落在LLM推理加速的推测解码、量化与端侧长上下文。
最值得看的是推测解码：SpecQuant用多父量化做自适应推理，RheoSampling解决随机动态树中的One-Hot困境，另有树结构推测解码适配DeepSeek-V4。
普通读者可先读这两篇8分精读，再按端侧部署需求跟进TierKV与WaveFront Decoding。
- 详情：[/202609/26/README](/202609/26/README)

### 精读区论文标签
1. [SpecQuant: Speculative Decoding with Multi-Parent Quantization for Adaptive LLM Inference](/202609/26/2609.21704v1-specquant-speculative-decoding-with-multi-parent-quantization-for-adaptive-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：投机解码与多父量化结合，实现自适应高效大模型推理
2. [RheoSampling: Resolving the One-Hot Dilemma in Stochastic Dynamic-Tree Speculative Decoding](/202609/26/2609.21827v1-rheosampling-resolving-the-one-hot-dilemma-in-stochastic-dynamic-tree-speculative-decoding)  
   标签：评分：8.0/10、query:llm-sd
   evidence：随机动态树投机解码，T>0下接受率下降
3. [Watermarkable Multi-Draft Speculative Sampling via Poisson Processes](/202609/26/2609.21858v1-watermarkable-multi-draft-speculative-sampling-via-poisson-processes)  
   标签：评分：8.0/10、query:llm
   evidence：提升LLM推理效率前沿的多草稿投机采样算法
4. [Efficient Mixture-of-Experts with Speculative Decoding via Expert Coactivation](/202609/26/2609.22471v1-efficient-mixture-of-experts-with-speculative-decoding-via-expert-coactivation)  
   标签：评分：8.0/10、query:llm-sd
   evidence：MoE结合投机解码，验证token与专家传输
5. [H-Spec: Parallel Speculative Decoding Without a Drafter-Side KV Cache](/202609/26/2609.24197v1-h-spec-parallel-speculative-decoding-without-a-drafter-side-kv-cache)  
   标签：评分：8.0/10、query:llm
   evidence：面向LLM加速的并行投机解码与草稿侧KV缓存去除
6. [When Parallel Drafter Meets Parallel Speculative Decoding](/202609/26/2609.27396v1-when-parallel-drafter-meets-parallel-speculative-decoding)  
   标签：评分：8.0/10、query:llm-sd
   evidence：并行投机解码，将草稿与验证重叠执行

### 速读区论文标签
1. [Adapting Tree-Structured Speculative Decoding to DeepSeek-V4 for Efficient Inference](/202609/26/2609.24698v1-adapting-tree-structured-speculative-decoding-to-deepseek-v4-for-efficient-inference)  
   标签：评分：8.0/10、query:llm
   evidence：树结构投机解码集成到DeepSeek-V4以加速LLM推理
2. [TierKV: Long-Context On-Device LLMs via Predictive Multi-Tier KV Caching](/202609/26/2609.21172v1-tierkv-long-context-on-device-llms-via-predictive-multi-tier-kv-caching)  
   标签：评分：7.0/10、query:llm
   evidence：端侧LLM推理的预测式多层KV缓存
3. [WaveFront Decoding: Parallelized Self-Speculative Decoding for Looped Language Models](/202609/26/2609.23033v1-wavefront-decoding-parallelized-self-speculative-decoding-for-looped-language-models)  
   标签：评分：7.0/10、query:llm-sd
   evidence：无训练自投机解码框架加速大语言模型解码延迟
4. [SPECTRA: Adaptive Execution of Speculative Decoding on a Runtime-Reconfigurable Tiled Architecture](/202609/26/2609.24847v1-spectra-adaptive-execution-of-speculative-decoding-on-a-runtime-reconfigurable-tiled-architecture)  
   标签：评分：7.0/10、query:llm
   evidence：面向投机解码自适应执行的运行时重构架构
5. [CompKV: Compensation-Aware KV Selection for Long-Context LLM Inference](/202609/26/2609.26300v1-compkv-compensation-aware-kv-selection-for-long-context-llm-inference)  
   标签：评分：7.0/10、query:llm
   evidence：长上下文LLM推理的KV选择与稀疏注意力
6. [Flash-dLLM: IO-Aware KV Caching and Parallel Decoding for Fast, Memory-Efficient Diffusion LLMs](/202609/26/2609.26796v1-flash-dllm-io-aware-kv-caching-and-parallel-decoding-for-fast-memory-efficient-diffusion-llms)  
   标签：评分：7.0/10、query:llm
   evidence：面向快速内存高效扩散LLM推理的IO感知KV缓存与并行解码
7. [NebulaSD: Many-for-Many Speculative Decoding](/202609/26/2609.29364v1-nebulasd-many-for-many-speculative-decoding)  
   标签：评分：7.0/10、query:llm
   evidence：面向大模型推理加速的多对多投机解码系统
8. [A Multi-Engine Dataflow for MoE Decoding on Scratchpad-Based Tensor Accelerators](/202609/26/2609.21137v2-a-multi-engine-dataflow-for-moe-decoding-on-scratchpad-based-tensor-accelerators)  
   标签：评分：6.0/10、query:llm
   evidence：多引擎数据流加速张量加速器上的MoE解码
9. [Compressing Long Context into Answer-Aligned Memory Embeddings for LLM Inference](/202609/26/2609.25537v1-compressing-long-context-into-answer-aligned-memory-embeddings-for-llm-inference)  
   标签：评分：6.0/10、query:llm
   evidence：通过KV缓存与长上下文压缩降低LLM推理开销
10. [From Token Importance to Conditional Removability: Rethinking Visual Token Pruning in Multimodal Large Language Models](/202609/26/2609.26484v1-from-token-importance-to-conditional-removability-rethinking-visual-token-pruning-in-multimodal-large-language-models)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：多模态大模型视觉token剪枝加速


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
