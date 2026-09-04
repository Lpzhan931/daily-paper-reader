<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-04
- 运行时间：2026-09-04 21:20:38 UTC
- 运行状态：成功
- 本次总论文数：11
- 精读区：6
- 速读区：5

### 今日简报（AI）
今日聚焦长上下文LLM加速：精读《Strong Drafts Need Compact Memories》与《CateKV》，直击KV缓存压缩与顺序一致性瓶颈。最值得关注：通过紧凑KV缓存与一致性控制，可将推测解码效率大幅提升，适合长文本生成场景。建议关注KV缓存压缩方向，后续可追踪其在实际部署中的鲁棒性。
- 详情：[/202609/04/README](/202609/04/README)

### 精读区论文标签
1. [Strong Drafts Need Compact Memories: Long-Context Speculative Decoding with Compressed KV Cache](/202609/04/2608.30252v1-strong-drafts-need-compact-memories-long-context-speculative-decoding-with-compressed-kv-cache)  
   标签：评分：9.0/10、query:llm
   evidence：结合投机解码与压缩KV缓存降低长上下文LLM解码时延，属大模型高效推理核心方向
2. [CateKV: On Sequential Consistency for Long-Context LLM Inference Acceleration](/202609/04/2608.30295v1-catekv-on-sequential-consistency-for-long-context-llm-inference-acceleration)  
   标签：评分：9.0/10、query:llm
   evidence：面向长上下文LLM推理的KV缓存优化与加速方法
3. [Faster Than Flash: Exploiting Attention Sparsity for Efficient Long-Context Decoding](/202609/04/2609.00097v1-faster-than-flash-exploiting-attention-sparsity-for-efficient-long-context-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：利用注意力稀疏性的软硬件协同设计加速长上下文解码，直接对应LLM高效推理
4. [HeadWiseKV: Budgeted Per-Head Cache Residency for Hybrid Long-Context Language Models](/202609/04/2609.02029v1-headwisekv-budgeted-per-head-cache-residency-for-hybrid-long-context-language-models)  
   标签：评分：9.0/10、query:llm
   evidence：面向混合长上下文语言模型的逐头KV缓存预算分配方法，训练-free压缩全局KV缓存
5. [Who Speaks for the Pruned? Visual Token Pruning as Coverage Optimization](/202609/04/2609.03158v1-who-speaks-for-the-pruned-visual-token-pruning-as-coverage-optimization)  
   标签：评分：9.0/10、query:vlm-spec
   evidence：面向视觉语言模型的免训练视觉token剪枝，直接降低推理成本
6. [ReTrace: Rejected-Trajectory Conditioning for Speculative Decoding](/202609/04/2608.29748v1-retrace-rejected-trajectory-conditioning-for-speculative-decoding)  
   标签：评分：8.0/10、query:llm-sd
   evidence：面向大语言模型的投机解码新方法，复用被拒绝的草稿后缀而非直接丢弃，契合投机解码验证主题

### 速读区论文标签
1. [SFAD: Speculative Factuality-Aware Decoding](/202609/04/2609.00796v1-sfad-speculative-factuality-aware-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：面向LLM的投机解码框架，在提升上下文忠实度时保持生成效率
2. [Multi-Access Speculative Inference: Uplink or Downlink?](/202609/04/2608.29618v1-multi-access-speculative-inference-uplink-or-downlink)  
   标签：评分：7.0/10、query:llm
   evidence：面向边缘多设备网络的协作投机推理，分析端侧小模型起草与服务器大模型验证中的上下行通信瓶颈
3. [hLLM: Single Pass Decoding for Generative Reranking](/202609/04/2609.01807v1-hllm-single-pass-decoding-for-generative-reranking)  
   标签：评分：7.0/10、query:llm
   evidence：面向生成式重排的单次前向解码方法，以O(1)次前向完成序数解码，提升LLM推理效率
4. [Trajectory-Level Speculative Decoding for Diffusion Language Models](/202609/04/2608.27514v1-trajectory-level-speculative-decoding-for-diffusion-language-models)  
   标签：评分：6.0/10、query:llm
   evidence：将投机解码推广到扩散语言模型，通过轨迹级草稿与块级验证提高推理吞吐
5. [SFAD: Speculative Factuality-Aware Decoding](/202609/04/2609.00796v2-sfad-speculative-factuality-aware-decoding)  
   标签：评分：6.0/10、query:llm
   evidence：用于大语言模型高效推理与事实性增强的投机解码框架


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
