<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-01
- 运行时间：2026-09-01 23:00:42 UTC
- 运行状态：成功
- 本次总论文数：15
- 精读区：6
- 速读区：9

### 今日简报（AI）
今日精读聚焦大模型推测解码，两篇高分论文分别面向智能体批量推理与多接入场景。最值得关注的是AgentSpec与Multi-Access方案，均获9.0分，可显著加速推理。若想快速入门，建议优先精读这两篇，再延伸速读扩散模型与文档感知相关条目。
- 详情：[/202609/01/README](/202609/01/README)

### 精读区论文标签
1. [AgentSpec: Speculative Decoding for Batch Inference of LLM Agents](/202609/01/2608.24004v1-agentspec-speculative-decoding-for-batch-inference-of-llm-agents)  
   标签：评分：9.0/10、query:llm
   evidence：面向LLM智能体批量推理的投机解码算法
2. [Multi-Access Speculative Inference: Uplink or Downlink?](/202609/01/2608.29618v1-multi-access-speculative-inference-uplink-or-downlink)  
   标签：评分：9.0/10、query:llm
   evidence：设备端小模型草稿、边缘大模型并行验证的投机推理
3. [ReTrace: Rejected-Trajectory Conditioning for Speculative Decoding](/202609/01/2608.29748v1-retrace-rejected-trajectory-conditioning-for-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：投机解码中利用拒绝轨迹改进草稿模型，减少计算浪费
4. [Verification-Aware Training for Speculative Decoding](/202609/01/2608.30135v1-verification-aware-training-for-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向大语言模型投机解码的验证感知训练，提升草稿接受率
5. [Strong Drafts Need Compact Memories: Long-Context Speculative Decoding with Compressed KV Cache](/202609/01/2608.30252v1-strong-drafts-need-compact-memories-long-context-speculative-decoding-with-compressed-kv-cache)  
   标签：评分：9.0/10、query:llm
   evidence：利用压缩的草稿侧KV缓存增强长上下文投机解码的草稿质量
6. [CateKV: On Sequential Consistency for Long-Context LLM Inference Acceleration](/202609/01/2608.30295v1-catekv-on-sequential-consistency-for-long-context-llm-inference-acceleration)  
   标签：评分：9.0/10、query:llm
   evidence：面向大语言模型高效推理的KV缓存优化

### 速读区论文标签
1. [Reservoir of Importance: Learning Semi-Structured Sparsity with Differentiable Subset Sampling](/202609/01/2608.23048v1-reservoir-of-importance-learning-semi-structured-sparsity-with-differentiable-subset-sampling)  
   标签：评分：8.0/10、query:llm
   evidence：基于可微子集采样的半结构化剪枝，加速大模型推理
2. [Trajectory-Level Speculative Decoding for Diffusion Language Models](/202609/01/2608.27514v1-trajectory-level-speculative-decoding-for-diffusion-language-models)  
   标签：评分：8.0/10、query:llm-sd
   evidence：面向扩散语言模型的投机解码与分块验证
3. [State-Conditioned Visual Evidence Retrieval for Fine-Grained Perception in Document Vision-Language Models](/202609/01/2608.28698v1-state-conditioned-visual-evidence-retrieval-for-fine-grained-perception-in-document-vision-language-models)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：通过状态条件视觉证据检索减少VLM自回归解码中的无效计算
4. [Accelerating Unified Multimodal Models with Core-Expansion Routing and Unified Computation Scheduling](/202609/01/2608.29291v1-accelerating-unified-multimodal-models-with-core-expansion-routing-and-unified-computation-scheduling)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：通过核心-扩展路由与统一计算调度加速多模态模型推理
5. [NeuroPrefetcher: Storage-Aware Sparse LLM Inference via Delta Prefetching](/202609/01/2608.22643v1-neuroprefetcher-storage-aware-sparse-llm-inference-via-delta-prefetching)  
   标签：评分：7.0/10、query:llm
   evidence：面向边缘设备的存储感知稀疏大模型推理，通过增量预取降低存储访问开销
6. [Dependency-Aware Revocable Decoding for Efficient Diffusion Large Language Model Inference](/202609/01/2608.26574v1-dependency-aware-revocable-decoding-for-efficient-diffusion-large-language-model-inference)  
   标签：评分：7.0/10、query:llm
   evidence：DARD 通过依赖感知的可撤销验证解码提升扩散大语言模型推理效率，属于大模型推理加速范畴
7. [AdaVLA: Adaptive Step Flow Matching for Training-free Acceleration of Vision-Language-Action Models](/202609/01/2608.29208v1-adavla-adaptive-step-flow-matching-for-training-free-acceleration-of-vision-language-action-models)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：视觉-语言-动作模型推理的免训练加速
8. [VisLens: Single-Pass Interpretable Visual Search for Multimodal LLMs](/202609/01/2608.30705v1-vislens-single-pass-interpretable-visual-search-for-multimodal-llms)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：多模态大模型推理加速：多次查询缩减为单次前向
9. [Instruction Distillation: Text Instructions as Visual Examples](/202609/01/2608.28696v1-instruction-distillation-text-instructions-as-visual-examples)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：指令蒸馏在推理阶段减少多模态大模型视觉上下文令牌占用，实现VLM推理加速


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
