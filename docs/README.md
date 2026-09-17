<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-17
- 运行时间：2026-09-17 21:52:48 UTC
- 运行状态：成功
- 本次总论文数：16
- 精读区：6
- 速读区：10

### 今日简报（AI）
2026-09-17 日报精选16篇推理加速论文，其中6篇精读聚焦GPU-PIM解码、移动端MoE与推测解码。最值得关注的是AMEND用审计边距实现GPU-PIM非阻塞丢弃，以及BigMoMo把大规模MoE推测解码搬上手机。普通读者可先看这两篇精读，再顺带浏览ECHO等速读文章了解分层编排思路。
- 详情：[/202609/17/README](/202609/17/README)

### 精读区论文标签
1. [AMEND: Audited Margins Enable Nonblocking Drops in GPU-PIM LLM Decoding](/202609/17/2609.09823v1-amend-audited-margins-enable-nonblocking-drops-in-gpu-pim-llm-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：KV缓存带宽与块稀疏注意力优化
2. [BigMoMo: Efficient Inference of Large-Scale MoE with Speculative Decoding on Mobile Devices](/202609/17/2609.14643v1-bigmomo-efficient-inference-of-large-scale-moe-with-speculative-decoding-on-mobile-devices)  
   标签：评分：8.0/10、query:llm
   evidence：投机解码多token验证窗口加速MoE推理
3. [Carryover Drafting: Recycling Rejected States for Speculative Decoding](/202609/17/2609.14717v1-carryover-drafting-recycling-rejected-states-for-speculative-decoding)  
   标签：评分：8.0/10、query:llm-sd
   evidence：投机解码回收被拒绝token状态
4. [How Lossless Is Lossless Speculative Decoding? The Role of Numerical Precision in Orthrus](/202609/17/2609.15504v1-how-lossless-is-lossless-speculative-decoding-the-role-of-numerical-precision-in-orthrus)  
   标签：评分：8.0/10、query:llm-sd
   evidence：检验无损投机解码主张与数值精度
5. [FlexEE: Self-Speculative and KV-Compatible Early Exiting for Offloading-Aware LLM Inference](/202609/17/2609.17008v1-flexee-self-speculative-and-kv-compatible-early-exiting-for-offloading-aware-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：面向LLM推理的自投机解码与KV兼容提前退出
6. [LoopSpec: Pipelined Self-Speculative Decoding for Looped Transformers](/202609/17/2609.17184v1-loopspec-pipelined-self-speculative-decoding-for-looped-transformers)  
   标签：评分：8.0/10、query:llm-sd
   evidence：面向循环Transformer的自投机解码

### 速读区论文标签
1. [ECHO: Early-layer Collaborative Hierarchical Orchestration with Bonus Logits in Speculative Decoding](/202609/17/2609.17241v1-echo-early-layer-collaborative-hierarchical-orchestration-with-bonus-logits-in-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：无草稿模型投机解码与分层验证加速推理
2. [ASPIRE: Asynchronous Batched Self-Speculative Decoding for Long-Context LLM Inference](/202609/17/2609.17943v1-aspire-asynchronous-batched-self-speculative-decoding-for-long-context-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：自投机解码加速批式长上下文推理
3. [PELM: Power Efficient On-Device LLM Inference with Speculative Decoding and Dynamic Voltage Frequency Scaling](/202609/17/2609.09662v1-pelm-power-efficient-on-device-llm-inference-with-speculative-decoding-and-dynamic-voltage-frequency-scaling)  
   标签：评分：7.0/10、query:llm
   evidence：面向端侧LLM的投机解码与功耗优化
4. [StackTok: Accelerating VLMs Inference with Budget-Adaptive Visual Token Selection](/202609/17/2609.16841v1-stacktok-accelerating-vlms-inference-with-budget-adaptive-visual-token-selection)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：通过视觉token选择加速VLM推理
5. [Rethinking Heterogeneous System Disaggregation for Subquadratic Attention](/202609/17/2609.13134v1-rethinking-heterogeneous-system-disaggregation-for-subquadratic-attention)  
   标签：评分：6.0/10、query:llm
   evidence：面向LLM推理效率的注意力感知解耦服务
6. [Self-Orchestrating Language Models: Leveraging Semantic Dependence for Efficient Inference](/202609/17/2609.14850v1-self-orchestrating-language-models-leveraging-semantic-dependence-for-efficient-inference)  
   标签：评分：6.0/10、query:llm
   evidence：自编排推理执行提升LLM效率
7. [Dynamic Semantic Compression for Efficient Latent-Space Inference in Large Language Models](/202609/17/2609.15338v1-dynamic-semantic-compression-for-efficient-latent-space-inference-in-large-language-models)  
   标签：评分：6.0/10、query:llm
   evidence：潜在空间推理降低LLM显存开销
8. [VideoMM: Adaptive Macro-Micro Inference for Efficient Video MLLMs](/202609/17/2609.16722v1-videomm-adaptive-macro-micro-inference-for-efficient-video-mllms)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：通过token削减实现多模态大模型高效推理
9. [Accelerating Diffusion Sampling via Speculative Draft Trees](/202609/17/2609.17691v1-accelerating-diffusion-sampling-via-speculative-draft-trees)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：草稿树投机采样加速生成
10. [rMuscle: Robotic Muscle Memory for Efficient Vision-Language-Action Model Inference](/202609/17/2609.19104v1-rmuscle-robotic-muscle-memory-for-efficient-vision-language-action-model-inference)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：降低VLA模型推理延迟


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
