<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-04-20
- 运行时间：2026-04-20 20:33:27 UTC
- 运行状态：成功
- 本次总论文数：12
- 精读区：6
- 速读区：6

### 今日简报（AI）
今日聚焦 LLM 推理性能巅峰，深度解析 KV 缓存重构与 TPU 高效算子优化。
重点关注 KV Packet 实现的免重算上下文独立缓存，以及 Ragged Paged Attention 在 TPU 上的极致推理表现。
建议开发者优先研读 KV 缓存优化方案，并警惕 FP16 在自回归推理中的数值偏差风险。
- 详情：[/202604/20/README](/202604/20/README)

### 精读区论文标签
1. [KV Packet: Recomputation-Free Context-Independent KV Caching for LLMs](/202604/20/2604.13226v2-kv-packet-recomputation-free-context-independent-kv-caching-for-llms)  
   标签：评分：10.0/10、query:llm
   evidence：无需重计算的KV缓存复用框架
2. [Ragged Paged Attention: A High-Performance and Flexible LLM Inference Kernel for TPU](/202604/20/2604.15464v1-ragged-paged-attention-a-high-performance-and-flexible-llm-inference-kernel-for-tpu)  
   标签：评分：10.0/10、query:llm
   evidence：用于TPU推理的高性能Paged Attention内核
3. [Faster LLM Inference via Sequential Monte Carlo](/202604/20/2604.15672v1-faster-llm-inference-via-sequential-monte-carlo)  
   标签：评分：10.0/10、query:llm-sd
   evidence：用于近似投机解码的顺序蒙特卡洛方法
4. [Accuracy Is Speed: Towards Long-Context-Aware Routing for Distributed LLM Serving](/202604/20/2604.15732v1-accuracy-is-speed-towards-long-context-aware-routing-for-distributed-llm-serving)  
   标签：评分：9.0/10、query:llm
   evidence：优化分布式LLM服务的吞吐量和延迟
5. [Optimizing Korean-Centric LLMs via Token Pruning](/202604/20/2604.16235v1-optimizing-korean-centric-llms-via-token-pruning)  
   标签：评分：9.0/10、query:llm
   evidence：通过针对特定语言的令牌剪枝优化大语言模型
6. [Fleet: Hierarchical Task-based Abstraction for Megakernels on Multi-Die GPUs](/202604/20/2604.15379v1-fleet-hierarchical-task-based-abstraction-for-megakernels-on-multi-die-gpus)  
   标签：评分：8.0/10、query:llm
   evidence：优化内存受限的LLM推理中的缓存利用率

### 速读区论文标签
1. [Dispatch-Aware Ragged Attention for Pruned Vision Transformers](/202604/20/2604.15408v1-dispatch-aware-ragged-attention-for-pruned-vision-transformers)  
   标签：评分：8.0/10、query:llm
   evidence：针对剪枝Transformer的注意力内核优化以降低延迟
2. [SAGE: Selective Attention-Guided Extraction for Token-Efficient](/202604/20/2604.15583v1-sage-selective-attention-guided-extraction-for-token-efficient)  
   标签：评分：8.0/10、query:llm
   evidence：高效的Token上下文削减框架
3. [The Illusion of Equivalence: Systematic FP16 Divergence in KV-Cached Autoregressive Inference](/202604/20/2604.15409v1-the-illusion-of-equivalence-systematic-fp16-divergence-in-kv-cached-autoregressive-inference)  
   标签：评分：7.0/10、query:llm
   evidence：KV缓存自回归推理中的数值差异分析
4. [AdaVFM: Adaptive Vision Foundation Models for Edge Intelligence via LLM-Guided Execution](/202604/20/2604.15622v1-adavfm-adaptive-vision-foundation-models-for-edge-intelligence-via-llm-guided-execution)  
   标签：评分：7.0/10、query:llm
   evidence：基础模型高效设备端推理的自适应框架
5. [DepCap: Adaptive Block-Wise Parallel Decoding for Efficient Diffusion LM Inference](/202604/20/2604.15750v1-depcap-adaptive-block-wise-parallel-decoding-for-efficient-diffusion-lm-inference)  
   标签：评分：7.0/10、query:llm
   evidence：扩散语言模型的高效并行解码推理
6. [Efficient Video Diffusion Models: Advancements and Challenges](/202604/20/2604.15911v1-efficient-video-diffusion-models-advancements-and-challenges)  
   标签：评分：7.0/10、query:llm
   evidence：关于高效推理的综述，涵盖高效注意力机制和模型压缩


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
