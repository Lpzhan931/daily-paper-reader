<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-03
- 运行时间：2026-09-03 21:31:13 UTC
- 运行状态：成功
- 本次总论文数：14
- 精读区：7
- 速读区：7

### 今日简报（AI）
今日精读7篇、速读7篇共14篇论文，聚焦推测解码与长上下文加速；最值得关注的是《Multi-Access Speculative Inference》与《ReTrace》两项9分工作，分别从接入架构和拒绝轨迹修正提升解码效率；下一步可优先了解推测解码中的通信/轨迹设计，再结合你的场景看速读列表中的代理式与KV缓存方案。
- 详情：[/202609/03/README](/202609/03/README)

### 精读区论文标签
1. [Multi-Access Speculative Inference: Uplink or Downlink?](/202609/03/2608.29618v1-multi-access-speculative-inference-uplink-or-downlink)  
   标签：评分：9.0/10、query:llm
   evidence：端侧草稿加边缘大模型验证的投机推理，加速LLM词元生成
2. [ReTrace: Rejected-Trajectory Conditioning for Speculative Decoding](/202609/03/2608.29748v1-retrace-rejected-trajectory-conditioning-for-speculative-decoding)  
   标签：评分：9.0/10、query:llm-sd
   evidence：针对投机解码验证阶段，利用被拒绝的草稿轨迹进行条件化以减少计算浪费
3. [Verification-Aware Training for Speculative Decoding](/202609/03/2608.30135v1-verification-aware-training-for-speculative-decoding)  
   标签：评分：9.0/10、query:llm-sd
   evidence：提出验证感知训练方法，使草稿模型建模投机解码的接受/拒绝模式，加速大模型推理
4. [Strong Drafts Need Compact Memories: Long-Context Speculative Decoding with Compressed KV Cache](/202609/03/2608.30252v1-strong-drafts-need-compact-memories-long-context-speculative-decoding-with-compressed-kv-cache)  
   标签：评分：9.0/10、query:llm
   evidence：压缩草稿侧KV缓存增强投机解码，降低长上下文解码延迟
5. [Faster Than Flash: Exploiting Attention Sparsity for Efficient Long-Context Decoding](/202609/03/2609.00097v1-faster-than-flash-exploiting-attention-sparsity-for-efficient-long-context-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：针对长上下文LLM解码显存墙的注意力稀疏化与内核融合方案，属于高效推理技术。
6. [HeadWiseKV: Budgeted Per-Head Cache Residency for Hybrid Long-Context Language Models](/202609/03/2609.02029v1-headwisekv-budgeted-per-head-cache-residency-for-hybrid-long-context-language-models)  
   标签：评分：9.0/10、query:llm
   evidence：面向混合长上下文语言模型的按头KV缓存预算压缩
7. [AceSpec: An Asymmetric Edge-Cloud Collaborative Framework for Communication-Efficient LLM Inference](/202609/03/2609.02514v1-acespec-an-asymmetric-edge-cloud-collaborative-framework-for-communication-efficient-llm-inference)  
   标签：评分：9.0/10、query:llm
   evidence：面向LLM推理的端云协作投机解码框架，核心是草稿-验证与通信优化。

### 速读区论文标签
1. [AsymSpec: Context-Asymmetric Speculative Decoding for Agentic LLMs](/202609/03/2608.26004v1-asymspec-context-asymmetric-speculative-decoding-for-agentic-llms)  
   标签：评分：8.0/10、query:llm
   evidence：提出AsymSpec非对称投机解码框架，加速智能体LLM推理
2. [Trajectory-Level Speculative Decoding for Diffusion Language Models](/202609/03/2608.27514v1-trajectory-level-speculative-decoding-for-diffusion-language-models)  
   标签：评分：8.0/10、query:llm
   evidence：面向扩散语言模型的轨迹级投机解码，通过并行验证加速语言模型推理
3. [CateKV: On Sequential Consistency for Long-Context LLM Inference Acceleration](/202609/03/2608.30295v1-catekv-on-sequential-consistency-for-long-context-llm-inference-acceleration)  
   标签：评分：8.0/10、query:llm
   evidence：面向长上下文LLM的混合KV缓存压缩，契合大模型高效推理主题。
4. [SFAD: Speculative Factuality-Aware Decoding](/202609/03/2609.00796v1-sfad-speculative-factuality-aware-decoding)  
   标签：评分：7.0/10、query:llm
   evidence：提出的投机解码框架可在不导致推理降级的情况下提升大语言模型上下文忠实度
5. [OUTLETS: Output-Length Prediction from Speculative Decoding Backbones](/202609/03/2609.01068v1-outlets-output-length-prediction-from-speculative-decoding-backbones)  
   标签：评分：7.0/10、query:llm
   evidence：利用投机解码骨干进行生成长度预测，服务于大模型吞吐和资源调度优化
6. [RVSD: Retrieval Vision Sparse Decoding for Mitigating Visual Hallucinations in Large Vision-Language Models](/202609/03/2609.02731v1-rvsd-retrieval-vision-sparse-decoding-for-mitigating-visual-hallucinations-in-large-vision-language-models)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：大型视觉语言模型中基于词元稀疏化的稀疏解码降低计算开销
7. [Visual Information-Guided Parallel Decoding for Diffusion Multimodal Large Language Models](/202609/03/2608.26580v1-visual-information-guided-parallel-decoding-for-diffusion-multimodal-large-language-models)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：面向扩散多模态大模型的视觉引导并行解码，可从解码侧降低多模态生成延迟。


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
