<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-22
- 运行时间：2026-09-22 22:34:26 UTC
- 运行状态：成功
- 本次总论文数：17
- 精读区：6
- 速读区：11

### 今日简报（AI）
今日精读6篇、速读11篇共17篇，焦点集中在推测解码的加速优化。最值得关注的是两篇9分工作：ECHO用早层协同分层编排加奖励logits，RheoSampling解决随机动态树推测解码中的one-hot困境。普通读者可先看这两篇精读，再顺带浏览ASPIRE等三篇8分速读，把握长上下文与自推测解码的进展。
- 详情：[/202609/22/README](/202609/22/README)

### 精读区论文标签
1. [ECHO: Early-layer Collaborative Hierarchical Orchestration with Bonus Logits in Speculative Decoding](/202609/22/2609.17241v1-echo-early-layer-collaborative-hierarchical-orchestration-with-bonus-logits-in-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：分层草稿树投机解码与低成本验证
2. [RheoSampling: Resolving the One-Hot Dilemma in Stochastic Dynamic-Tree Speculative Decoding](/202609/22/2609.21827v1-rheosampling-resolving-the-one-hot-dilemma-in-stochastic-dynamic-tree-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向LLM加速的随机动态树投机解码
3. [Acceptance-Aware Draft Model Training for Speculative Decoding](/202609/22/2609.24150v1-acceptance-aware-draft-model-training-for-speculative-decoding)  
   标签：评分：9.0/10、query:vlm-spec
   evidence：投机解码的接受度感知训练，验证策略
4. [H-Spec: Parallel Speculative Decoding Without a Drafter-Side KV Cache](/202609/22/2609.24197v1-h-spec-parallel-speculative-decoding-without-a-drafter-side-kv-cache)  
   标签：评分：9.0/10、query:llm
   evidence：去除草稿侧KV缓存的并行投机解码
5. [Adapting Tree-Structured Speculative Decoding to DeepSeek-V4 for Efficient Inference](/202609/22/2609.24698v1-adapting-tree-structured-speculative-decoding-to-deepseek-v4-for-efficient-inference)  
   标签：评分：9.0/10、query:llm-sd
   evidence：面向LLM推理的树结构投机解码与分支感知因果验证
6. [How Lossless Is Lossless Speculative Decoding? The Role of Numerical Precision in Orthrus](/202609/22/2609.15504v1-how-lossless-is-lossless-speculative-decoding-the-role-of-numerical-precision-in-orthrus)  
   标签：评分：8.0/10、query:llm-sd
   evidence：复现无损投机解码并检验其验证可靠性

### 速读区论文标签
1. [FlexEE: Self-Speculative and KV-Compatible Early Exiting for Offloading-Aware LLM Inference](/202609/22/2609.17008v1-flexee-self-speculative-and-kv-compatible-early-exiting-for-offloading-aware-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：结合早退的自投机解码加速资源受限下的LLM推理
2. [ASPIRE: Asynchronous Batched Self-Speculative Decoding for Long-Context LLM Inference](/202609/22/2609.17943v1-aspire-asynchronous-batched-self-speculative-decoding-for-long-context-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：面向长上下文LLM推理加速的批处理自投机解码
3. [To Copy or Not to Copy: Controlling Speculative Decoding via Intrinsic Model Signals](/202609/22/2609.20186v1-to-copy-or-not-to-copy-controlling-speculative-decoding-via-intrinsic-model-signals)  
   标签：评分：8.0/10、query:llm-sd
   evidence：利用模型内在信号控制投机解码的草稿策略
4. [GDN Tree-Scan: Served Tree Verification for Recurrent-Hybrid Language Models](/202609/22/2609.23900v1-gdn-tree-scan-served-tree-verification-for-recurrent-hybrid-language-models)  
   标签：评分：8.0/10、query:llm-sd
   evidence：面向混合语言模型的树投机解码验证策略
5. [LoopSpec: Pipelined Self-Speculative Decoding for Looped Transformers](/202609/22/2609.17184v1-loopspec-pipelined-self-speculative-decoding-for-looped-transformers)  
   标签：评分：7.0/10、query:llm
   evidence：面向循环Transformer的自投机解码降低解码延迟
6. [SpecQuant: Speculative Decoding with Multi-Parent Quantization for Adaptive LLM Inference](/202609/22/2609.21704v1-specquant-speculative-decoding-with-multi-parent-quantization-for-adaptive-llm-inference)  
   标签：评分：7.0/10、query:llm
   evidence：投机解码结合量化实现自适应大模型推理加速
7. [Watermarkable Multi-Draft Speculative Sampling via Poisson Processes](/202609/22/2609.21858v1-watermarkable-multi-draft-speculative-sampling-via-poisson-processes)  
   标签：评分：7.0/10、query:llm-sd
   evidence：面向LLM推理效率的多草案投机采样算法，属投机解码核心方法
8. [Efficient Mixture-of-Experts with Speculative Decoding via Expert Coactivation](/202609/22/2609.22471v1-efficient-mixture-of-experts-with-speculative-decoding-via-expert-coactivation)  
   标签：评分：7.0/10、query:llm
   evidence：投机解码结合MoE以加速LLM推理
9. [Dynamic Semantic Compression for Efficient Latent-Space Inference in Large Language Models](/202609/22/2609.15338v1-dynamic-semantic-compression-for-efficient-latent-space-inference-in-large-language-models)  
   标签：评分：6.0/10、query:llm
   evidence：基于语义压缩的大语言模型高效潜在空间推理
10. [Understanding and Exploiting Diagonal Attention Sparsity in Autoregressive Image Generation](/202609/22/2609.19702v1-understanding-and-exploiting-diagonal-attention-sparsity-in-autoregressive-image-generation)  
   标签：评分：6.0/10、query:llm
   evidence：对角注意力稀疏性缓解自回归多模态解码中的KV缓存访问瓶颈
11. [On-Demand Attention: Language Models Know When to Recall](/202609/22/2609.20734v1-on-demand-attention-language-models-know-when-to-recall)  
   标签：评分：6.0/10、query:llm
   evidence：选择性全局注意力与KV缓存保留实现高效长上下文解码


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
