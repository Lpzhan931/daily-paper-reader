<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-02
- 运行时间：2026-08-02 20:21:59 UTC
- 运行状态：成功
- 本次总论文数：10
- 精读区：6
- 速读区：4

### 今日简报（AI）
今日聚焦LLM推理优化，投机解码成高价值方向，AngelSpec以9.0分领跑精读；速读关注动态算子调度、MLA功能重建及视觉token剪枝。最值得重点关注投机解码的工程实现与跨平台调度优化策略。建议普通读者优先追踪AngelSpec及动态调度相关技术，它们对实际部署效率提升最直接。
- 详情：[/202608/02/README](/202608/02/README)

### 精读区论文标签
1. [AngelSpec: Towards Real-World High Performance Inference with Speculative Decoding](/202608/02/2607.25852v1-angelspec-towards-real-world-high-performance-inference-with-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向大语言模型投机解码的统一训练框架，兼顾多种草稿结构
2. [AngelSpec: Towards Real-World High Performance Inference with Speculative Decoding](/202608/02/2607.25852v2-angelspec-towards-real-world-high-performance-inference-with-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向MTP和块并行投机解码的统一训练框架，直接针对LLM高性能推理加速。
3. [Revisiting Lossy Verification in Speculative Decoding: Mechanisms, Trade-offs, and Failure Modes](/202608/02/2607.26627v1-revisiting-lossy-verification-in-speculative-decoding-mechanisms-trade-offs-and-failure-modes)  
   标签：评分：9.0/10、query:llm-sd
   evidence：系统分析投机解码中的有损验证机制、权衡与失败模式
4. [A Sparse Glimpse of the Whole: Train-Free Self-Speculative Decoding](/202608/02/2607.27735v1-a-sparse-glimpse-of-the-whole-train-free-self-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：利用稀疏KV缓存的免训练自投机解码，加速大语言模型长上下文推理
5. [WIDE: Boosting Adaptive LLM Inference via Token-level Dynamic Width Pruning](/202608/02/2607.28418v1-wide-boosting-adaptive-llm-inference-via-token-level-dynamic-width-pruning)  
   标签：评分：9.0/10、query:llm
   evidence：令牌级动态宽度剪枝用于自适应大语言模型推理，同时优化预填充和解码阶段。
6. [DraftExpert: Expansion-Aware Self-Speculative Decoding for End-Device MoE Inference](/202608/02/2607.24434v1-draftexpert-expansion-aware-self-speculative-decoding-for-end-device-moe-inference)  
   标签：评分：8.0/10、query:llm
   evidence：面向端侧MoE大模型的自投机解码加速推理

### 速读区论文标签
1. [Beyond Prefill-Decode Disaggregation: Dissecting LLM Inference for Heterogeneous Platforms via Dynamic Operator Scheduling](/202608/02/2607.25498v1-beyond-prefill-decode-disaggregation-dissecting-llm-inference-for-heterogeneous-platforms-via-dynamic-operator-scheduling)  
   标签：评分：8.0/10、query:llm
   evidence：面向异构平台的大语言模型推理，联合优化算子调度与权重布局
2. [Beyond KV Reconstruction: Functional Reconstruction for MLA Draft Models in Speculative Decoding](/202608/02/2607.27269v1-beyond-kv-reconstruction-functional-reconstruction-for-mla-draft-models-in-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：投机解码中MLA草稿模型的功能重建方法
3. [LAST: The Last Query Token Guides Visual Token Pruning for Edge-Cloud Collaborative MLLM Inference](/202608/02/2607.27952v1-last-the-last-query-token-guides-visual-token-pruning-for-edge-cloud-collaborative-mllm-inference)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：查询引导的视觉Token剪枝降低云端MLLM推理成本与延迟。
4. [Rethinking the Generation Order of Block Diffusion Language Models](/202608/02/2607.24306v1-rethinking-the-generation-order-of-block-diffusion-language-models)  
   标签：评分：7.0/10、query:llm
   evidence：针对扩散语言模型的并行自回归解码方法，相比自回归解码获得加速，属于高效语言模型推理。


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
