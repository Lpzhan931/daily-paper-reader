<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-20
- 运行时间：2026-09-20 21:23:20 UTC
- 运行状态：成功
- 本次总论文数：11
- 精读区：6
- 速读区：5

### 今日简报（AI）
2026-09-20日报：11篇论文聚焦LLM推理加速，6篇精读、5篇速读，核心看点是推测解码与长上下文/移动端部署。  
最值得看ASPIRE（9.0）的异步批处理自推测解码，以及BigMoMo（8.0）在移动端跑大规模MoE的推测解码方案。  
普通读者下一步可先读ASPIRE，再顺着LoopSpec、ECHO和On-Demand Attention理解自推测、分层编排与按需注意力如何省算力。
- 详情：[/202609/20/README](/202609/20/README)

### 精读区论文标签
1. [ASPIRE: Asynchronous Batched Self-Speculative Decoding for Long-Context LLM Inference](/202609/20/2609.17943v1-aspire-asynchronous-batched-self-speculative-decoding-for-long-context-llm-inference)  
   标签：评分：9.0/10、query:llm
   evidence：面向长上下文LLM推理的自投机解码
2. [BigMoMo: Efficient Inference of Large-Scale MoE with Speculative Decoding on Mobile Devices](/202609/20/2609.14643v1-bigmomo-efficient-inference-of-large-scale-moe-with-speculative-decoding-on-mobile-devices)  
   标签：评分：8.0/10、query:llm
   evidence：利用投机解码验证窗口加速大模型推理
3. [Carryover Drafting: Recycling Rejected States for Speculative Decoding](/202609/20/2609.14717v1-carryover-drafting-recycling-rejected-states-for-speculative-decoding)  
   标签：评分：8.0/10、query:llm-sd
   evidence：投机解码验证阶段回收被拒绝token的隐藏状态
4. [How Lossless Is Lossless Speculative Decoding? The Role of Numerical Precision in Orthrus](/202609/20/2609.15504v1-how-lossless-is-lossless-speculative-decoding-the-role-of-numerical-precision-in-orthrus)  
   标签：评分：8.0/10、query:llm-sd
   evidence：在数值精度下检验投机解码的无损性与验证机制
5. [FlexEE: Self-Speculative and KV-Compatible Early Exiting for Offloading-Aware LLM Inference](/202609/20/2609.17008v1-flexee-self-speculative-and-kv-compatible-early-exiting-for-offloading-aware-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：自推测解码与KV兼容提前退出用于高效LLM推理
6. [To Copy or Not to Copy: Controlling Speculative Decoding via Intrinsic Model Signals](/202609/20/2609.20186v1-to-copy-or-not-to-copy-controlling-speculative-decoding-via-intrinsic-model-signals)  
   标签：评分：8.0/10、query:llm-sd
   evidence：通过模型内在信号控制投机解码

### 速读区论文标签
1. [LoopSpec: Pipelined Self-Speculative Decoding for Looped Transformers](/202609/20/2609.17184v1-loopspec-pipelined-self-speculative-decoding-for-looped-transformers)  
   标签：评分：8.0/10、query:llm
   evidence：面向循环Transformer的加速自投机解码框架
2. [ECHO: Early-layer Collaborative Hierarchical Orchestration with Bonus Logits in Speculative Decoding](/202609/20/2609.17241v1-echo-early-layer-collaborative-hierarchical-orchestration-with-bonus-logits-in-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：无草稿模型的分层投机解码加速LLM推理
3. [On-Demand Attention: Language Models Know When to Recall](/202609/20/2609.20734v1-on-demand-attention-language-models-know-when-to-recall)  
   标签：评分：8.0/10、query:llm
   evidence：面向长上下文LLM推理的注意力与KV缓存效率
4. [Self-Orchestrating Language Models: Leveraging Semantic Dependence for Efficient Inference](/202609/20/2609.14850v1-self-orchestrating-language-models-leveraging-semantic-dependence-for-efficient-inference)  
   标签：评分：6.0/10、query:llm
   evidence：以语义依赖自编排实现LLM高效推理
5. [Understanding and Exploiting Diagonal Attention Sparsity in Autoregressive Image Generation](/202609/20/2609.19702v1-understanding-and-exploiting-diagonal-attention-sparsity-in-autoregressive-image-generation)  
   标签：评分：6.0/10、query:llm
   evidence：KV缓存访问瓶颈与稀疏注意力加速多模态解码


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
