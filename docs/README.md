<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-07
- 运行时间：2026-09-07 22:58:27 UTC
- 运行状态：成功
- 本次总论文数：12
- 精读区：6
- 速读区：6

### 今日简报（AI）
今日重点围绕长上下文LLM推理加速，聚焦投机解码与KV缓存优化；最值得关注《ReTrace》与《Strong Drafts》两篇9分工作，分别从拒绝轨迹条件化和压缩KV缓存提升解码效率。建议优先精读这两篇，再以CateKV、Tail-Replay等缓存/前缀方法作对比参考，深入理解系统瓶颈。
- 详情：[/202609/07/README](/202609/07/README)

### 精读区论文标签
1. [ReTrace: Rejected-Trajectory Conditioning for Speculative Decoding](/202609/07/2608.29748v1-retrace-rejected-trajectory-conditioning-for-speculative-decoding)  
   标签：评分：9.0/10、query:llm-sd
   evidence：投机解码的拒绝轨迹条件化，避免首个拒绝后丢弃草稿后缀导致的计算浪费
2. [Strong Drafts Need Compact Memories: Long-Context Speculative Decoding with Compressed KV Cache](/202609/07/2608.30252v1-strong-drafts-need-compact-memories-long-context-speculative-decoding-with-compressed-kv-cache)  
   标签：评分：9.0/10、query:llm
   evidence：结合压缩KV缓存与投机解码加速长上下文LLM推理，命中KV缓存优化和投机解码综合主题
3. [HeadWiseKV: Budgeted Per-Head Cache Residency for Hybrid Long-Context Language Models](/202609/07/2609.02029v1-headwisekv-budgeted-per-head-cache-residency-for-hybrid-long-context-language-models)  
   标签：评分：9.0/10、query:llm
   evidence：面向混合长上下文语言模型的KV缓存优化与按头预算分配
4. [Multi-Access Speculative Inference: Uplink or Downlink?](/202609/07/2608.29618v1-multi-access-speculative-inference-uplink-or-downlink)  
   标签：评分：8.0/10、query:llm
   evidence：基于SPIN的多接入投机推理，面向边缘大模型加速
5. [Verification-Aware Training for Speculative Decoding](/202609/07/2608.30135v1-verification-aware-training-for-speculative-decoding)  
   标签：评分：8.0/10、query:llm-sd
   evidence：投机解码；验证感知训练；接受拒绝监督
6. [SFAD: Speculative Factuality-Aware Decoding](/202609/07/2609.00796v1-sfad-speculative-factuality-aware-decoding)  
   标签：评分：8.0/10、query:llm-sd
   evidence：提出面向大模型的投机解码框架SFAD，在保持效率的同时用偏好数据增强事实一致性;

### 速读区论文标签
1. [CateKV: On Sequential Consistency for Long-Context LLM Inference Acceleration](/202609/07/2608.30295v1-catekv-on-sequential-consistency-for-long-context-llm-inference-acceleration)  
   标签：评分：8.0/10、query:llm
   evidence：面向长上下文LLM推理加速的KV缓存优化方法
2. [Tail-Replay: Escaping the Curse of Linear Attention in Prefix Caching for Hybrid LLMs](/202609/07/2608.30310v1-tail-replay-escaping-the-curse-of-linear-attention-in-prefix-caching-for-hybrid-llms)  
   标签：评分：8.0/10、query:llm
   evidence：面向混合LLM的前缀缓存与KV管理优化，契合大模型高效推理主题
3. [Faster Than Flash: Exploiting Attention Sparsity for Efficient Long-Context Decoding](/202609/07/2609.00097v1-faster-than-flash-exploiting-attention-sparsity-for-efficient-long-context-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：利用注意力稀疏性和融合内核加速长上下文LLM解码，属于高效LLM推理主题
4. [Don't Drop Dropout: Optimizing Layer Sparsity for Efficient LLM Training and Inference](/202609/07/2609.05275v1-dont-drop-dropout-optimizing-layer-sparsity-for-efficient-llm-training-and-inference)  
   标签：评分：7.0/10、query:llm
   evidence：层dropout作为层稀疏性优化，改善LLM训练并支持零样本层剪枝的高效推理
5. [hLLM: Single Pass Decoding for Generative Reranking](/202609/07/2609.01807v1-hllm-single-pass-decoding-for-generative-reranking)  
   标签：评分：6.0/10、query:llm
   evidence：大模型解码加速；生成式重排序用O(1)前向替代自回归逐token解码
6. [SPD: Single Pass Decoding for Generative Reranking](/202609/07/2609.01807v2-spd-single-pass-decoding-for-generative-reranking)  
   标签：评分：6.0/10、query:llm
   evidence：面向生成式重排序的LLM高效解码，将自回归串行前向降为O(1)次，属于大模型推理加速方向


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
