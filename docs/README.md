<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-07
- 运行时间：2026-08-07 20:20:22 UTC
- 运行状态：成功
- 本次总论文数：12
- 精读区：6
- 速读区：6

### 今日简报（AI）
今日推荐12篇论文，含6篇精读与6篇速读，聚焦推测解码与视觉token优化。最值得关注两篇9.0分精读：无需训练的自我推测解码，以及块并行推测解码的局部不确定性修复。建议优先精读这两篇，速读可留意视觉token剪枝与实时VLA推理。
- 详情：[/202608/07/README](/202608/07/README)

### 精读区论文标签
1. [A Sparse Glimpse of the Whole: Train-Free Self-Speculative Decoding](/202608/07/2607.27735v1-a-sparse-glimpse-of-the-whole-train-free-self-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：免训练自投机解码，结合稀疏可召回KV缓存加速大语言模型推理
2. [CURE: Local Uncertainty Repair for Block-Parallel Speculative Decoding](/202608/07/2608.00531v1-cure-local-uncertainty-repair-for-block-parallel-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向LLM快速推理的投机解码，结合不确定性驱动的修复与验证开销控制
3. [Bole: Efficient Tree Speculation for Hybrid-Attention Language Models](/202608/07/2608.01651v1-bole-efficient-tree-speculation-for-hybrid-attention-language-models)  
   标签：评分：9.0/10、query:llm-sd
   evidence：面向混合注意力语言模型的树投机解码与内核-运行时协同设计
4. [DBLAST: Dependent Block Drafting for Stochastic Speculative Decoding](/202608/07/2608.05448v1-dblast-dependent-block-drafting-for-stochastic-speculative-decoding)  
   标签：评分：9.0/10、query:llm-sd
   evidence：面向随机非贪心采样的依赖块草稿投机解码，提升大模型推理加速
5. [AOSpec: Action and Observation Co-Speculation for Low-Latency Agent Serving](/202608/07/2608.00881v1-aospec-action-and-observation-co-speculation-for-low-latency-agent-serving)  
   标签：评分：8.0/10、query:llm
   evidence：面向LLM智能体的投机解码方法，降低服务延迟
6. [From Chains to Trees: Parent-Conditioned Drafting for Semi-Autoregressive Speculative Decoding](/202608/07/2608.02123v1-from-chains-to-trees-parent-conditioned-drafting-for-semi-autoregressive-speculative-decoding)  
   标签：评分：8.0/10、query:llm-sd
   evidence：改进LLM投机解码中草稿的生成与验证存活率，属于半自回归投机解码核心方法

### 速读区论文标签
1. [DiffPrune: differentiable information throttling for token pruning in vision-language models](/202608/07/2608.01985v1-diffprune-differentiable-information-throttling-for-token-pruning-in-vision-language-models)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：可微信息节流用于VLM视觉token剪枝，降低计算成本
2. [RUTA: Principled Visual Token Allocation via Rate-Utility Optimization](/202608/07/2608.04132v1-ruta-principled-visual-token-allocation-via-rate-utility-optimization)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：面向VLM推理加速的视觉token分配
3. [Deltoris: Enabling Real-time VLA Inference in Embodied AI via Bit-level Sparsity and Speculative Inference](/202608/07/2608.04428v1-deltoris-enabling-real-time-vla-inference-in-embodied-ai-via-bit-level-sparsity-and-speculative-inference)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：明确使用投机推理与比特级稀疏性加速VLA推理，符合视觉语言模型推理加速要求
4. [DIVE: Dynamic Iterative Visual Evidence Construction for Efficient Vision-Language Models](/202608/07/2608.04496v1-dive-dynamic-iterative-visual-evidence-construction-for-efficient-vision-language-models)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：通过动态视觉token剪枝加速视觉语言模型推理
5. [QEvict: Recoverable Quantized KV Eviction for Attention-Drift-Robust Long-Context Decoding](/202608/07/2608.05326v1-qevict-recoverable-quantized-kv-eviction-for-attention-drift-robust-long-context-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：直接针对LLM推理的KV缓存内存优化，提出可恢复的驱逐策略
6. [ParVL: Parallel Scaling and Expandable Compute Allocation for Multimodal LLMs](/202608/07/2608.04010v1-parvl-parallel-scaling-and-expandable-compute-allocation-for-multimodal-llms)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：面向多模态大模型的并行扩展与计算分配，降低推理开销


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
