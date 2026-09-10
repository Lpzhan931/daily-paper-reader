<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-10
- 运行时间：2026-09-10 21:55:46 UTC
- 运行状态：成功
- 本次总论文数：10
- 精读区：4
- 速读区：6

### 今日简报（AI）
今日筛选10篇LLM推理系统论文，精读4篇、速读6篇，精读中AceSpec（端云协同、通信高效）与DFlow（块扩散投机解码的验证器信息流）均获8.0分，最值得关注。
两个方向最亮眼：一是用非对称端云协同压缩LLM推理通信开销，二是从验证器信息流入手优化扩散式投机解码，速读里还有HeadWiseKV的按头缓存、PELM的功耗优化与AMEND的GPU-PIM非阻塞丢弃等7.0分工作。
普通读者可先读AceSpec了解端云协同思路，再按需查阅DFlow与HeadWiseKV，重点关注“省通信、省显存、省电”这三条主线。
- 详情：[/202609/10/README](/202609/10/README)

### 精读区论文标签
1. [AceSpec: An Asymmetric Edge-Cloud Collaborative Framework for Communication-Efficient LLM Inference](/202609/10/2609.02514v1-acespec-an-asymmetric-edge-cloud-collaborative-framework-for-communication-efficient-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：面向高效大模型推理的边缘-云投机解码
2. [DFlow: Enabling Verifier Information Flow in Block Diffusion Speculative Decoding](/202609/10/2609.06498v1-dflow-enabling-verifier-information-flow-in-block-diffusion-speculative-decoding)  
   标签：评分：8.0/10、query:llm-sd
   evidence：投机解码验证中的验证器信息流
3. [Online Draft Co-Training for Speculative Decoding in Large-Scale, Long-Context RL Post-Training](/202609/10/2609.07108v1-online-draft-co-training-for-speculative-decoding-in-large-scale-long-context-rl-post-training)  
   标签：评分：8.0/10、query:llm-sd
   evidence：面向投机解码的在线草稿模型协同训练，加速rollout生成
4. [Osprey: Target-agnostic Pre-training Makes Stronger Drafters in Speculative Decoding](/202609/10/2609.09338v1-osprey-target-agnostic-pre-training-makes-stronger-drafters-in-speculative-decoding)  
   标签：评分：8.0/10、query:llm-sd
   evidence：面向投机解码的草稿模型目标无关预训练

### 速读区论文标签
1. [HeadWiseKV: Budgeted Per-Head Cache Residency for Hybrid Long-Context Language Models](/202609/10/2609.02029v1-headwisekv-budgeted-per-head-cache-residency-for-hybrid-long-context-language-models)  
   标签：评分：7.0/10、query:llm
   evidence：按预算分配每头KV缓存驻留，降低长上下文推理显存并提升吞吐
2. [PELM: Power Efficient On-Device LLM Inference with Speculative Decoding and Dynamic Voltage Frequency Scaling](/202609/10/2609.09662v1-pelm-power-efficient-on-device-llm-inference-with-speculative-decoding-and-dynamic-voltage-frequency-scaling)  
   标签：评分：7.0/10、query:llm
   evidence：用于端侧LLM推理的投机解码与能效优化
3. [AMEND: Audited Margins Enable Nonblocking Drops in GPU-PIM LLM Decoding](/202609/10/2609.09823v1-amend-audited-margins-enable-nonblocking-drops-in-gpu-pim-llm-decoding)  
   标签：评分：7.0/10、query:llm
   evidence：面向LLM解码的KV缓存与高效注意力优化
4. [Don't Drop Dropout: Optimizing Layer Sparsity for Efficient LLM Training and Inference](/202609/10/2609.05275v1-dont-drop-dropout-optimizing-layer-sparsity-for-efficient-llm-training-and-inference)  
   标签：评分：6.0/10、query:llm
   evidence：面向高效LLM训练与推理的层稀疏化
5. [FastE: Readout-Triggered Token Compression for LLM Embedding Inference](/202609/10/2609.08407v1-faste-readout-triggered-token-compression-for-llm-embedding-inference)  
   标签：评分：6.0/10、query:llm
   evidence：免训练token压缩以加速LLM嵌入推理
6. [Beyond One-Size-Fits-All: Sample-Adaptive Strategy Routing for Vision Token Pruning in MLLMs](/202609/10/2609.10346v1-beyond-one-size-fits-all-sample-adaptive-strategy-routing-for-vision-token-pruning-in-mllms)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：视觉token剪枝以降低多模态大模型推理成本


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
