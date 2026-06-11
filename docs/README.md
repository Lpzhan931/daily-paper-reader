<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-06-11
- 运行时间：2026-06-11 21:44:26 UTC
- 运行状态：成功
- 本次总论文数：16
- 精读区：6
- 速读区：10

### 今日简报（AI）
今日收录16篇论文，重点关注注意力机制与检索增强生成效率优化。精读推荐《LazyAttention》与《Depth-Attention》两项高评分工作，速读关注推测解码加速及超长上下文方案。普通读者可重点了解延迟位置编码与跨层值混合两种优化思路。
- 详情：[/202606/11/README](/202606/11/README)

### 精读区论文标签
1. [LazyAttention: Efficient Retrieval-Augmented Generation with Deferred Positional Encoding](/202606/11/2606.04302v1-lazyattention-efficient-retrieval-augmented-generation-with-deferred-positional-encoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向高效LLM推理的KV缓存优化
2. [Depth-Attention: Cross-Layer Value Mixing for Language Models](/202606/11/2606.05014v1-depth-attention-cross-layer-value-mixing-for-language-models)  
   标签：评分：9.0/10、query:llm
   evidence：注意力中的跨层值混合用于高效LLM推理
3. [AdaPLD: Adaptive Retrieval and Reuse for Efficient Model-Free Speculative Decoding](/202606/11/2606.05742v1-adapld-adaptive-retrieval-and-reuse-for-efficient-model-free-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：自适应检索与重用的无模型投机解码
4. [AVIS: Adaptive Test-Time Scaling for Vision-Language Models](/202606/11/2606.11576v1-avis-adaptive-test-time-scaling-for-vision-language-models)  
   标签：评分：9.0/10、query:vlm-spec
   evidence：针对VLM推理加速的自适应测试时缩放
5. [VIA-SD: Verification via Intra-Model Routing for Speculative Decoding](/202606/11/2606.12243v1-via-sd-verification-via-intra-model-routing-for-speculative-decoding)  
   标签：评分：9.0/10、query:llm-sd
   evidence：通过模型内路由和精简验证器进行投机解码验证
6. [Teaching Diffusion to Speculate Left-to-Right](/202606/11/2606.11552v1-teaching-diffusion-to-speculate-left-to-right)  
   标签：评分：8.0/10、query:llm-sd
   evidence：使用扩散语言模型作为草稿模型进行LLM投机解码

### 速读区论文标签
1. [D^2SD: Accelerating Speculative Decoding with Dual Diffusion Draft Models](/202606/11/2606.04446v1-d2sd-accelerating-speculative-decoding-with-dual-diffusion-draft-models)  
   标签：评分：8.0/10、query:llm
   evidence：针对LLM加速的投机解码，使用双扩散草稿模型
2. [FlashMemory-DeepSeek-V4: Lightning Index Ultra-Long Context via Lookahead Sparse Attention](/202606/11/2606.09079v1-flashmemory-deepseek-v4-lightning-index-ultra-long-context-via-lookahead-sparse-attention)  
   标签：评分：8.0/10、query:llm
   evidence：使用前瞻稀疏注意力管理长上下文LLM的KV缓存
3. [FlashMemory-DeepSeek-V4: Lightning Index Ultra-Long Context via Lookahead Sparse Attention](/202606/11/2606.09079v2-flashmemory-deepseek-v4-lightning-index-ultra-long-context-via-lookahead-sparse-attention)  
   标签：评分：8.0/10、query:llm
   evidence：前瞻稀疏注意力用于大语言模型推理中的KV缓存优化
4. [Express Language Modeling](/202606/11/2606.10944v1-express-language-modeling)  
   标签：评分：8.0/10、query:llm
   evidence：高效的注意力近似和KV缓存压缩用于大语言模型推理
5. [Task-Aware Structured Memory for Dynamic Multi-modal In-Context Learning](/202606/11/2606.11853v1-task-aware-structured-memory-for-dynamic-multi-modal-in-context-learning)  
   标签：评分：8.0/10、query:llm
   evidence：针对多模态LLM的KV缓存压缩，提升推理效率
6. [Breaking Entropy Bounds: Accelerating RL Training via MTP with Rejection Sampling](/202606/11/2606.12370v1-breaking-entropy-bounds-accelerating-rl-training-via-mtp-with-rejection-sampling)  
   标签：评分：8.0/10、query:llm-sd
   evidence：研究RL训练中MTP接受率，提出基于拒绝采样的投机解码加速方法
7. [Reroute, Don't Remove: Recoverable Visual Token Routing for Vision-Language Models](/202606/11/2606.12412v1-reroute-dont-remove-recoverable-visual-token-routing-for-vision-language-models)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：可恢复的视觉令牌路由以减少VLM推理中的KV缓存和注意力开销
8. [Frames2LoRA: Parametric Video Internalization for Vision-Language Models](/202606/11/2606.04351v2-frames2lora-parametric-video-internalization-for-vision-language-models)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：通过将视频内化为LoRA适配器减少VLM推理中的视觉令牌
9. [miniReranker: Efficient Multimodal Reranking through Visual Cache Reuse and Interaction Sparsity](/202606/11/2606.10759v1-minireranker-efficient-multimodal-reranking-through-visual-cache-reuse-and-interaction-sparsity)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：利用视觉缓存重用提高多模态重排序效率
10. [MM-Matryoshka: Towards Budget-Elastic Visual Document Retrieval via a 2D Multimodal Matryoshka Training Framework](/202606/11/2606.07654v1-mm-matryoshka-towards-budget-elastic-visual-document-retrieval-via-a-2d-multimodal-matryoshka-training-framework)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：二维Matryoshka训练实现预算弹性的视觉文档检索,支持性能与开销权衡


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
