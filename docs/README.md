<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-06
- 运行时间：2026-09-06 21:48:05 UTC
- 运行状态：成功
- 本次总论文数：12
- 精读区：6
- 速读区：6

### 今日简报（AI）
今日12篇论文聚焦长上下文LLM推理加速，其中精读6篇、速读6篇。  
最值得关注的是推测解码与压缩KV缓存结合的两个9.0分工作（ReTrace、Strong Drafts），以及8.0分的注意力稀疏解码方案。  
普通读者可重点关注“压缩KV缓存+推测解码”这一组合方向，其在不牺牲质量前提下显著提升长上下文生成效率。
- 详情：[/202609/06/README](/202609/06/README)

### 精读区论文标签
1. [ReTrace: Rejected-Trajectory Conditioning for Speculative Decoding](/202609/06/2608.29748v1-retrace-rejected-trajectory-conditioning-for-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：投机解码中对拒绝轨迹的再利用，契合LLM高效推理主题
2. [Strong Drafts Need Compact Memories: Long-Context Speculative Decoding with Compressed KV Cache](/202609/06/2608.30252v1-strong-drafts-need-compact-memories-long-context-speculative-decoding-with-compressed-kv-cache)  
   标签：评分：9.0/10、query:llm
   evidence：面向长上下文LLM的投机解码结合压缩草稿侧KV缓存
3. [Tail-Replay: Escaping the Curse of Linear Attention in Prefix Caching for Hybrid LLMs](/202609/06/2608.30310v1-tail-replay-escaping-the-curse-of-linear-attention-in-prefix-caching-for-hybrid-llms)  
   标签：评分：9.0/10、query:llm
   evidence：面向混合架构大语言模型的前缀缓存难题，提出无约束令牌级前缀复用机制，属KV缓存优化核心主题。
4. [Multi-Access Speculative Inference: Uplink or Downlink?](/202609/06/2608.29618v1-multi-access-speculative-inference-uplink-or-downlink)  
   标签：评分：8.0/10、query:llm
   evidence：将SPIN投机解码扩展到多设备边缘网络，分析上行/下行纠正位置对通信开销的影响
5. [Verification-Aware Training for Speculative Decoding](/202609/06/2608.30135v1-verification-aware-training-for-speculative-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：通过验证感知的草稿模型训练改进大模型投机解码，直接推动LLM高效推理。
6. [From Saliency to Discriminability: Rank-Preserving Visual Token Pruning for VLM Rerankers](/202609/06/2609.00667v1-from-saliency-to-discriminability-rank-preserving-visual-token-pruning-for-vlm-rerankers)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：面向VLM重排器的保序训练无关视觉标记剪枝，降低推理开销

### 速读区论文标签
1. [CateKV: On Sequential Consistency for Long-Context LLM Inference Acceleration](/202609/06/2608.30295v1-catekv-on-sequential-consistency-for-long-context-llm-inference-acceleration)  
   标签：评分：8.0/10、query:llm
   evidence：面向LLM推理加速的KV缓存优化与显存开销降低
2. [Event-Driven Language Models with Sparse Neural Activity for Neuromorphic Hardware](/202609/06/2608.30439v1-event-driven-language-models-with-sparse-neural-activity-for-neuromorphic-hardware)  
   标签：评分：8.0/10、query:llm
   evidence：提出在量化线性注意力大模型中诱导稀疏激活以减少计算的方法，服务于大模型高效推理这一主题。
3. [Faster Than Flash: Exploiting Attention Sparsity for Efficient Long-Context Decoding](/202609/06/2609.00097v1-faster-than-flash-exploiting-attention-sparsity-for-efficient-long-context-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：利用注意力稀疏性的软硬协同设计加速长上下文解码
4. [HeadWiseKV: Budgeted Per-Head Cache Residency for Hybrid Long-Context Language Models](/202609/06/2609.02029v1-headwisekv-budgeted-per-head-cache-residency-for-hybrid-long-context-language-models)  
   标签：评分：8.0/10、query:llm
   evidence：面向混合长上下文语言模型的免训练逐头KV缓存预算压缩
5. [SFAD: Speculative Factuality-Aware Decoding](/202609/06/2609.00796v1-sfad-speculative-factuality-aware-decoding)  
   标签：评分：6.0/10、query:llm
   evidence：面向LLM的投机解码框架，在不损害推理效率的前提下提升上下文忠实度
6. [OUTLETS: Output-Length Prediction from Speculative Decoding Backbones](/202609/06/2609.01068v1-outlets-output-length-prediction-from-speculative-decoding-backbones)  
   标签：评分：6.0/10、query:llm
   evidence：利用投机解码骨架（如EAGLE-3）的潜表示预测输出长度，服务于LLM高效推理与资源调度。


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
