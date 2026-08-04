<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-04
- 运行时间：2026-08-04 21:50:06 UTC
- 运行状态：成功
- 本次总论文数：18
- 精读区：9
- 速读区：9

### 今日简报（AI）
1) 今日18篇论文聚焦推测解码与端侧推理优化，9篇精读覆盖有损验证机制与MoE自推测解码。  
2) 最值得关注《Revisiting Lossy Verification》揭示推测解码中验证损失的权衡与失败模式，以及《DraftExpert》面向终端设备的扩张感知自推测解码方案。  
3) 建议优先深入推测解码的可靠性边界，并关注MLA重构与视频token压缩等加速推理的新方向。
- 详情：[/202608/04/README](/202608/04/README)

### 精读区论文标签
1. [Revisiting Lossy Verification in Speculative Decoding: Mechanisms, Trade-offs, and Failure Modes](/202608/04/2607.26627v1-revisiting-lossy-verification-in-speculative-decoding-mechanisms-trade-offs-and-failure-modes)  
   标签：评分：10.0/10、query:llm-sd
   evidence：有损验证，投机解码，统一分布分析
2. [DraftExpert: Expansion-Aware Self-Speculative Decoding for End-Device MoE Inference](/202608/04/2607.24434v1-draftexpert-expansion-aware-self-speculative-decoding-for-end-device-moe-inference)  
   标签：评分：9.0/10、query:llm-sd
   evidence：面向MoE大语言模型的自投机解码，匹配大模型投机解码需求
3. [AngelSpec: Towards Real-World High Performance Inference with Speculative Decoding](/202608/04/2607.25852v1-angelspec-towards-real-world-high-performance-inference-with-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向大语言模型推断加速的投机解码方法
4. [AngelSpec: Towards Real-World High Performance Inference with Speculative Decoding](/202608/04/2607.25852v2-angelspec-towards-real-world-high-performance-inference-with-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：统一训练MTP与块并行投机解码，面向真实工作负载的高性能LLM推理
5. [A Sparse Glimpse of the Whole: Train-Free Self-Speculative Decoding](/202608/04/2607.27735v1-a-sparse-glimpse-of-the-whole-train-free-self-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向长上下文LLM推理的无训练自投机解码，动态稀疏KV缓存，直接对应投机解码与KV缓存优化。
6. [CURE: Local Uncertainty Repair for Block-Parallel Speculative Decoding](/202608/04/2608.00531v1-cure-local-uncertainty-repair-for-block-parallel-speculative-decoding)  
   标签：评分：9.0/10、query:llm-sd
   evidence：投机解码结合局部不确定性修复并降低验证拒绝率
7. [Bole: Efficient Tree Speculation for Hybrid-Attention Language Models](/202608/04/2608.01651v1-bole-efficient-tree-speculation-for-hybrid-attention-language-models)  
   标签：评分：9.0/10、query:llm
   evidence：混合注意力语言模型的高效树投机解码，通过内核-运行时协同设计降低验证延迟与内存开销。
8. [From Chains to Trees: Parent-Conditioned Drafting for Semi-Autoregressive Speculative Decoding](/202608/04/2608.02123v1-from-chains-to-trees-parent-conditioned-drafting-for-semi-autoregressive-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：半自回归投机解码，树形草拟，提升验证接受率
9. [Messages, Not Tokens: Grounded Coresets for Faithful VLM Compression](/202608/04/2608.02134v1-messages-not-tokens-grounded-coresets-for-faithful-vlm-compression)  
   标签：评分：9.0/10、query:vlm-spec
   evidence：通过视觉令牌压缩降低VLM推理成本与KV缓存开销

### 速读区论文标签
1. [Beyond KV Reconstruction: Functional Reconstruction for MLA Draft Models in Speculative Decoding](/202608/04/2607.27269v1-beyond-kv-reconstruction-functional-reconstruction-for-mla-draft-models-in-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：针对MLA草稿模型的功能重建以改善投机解码一致性
2. [AOSpec: Action and Observation Co-Speculation for Low-Latency Agent Serving](/202608/04/2608.00881v1-aospec-action-and-observation-co-speculation-for-low-latency-agent-serving)  
   标签：评分：8.0/10、query:llm
   evidence：对智能体动作与观测进行协同投机解码，降低LLM服务延迟
3. [CRAFT: Compression via Recursive Adaptive Fusion of Video Tokens for Vision-Language Models](/202608/04/2608.01644v1-craft-compression-via-recursive-adaptive-fusion-of-video-tokens-for-vision-language-models)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：视频令牌压缩，预填充加速，递归自适应融合
4. [Rethinking the Generation Order of Block Diffusion Language Models](/202608/04/2607.24306v1-rethinking-the-generation-order-of-block-diffusion-language-models)  
   标签：评分：7.0/10、query:llm
   evidence：面向扩散语言模型高效生成的并行自回归解码方法
5. [Beyond Prefill-Decode Disaggregation: Dissecting LLM Inference for Heterogeneous Platforms via Dynamic Operator Scheduling](/202608/04/2607.25498v1-beyond-prefill-decode-disaggregation-dissecting-llm-inference-for-heterogeneous-platforms-via-dynamic-operator-scheduling)  
   标签：评分：7.0/10、query:llm
   evidence：面向异构平台高效LLM推理的动态算子调度与分块权重布局优化
6. [Linear Multi-Timescale Retention as a Memory-Efficient Vision-Language Bridge](/202608/04/2608.01614v1-linear-multi-timescale-retention-as-a-memory-efficient-vision-language-bridge)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：以线性保留模块替代Softmax注意力，降低VLM跨模态桥接的内存复杂度
7. [DAVET: Denoising-Aware Visual Evidence Trajectory Allocation for Diffusion Vision-Language Models](/202608/04/2608.01821v1-davet-denoising-aware-visual-evidence-trajectory-allocation-for-diffusion-vision-language-models)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：面向扩散视觉语言模型的适应性视觉证据分配以降低推理成本
8. [FibVLA: An Efficient Temporal Vision-Language-Action Model with Fibonacci Sampling](/202608/04/2607.29596v1-fibvla-an-efficient-temporal-vision-language-action-model-with-fibonacci-sampling)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：面向长上下文历史与推理效率冲突的VLA高效采样框架
9. [Same Semantics, Different Paths: Self-Improving Alignment for Vision-Text Compression](/202608/04/2608.02109v1-same-semantics-different-paths-self-improving-alignment-for-vision-text-compression)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：视觉-文本压缩减少了视觉语言处理中的令牌消耗，可能有助于推理加速


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
