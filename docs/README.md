<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-05
- 运行时间：2026-09-05 22:02:27 UTC
- 运行状态：成功
- 本次总论文数：12
- 精读区：8
- 速读区：4

### 今日简报（AI）
今日精读聚焦投机解码的前沿优化，涵盖多接入通信与拒绝轨迹修正两大方向，速读则关注多模态加速与注意力稀疏化。

最值得精读的是《Multi-Access Speculative Inference》与《ReTrace》，均获9.0高分，分别从上下行链路权衡与拒绝样本再利用角度提升推理效率。

下一步建议重点关注投机解码在事实准确性与长上下文场景中的实际收益，并结合注意力稀疏技术验证可落地性。
- 详情：[/202609/05/README](/202609/05/README)

### 精读区论文标签
1. [Multi-Access Speculative Inference: Uplink or Downlink?](/202609/05/2608.29618v1-multi-access-speculative-inference-uplink-or-downlink)  
   标签：评分：9.0/10、query:llm
   evidence：面向边缘网络的LLM投机推理，涉及小模型草稿与大模型验证，是LLM高效推理加速的核心主题。
2. [ReTrace: Rejected-Trajectory Conditioning for Speculative Decoding](/202609/05/2608.29748v1-retrace-rejected-trajectory-conditioning-for-speculative-decoding)  
   标签：评分：9.0/10、query:llm-sd
   evidence：核心投机解码方法，通过利用被拒绝后缀来加速大模型生成
3. [Verification-Aware Training for Speculative Decoding](/202609/05/2608.30135v1-verification-aware-training-for-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：提出面向投机解码的验证感知训练，显式模拟逐位置接受/拒绝验证模式以加速大语言模型推理
4. [Strong Drafts Need Compact Memories: Long-Context Speculative Decoding with Compressed KV Cache](/202609/05/2608.30252v1-strong-drafts-need-compact-memories-long-context-speculative-decoding-with-compressed-kv-cache)  
   标签：评分：9.0/10、query:llm
   evidence：长上下文投机解码结合压缩KV缓存，直接属于LLM高效推理技术
5. [CateKV: On Sequential Consistency for Long-Context LLM Inference Acceleration](/202609/05/2608.30295v1-catekv-on-sequential-consistency-for-long-context-llm-inference-acceleration)  
   标签：评分：9.0/10、query:llm
   evidence：利用注意力头序列一致性设计混合KV缓存以加速长上下文LLM推理，属于LLM KV缓存优化核心方向
6. [Tail-Replay: Escaping the Curse of Linear Attention in Prefix Caching for Hybrid LLMs](/202609/05/2608.30310v1-tail-replay-escaping-the-curse-of-linear-attention-in-prefix-caching-for-hybrid-llms)  
   标签：评分：9.0/10、query:llm
   evidence：面向混合大语言模型的前缀缓存机制，支持无约束token级前缀重用，属于KV缓存与高效推理优化
7. [SFAD: Speculative Factuality-Aware Decoding](/202609/05/2609.00796v2-sfad-speculative-factuality-aware-decoding)  
   标签：评分：9.0/10、query:vlm-spec
   evidence：提出结合事实性感知验证策略的投机解码框架，直接对应投机解码验证策略研究。
8. [HeadWiseKV: Budgeted Per-Head Cache Residency for Hybrid Long-Context Language Models](/202609/05/2609.02029v1-headwisekv-budgeted-per-head-cache-residency-for-hybrid-long-context-language-models)  
   标签：评分：9.0/10、query:llm
   evidence：对混合长上下文LLM的KV缓存进行按头驻留预算压缩，直接命中大模型高效推理与KV缓存优化主题

### 速读区论文标签
1. [Accelerating Unified Multimodal Models with Core-Expansion Routing and Unified Computation Scheduling](/202609/05/2608.29291v3-accelerating-unified-multimodal-models-with-core-expansion-routing-and-unified-computation-scheduling)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：通过核心-扩展路由与统一计算调度加速统一多模态模型推理，对VLM推理加速有直接参考价值
2. [Faster Than Flash: Exploiting Attention Sparsity for Efficient Long-Context Decoding](/202609/05/2609.00097v1-faster-than-flash-exploiting-attention-sparsity-for-efficient-long-context-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：基于注意力稀疏性的长上下文大模型高效解码
3. [SFAD: Speculative Factuality-Aware Decoding](/202609/05/2609.00796v1-sfad-speculative-factuality-aware-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：面向高效且可信LLM生成的投机解码框架
4. [CoFiE: Coarse-to-Fine Evidence Selection for Efficient Streaming Video Understanding](/202609/05/2609.03675v1-cofie-coarse-to-fine-evidence-selection-for-efficient-streaming-video-understanding)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：通过编码前粗粒度帧过滤与预填充阶段细粒度令牌精炼降低流式视频VLM的端到端推理延迟


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
