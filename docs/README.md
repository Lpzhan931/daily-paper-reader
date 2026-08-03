<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-03
- 运行时间：2026-08-03 21:31:36 UTC
- 运行状态：成功
- 本次总论文数：10
- 精读区：6
- 速读区：4

### 今日简报（AI）
今日精读聚焦投机解码中的有损验证机制与端侧MoE自投机解码，速读涵盖动态算子调度、动态宽度剪枝及多模态扩散模型内容漂移。最值得关注的是投机解码失败模式与端侧部署的扩展感知自解码方案，以及动态剪枝对自适应推理的加速潜力。普通读者可优先关注推理加速中的质量-效率权衡，留意有损验证与剪枝对输出一致性的影响。
- 详情：[/202608/03/README](/202608/03/README)

### 精读区论文标签
1. [Revisiting Lossy Verification in Speculative Decoding: Mechanisms, Trade-offs, and Failure Modes](/202608/03/2607.26627v1-revisiting-lossy-verification-in-speculative-decoding-mechanisms-trade-offs-and-failure-modes)  
   标签：评分：10.0/10、query:llm-sd
   evidence：投机解码中的有损验证机制分析，归类宽松验证方法并揭示质量退化风险
2. [DraftExpert: Expansion-Aware Self-Speculative Decoding for End-Device MoE Inference](/202608/03/2607.24434v1-draftexpert-expansion-aware-self-speculative-decoding-for-end-device-moe-inference)  
   标签：评分：9.0/10、query:llm
   evidence：面向端侧MoE LLM推理的扩张感知自投机解码
3. [AngelSpec: Towards Real-World High Performance Inference with Speculative Decoding](/202608/03/2607.25852v1-angelspec-towards-real-world-high-performance-inference-with-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：统一多token预测与块并行投机解码框架，面向高性能大模型推理
4. [AngelSpec: Towards Real-World High Performance Inference with Speculative Decoding](/202608/03/2607.25852v2-angelspec-towards-real-world-high-performance-inference-with-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：统一训练框架，适配多种投机解码结构的真实负载推理
5. [Beyond KV Reconstruction: Functional Reconstruction for MLA Draft Models in Speculative Decoding](/202608/03/2607.27269v1-beyond-kv-reconstruction-functional-reconstruction-for-mla-draft-models-in-speculative-decoding)  
   标签：评分：9.0/10、query:llm-sd
   evidence：针对投机解码中MLA草稿模型的功能重建，提升草稿与目标模型的一致性
6. [A Sparse Glimpse of the Whole: Train-Free Self-Speculative Decoding](/202608/03/2607.27735v1-a-sparse-glimpse-of-the-whole-train-free-self-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向长上下文LLM的无训练自投机解码，结合稀疏KV缓存

### 速读区论文标签
1. [Beyond Prefill-Decode Disaggregation: Dissecting LLM Inference for Heterogeneous Platforms via Dynamic Operator Scheduling](/202608/03/2607.25498v1-beyond-prefill-decode-disaggregation-dissecting-llm-inference-for-heterogeneous-platforms-via-dynamic-operator-scheduling)  
   标签：评分：8.0/10、query:llm
   evidence：面向异构平台的动态算子调度，优化LLM推理时延
2. [WIDE: Boosting Adaptive LLM Inference via Token-level Dynamic Width Pruning](/202608/03/2607.28418v1-wide-boosting-adaptive-llm-inference-via-token-level-dynamic-width-pruning)  
   标签：评分：8.0/10、query:llm
   evidence：词元级动态宽度剪枝，端到端可微，兼顾预填充与解码阶段
3. [Faster but Different: Diagnosing and Controlling Content Drift in Accelerated Multimodal Diffusion Language Models](/202608/03/2607.29079v1-faster-but-different-diagnosing-and-controlling-content-drift-in-accelerated-multimodal-diffusion-language-models)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：研究多模态扩散大模型中类投机解码加速及其内容漂移
4. [Where and When to Commit: Candidate-Aware Decoding for Diffusion Language Models](/202608/03/2607.28166v1-where-and-when-to-commit-candidate-aware-decoding-for-diffusion-language-models)  
   标签：评分：6.0/10、query:llm
   evidence：面向扩散语言模型的免训练候选感知早停解码，与高效推理加速方法相关


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
