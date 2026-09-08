<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-08
- 运行时间：2026-09-08 22:22:58 UTC
- 运行状态：成功
- 本次总论文数：12
- 精读区：6
- 速读区：6

### 今日简报（AI）
- 今日共生成 12 篇推荐（精读 6 篇，速读 6 篇）
- 精读：《Strong Drafts Need Compact Memories: Long-Context Speculative Decoding with Compressed KV Cache》（9.0/10）, 《CateKV: On Sequential Consistency for Long-Context LLM Inference Acceleration》（9.0/10）
- 速读：《SPD: Single Pass Decoding for Generative Reranking》（8.0/10）, 《HeadWiseKV: Budgeted Per-Head Cache Residency for Hybrid Long-Context Language Models》（8.0/10）, 《Don't Drop Dropout: Optimizing Layer Sparsity for Efficient LLM Training and Inference》（8.0/10）
- 这些结果覆盖了当下较热的方向，建议先看精读区论文的关键问题与方法。
- 详情：[/202609/08/README](/202609/08/README)

### 精读区论文标签
1. [Strong Drafts Need Compact Memories: Long-Context Speculative Decoding with Compressed KV Cache](/202609/08/2608.30252v1-strong-drafts-need-compact-memories-long-context-speculative-decoding-with-compressed-kv-cache)  
   标签：评分：9.0/10、query:llm
   evidence：将压缩KV缓存与长上下文投机解码结合，降低LLM推理延迟
2. [CateKV: On Sequential Consistency for Long-Context LLM Inference Acceleration](/202609/08/2608.30295v1-catekv-on-sequential-consistency-for-long-context-llm-inference-acceleration)  
   标签：评分：9.0/10、query:llm
   evidence：基于序列一致性的混合KV缓存方法，直接对应KV缓存优化和LLM推理加速主题。
3. [Faster Than Flash: Exploiting Attention Sparsity for Efficient Long-Context Decoding](/202609/08/2609.00097v1-faster-than-flash-exploiting-attention-sparsity-for-efficient-long-context-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：利用注意力稀疏性、融合内核与top-delta过滤实现长上下文高效解码，直接契合大语言模型高效推理主题
4. [Verification-Aware Training for Speculative Decoding](/202609/08/2608.30135v1-verification-aware-training-for-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：投机解码与验证感知草稿训练，用于加速大模型推理
5. [Tail-Replay: Escaping the Curse of Linear Attention in Prefix Caching for Hybrid LLMs](/202609/08/2608.30310v1-tail-replay-escaping-the-curse-of-linear-attention-in-prefix-caching-for-hybrid-llms)  
   标签：评分：8.0/10、query:llm
   evidence：针对混合大模型线性注意力缓存状态无法回滚的问题，提出更灵活的前缀缓存机制
6. [hLLM: Single Pass Decoding for Generative Reranking](/202609/08/2609.01807v1-hllm-single-pass-decoding-for-generative-reranking)  
   标签：评分：8.0/10、query:llm
   evidence：面向大模型推理效率的单遍解码策略，把串行自回归解码压缩为常数次前向传播

### 速读区论文标签
1. [SPD: Single Pass Decoding for Generative Reranking](/202609/08/2609.01807v2-spd-single-pass-decoding-for-generative-reranking)  
   标签：评分：8.0/10、query:llm
   evidence：面向受限排序输出的LLM解码加速，避免逐词自回归前向
2. [HeadWiseKV: Budgeted Per-Head Cache Residency for Hybrid Long-Context Language Models](/202609/08/2609.02029v1-headwisekv-budgeted-per-head-cache-residency-for-hybrid-long-context-language-models)  
   标签：评分：8.0/10、query:llm
   evidence：面向混合长上下文LLM的无训练逐头KV缓存压缩与分配，属于KV缓存优化
3. [Don't Drop Dropout: Optimizing Layer Sparsity for Efficient LLM Training and Inference](/202609/08/2609.05275v1-dont-drop-dropout-optimizing-layer-sparsity-for-efficient-llm-training-and-inference)  
   标签：评分：8.0/10、query:llm
   evidence：通过层稀疏性与层丢失策略同时提升大语言模型训练效率和推理阶段层剪枝的鲁棒性
4. [OUTLETS: Output-Length Prediction from Speculative Decoding Backbones](/202609/08/2609.01068v1-outlets-output-length-prediction-from-speculative-decoding-backbones)  
   标签：评分：7.0/10、query:llm
   evidence：利用投机解码草稿解码器的潜在信号预测输出长度，以优化大模型服务
5. [SFAD: Speculative Factuality-Aware Decoding](/202609/08/2609.00796v1-sfad-speculative-factuality-aware-decoding)  
   标签：评分：6.0/10、query:llm
   evidence：面向大语言模型的投机解码框架，在保持生成效率的同时增强事实一致性
6. [LookThere! Sparse Vision by Reinforced Selection](/202609/08/2609.04698v1-lookthere-sparse-vision-by-reinforced-selection)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：用强化学习选择图像token加速视觉Transformer推理，方法可迁移至VLM推理加速


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
