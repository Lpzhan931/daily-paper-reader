<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-14
- 运行时间：2026-08-14 20:52:35 UTC
- 运行状态：成功
- 本次总论文数：11
- 精读区：7
- 速读区：4

### 今日简报（AI）
今日聚焦推测解码与KV缓存优化，11篇论文中7篇精读、4篇速读。最值得关注的两篇9分工作：《DBLAST》改进随机推测解码，而《OasisKV》通过前瞻稀疏预取突破HBM限制。建议优先精读这两篇，并留意边缘设备上的内存自适应推测调度方向。
- 详情：[/202608/14/README](/202608/14/README)

### 精读区论文标签
1. [DBLAST: Dependent Block Drafting for Stochastic Speculative Decoding](/202608/14/2608.05448v1-dblast-dependent-block-drafting-for-stochastic-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向LLM随机投机解码的依赖块草稿方法
2. [OasisKV: Scaling In-Decode KV Cache Beyond HBM with Lookahead Sparse Prefetching](/202608/14/2608.08097v1-oasiskv-scaling-in-decode-kv-cache-beyond-hbm-with-lookahead-sparse-prefetching)  
   标签：评分：9.0/10、query:llm
   evidence：通过KV缓存与HBM解耦及前瞻稀疏预取优化大语言模型推理
3. [LibraSpec: Dynamic Diffusion-Based Speculative Decoding via Marginal-Gain-Driven Optimization](/202608/14/2608.08721v1-libraspec-dynamic-diffusion-based-speculative-decoding-via-marginal-gain-driven-optimization)  
   标签：评分：9.0/10、query:llm
   evidence：面向扩散草稿模型的LLM投机解码动态推测长度优化
4. [DistillCache: KL-Guided Adaptive KV-Cache Eviction for Memory-Efficient LLM Inference](/202608/14/2608.08878v1-distillcache-kl-guided-adaptive-kv-cache-eviction-for-memory-efficient-llm-inference)  
   标签：评分：9.0/10、query:llm
   evidence：基于强化学习的KV缓存逐出，降低LLM推理内存，符合大模型高效推理主题
5. [FlashDrive: Flash Vision-Language-Action Inference for Autonomous Driving](/202608/14/2608.12932v1-flashdrive-flash-vision-language-action-inference-for-autonomous-driving)  
   标签：评分：9.0/10、query:vlm-spec
   evidence：VLA推理加速框架，针对串行token生成等多个瓶颈
6. [SPADE: Speculative Decoding for Precise and Low Cost Distributed Edge Cloud Inference](/202608/14/2608.13076v1-spade-speculative-decoding-for-precise-and-low-cost-distributed-edge-cloud-inference)  
   标签：评分：9.0/10、query:llm
   evidence：面向大语言模型高效推理的边云协同投机解码框架
7. [DARTree: Speculative Diffusion Decoding with Autoregressive Draft Trees](/202608/14/2608.13524v1-dartree-speculative-diffusion-decoding-with-autoregressive-draft-trees)  
   标签：评分：9.0/10、query:llm
   evidence：基于自回归草稿树的免训练投机解码方法，用于加速大语言模型推理

### 速读区论文标签
1. [MemSpec: Memory-Aware Runtime for Adaptive Draft Scheduling in Speculative Decoding on Edge Devices](/202608/14/2608.10362v1-memspec-memory-aware-runtime-for-adaptive-draft-scheduling-in-speculative-decoding-on-edge-devices)  
   标签：评分：8.0/10、query:llm
   evidence：面向边缘设备投机解码的自适应草稿调度内存感知运行时
2. [Reduced Matrix Multiplication: Input-Adaptive Matrix-Product Reduction for LLM Inference](/202608/14/2608.13426v1-reduced-matrix-multiplication-input-adaptive-matrix-product-reduction-for-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：输入自适应的矩阵乘法缩减，无需训练即可加速LLM推理
3. [Ripple-Pivot Search: Active Parallel Decoding for Diffusion Large Language Models](/202608/14/2608.11742v1-ripple-pivot-search-active-parallel-decoding-for-diffusion-large-language-models)  
   标签：评分：6.0/10、query:llm
   evidence：面向扩散大语言模型的并行解码加速
4. [Alignment Drift in Single-Model Speculative Decoding for ASR: Mechanism, Correction, and Cost](/202608/14/2608.12703v1-alignment-drift-in-single-model-speculative-decoding-for-asr-mechanism-correction-and-cost)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：投机解码的接受与纠正机制


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
