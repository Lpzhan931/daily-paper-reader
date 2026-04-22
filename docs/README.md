<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-04-22
- 运行时间：2026-04-22 20:39:43 UTC
- 运行状态：成功
- 本次总论文数：18
- 精读区：8
- 速读区：10

### 今日简报（AI）
今日深度研读 18 篇 AI 论文，聚焦大模型长文本推理优化与 KV Cache 压缩技术。
满分论文 SAW-INT4 与 DASH-KV 分别通过系统感知量化和非对称哈希，实现了推理性能的跨越式提升。
建议优先关注 KV Cache 优化方案，这是当前解决长文本推理成本与速度瓶颈的核心路径。
- 详情：[/202604/22/README](/202604/22/README)

### 精读区论文标签
1. [SAW-INT4: System-Aware 4-Bit KV-Cache Quantization for Real-World LLM Serving](/202604/22/2604.19157v1-saw-int4-system-aware-4-bit-kv-cache-quantization-for-real-world-llm-serving)  
   标签：评分：10.0/10、query:llm
   evidence：系统感知的4比特KV缓存量化
2. [DASH-KV: Accelerating Long-Context LLM Inference via Asymmetric KV Cache Hashing](/202604/22/2604.19351v1-dash-kv-accelerating-long-context-llm-inference-via-asymmetric-kv-cache-hashing)  
   标签：评分：10.0/10、query:llm
   evidence：通过KV缓存哈希加速长文本推理
3. [GRASPrune: Global Gating for Budgeted Structured Pruning of Large Language Models](/202604/22/2604.19398v1-grasprune-global-gating-for-budgeted-structured-pruning-of-large-language-models)  
   标签：评分：10.0/10、query:llm
   evidence：FFN和KV头的结构化剪枝
4. [Topology-Aware Layer Pruning for Large Vision-Language Models](/202604/22/2604.16502v1-topology-aware-layer-pruning-for-large-vision-language-models)  
   标签：评分：9.0/10、query:llm
   evidence：大模型的层剪枝
5. [How Much Cache Does Reasoning Need? Depth-Cache Tradeoffs in KV-Compressed Transformers](/202604/22/2604.17935v1-how-much-cache-does-reasoning-need-depth-cache-tradeoffs-in-kv-compressed-transformers)  
   标签：评分：9.0/10、query:llm
   evidence：KV缓存压缩与权衡研究
6. [Unlocking the Edge deployment and ondevice acceleration of multi-LoRA enabled one-for-all foundational LLM](/202604/22/2604.18655v1-unlocking-the-edge-deployment-and-ondevice-acceleration-of-multi-lora-enabled-one-for-all-foundational-llm)  
   标签：评分：9.0/10、query:llm
   evidence：端侧加速与多流解码
7. [Efficient Mixture-of-Experts LLM Inference with Apple Silicon NPUs](/202604/22/2604.18788v1-efficient-mixture-of-experts-llm-inference-with-apple-silicon-npus)  
   标签：评分：9.0/10、query:llm
   evidence：在NPU上实现高效的MoE大模型推理
8. [SimDiff: Depth Pruning via Similarity and Difference](/202604/22/2604.19520v1-simdiff-depth-pruning-via-similarity-and-difference)  
   标签：评分：9.0/10、query:llm
   evidence：用于提升LLM效率的深度剪枝

### 速读区论文标签
1. [Event Tensor: A Unified Abstraction for Compiling Dynamic Megakernel](/202604/22/2604.13327v2-event-tensor-a-unified-abstraction-for-compiling-dynamic-megakernel)  
   标签：评分：8.0/10、query:llm
   evidence：为大模型推理吞吐量编译动态大算子
2. [Predicting LLM Compression Degradation from Spectral Statistics](/202604/22/2604.18085v1-predicting-llm-compression-degradation-from-spectral-statistics)  
   标签：评分：8.0/10、query:llm
   evidence：预测LLM压缩性能下降
3. [Copy-as-Decode: Grammar-Constrained Parallel Prefill for LLM Editing](/202604/22/2604.18170v1-copy-as-decode-grammar-constrained-parallel-prefill-for-llm-editing)  
   标签：评分：8.0/10、query:llm
   evidence：与投机解码共享内核的并行预填充机制
4. [$R^2$-dLLM: Accelerating Diffusion Large Language Models via Spatio-Temporal Redundancy Reduction](/202604/22/2604.18995v1-r2-dllm-accelerating-diffusion-large-language-models-via-spatio-temporal-redundancy-reduction)  
   标签：评分：8.0/10、query:llm
   evidence：加速扩散大语言模型解码
5. [LBLLM: Lightweight Binarization of Large Language Models via Three-Stage Distillation](/202604/22/2604.19167v1-lbllm-lightweight-binarization-of-large-language-models-via-three-stage-distillation)  
   标签：评分：8.0/10、query:llm
   evidence：用于LLM部署的轻量化二值化
6. [Learning to Seek Help: Dynamic Collaboration Between Small and Large Language Models](/202604/22/2604.17827v1-learning-to-seek-help-dynamic-collaboration-between-small-and-large-language-models)  
   标签：评分：7.0/10、query:llm
   evidence：大小模型动态协作以实现高效推理
7. [Linear-Time and Constant-Memory Text Embeddings Based on Recurrent Language Models](/202604/22/2604.18199v1-linear-time-and-constant-memory-text-embeddings-based-on-recurrent-language-models)  
   标签：评分：7.0/10、query:llm
   evidence：Transformer推理的高效替代方案
8. [Geometry-Guided 3D Visual Token Pruning for Video-Language Models](/202604/22/2604.18260v1-geometry-guided-3d-visual-token-pruning-for-video-language-models)  
   标签：评分：7.0/10、query:llm
   evidence：用于高效推理的视觉标记剪枝
9. [BARD: Bridging AutoRegressive and Diffusion Vision-Language Models Via Highly Efficient Progressive Block Merging and Stage-Wise Distillation](/202604/22/2604.16514v2-bard-bridging-autoregressive-and-diffusion-vision-language-models-via-highly-efficient-progressive-block-merging-and-stage-wise-distillation)  
   标签：评分：6.0/10、query:llm
   evidence：视觉语言模型的并行解码范式
10. [NIM4-ASR: Towards Efficient, Robust, and Customizable Real-Time LLM-Based ASR](/202604/22/2604.18105v1-nim4-asr-towards-efficient-robust-and-customizable-real-time-llm-based-asr)  
   标签：评分：6.0/10、query:llm
   evidence：高效的基于LLM的语音识别框架


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
