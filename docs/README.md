<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-06-06
- 运行时间：2026-06-06 21:14:24 UTC
- 运行状态：成功
- 本次总论文数：16
- 精读区：6
- 速读区：10

### 今日简报（AI）
今日精选16篇，精读《DREAM-S》（10分）与《VisionPulse》（9分）领衔，聚焦多模态生成效率。  
最值得关注方向：可搜索草稿与目标感知精炼的投机解码（DREAM-S）和动态视觉稀疏化推理（VisionPulse）。  
普通读者建议优先精读这两篇，理解加速多模态模型的不妥协之道；速读中跨语言投机解码与KV缓存管理亦值得跟进。
- 详情：[/202606/06/README](/202606/06/README)

### 精读区论文标签
1. [DREAM-S: Speculative Decoding with Searchable Drafting and Target-Aware Refinement for Multimodal Generation](/202606/06/2606.00535v1-dream-s-speculative-decoding-with-searchable-drafting-and-target-aware-refinement-for-multimodal-generation)  
   标签：评分：10.0/10、query:vlm-spec
   evidence：针对视觉语言模型的投机解码框架
2. [VisionPulse: Dynamic Visual Sparsity for Efficient Multimodal Reasoning](/202606/06/2605.31457v1-visionpulse-dynamic-visual-sparsity-for-efficient-multimodal-reasoning)  
   标签：评分：9.0/10、query:vlm-spec
   evidence：提出逐步视觉令牌剪枝加速多模态推理，直接针对视觉语言模型推理加速
3. [MomentKV: Closing the Directional Gap in KV Cache Eviction for Long-Context Inference](/202606/06/2606.01563v1-momentkv-closing-the-directional-gap-in-kv-cache-eviction-for-long-context-inference)  
   标签：评分：9.0/10、query:llm
   evidence：KV缓存驱逐策略解决方向性不匹配，直接相关于大语言模型KV缓存优化
4. [Multi-Segment Attention: Enabling Efficient KV-Cache Management for Faster Large Language Model Serving](/202606/06/2606.02964v1-multi-segment-attention-enabling-efficient-kv-cache-management-for-faster-large-language-model-serving)  
   标签：评分：9.0/10、query:llm
   evidence：用于加速LLM服务的KV缓存管理系统
5. [D^2SD: Accelerating Speculative Decoding with Dual Diffusion Draft Models](/202606/06/2606.04446v1-d2sd-accelerating-speculative-decoding-with-dual-diffusion-draft-models)  
   标签：评分：9.0/10、query:llm
   evidence：使用双扩散草稿模型加速投机解码，直接相关于大语言模型高效推理
6. [AdaPLD: Adaptive Retrieval and Reuse for Efficient Model-Free Speculative Decoding](/202606/06/2606.05742v1-adapld-adaptive-retrieval-and-reuse-for-efficient-model-free-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向LLM加速的无模型投机解码

### 速读区论文标签
1. [Speculative Decoding Across Languages](/202606/06/2605.30580v1-speculative-decoding-across-languages)  
   标签：评分：8.0/10、query:llm
   evidence：跨语言投机解码加速LLM推理
2. [Cost-Aware Diffusion Draft Trees for Speculative Decoding](/202606/06/2606.01813v1-cost-aware-diffusion-draft-trees-for-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：针对LLM的投机解码，提出成本感知扩散草稿树
3. [TGV-KV: Text-Grounded KV Eviction for Vision-Language Models](/202606/06/2606.03075v1-tgv-kv-text-grounded-kv-eviction-for-vision-language-models)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：文本引导的KV驱逐减少VLM推理内存
4. [Depth-Attention: Cross-Layer Value Mixing for Language Models](/202606/06/2606.05014v1-depth-attention-cross-layer-value-mixing-for-language-models)  
   标签：评分：7.0/10、query:llm
   evidence：注意力内部的跨层值混合，与LLM高效注意力机制相关
5. [Minimizing the Hidden Cost of Scales: Graph-Guided Ultra-Low-Bit Quantization for Large Language Models](/202606/06/2606.05429v1-minimizing-the-hidden-cost-of-scales-graph-guided-ultra-low-bit-quantization-for-large-language-models)  
   标签：评分：7.0/10、query:llm
   evidence：图引导的超低比特量化用于LLM高效推理
6. [Video-Rate Streaming Stylization on a Vision-Aware MLLM-Conditioned Edit Diffusion: Asymmetric Batched Inference on a Distilled UNet + MLLM Text Encoder](/202606/06/2606.05981v1-video-rate-streaming-stylization-on-a-vision-aware-mllm-conditioned-edit-diffusion-asymmetric-batched-inference-on-a-distilled-unet--mllm-text-encoder)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：MLLM推理的异步批处理流水线与缓存优化，与VLM推理加速相关
7. [Hyperbolic and Evidence-Prioritized Experts for Large Vision-Language Models](/202606/06/2606.00275v1-hyperbolic-and-evidence-prioritized-experts-for-large-vision-language-models)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：通过混合专家机制提升大型视觉语言模型的计算效率
8. [ChannelTok: Efficient Flexible-Length Vision Tokenization](/202606/06/2606.04461v1-channeltok-efficient-flexible-length-vision-tokenization)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：高效的灵活长度视觉标记化，可加速VLM推理
9. [Parallel Jacobi Decoding for Fast Autoregressive Image Generation](/202606/06/2606.05703v1-parallel-jacobi-decoding-for-fast-autoregressive-image-generation)  
   标签：评分：6.0/10、query:llm
   evidence：无需训练的并行解码方法加速自回归生成
10. [Let It Be Simple: One-Step Action Generation for Vision-Language-Action Models](/202606/06/2606.05737v1-let-it-be-simple-one-step-action-generation-for-vision-language-action-models)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：一步动作生成加速VLA模型推理


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
