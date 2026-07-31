<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-07-31
- 运行时间：2026-07-31 21:26:26 UTC
- 运行状态：成功
- 本次总论文数：18
- 精读区：7
- 速读区：11

### 今日简报（AI）
今日18篇论文聚焦大模型高效推理，核心方向为剪枝与稀疏化技术。最值得精读的是统一静态/动态剪枝框架及面向多模态大模型的SepPrune，二者均获9.0高分。建议优先关注剪枝方法在长上下文和多模态场景中的落地效果。
- 详情：[/202607/31/README](/202607/31/README)

### 精读区论文标签
1. [Unified Static-Dynamic Pruning for Efficient LLM Inference](/202607/31/2607.21985v1-unified-static-dynamic-pruning-for-efficient-llm-inference)  
   标签：评分：9.0/10、query:llm
   evidence：面向GPU高效大语言模型推理的静态与动态统一权值剪枝框架
2. [SepPrune:A Separator-based Pruning Framework for Efficient Multimodal Large Language Models](/202607/31/2607.25818v1-sepprunea-separator-based-pruning-framework-for-efficient-multimodal-large-language-models)  
   标签：评分：9.0/10、query:vlm-spec
   evidence：基于分隔符的视觉token剪枝以降低多模态LLM推理开销
3. [AngelSpec: Towards Real-World High Performance Inference with Speculative Decoding](/202607/31/2607.25852v1-angelspec-towards-real-world-high-performance-inference-with-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：针对大语言模型投机解码提出统一训练框架，联合MTP与块并行草稿提升真实推理性能
4. [AngelSpec: Towards Real-World High Performance Inference with Speculative Decoding](/202607/31/2607.25852v2-angelspec-towards-real-world-high-performance-inference-with-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向大模型加速的投机解码方法
5. [Revisiting Lossy Verification in Speculative Decoding: Mechanisms, Trade-offs, and Failure Modes](/202607/31/2607.26627v1-revisiting-lossy-verification-in-speculative-decoding-mechanisms-trade-offs-and-failure-modes)  
   标签：评分：9.0/10、query:llm-sd
   evidence：对投机解码中宽松验证机制的原理性分析
6. [Beyond KV Reconstruction: Functional Reconstruction for MLA Draft Models in Speculative Decoding](/202607/31/2607.27269v1-beyond-kv-reconstruction-functional-reconstruction-for-mla-draft-models-in-speculative-decoding)  
   标签：评分：9.0/10、query:llm-sd
   evidence：投机解码中MLA草稿模型，聚焦草稿与目标验证的一致性
7. [A Sparse Glimpse of the Whole: Train-Free Self-Speculative Decoding](/202607/31/2607.27735v1-a-sparse-glimpse-of-the-whole-train-free-self-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：免训练自投机解码结合稀疏KV缓存，加速大语言模型长上下文推理

### 速读区论文标签
1. [Adaptive Depth Sparse Framework: Similarity-Driven Resource Allocation for Pre-Trained LLMs](/202607/31/2607.21291v1-adaptive-depth-sparse-framework-similarity-driven-resource-allocation-for-pre-trained-llms)  
   标签：评分：8.0/10、query:llm
   evidence：基于相似性的层间稀疏分配加速预训练LLM推理
2. [RIS-Kernel: A Model-Agnostic Architecture for Long-Context LLM Inference via Sparse Attention](/202607/31/2607.21927v1-ris-kernel-a-model-agnostic-architecture-for-long-context-llm-inference-via-sparse-attention)  
   标签：评分：8.0/10、query:llm
   evidence：面向长上下文LLM高效推理的稀疏注意力架构
3. [OmniScope: Modality-Decoupled Token Compression for Omnimodal Large Language Models](/202607/31/2607.23193v1-omniscope-modality-decoupled-token-compression-for-omnimodal-large-language-models)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：面向全模态大语言模型的词元压缩，通过减少词元数量加速推理
4. [OmniScope: Modality-Decoupled Token Compression for Omnimodal Large Language Models](/202607/31/2607.23193v2-omniscope-modality-decoupled-token-compression-for-omnimodal-large-language-models)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：面向全模态大模型的免训练模态解耦token压缩，用以降低推理开销
5. [DraftExpert: Expansion-Aware Self-Speculative Decoding for End-Device MoE Inference](/202607/31/2607.24434v1-draftexpert-expansion-aware-self-speculative-decoding-for-end-device-moe-inference)  
   标签：评分：8.0/10、query:llm-sd
   evidence：面向端侧MoE推理的自投机解码方法
6. [Beyond Prefill-Decode Disaggregation: Dissecting LLM Inference for Heterogeneous Platforms via Dynamic Operator Scheduling](/202607/31/2607.25498v1-beyond-prefill-decode-disaggregation-dissecting-llm-inference-for-heterogeneous-platforms-via-dynamic-operator-scheduling)  
   标签：评分：8.0/10、query:llm
   evidence：面向LLM推理的动态算子调度框架，优化异构平台上的延迟与吞吐
7. [Calibrate Before Reason: Robust Visual Token Reduction against Semantic Drift in VLMs](/202607/31/2607.27700v1-calibrate-before-reason-robust-visual-token-reduction-against-semantic-drift-in-vlms)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：通过视觉Token缩减加速VLM推理
8. [Capturing Token Tendencies for Training-Free Token Pruning in Multimodal Large Language Models](/202607/31/2607.28341v1-capturing-token-tendencies-for-training-free-token-pruning-in-multimodal-large-language-models)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：面向多模态大语言模型的免训练视觉词元剪枝，提升推理效率
9. [MemVLN: Episodic and Procedural Memory for Vision-and-Language Navigation](/202607/31/2607.23504v1-memvln-episodic-and-procedural-memory-for-vision-and-language-navigation)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：VLM导航系统实现实时推理效率与低延迟动作执行
10. [Sol-Attn: Accelerating Video Generation Inference via On-the-Fly Attention Sparsification](/202607/31/2607.24027v1-sol-attn-accelerating-video-generation-inference-via-on-the-fly-attention-sparsification)  
   标签：评分：6.0/10、query:llm
   evidence：面向长序列注意力瓶颈的训练无关动态稀疏注意力，可迁移至高效推理
11. [Rethinking the Generation Order of Block Diffusion Language Models](/202607/31/2607.24306v1-rethinking-the-generation-order-of-block-diffusion-language-models)  
   标签：评分：6.0/10、query:llm
   evidence：针对块扩散语言模型提出并行自回归解码方法，加速文本生成


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
