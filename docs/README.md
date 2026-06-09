<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-06-09
- 运行时间：2026-06-09 21:57:27 UTC
- 运行状态：成功
- 本次总论文数：11
- 精读区：6
- 速读区：5

### 今日简报（AI）
今日日报聚焦两篇9分重磅论文，分别提出代价感知扩散起草树与多段注意力机制，直击大模型推理效率瓶颈。  
最值得看的方向：投机解码中的扩散式草稿树（Cost-Aware Diffusion Draft Trees）与KV缓存管理优化（Multi-Segment Attention），均获9.0/10高分。  
建议普通读者优先精读这两篇论文，重点关注如何以更低算力成本加速模型推理，并留意速读中的跨层值混合与超低位量化思路作为补充。
- 详情：[/202606/09/README](/202606/09/README)

### 精读区论文标签
1. [Cost-Aware Diffusion Draft Trees for Speculative Decoding](/202606/09/2606.01813v1-cost-aware-diffusion-draft-trees-for-speculative-decoding)  
   标签：评分：9.0/10、query:llm-sd
   evidence：面向LLM的代价感知扩散草案树投机解码
2. [Multi-Segment Attention: Enabling Efficient KV-Cache Management for Faster Large Language Model Serving](/202606/09/2606.02964v1-multi-segment-attention-enabling-efficient-kv-cache-management-for-faster-large-language-model-serving)  
   标签：评分：9.0/10、query:llm
   evidence：面向LLM推理的KV缓存管理系统AsymCache，显式将缓存驻留决策与GPU内核效率对齐
3. [D^2SD: Accelerating Speculative Decoding with Dual Diffusion Draft Models](/202606/09/2606.04446v1-d2sd-accelerating-speculative-decoding-with-dual-diffusion-draft-models)  
   标签：评分：9.0/10、query:llm
   evidence：针对大语言模型的投机解码加速方法，采用双扩散草稿模型
4. [MomentKV: Closing the Directional Gap in KV Cache Eviction for Long-Context Inference](/202606/09/2606.01563v1-momentkv-closing-the-directional-gap-in-kv-cache-eviction-for-long-context-inference)  
   标签：评分：8.0/10、query:llm
   evidence：KV缓存淘汰优化长上下文LLM推理
5. [AdaPLD: Adaptive Retrieval and Reuse for Efficient Model-Free Speculative Decoding](/202606/09/2606.05742v1-adapld-adaptive-retrieval-and-reuse-for-efficient-model-free-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：无模型投机解码中的自适应检索与重用
6. [Look Less, Reason More: Block-wise Attention Skipping for Efficient Multimodal LLMs](/202606/09/2606.08511v1-look-less-reason-more-block-wise-attention-skipping-for-efficient-multimodal-llms)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：基于视觉注意力饱和的逐块注意力跳过方法用于MLLM推理加速

### 速读区论文标签
1. [Depth-Attention: Cross-Layer Value Mixing for Language Models](/202606/09/2606.05014v1-depth-attention-cross-layer-value-mixing-for-language-models)  
   标签：评分：7.0/10、query:llm
   evidence：跨层值混合注意力提高LLM推理效率
2. [Minimizing the Hidden Cost of Scales: Graph-Guided Ultra-Low-Bit Quantization for Large Language Models](/202606/09/2606.05429v1-minimizing-the-hidden-cost-of-scales-graph-guided-ultra-low-bit-quantization-for-large-language-models)  
   标签：评分：7.0/10、query:llm
   evidence：面向大语言模型高效推理的超低位量化方法
3. [Late-Layer Fusion is Enough: Dual-Path Vision Token Routing for Multimodal Large Language Models under Visual Saturation](/202606/09/2606.09131v1-late-layer-fusion-is-enough-dual-path-vision-token-routing-for-multimodal-large-language-models-under-visual-saturation)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：通过双路径视觉令牌路由解决视觉饱和问题，提升多模态大语言模型推理效率
4. [Parallel Jacobi Decoding for Fast Autoregressive Image Generation](/202606/09/2606.05703v1-parallel-jacobi-decoding-for-fast-autoregressive-image-generation)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：并行雅可比解码加快自回归图像生成，类似于投机解码
5. [Learnable Token Sparsification for Efficient Gigapixel Whole Slide Image Reasoning](/202606/09/2606.08641v1-learnable-token-sparsification-for-efficient-gigapixel-whole-slide-image-reasoning)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：针对十亿像素图像的视觉语言模型推理，提出可学习令牌稀疏化以减少计算开销


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
