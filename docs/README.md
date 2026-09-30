<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-30
- 运行时间：2026-09-30 23:26:14 UTC
- 运行状态：成功
- 本次总论文数：11
- 精读区：5
- 速读区：6

### 今日简报（AI）
今日扫读11篇、精读5篇，主线集中在推理加速与解码优化。

最值得看的是精读中的《Mentored Decoding》（9.0/10）和《NebulaSD》（8.0/10），两篇都指向更快的推测解码；速读里的Flash-dLLM、Distance-KV、SPIDER也围绕KV缓存、长上下文与多模态剪枝提效。

普通读者可先从“推测解码如何不掉精度地提速”入手，再按需关注长上下文和显存优化方向。
- 详情：[/202609/30/README](/202609/30/README)

### 精读区论文标签
1. [Mentored Decoding: Faster Inference meets Boosting](/202609/30/2609.30474v1-mentored-decoding-faster-inference-meets-boosting)  
   标签：评分：9.0/10、query:llm-sd
   evidence：有损投机解码与宽松接受准则，并用Boosting理论证明
2. [NebulaSD: Many-for-Many Speculative Decoding](/202609/30/2609.29364v1-nebulasd-many-for-many-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：分离草稿与目标资源池的投机解码系统
3. [Whisper-Flash: Acoustically Conditioned Parallel Drafting for Faster Whisper Decoding](/202609/30/2609.32869v1-whisper-flash-acoustically-conditioned-parallel-drafting-for-faster-whisper-decoding)  
   标签：评分：8.0/10、query:llm-sd
   evidence：起草加验证的投机解码加速解码
4. [Resource-Efficient Speculative Decoding for Long-Context LLM Serving](/202609/30/2609.33184v1-resource-efficient-speculative-decoding-for-long-context-llm-serving)  
   标签：评分：8.0/10、query:llm
   evidence：结合KV卸载的投机解码用于LLM服务
5. [Shallow Queries, Mature Values: Depth-Asynchronous Self-Speculation for Looped Transformers](/202609/30/2609.34538v1-shallow-queries-mature-values-depth-asynchronous-self-speculation-for-looped-transformers)  
   标签：评分：8.0/10、query:llm
   evidence：自投机解码加速循环Transformer推理

### 速读区论文标签
1. [Flash-dLLM: IO-Aware KV Caching and Parallel Decoding for Fast, Memory-Efficient Diffusion LLMs](/202609/30/2609.26796v1-flash-dllm-io-aware-kv-caching-and-parallel-decoding-for-fast-memory-efficient-diffusion-llms)  
   标签：评分：7.0/10、query:llm
   evidence：面向LLM推理加速的KV缓存与并行解码
2. [Distance-KV: Exploiting Relative Distance for Efficient Long-Context Inference](/202609/30/2609.32663v1-distance-kv-exploiting-relative-distance-for-efficient-long-context-inference)  
   标签：评分：7.0/10、query:llm
   evidence：面向长上下文LLM高效推理的KV缓存压缩
3. [SPIDER: Multi-Layer Semantic Token Pruning and Adaptive Sub-Layer Skipping in Multimodal Large Language Models](/202609/30/2609.34977v1-spider-multi-layer-semantic-token-pruning-and-adaptive-sub-layer-skipping-in-multimodal-large-language-models)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：通过token剪枝与子层跳过多模态大模型推理加速
4. [Beneath the Tokens: A Performance Engineering Study of Multi-Token Prediction in GPU-Accelerated LLM Inference](/202609/30/2609.35188v1-beneath-the-tokens-a-performance-engineering-study-of-multi-token-prediction-in-gpu-accelerated-llm-inference)  
   标签：评分：7.0/10、query:llm
   evidence：多令牌预测加速LLM推理吞吐
5. [NavJev: Efficient Vision-Language Navigation via Action-Centric Visual Compression and Discriminative Action-Semantic Memory](/202609/30/2609.34969v1-navjev-efficient-vision-language-navigation-via-action-centric-visual-compression-and-discriminative-action-semantic-memory)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：高效视觉语言导航降低多模态推理延迟
6. [Just MLPs: Efficient Visual State Reconstruction for Multimodal Language Models](/202609/30/2609.34972v1-just-mlps-efficient-visual-state-reconstruction-for-multimodal-language-models)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：降低多模态大模型视觉token计算开销


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
