<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-09
- 运行时间：2026-08-09 19:37:37 UTC
- 运行状态：成功
- 本次总论文数：7
- 精读区：6
- 速读区：1

### 今日简报（AI）
今日精读聚焦混合注意力模型的高效树投机与长上下文量化KV驱逐，速读关注三元LLM的查找表加速，共7篇论文。

最值得看的两大方向：Bole通过树投机显著提升混合注意力模型的解码效率；QEvict以可恢复量化KV驱逐应对注意力漂移，兼顾长上下文性能与显存占用。

下一步建议普通读者优先关注KV缓存压缩技术，这对实际部署长上下文LLM的显存与速度优化最直接。
- 详情：[/202608/09/README](/202608/09/README)

### 精读区论文标签
1. [Bole: Efficient Tree Speculation for Hybrid-Attention Language Models](/202608/09/2608.01651v1-bole-efficient-tree-speculation-for-hybrid-attention-language-models)  
   标签：评分：9.0/10、query:llm
   evidence：面向混合注意力大语言模型的树结构投机解码，直接加速LLM推理
2. [QEvict: Recoverable Quantized KV Eviction for Attention-Drift-Robust Long-Context Decoding](/202608/09/2608.05326v1-qevict-recoverable-quantized-kv-eviction-for-attention-drift-robust-long-context-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向注意力漂移的长上下文解码的量化KV驱逐方法，直接涉及LLM推理的KV缓存优化
3. [CURE: Local Uncertainty Repair for Block-Parallel Speculative Decoding](/202608/09/2608.00531v1-cure-local-uncertainty-repair-for-block-parallel-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：面向并行块投机解码的局部不确定性修复，降低拒绝率并提升加速，直接推进大模型推理加速。
4. [AOSpec: Action and Observation Co-Speculation for Low-Latency Agent Serving](/202608/09/2608.00881v1-aospec-action-and-observation-co-speculation-for-low-latency-agent-serving)  
   标签：评分：8.0/10、query:llm
   evidence：面向低延迟LLM智能体服务的动作与观察协同投机
5. [From Chains to Trees: Parent-Conditioned Drafting for Semi-Autoregressive Speculative Decoding](/202608/09/2608.02123v1-from-chains-to-trees-parent-conditioned-drafting-for-semi-autoregressive-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：面向半自回归投机解码的父条件草稿树，提高草稿存活率并加速大模型推理。
6. [DBLAST: Dependent Block Drafting for Stochastic Speculative Decoding](/202608/09/2608.05448v1-dblast-dependent-block-drafting-for-stochastic-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：面向随机采样的投机解码，通过依赖块草稿缓解接受长度退化，推动大模型推理加速。

### 速读区论文标签
1. [Unified Lookup-Table Inference with Signed-Digit K/V Caches for Ternary LLMs](/202608/09/2608.03229v1-unified-lookup-table-inference-with-signed-digit-kv-caches-for-ternary-llms)  
   标签：评分：7.0/10、query:llm
   evidence：面向三值大语言模型的高效查找表推理与带符号数字键值缓存，降低注意力内存与计算开销


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
