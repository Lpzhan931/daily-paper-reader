<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-06-08
- 运行时间：2026-06-08 21:00:12 UTC
- 运行状态：成功
- 本次总论文数：12
- 精读区：6
- 速读区：6

### 今日简报（AI）
今日精读聚焦KV缓存优化，两篇高分论文《MomentKV》与《Multi-Segment Attention》均获9.0分，分别从方向性淘汰与多段注意力管理角度提升长上下文推理效率。最值得关注方向：KV缓存淘汰的“方向性缺口”解决思路，以及联合缓存管理加速大模型服务。建议普通读者优先阅读这两篇，它们直接关系到长上下文场景下的显存与速度瓶颈。
- 详情：[/202606/08/README](/202606/08/README)

### 精读区论文标签
1. [MomentKV: Closing the Directional Gap in KV Cache Eviction for Long-Context Inference](/202606/08/2606.01563v1-momentkv-closing-the-directional-gap-in-kv-cache-eviction-for-long-context-inference)  
   标签：评分：9.0/10、query:llm
   evidence：用于长上下文LLM推理的KV缓存驱逐方法
2. [Multi-Segment Attention: Enabling Efficient KV-Cache Management for Faster Large Language Model Serving](/202606/08/2606.02964v1-multi-segment-attention-enabling-efficient-kv-cache-management-for-faster-large-language-model-serving)  
   标签：评分：9.0/10、query:llm
   evidence：用于加速LLM服务的KV缓存管理
3. [LazyAttention: Efficient Retrieval-Augmented Generation with Deferred Positional Encoding](/202606/08/2606.04302v1-lazyattention-efficient-retrieval-augmented-generation-with-deferred-positional-encoding)  
   标签：评分：9.0/10、query:llm
   evidence：通过延迟位置编码加速LLM推理的KV缓存方法
4. [D^2SD: Accelerating Speculative Decoding with Dual Diffusion Draft Models](/202606/08/2606.04446v1-d2sd-accelerating-speculative-decoding-with-dual-diffusion-draft-models)  
   标签：评分：9.0/10、query:llm
   evidence：利用双重扩散草稿模型加速LLM投机解码
5. [AdaPLD: Adaptive Retrieval and Reuse for Efficient Model-Free Speculative Decoding](/202606/08/2606.05742v1-adapld-adaptive-retrieval-and-reuse-for-efficient-model-free-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：通过自适应检索和重用草稿的LLM投机解码
6. [Cost-Aware Diffusion Draft Trees for Speculative Decoding](/202606/08/2606.01813v1-cost-aware-diffusion-draft-trees-for-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：投机解码中成本感知草稿树优化语言模型吞吐量

### 速读区论文标签
1. [Query-based Cross-Modal Projector Bolstering Mamba Multimodal LLM](/202606/08/2606.04719v1-query-based-cross-modal-projector-bolstering-mamba-multimodal-llm)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：基于查询的跨模态投影器压缩视觉token以加速VLM推理
2. [Depth-Attention: Cross-Layer Value Mixing for Language Models](/202606/08/2606.05014v1-depth-attention-cross-layer-value-mixing-for-language-models)  
   标签：评分：7.0/10、query:llm
   evidence：跨层注意力机制用于高效LLM推理
3. [Parallel Jacobi Decoding for Fast Autoregressive Image Generation](/202606/08/2606.05703v1-parallel-jacobi-decoding-for-fast-autoregressive-image-generation)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：雅可比式解码加速自回归生成，可迁移至VLM投机解码
4. [Video-Rate Streaming Stylization on a Vision-Aware MLLM-Conditioned Edit Diffusion: Asymmetric Batched Inference on a Distilled UNet + MLLM Text Encoder](/202606/08/2606.05981v1-video-rate-streaming-stylization-on-a-vision-aware-mllm-conditioned-edit-diffusion-asymmetric-batched-inference-on-a-distilled-unet--mllm-text-encoder)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：多模态大语言模型的不对称批量推理提高吞吐量
5. [Selective Coupling of Decoupled Informative Regions: Masked Attention Alignment for Data-Free Quantization of Vision Transformers](/202606/08/2606.04373v1-selective-coupling-of-decoupled-informative-regions-masked-attention-alignment-for-data-free-quantization-of-vision-transformers)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：视觉Transformer的数据无关量化方法，可加速VLM推理
6. [MemDreamer: Decoupling Perception and Reasoning for Long Video Understanding via Hierarchical Graph Memory and Agentic Retrieval Mechanism](/202606/08/2606.07512v1-memdreamer-decoupling-perception-and-reasoning-for-long-video-understanding-via-hierarchical-graph-memory-and-agentic-retrieval-mechanism)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：层级图记忆避免长视频VLM推理中的标记爆炸


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
