<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-01
- 运行时间：2026-08-01 20:59:27 UTC
- 运行状态：成功
- 本次总论文数：13
- 精读区：7
- 速读区：6

### 今日简报（AI）
今日聚焦大模型推理效率，精读2篇高分论文并速览3篇相关研究。
最值得关注的是统一静态-动态剪枝与面向端侧MoE的自投机解码，均获9.0分，可显著加速推理。
建议普通读者优先了解剪枝与投机解码的组合思路，以低成本提升大模型部署性能。
- 详情：[/202608/01/README](/202608/01/README)

### 精读区论文标签
1. [Unified Static-Dynamic Pruning for Efficient LLM Inference](/202608/01/2607.21985v1-unified-static-dynamic-pruning-for-efficient-llm-inference)  
   标签：评分：9.0/10、query:llm
   evidence：统一静态-动态剪枝的稀疏推理框架，用于GPU上的高效大模型推理。
2. [DraftExpert: Expansion-Aware Self-Speculative Decoding for End-Device MoE Inference](/202608/01/2607.24434v1-draftexpert-expansion-aware-self-speculative-decoding-for-end-device-moe-inference)  
   标签：评分：9.0/10、query:llm
   evidence：面向端侧MoE LLM推理的自投机解码
3. [AngelSpec: Towards Real-World High Performance Inference with Speculative Decoding](/202608/01/2607.25852v1-angelspec-towards-real-world-high-performance-inference-with-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：统一自回归MTP与块并行扩散两类投机解码结构，提升真实负载下的大模型推理性能
4. [AngelSpec: Towards Real-World High Performance Inference with Speculative Decoding](/202608/01/2607.25852v2-angelspec-towards-real-world-high-performance-inference-with-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：用于加速LLM推理的投机解码；面向MTP与块平行草稿器的统一训练框架
5. [Revisiting Lossy Verification in Speculative Decoding: Mechanisms, Trade-offs, and Failure Modes](/202608/01/2607.26627v1-revisiting-lossy-verification-in-speculative-decoding-mechanisms-trade-offs-and-failure-modes)  
   标签：评分：9.0/10、query:llm-sd
   evidence：投机解码中有损验证机制的分析
6. [Beyond KV Reconstruction: Functional Reconstruction for MLA Draft Models in Speculative Decoding](/202608/01/2607.27269v1-beyond-kv-reconstruction-functional-reconstruction-for-mla-draft-models-in-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：通过功能重建提升MLA草稿模型与目标验证的一致性，同时优化KV缓存与投机解码效率
7. [A Sparse Glimpse of the Whole: Train-Free Self-Speculative Decoding](/202608/01/2607.27735v1-a-sparse-glimpse-of-the-whole-train-free-self-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：免训练自投机解码，结合KV缓存稀疏化与验证复用

### 速读区论文标签
1. [Beyond Prefill-Decode Disaggregation: Dissecting LLM Inference for Heterogeneous Platforms via Dynamic Operator Scheduling](/202608/01/2607.25498v1-beyond-prefill-decode-disaggregation-dissecting-llm-inference-for-heterogeneous-platforms-via-dynamic-operator-scheduling)  
   标签：评分：8.0/10、query:llm
   evidence：面向大语言模型高效推理的动态算子调度
2. [WIDE: Boosting Adaptive LLM Inference via Token-level Dynamic Width Pruning](/202608/01/2607.28418v1-wide-boosting-adaptive-llm-inference-via-token-level-dynamic-width-pruning)  
   标签：评分：8.0/10、query:llm
   evidence：令牌级动态宽度剪枝实现自适应大模型推理
3. [VisualRouter: Query-Grounded Visual Sampling for Long Video Understanding](/202608/01/2607.28463v1-visualrouter-query-grounded-visual-sampling-for-long-video-understanding)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：基于查询的帧采样减少视觉令牌，无需训练即可用于长视频VLM理解。
4. [ReToken: One Token to Improve Vision-Language Models for Visual Retrieval](/202608/01/2607.28627v1-retoken-one-token-to-improve-vision-language-models-for-visual-retrieval)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：从预填充KV缓存中选取少量相关视觉令牌，降低内存占用并提高效率。
5. [RIS-Kernel: A Model-Agnostic Architecture for Long-Context LLM Inference via Sparse Attention](/202608/01/2607.21927v1-ris-kernel-a-model-agnostic-architecture-for-long-context-llm-inference-via-sparse-attention)  
   标签：评分：7.0/10、query:llm
   evidence：面向长上下文大语言模型高效推理的稀疏注意力
6. [Where and When to Commit: Candidate-Aware Decoding for Diffusion Language Models](/202608/01/2607.28166v1-where-and-when-to-commit-candidate-aware-decoding-for-diffusion-language-models)  
   标签：评分：6.0/10、query:llm
   evidence：针对扩散语言模型的训练无关提前退出解码加速


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
