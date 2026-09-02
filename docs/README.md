<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-02
- 运行时间：2026-09-02 22:53:19 UTC
- 运行状态：成功
- 本次总论文数：17
- 精读区：7
- 速读区：10

### 今日简报（AI）
今日聚焦大模型推理加速，精读17篇中7篇，重点关注投机解码在视觉语言模型与Agent批量推理中的无损提速方案；最值得关注的方向是将草稿生成融入单次前向传播，及针对Agent批处理设计的专用投机解码框架，均在各自场景实现显著收益。若想快速上手，可从视觉Token剪枝与多模态路由调度入手，先用成本较低的裁剪类技巧观察效果，再逐步尝试架构级优化。
- 详情：[/202609/02/README](/202609/02/README)

### 精读区论文标签
1. [Vision Is Not Overhead: One-Pass Block Drafting for Lossless Speculative Decoding in Vision-Language Models](/202609/02/2609.00355v1-vision-is-not-overhead-one-pass-block-drafting-for-lossless-speculative-decoding-in-vision-language-models)  
   标签：评分：10.0/10、query:vlm-spec
   evidence：面向视觉语言模型的无损投机解码，使用单遍块草稿
2. [AgentSpec: Speculative Decoding for Batch Inference of LLM Agents](/202609/02/2608.24004v1-agentspec-speculative-decoding-for-batch-inference-of-llm-agents)  
   标签：评分：9.0/10、query:llm
   evidence：面向LLM智能体批量推理的投机解码，提升延迟和Token预算利用效率
3. [Trajectory-Level Speculative Decoding for Diffusion Language Models](/202609/02/2608.27514v1-trajectory-level-speculative-decoding-for-diffusion-language-models)  
   标签：评分：9.0/10、query:llm
   evidence：面向扩散语言模型的轨迹级投机解码以提升吞吐
4. [ReTrace: Rejected-Trajectory Conditioning for Speculative Decoding](/202609/02/2608.29748v1-retrace-rejected-trajectory-conditioning-for-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：利用被拒绝的草稿轨迹改进投机解码中前缀验证拒绝后的解码推进
5. [Verification-Aware Training for Speculative Decoding](/202609/02/2608.30135v1-verification-aware-training-for-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向大语言模型投机解码的验证感知训练，从训练侧改进草稿验证
6. [CateKV: On Sequential Consistency for Long-Context LLM Inference Acceleration](/202609/02/2608.30295v1-catekv-on-sequential-consistency-for-long-context-llm-inference-acceleration)  
   标签：评分：9.0/10、query:llm
   evidence：利用注意力头序贯一致性缩减长上下文大语言模型推理的KV缓存与计算
7. [SinkPruner: Sink-Free Visual Token Pruning for Multimodal Large Language Models](/202609/02/2609.01004v1-sinkpruner-sink-free-visual-token-pruning-for-multimodal-large-language-models)  
   标签：评分：9.0/10、query:vlm-spec
   evidence：无训练视觉令牌剪枝，降低MLLM推理开销

### 速读区论文标签
1. [Multi-Image Visual Token Pruning in Large Visual Language Models](/202609/02/2608.26806v2-multi-image-visual-token-pruning-in-large-visual-language-models)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：面向大视觉语言模型多图像高开销问题，提出无需训练的自适应视觉token剪枝以加速推理
2. [Accelerating Unified Multimodal Models with Core-Expansion Routing and Unified Computation Scheduling](/202609/02/2608.29291v2-accelerating-unified-multimodal-models-with-core-expansion-routing-and-unified-computation-scheduling)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：削减统一多模态模型推理中令牌、层与时间步的冗余计算
3. [Multi-Access Speculative Inference: Uplink or Downlink?](/202609/02/2608.29618v1-multi-access-speculative-inference-uplink-or-downlink)  
   标签：评分：8.0/10、query:llm
   evidence：将投机解码扩展到边缘多设备场景，端侧小模型草拟并由服务端大模型验证以加速生成
4. [Strong Drafts Need Compact Memories: Long-Context Speculative Decoding with Compressed KV Cache](/202609/02/2608.30252v1-strong-drafts-need-compact-memories-long-context-speculative-decoding-with-compressed-kv-cache)  
   标签：评分：8.0/10、query:llm
   evidence：面向长上下文大语言模型的投机解码与压缩KV缓存优化
5. [Faster Than Flash: Exploiting Attention Sparsity for Efficient Long-Context Decoding](/202609/02/2609.00097v1-faster-than-flash-exploiting-attention-sparsity-for-efficient-long-context-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：FFD 面向长上下文LLM解码，通过注意力稀疏性进行硬件算法协同优化，属于高效LLM推理相关论文。
6. [SFAD: Speculative Factuality-Aware Decoding](/202609/02/2609.00796v1-sfad-speculative-factuality-aware-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：面向大语言模型的投机解码框架，兼顾事实一致性与高效推理
7. [S$^2$Prune: Spatially Structured Visual Token Pruning for Multimodal Large Language Models](/202609/02/2609.01224v1-s2prune-spatially-structured-visual-token-pruning-for-multimodal-large-language-models)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：面向多模态大语言模型推理的无训练空间结构化视觉Token剪枝
8. [A Glance Is All You Need: Single-Pass Fine-Grained Image Captioning with SimLoss](/202609/02/2609.00591v1-a-glance-is-all-you-need-single-pass-fine-grained-image-captioning-with-simloss)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：用单遍描述替代多阶段验证改写，降低视觉语言模型推理延迟
9. [Dependency-Aware Revocable Decoding for Efficient Diffusion Large Language Model Inference](/202609/02/2608.26574v1-dependency-aware-revocable-decoding-for-efficient-diffusion-large-language-model-inference)  
   标签：评分：6.0/10、query:llm
   evidence：面向高效扩散大语言模型推理的依赖感知可撤销解码与验证
10. [Compressing AI Traffic: Standardized Neural Network Coding of Visual-Token Representations in Split Vision-Language Inference](/202609/02/2609.01200v1-compressing-ai-traffic-standardized-neural-network-coding-of-visual-token-representations-in-split-vision-language-inference)  
   标签：评分：6.0/10、query:vlm-spec
   evidence：压缩拆分式视觉语言推理中视觉令牌表示，降低跨端通信开销以加速推理


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
