<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-05
- 运行时间：2026-08-05 20:30:09 UTC
- 运行状态：成功
- 本次总论文数：14
- 精读区：10
- 速读区：4

### 今日简报（AI）
今日14篇论文聚焦推理加速，投机解码成最大热点。  
精读双雄《Approximate Speculative Decoding》（10分）与《AngelSpec》（9分）均瞄准投机解码的实用化优化，值得优先关注。  
若想快速落地方案，可结合速读中的动态调度与预取技术，从系统层面协同提速。
- 详情：[/202608/05/README](/202608/05/README)

### 精读区论文标签
1. [Approximate Speculative Decoding](/202608/05/2608.03447v1-approximate-speculative-decoding)  
   标签：评分：10.0/10、query:llm-sd
   evidence：通过预算化最长前缀选择放宽投机解码中的贪心验证机制
2. [AngelSpec: Towards Real-World High Performance Inference with Speculative Decoding](/202608/05/2607.25852v1-angelspec-towards-real-world-high-performance-inference-with-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：统一MTP与块并行草稿的投机解码框架，加速大模型推理
3. [AngelSpec: Towards Real-World High Performance Inference with Speculative Decoding](/202608/05/2607.25852v2-angelspec-towards-real-world-high-performance-inference-with-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向大语言模型推理加速的投机解码，统一MTP与块并行草稿训练
4. [Revisiting Lossy Verification in Speculative Decoding: Mechanisms, Trade-offs, and Failure Modes](/202608/05/2607.26627v1-revisiting-lossy-verification-in-speculative-decoding-mechanisms-trade-offs-and-failure-modes)  
   标签：评分：9.0/10、query:llm-sd
   evidence：投机解码中的有损验证；宽松验证机制、权衡与失败模式
5. [Beyond KV Reconstruction: Functional Reconstruction for MLA Draft Models in Speculative Decoding](/202608/05/2607.27269v1-beyond-kv-reconstruction-functional-reconstruction-for-mla-draft-models-in-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向LLM的投机解码与KV缓存优化，通过功能重建提升草稿与目标的一致性
6. [A Sparse Glimpse of the Whole: Train-Free Self-Speculative Decoding](/202608/05/2607.27735v1-a-sparse-glimpse-of-the-whole-train-free-self-speculative-decoding)  
   标签：评分：9.0/10、query:llm-sd
   evidence：基于稀疏KV缓存草稿的无训练自投机解码框架，加速LLM推理
7. [CURE: Local Uncertainty Repair for Block-Parallel Speculative Decoding](/202608/05/2608.00531v1-cure-local-uncertainty-repair-for-block-parallel-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：利用局部不确定性修复提升块并行投机解码的验证接受率
8. [Bole: Efficient Tree Speculation for Hybrid-Attention Language Models](/202608/05/2608.01651v1-bole-efficient-tree-speculation-for-hybrid-attention-language-models)  
   标签：评分：9.0/10、query:llm
   evidence：面向混合注意力LLM的高效树投机，降低验证延迟与瞬态内存
9. [From Chains to Trees: Parent-Conditioned Drafting for Semi-Autoregressive Speculative Decoding](/202608/05/2608.02123v1-from-chains-to-trees-parent-conditioned-drafting-for-semi-autoregressive-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向LLM投机解码加速；提出PCTree进行树形半自回归草稿生成
10. [Adaptive Two-Stage Visual Token Pruning for Efficient Inference in Video-Language Models](/202608/05/2608.03112v1-adaptive-two-stage-visual-token-pruning-for-efficient-inference-in-video-language-models)  
   标签：评分：9.0/10、query:vlm-spec
   evidence：针对视频语言模型的自适应两阶段视觉Token剪枝，降低推理延迟

### 速读区论文标签
1. [Beyond Prefill-Decode Disaggregation: Dissecting LLM Inference for Heterogeneous Platforms via Dynamic Operator Scheduling](/202608/05/2607.25498v1-beyond-prefill-decode-disaggregation-dissecting-llm-inference-for-heterogeneous-platforms-via-dynamic-operator-scheduling)  
   标签：评分：8.0/10、query:llm
   evidence：面向异构平台的LLM推理动态算子调度加速
2. [DualDecoder: Accelerate Long Context LLM Inference by Predictive Prefetch](/202608/05/2607.26475v1-dualdecoder-accelerate-long-context-llm-inference-by-predictive-prefetch)  
   标签：评分：8.0/10、query:llm
   evidence：通过预测性预取和KV缓存卸载加速长上下文LLM推理
3. [SlimVLM: Sensitivity-aware Dynamic Structured Pruning with Adaptive Visual Token Selection for Efficient Vision-Language Models](/202608/05/2608.03580v1-slimvlm-sensitivity-aware-dynamic-structured-pruning-with-adaptive-visual-token-selection-for-efficient-vision-language-models)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：面向VLM的结构化剪枝与自适应视觉Token选择，降低计算开销
4. [DeVIT: Low-Power Vision Transformer Acceleration Using Delta Computation](/202608/05/2608.01343v1-devit-low-power-vision-transformer-acceleration-using-delta-computation)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：通过增量计算加速视觉Transformer，可望降低VLM视觉编码器成本


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
