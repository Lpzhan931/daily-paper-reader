<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-11
- 运行时间：2026-09-11 21:40:31 UTC
- 运行状态：成功
- 本次总论文数：8
- 精读区：5
- 速读区：3

### 今日简报（AI）
1) 今日8篇论文精读5篇、速读3篇，主线是推测解码、LLM训练/推理效率与推理时安全。
2) 最值得看的是9.0分的《DFlow》和8.0分的《Online Draft Co-Training》，前者关注块扩散推测解码的验证器信息流，后者关注大规模长上下文RL后训练中的在线草稿协同训练。
3) 普通读者可先读DFlow把握推测解码加速思路，再按需浏览Dropout层稀疏、FastE的token压缩和SpecGuard的免费后门检测。
- 详情：[/202609/11/README](/202609/11/README)

### 精读区论文标签
1. [DFlow: Enabling Verifier Information Flow in Block Diffusion Speculative Decoding](/202609/11/2609.06498v1-dflow-enabling-verifier-information-flow-in-block-diffusion-speculative-decoding)  
   标签：评分：9.0/10、query:llm-sd
   evidence：块扩散投机解码与验证器信息流
2. [Online Draft Co-Training for Speculative Decoding in Large-Scale, Long-Context RL Post-Training](/202609/11/2609.07108v1-online-draft-co-training-for-speculative-decoding-in-large-scale-long-context-rl-post-training)  
   标签：评分：8.0/10、query:llm
   evidence：面向大规模长上下文强化学习后训练的投机解码在线草稿协同训练
3. [Osprey: Target-agnostic Pre-training Makes Stronger Drafters in Speculative Decoding](/202609/11/2609.09338v1-osprey-target-agnostic-pre-training-makes-stronger-drafters-in-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：面向投机解码的目标无关草稿模型预训练以加速大模型推理
4. [PELM: Power Efficient On-Device LLM Inference with Speculative Decoding and Dynamic Voltage Frequency Scaling](/202609/11/2609.09662v1-pelm-power-efficient-on-device-llm-inference-with-speculative-decoding-and-dynamic-voltage-frequency-scaling)  
   标签：评分：8.0/10、query:llm
   evidence：面向端侧高效 LLM 推理的投机解码
5. [AMEND: Audited Margins Enable Nonblocking Drops in GPU-PIM LLM Decoding](/202609/11/2609.09823v1-amend-audited-margins-enable-nonblocking-drops-in-gpu-pim-llm-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：预测块稀疏KV判决以缓解显存带宽瓶颈的解码加速

### 速读区论文标签
1. [Don't Drop Dropout: Optimizing Layer Sparsity for Efficient LLM Training and Inference](/202609/11/2609.05275v1-dont-drop-dropout-optimizing-layer-sparsity-for-efficient-llm-training-and-inference)  
   标签：评分：6.0/10、query:llm
   evidence：面向高效LLM训练与推理的层稀疏性
2. [FastE: Readout-Triggered Token Compression for LLM Embedding Inference](/202609/11/2609.08407v1-faste-readout-triggered-token-compression-for-llm-embedding-inference)  
   标签：评分：6.0/10、query:llm
   evidence：面向高效LLM嵌入推理的免训练token压缩
3. [SpecGuard: Inference-Time Backdoor Detection For Free](/202609/11/2609.11799v1-specguard-inference-time-backdoor-detection-for-free)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：复用投机解码验证机制实现推理时后门检测


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
