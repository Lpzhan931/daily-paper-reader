<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-21
- 运行时间：2026-09-21 23:10:21 UTC
- 运行状态：成功
- 本次总论文数：17
- 精读区：6
- 速读区：11

### 今日简报（AI）
今天共处理 17 篇论文，精读 6 篇、速读 11 篇，主线高度集中在投机解码与长上下文 LLM 推理加速。

最值得看的是两篇 9.0 分精读——《How Lossless Is Lossless Speculative Decoding?》从数值精度角度追问"无损"到底有多无损，《To Copy or Not to Copy》则用模型内在信号来控制投机解码中的复制决策。

普通读者可先抓住"无损是否真无损"这一精度代价问题，再顺着 ASPIRE 的异步批处理自投机与 TierKV 的多层 KV 缓存，理解长上下文推理的工程化思路。
- 详情：[/202609/21/README](/202609/21/README)

### 精读区论文标签
1. [How Lossless Is Lossless Speculative Decoding? The Role of Numerical Precision in Orthrus](/202609/21/2609.15504v1-how-lossless-is-lossless-speculative-decoding-the-role-of-numerical-precision-in-orthrus)  
   标签：评分：9.0/10、query:llm-sd
   evidence：检验投机解码的无损声明与验证接受行为
2. [To Copy or Not to Copy: Controlling Speculative Decoding via Intrinsic Model Signals](/202609/21/2609.20186v1-to-copy-or-not-to-copy-controlling-speculative-decoding-via-intrinsic-model-signals)  
   标签：评分：9.0/10、query:llm-sd
   evidence：通过草拟策略控制加速LLM推理的投机解码
3. [BigMoMo: Efficient Inference of Large-Scale MoE with Speculative Decoding on Mobile Devices](/202609/21/2609.14643v1-bigmomo-efficient-inference-of-large-scale-moe-with-speculative-decoding-on-mobile-devices)  
   标签：评分：8.0/10、query:llm
   evidence：面向移动端大规模MoE高效推理的投机解码
4. [Carryover Drafting: Recycling Rejected States for Speculative Decoding](/202609/21/2609.14717v1-carryover-drafting-recycling-rejected-states-for-speculative-decoding)  
   标签：评分：8.0/10、query:llm-sd
   evidence：投机解码复用验证阶段被拒绝token的隐状态
5. [FlexEE: Self-Speculative and KV-Compatible Early Exiting for Offloading-Aware LLM Inference](/202609/21/2609.17008v1-flexee-self-speculative-and-kv-compatible-early-exiting-for-offloading-aware-llm-inference)  
   标签：评分：8.0/10、query:llm-sd
   evidence：基于局部词表的自投机解码实现低成本token接受
6. [LoopSpec: Pipelined Self-Speculative Decoding for Looped Transformers](/202609/21/2609.17184v1-loopspec-pipelined-self-speculative-decoding-for-looped-transformers)  
   标签：评分：8.0/10、query:llm
   evidence：面向循环Transformer的自投机解码

### 速读区论文标签
1. [ECHO: Early-layer Collaborative Hierarchical Orchestration with Bonus Logits in Speculative Decoding](/202609/21/2609.17241v1-echo-early-layer-collaborative-hierarchical-orchestration-with-bonus-logits-in-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：免草稿模型投机解码与低成本验证
2. [ASPIRE: Asynchronous Batched Self-Speculative Decoding for Long-Context LLM Inference](/202609/21/2609.17943v1-aspire-asynchronous-batched-self-speculative-decoding-for-long-context-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：面向长上下文LLM推理的异步批处理自投机解码
3. [TierKV: Long-Context On-Device LLMs via Predictive Multi-Tier KV Caching](/202609/21/2609.21172v1-tierkv-long-context-on-device-llms-via-predictive-multi-tier-kv-caching)  
   标签：评分：8.0/10、query:llm
   evidence：KV缓存优化与多级缓存用于端侧LLM高效推理
4. [SpecQuant: Speculative Decoding with Multi-Parent Quantization for Adaptive LLM Inference](/202609/21/2609.21704v1-specquant-speculative-decoding-with-multi-parent-quantization-for-adaptive-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：投机解码结合量化实现自适应LLM推理加速
5. [RheoSampling: Resolving the One-Hot Dilemma in Stochastic Dynamic-Tree Speculative Decoding](/202609/21/2609.21827v1-rheosampling-resolving-the-one-hot-dilemma-in-stochastic-dynamic-tree-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：随机动态树投机解码与接受率问题
6. [On-Demand Attention: Language Models Know When to Recall](/202609/21/2609.20734v1-on-demand-attention-language-models-know-when-to-recall)  
   标签：评分：7.0/10、query:llm
   evidence：高效长上下文解码，保留KV缓存，vLLM条件执行
7. [Elastic Threshold Attention: Learned Contextual Sparsity for Long-Context Decoding](/202609/21/2609.20888v1-elastic-threshold-attention-learned-contextual-sparsity-for-long-context-decoding)  
   标签：评分：7.0/10、query:llm
   evidence：KV缓存带宽瓶颈与稀疏注意力加速解码
8. [Accelerating Dense LLMs via L0-regularized Mixture-of-Experts](/202609/21/2609.21672v1-accelerating-dense-llms-via-l0-regularized-mixture-of-experts)  
   标签：评分：7.0/10、query:llm
   evidence：L0正则化专家混合加速稠密LLM推理
9. [Self-Orchestrating Language Models: Leveraging Semantic Dependence for Efficient Inference](/202609/21/2609.14850v1-self-orchestrating-language-models-leveraging-semantic-dependence-for-efficient-inference)  
   标签：评分：6.0/10、query:llm
   evidence：自编排语言模型用于高效推理与降低解码延迟
10. [Dynamic Semantic Compression for Efficient Latent-Space Inference in Large Language Models](/202609/21/2609.15338v1-dynamic-semantic-compression-for-efficient-latent-space-inference-in-large-language-models)  
   标签：评分：6.0/10、query:llm
   evidence：面向LLM高效的隐空间片段级推理
11. [Efficient Quantization-Aware Distillation with Cross-Modal Alignment for Edge Vision-Language Models](/202609/21/2609.16689v1-efficient-quantization-aware-distillation-with-cross-modal-alignment-for-edge-vision-language-models)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：量化感知蒸馏用于边缘视觉语言模型高效部署


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
