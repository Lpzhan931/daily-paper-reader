<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-20
- 运行时间：2026-08-20 20:22:04 UTC
- 运行状态：成功
- 本次总论文数：16
- 精读区：6
- 速读区：10

### 今日简报（AI）
今日聚焦推测解码，两篇高分精读直指边缘云推理与扩散模型效率优化。  
最值得关注：SPADE 实现低开销分布式边缘推理，DARTree 用自回归草稿树加速扩散解码。  
下一步可探索解码综述与超低位量化方法，从算法和内核协同层面提升部署性能。
- 详情：[/202608/20/README](/202608/20/README)

### 精读区论文标签
1. [SPADE: Speculative Decoding for Precise and Low Cost Distributed Edge Cloud Inference](/202608/20/2608.13076v1-spade-speculative-decoding-for-precise-and-low-cost-distributed-edge-cloud-inference)  
   标签：评分：9.0/10、query:llm
   evidence：面向分布式边缘云LLM推理加速的投机解码
2. [DARTree: Speculative Diffusion Decoding with Autoregressive Draft Trees](/202608/20/2608.13524v1-dartree-speculative-diffusion-decoding-with-autoregressive-draft-trees)  
   标签：评分：9.0/10、query:llm
   evidence：基于草稿树的投机解码方法，加速大模型推理
3. [S2-MoE: Enabling Efficient Self-Speculative Decoding for Mixture-of-Experts on Edge Devices](/202608/20/2608.15018v2-s2-moe-enabling-efficient-self-speculative-decoding-for-mixture-of-experts-on-edge-devices)  
   标签：评分：9.0/10、query:llm-sd
   evidence：面向MoE大语言模型的自投机解码框架，在边缘设备上降低验证开销
4. [S2-MoE: Enabling Efficient Self-Speculative Decoding for Mixture-of-Experts on Edge Devices](/202608/20/2608.15018v1-s2-moe-enabling-efficient-self-speculative-decoding-for-mixture-of-experts-on-edge-devices)  
   标签：评分：8.0/10、query:llm
   evidence：面向MoE大模型的自投机解码框架，减少验证开销以加速LLM推理
5. [DeltaLog: Deferred Materialization of Recurrent States for Linear Attention Decoding](/202608/20/2608.15533v1-deltalog-deferred-materialization-of-recurrent-states-for-linear-attention-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：通过延迟物化循环状态降低线性注意力解码内存开销，直接优化大模型推理效率
6. [Accelerating Visual On-Policy Distillation with Batched Speculative Jacobi Rollouts](/202608/20/2608.18183v1-accelerating-visual-on-policy-distillation-with-batched-speculative-jacobi-rollouts)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：批量投机Jacobi解码用于视觉自回归生成

### 速读区论文标签
1. [Beyond Tokens: A Survey on Decoding Methods for Large Language and Vision-Language Models](/202608/20/2608.14797v1-beyond-tokens-a-survey-on-decoding-methods-for-large-language-and-vision-language-models)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：涵盖LLM与LVLM解码方法、包括并行生成加速的综述
2. [FluxBin: Flexible LUT-based Ultra-low-bit LLM Inference by Algorithm-Kernel Synergy](/202608/20/2608.15602v1-fluxbin-flexible-lut-based-ultra-low-bit-llm-inference-by-algorithm-kernel-synergy)  
   标签：评分：8.0/10、query:llm
   evidence：基于查找表的超低位宽LLM推理加速，算法-内核协同设计
3. [Role-Conditioned Sub-Token Routing for Efficient Vision-Language-Action Policies](/202608/20/2608.18410v1-role-conditioned-sub-token-routing-for-efficient-vision-language-action-policies)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：通过子词元压缩直接加速VLM/VLA推理
4. [Ripple-Pivot Search: Active Parallel Decoding for Diffusion Large Language Models](/202608/20/2608.11742v1-ripple-pivot-search-active-parallel-decoding-for-diffusion-large-language-models)  
   标签：评分：7.0/10、query:llm
   evidence：主动并行解码加速扩散语言模型推理
5. [Reduced Matrix Multiplication: Input-Adaptive Matrix-Product Reduction for LLM Inference](/202608/20/2608.13426v1-reduced-matrix-multiplication-input-adaptive-matrix-product-reduction-for-llm-inference)  
   标签：评分：7.0/10、query:llm
   evidence：面向LLM推理的输入自适应矩阵乘积约简，降低计算开销
6. [Dynamic Multi-Byte Prediction With Hierarchical Language Models](/202608/20/2608.15454v1-dynamic-multi-byte-prediction-with-hierarchical-language-models)  
   标签：评分：7.0/10、query:llm
   evidence：多字节并行预测加速分层语言模型推理
7. [FlashQuant: Sparse-Dense Fusion for Memory-Efficient Outlier-Aware LLM Inference](/202608/20/2608.15531v1-flashquant-sparse-dense-fusion-for-memory-efficient-outlier-aware-llm-inference)  
   标签：评分：7.0/10、query:llm
   evidence：面向解码负载的内存高效离群点感知LLM推理融合
8. [SEER: Long-Context Reasoning via Selective Visual-Text Compression](/202608/20/2608.15962v1-seer-long-context-reasoning-via-selective-visual-text-compression)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：通过选择性视觉-文本压缩实现高效的长上下文VLM推理
9. [MOSS-VL Technical Report](/202608/20/2608.15045v1-moss-vl-technical-report)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：面向实时流式交互的VLM技术报告，采用门控交叉注意力提升效率
10. [Do Visual Grounding Decoders Need Feed-Forward Networks? A Controlled Study over Frozen Vision-Language Features](/202608/20/2608.15061v1-do-visual-grounding-decoders-need-feed-forward-networks-a-controlled-study-over-frozen-vision-language-features)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：控制实验表明视觉定位解码器可省略前馈网络，减少参数并提升VLM推理效率


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
