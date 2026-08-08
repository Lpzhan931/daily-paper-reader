<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-08
- 运行时间：2026-08-08 20:22:53 UTC
- 运行状态：成功
- 本次总论文数：9
- 精读区：6
- 速读区：3

### 今日简报（AI）
今日精读聚焦投机解码优化，9篇论文中6篇精读，重点覆盖块并行与近似解码方案。  
最值得看的是两篇9分工作：《CURE》用局部不确定性修复提升块并行解码质量，《Approximate Speculative Decoding》探索近似加速路径。  
建议优先精读这两篇高分论文，再结合速读中的树形半自回归drafting方法，可系统把握投机解码的前沿改进思路。
- 详情：[/202608/08/README](/202608/08/README)

### 精读区论文标签
1. [CURE: Local Uncertainty Repair for Block-Parallel Speculative Decoding](/202608/08/2608.00531v1-cure-local-uncertainty-repair-for-block-parallel-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向块并行投机解码，在验证阶段定位高不确定性令牌并动态修复，降低拒绝率、提升加速比
2. [Approximate Speculative Decoding](/202608/08/2608.03447v1-approximate-speculative-decoding)  
   标签：评分：9.0/10、query:vlm-spec
   evidence：提出免训练的近似投机解码验证器，采用预算化最长前缀选择，即一种宽松验证策略
3. [QEvict: Recoverable Quantized KV Eviction for Attention-Drift-Robust Long-Context Decoding](/202608/08/2608.05326v1-qevict-recoverable-quantized-kv-eviction-for-attention-drift-robust-long-context-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向注意力漂移鲁棒的长上下文解码的可恢复量化KV驱逐，属于大语言模型KV缓存优化核心方向
4. [DBLAST: Dependent Block Drafting for Stochastic Speculative Decoding](/202608/08/2608.05448v1-dblast-dependent-block-drafting-for-stochastic-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向随机投机解码的依赖块草稿生成，核心方法用于大语言模型推理加速
5. [AOSpec: Action and Observation Co-Speculation for Low-Latency Agent Serving](/202608/08/2608.00881v1-aospec-action-and-observation-co-speculation-for-low-latency-agent-serving)  
   标签：评分：8.0/10、query:llm
   evidence：面向低延迟LLM智能体服务的无损动作与观察协同投机，直接涉及投机解码与推理加速
6. [Bole: Efficient Tree Speculation for Hybrid-Attention Language Models](/202608/08/2608.01651v1-bole-efficient-tree-speculation-for-hybrid-attention-language-models)  
   标签：评分：8.0/10、query:llm
   evidence：面向混合注意力LLM的树投机解码协同设计，优化验证延迟与内存开销

### 速读区论文标签
1. [Coverage-Driven Adaptive Keyframe Selection for Video Understanding](/202608/08/2608.00714v1-coverage-driven-adaptive-keyframe-selection-for-video-understanding)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：通过基于覆盖度和相关性的自适应关键帧选择，降低大型视觉语言模型的推理开销
2. [From Chains to Trees: Parent-Conditioned Drafting for Semi-Autoregressive Speculative Decoding](/202608/08/2608.02123v1-from-chains-to-trees-parent-conditioned-drafting-for-semi-autoregressive-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：面向LLM推理加速的投机解码方法，使用父条件草稿树
3. [Distill What the Student Can See: Fisher-Projected On-Policy Distillation for Vision-Language Models](/202608/08/2608.01263v1-distill-what-the-student-can-see-fisher-projected-on-policy-distillation-for-vision-language-models)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：VLM生成中的token级师生分布匹配，与投机解码草稿模型训练相关


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
