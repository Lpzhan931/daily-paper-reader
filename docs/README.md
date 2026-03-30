<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-03-30
- 运行时间：2026-03-30 20:17:04 UTC
- 运行状态：成功
- 本次总论文数：17
- 精读区：6
- 速读区：11

### 今日简报（AI）
今日聚焦多模态与蛋白质大模型的效率突破，深入探讨了 Token 剪枝与超低位量化等 17 篇前沿进展。
重点推荐 ReDiPrune 的相关性-多样性剪枝方案，以及 TurboESM 实现的蛋白质模型 3-bit KV 缓存极速量化。
建议关注端侧部署与长文本优化的读者，从 GUI 智能体及 VLA 模型的稀疏化策略中寻找落地灵感。
- 详情：[/202603/30/README](/202603/30/README)

### 精读区论文标签
1. [ReDiPrune: Relevance-Diversity Pre-Projection Token Pruning for Efficient Multimodal LLMs](/202603/30/2603.24680v1-rediprune-relevance-diversity-pre-projection-token-pruning-for-efficient-multimodal-llms)  
   标签：评分：9.0/10、query:llm
   evidence：用于高效多模态大模型的免训练Token剪枝
2. [TurboESM: Ultra-Efficient 3-Bit KV Cache Quantization for Protein Language Models with Orthogonal Rotation and QJL Correction](/202603/30/2603.26110v1-turboesm-ultra-efficient-3-bit-kv-cache-quantization-for-protein-language-models-with-orthogonal-rotation-and-qjl-correction)  
   标签：评分：9.0/10、query:llm
   evidence：蛋白质模型中的3比特KV缓存量化
3. [Rocks, Pebbles and Sand: Modality-aware Scheduling for Multimodal Large Language Model Inference](/202603/30/2603.26498v1-rocks-pebbles-and-sand-modality-aware-scheduling-for-multimodal-large-language-model-inference)  
   标签：评分：9.0/10、query:llm
   evidence：针对多模态大模型推理的模态感知调度以降低延迟
4. [MemBoost: A Memory-Boosted Framework for Cost-Aware LLM Inference](/202603/30/2603.26557v1-memboost-a-memory-boosted-framework-for-cost-aware-llm-inference)  
   标签：评分：9.0/10、query:llm
   evidence：成本感知的LLM服务框架，支持答案复用和路由
5. [SiftMoE: Similarity-Aware Energy-Efficient Expert Selection for Wireless Distributed MoE Inference](/202603/30/2603.23888v1-siftmoe-similarity-aware-energy-efficient-expert-selection-for-wireless-distributed-moe-inference)  
   标签：评分：8.0/10、query:llm
   evidence：分布式MoE推理中的能效专家选择策略
6. [PackForcing: Short Video Training Suffices for Long Video Sampling and Long Context Inference](/202603/30/2603.25730v1-packforcing-short-video-training-suffices-for-long-video-sampling-and-long-context-inference)  
   标签：评分：8.0/10、query:llm
   evidence：针对长上下文的三分区KV缓存策略

### 速读区论文标签
1. [ETA-VLA: Efficient Token Adaptation via Temporal Fusion and Intra-LLM Sparsification for Vision-Language-Action Models](/202603/30/2603.25766v1-eta-vla-efficient-token-adaptation-via-temporal-fusion-and-intra-llm-sparsification-for-vision-language-action-models)  
   标签：评分：8.0/10、query:llm
   evidence：LLM内部稀疏化以缓解自注意力机制的平方复杂度
2. [Density-aware Soft Context Compression with Semi-Dynamic Compression Ratio](/202603/30/2603.25926v1-density-aware-soft-context-compression-with-semi-dynamic-compression-ratio)  
   标签：评分：8.0/10、query:llm
   evidence：软上下文压缩以减少计算负载
3. [Rethinking Token Pruning for Historical Screenshots in GUI Visual Agents: Semantic, Spatial, and Temporal Perspectives](/202603/30/2603.26041v1-rethinking-token-pruning-for-historical-screenshots-in-gui-visual-agents-semantic-spatial-and-temporal-perspectives)  
   标签：评分：8.0/10、query:llm
   evidence：针对GUI视觉智能体历史截图的Token剪枝技术
4. [LLaDA-TTS: Unifying Speech Synthesis and Zero-Shot Editing via Masked Diffusion Modeling](/202603/30/2603.26364v1-llada-tts-unifying-speech-synthesis-and-zero-shot-editing-via-masked-diffusion-modeling)  
   标签：评分：8.0/10、query:llm
   evidence：通过掩码扩散模型实现并行生成，获得2倍加速
5. [QMoP: Query Guided Mixture-of-Projector for Efficient Visual Token Compression](/202603/30/2603.21232v1-qmop-query-guided-mixture-of-projector-for-efficient-visual-token-compression)  
   标签：评分：7.0/10、query:llm
   evidence：基于剪枝的分支用于细粒度Token选择
6. [From Static Templates to Dynamic Runtime Graphs: A Survey of Workflow Optimization for LLM Agents](/202603/30/2603.22386v1-from-static-templates-to-dynamic-runtime-graphs-a-survey-of-workflow-optimization-for-llm-agents)  
   标签：评分：7.0/10、query:llm
   evidence：LLM智能体工作流优化的综述
7. [Knowledge Access Beats Model Size: Memory Augmented Routing for Persistent AI Agents](/202603/30/2603.23013v1-knowledge-access-beats-model-size-memory-augmented-routing-for-persistent-ai-agents)  
   标签：评分：7.0/10、query:llm
   evidence：利用记忆增强推理框架降低推理成本
8. [SumRank: Aligning Summarization Models for Long-Document Listwise Reranking](/202603/30/2603.24204v1-sumrank-aligning-summarization-models-for-long-document-listwise-reranking)  
   标签：评分：7.0/10、query:llm
   evidence：压缩长文档以提高效率
9. [When Perplexity Lies: Generation-Focused Distillation of Hybrid Sequence Models](/202603/30/2603.26556v1-when-perplexity-lies-generation-focused-distillation-of-hybrid-sequence-models)  
   标签：评分：7.0/10、query:llm
   evidence：将Transformer蒸馏为高效混合模型以降低推理成本
10. [DSPA: Dynamic SAE Steering for Data-Efficient Preference Alignment](/202603/30/2603.21461v1-dspa-dynamic-sae-steering-for-data-efficient-preference-alignment)  
   标签：评分：6.0/10、query:llm
   evidence：无需权重更新的推理阶段偏好对齐方法
11. [TorR: Towards Brain-Inspired Task-Oriented Reasoning via Cache-Oriented Algorithm-Architecture Co-design](/202603/30/2603.22855v1-torr-towards-brain-inspired-task-oriented-reasoning-via-cache-oriented-algorithm-architecture-co-design)  
   标签：评分：6.0/10、query:llm
   evidence：面向缓存的算法-架构协同设计


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
