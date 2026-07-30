<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-07-30
- 运行时间：2026-07-30 21:35:18 UTC
- 运行状态：成功
- 本次总论文数：14
- 精读区：6
- 速读区：8

### 今日简报（AI）
今日推荐6篇精读、8篇速读，重点聚焦提升大模型推理效率与资源优化技术。  
最值得关注的是《AngelSpec》实现的推测解码高性能方案（9.0分）和《TurboVLA》在RTX 4090上以32Hz运行视觉-语言-动作模型且显存低于1GB的突破（8.0分）。  
建议优先阅读这两篇，以了解当前降低模型部署成本、提升实时性的实用方向。
- 详情：[/202607/30/README](/202607/30/README)

### 精读区论文标签
1. [AngelSpec: Towards Real-World High Performance Inference with Speculative Decoding](/202607/30/2607.25852v1-angelspec-towards-real-world-high-performance-inference-with-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：提出统一训练框架AngelSpec，支持自回归多token预测和块并行扩散的投机解码，用于加速大语言模型推理
2. [AngelSpec: Towards Real-World High Performance Inference with Speculative Decoding](/202607/30/2607.25852v2-angelspec-towards-real-world-high-performance-inference-with-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：提出AngelSpec，一个统一训练框架，支持多令牌预测和块并行投机解码
3. [Revisiting Lossy Verification in Speculative Decoding: Mechanisms, Trade-offs, and Failure Modes](/202607/30/2607.26627v1-revisiting-lossy-verification-in-speculative-decoding-mechanisms-trade-offs-and-failure-modes)  
   标签：评分：9.0/10、query:llm-sd
   evidence：投机解码中有损验证机制分析
4. [RIS-Kernel: A Model-Agnostic Architecture for Long-Context LLM Inference via Sparse Attention](/202607/30/2607.21927v1-ris-kernel-a-model-agnostic-architecture-for-long-context-llm-inference-via-sparse-attention)  
   标签：评分：8.0/10、query:llm
   evidence：提出模型无关的稀疏注意力架构RIS，用于加速长上下文大语言模型推理
5. [Unified Static-Dynamic Pruning for Efficient LLM Inference](/202607/30/2607.21985v1-unified-static-dynamic-pruning-for-efficient-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：提出统一静态-动态剪枝框架SPDP，用于高效大语言模型推理
6. [DraftExpert: Expansion-Aware Self-Speculative Decoding for End-Device MoE Inference](/202607/30/2607.24434v1-draftexpert-expansion-aware-self-speculative-decoding-for-end-device-moe-inference)  
   标签：评分：8.0/10、query:llm-sd
   evidence：针对MoE模型的扩展感知自投机解码方法

### 速读区论文标签
1. [Rethinking the Generation Order of Block Diffusion Language Models](/202607/30/2607.24306v1-rethinking-the-generation-order-of-block-diffusion-language-models)  
   标签：评分：8.0/10、query:llm
   evidence：提出并行自回归解码（PARD）以加速块扩散语言模型生成
2. [TurboVLA: Real-Time Vision-Language-Action Model at 32 Hz on an RTX 4090 with <1 GB VRAM](/202607/30/2607.27205v1-turbovla-real-time-vision-language-action-model-at-32-hz-on-an-rtx-4090-with-1-gb-vram)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：实时视觉-语言-动作模型推理加速
3. [Adaptive Depth Sparse Framework: Similarity-Driven Resource Allocation for Pre-Trained LLMs](/202607/30/2607.21291v1-adaptive-depth-sparse-framework-similarity-driven-resource-allocation-for-pre-trained-llms)  
   标签：评分：7.0/10、query:llm
   evidence：提出自适应深度稀疏框架（AdaDSF），通过层间稀疏化加速LLM推理，无需完全重训练
4. [WaveZip: Wavelet-Driven Space-Time Decoupling for Video Token Condensation](/202607/30/2607.23265v1-wavezip-wavelet-driven-space-time-decoupling-for-video-token-condensation)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：面向大视觉语言模型的视频令牌高效压缩
5. [PathSelect: Sequential Token Selection for Whole Slide Pathology](/202607/30/2607.23631v1-pathselect-sequential-token-selection-for-whole-slide-pathology)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：提出PathSelect，通过顺序token选择实现病理图像VLM的高效推理
6. [OmniDelta: Skill-Driven Budget Allocation for Token Compression in OmniLLMs](/202607/30/2607.25669v1-omnidelta-skill-driven-budget-allocation-for-token-compression-in-omnillms)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：多模态大模型令牌压缩加速推理
7. [UniGen-AR: Unifying Visual Generation with Auto-Regressive Modeling](/202607/30/2607.24157v1-unigen-ar-unifying-visual-generation-with-auto-regressive-modeling)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：通过MLLM与VAR解码器配对解决多模态生成推理延迟
8. [SepPrune:A Separator-based Pruning Framework for Efficient Multimodal Large Language Models](/202607/30/2607.25818v1-sepprunea-separator-based-pruning-framework-for-efficient-multimodal-large-language-models)  
   标签：评分：6.0/10、query:llm
   evidence：用于高效多模态大模型推理的视觉token剪枝方法


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
