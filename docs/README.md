<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-07-07
- 运行时间：2026-07-07 21:50:57 UTC
- 运行状态：成功
- 本次总论文数：9
- 精读区：5
- 速读区：4

### 今日简报（AI）
今日精读两篇高分论文，分别聚焦长上下文LLM的层级语义记忆KV缓存与CPU受限场景下多策略自适应推测解码，速读则涉及视觉表示的弹性建模与对象证据保留的token合并。

最值得深入的方向：长上下文LLM推理的效率优化（SeKV的分辨率自适应缓存）和CPU环境下的推理加速（AdaptiveSD的稳定性感知推测解码）。

建议优先精读这两篇9分论文，并关注其实际部署中的性能提升，后续可结合速读中的视觉token合并方法拓展多模态推理效率。
- 详情：[/202607/07/README](/202607/07/README)

### 精读区论文标签
1. [SeKV: Resolution-Adaptive KV Cache with Hierarchical Semantic Memory for Long-Context LLM Inference](/202607/07/2606.31145v1-sekv-resolution-adaptive-kv-cache-with-hierarchical-semantic-memory-for-long-context-llm-inference)  
   标签：评分：9.0/10、query:llm
   evidence：提出具有层次语义记忆的分辨率自适应KV缓存，用于长上下文大语言模型推理
2. [AdaptiveSD A Stability-Aware, Runtime-Adaptive Speculative Decoding Framework with Multi-Policy Orchestration for CPU-Constrained LLM Inference](/202607/07/2607.03876v1-adaptivesd-a-stability-aware-runtime-adaptive-speculative-decoding-framework-with-multi-policy-orchestration-for-cpu-constrained-llm-inference)  
   标签：评分：9.0/10、query:llm
   evidence：面向大语言模型推理的运行时自适应投机解码
3. [DSpark: Confidence-Scheduled Speculative Decoding with Semi-Autoregressive Generation](/202607/07/2607.05147v1-dspark-confidence-scheduled-speculative-decoding-with-semi-autoregressive-generation)  
   标签：评分：9.0/10、query:llm
   evidence：DSpark置信度调度投机解码加速LLM推理
4. [Predict, Reuse, and Repair: Accelerating Dynamic Sparse Attention for Long-Context LLM Decoding](/202607/07/2606.30389v1-predict-reuse-and-repair-accelerating-dynamic-sparse-attention-for-long-context-llm-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：通过预测稀疏注意力块加速大语言模型解码的投机-重用-修复运行时
5. [TORINO: Token Reduction via Interpretable Concept Overlap in Vision-Language Models](/202607/07/2607.04593v1-torino-token-reduction-via-interpretable-concept-overlap-in-vision-language-models)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：提出利用稀疏自编码器的即插即用视觉令牌缩减框架

### 速读区论文标签
1. [RADIO1D: Elastic Representations for Condensed Vision Modeling](/202607/07/2607.03624v1-radio1d-elastic-representations-for-condensed-vision-modeling)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：将图像压缩为紧凑的一维令牌序列，减少视觉令牌以加速推理
2. [Do All Visual Tokens Matter Equally? Object-Evidence Preserving Token Merging for Vision-Language Retrieval](/202607/07/2607.04605v1-do-all-visual-tokens-matter-equally-object-evidence-preserving-token-merging-for-vision-language-retrieval)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：视觉语言模型推理加速中的令牌合并
3. [Towards High-Resolution Visual Perception via Hierarchical Entity Exploration](/202607/07/2607.00816v1-towards-high-resolution-visual-perception-via-hierarchical-entity-exploration)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：无训练层次化探索加速高分辨率视觉语言模型感知
4. [Parallelized Autoregressive Decoding for Omni-Modal Dense Video Captioning](/202607/07/2607.02963v1-parallelized-autoregressive-decoding-for-omni-modal-dense-video-captioning)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：并行化自回归解码加速视频密描


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
