<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-19
- 运行时间：2026-08-19 20:39:59 UTC
- 运行状态：成功
- 本次总论文数：17
- 精读区：6
- 速读区：11

### 今日简报（AI）
今日聚焦推测解码在边缘与云边协同场景的加速与资源优化；最值得看精读《MemSpec》与《SPADE》，分别解决边缘设备内存感知调度和分布式低成本推理问题；建议关注推测解码对端侧生成延迟的改善潜力。
- 详情：[/202608/19/README](/202608/19/README)

### 精读区论文标签
1. [MemSpec: Memory-Aware Runtime for Adaptive Draft Scheduling in Speculative Decoding on Edge Devices](/202608/19/2608.10362v1-memspec-memory-aware-runtime-for-adaptive-draft-scheduling-in-speculative-decoding-on-edge-devices)  
   标签：评分：9.0/10、query:llm
   evidence：面向边缘设备上LLM投机解码的自适应草稿调度，提升推理效率
2. [SPADE: Speculative Decoding for Precise and Low Cost Distributed Edge Cloud Inference](/202608/19/2608.13076v1-spade-speculative-decoding-for-precise-and-low-cost-distributed-edge-cloud-inference)  
   标签：评分：9.0/10、query:llm
   evidence：面向大语言模型的投机解码以加速推理
3. [From Positionwise Confidence to Prefix Scheduling: Verifier Skipping in Speculative Decoding](/202608/19/2608.14787v1-from-positionwise-confidence-to-prefix-scheduling-verifier-skipping-in-speculative-decoding)  
   标签：评分：9.0/10、query:llm-sd
   evidence：投机解码中的验证器跳过与有损验证策略
4. [SA-GEM: Scale-Adaptive and Geospatial Evidence-Modulated Token Pruning for Efficient Remote Sensing Large Vision-Language Models](/202608/19/2608.15075v1-sa-gem-scale-adaptive-and-geospatial-evidence-modulated-token-pruning-for-efficient-remote-sensing-large-vision-language-models)  
   标签：评分：9.0/10、query:vlm-spec
   evidence：面向遥感VLM高效推理的令牌剪枝框架，直接加速视觉语言模型。
5. [Algorithm-Architecture Co-Design for Efficient VLA Inference via Speculative Inference and Verification](/202608/19/2608.15636v1-algorithm-architecture-co-design-for-efficient-vla-inference-via-speculative-inference-and-verification)  
   标签：评分：9.0/10、query:vlm-spec
   evidence：面向VLA模型的投机推理与验证以加速推理
6. [Memory Tree Guided Key Frame Querying for Efficient 3D Question Answering](/202608/19/2608.18009v1-memory-tree-guided-key-frame-querying-for-efficient-3d-question-answering)  
   标签：评分：9.0/10、query:vlm-spec
   evidence：提出记忆树引导的关键帧选择，降低三维问答中VLM推理开销

### 速读区论文标签
1. [Trie Automata for Constrained Decoding over Large Finite Sets](/202608/19/2608.12574v1-trie-automata-for-constrained-decoding-over-large-finite-sets)  
   标签：评分：8.0/10、query:llm
   evidence：面向LLM推理的高效约束解码机制，降低每步有效令牌计算开销。
2. [Decoupled Contrastive Decoding via Expert-Aligned Drafting](/202608/19/2608.12913v1-decoupled-contrastive-decoding-via-expert-aligned-drafting)  
   标签：评分：8.0/10、query:llm-sd
   evidence：用投机解码加速LLM对比解码，研究草稿与验证的对齐
3. [Reduced Matrix Multiplication: Input-Adaptive Matrix-Product Reduction for LLM Inference](/202608/19/2608.13426v1-reduced-matrix-multiplication-input-adaptive-matrix-product-reduction-for-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：免训练的输入自适应矩阵乘缩减方法，加速LLM推理。
4. [DARTree: Speculative Diffusion Decoding with Autoregressive Draft Trees](/202608/19/2608.13524v1-dartree-speculative-diffusion-decoding-with-autoregressive-draft-trees)  
   标签：评分：8.0/10、query:llm
   evidence：提出了一种无需训练的投机解码方法，利用自回归草稿树改进并行验证和候选覆盖。
5. [S2-MoE: Enabling Efficient Self-Speculative Decoding for Mixture-of-Experts on Edge Devices](/202608/19/2608.15018v1-s2-moe-enabling-efficient-self-speculative-decoding-for-mixture-of-experts-on-edge-devices)  
   标签：评分：8.0/10、query:llm
   evidence：提出了面向混合专家边缘推理的自投机解码方法，提升验证效率并减少重复验证。
6. [EcoVLA: Energy-Efficient Device-Edge Co-Inference for Vision-Language-Action Models under Real-Time Constraints](/202608/19/2608.15502v1-ecovla-energy-efficient-device-edge-co-inference-for-vision-language-action-models-under-real-time-constraints)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：针对视觉-语言-动作模型在实时约束下的推理加速，采用设备-边缘协同推理方案。
7. [FlashQuant: Sparse-Dense Fusion for Memory-Efficient Outlier-Aware LLM Inference](/202608/19/2608.15531v1-flashquant-sparse-dense-fusion-for-memory-efficient-outlier-aware-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：融合稀疏与稠密计算的异常值感知量化，降低内存访问并加速LLM解码
8. [DeltaLog: Deferred Materialization of Recurrent States for Linear Attention Decoding](/202608/19/2608.15533v1-deltalog-deferred-materialization-of-recurrent-states-for-linear-attention-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：减少线性注意力解码中循环状态物化开销
9. [MoE-ViE: Mixture of Experts Vision Encoder for Efficient Image and Video Understanding](/202608/19/2608.17402v1-moe-vie-mixture-of-experts-vision-encoder-for-efficient-image-and-video-understanding)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：用于高效图像视频理解的MoE视觉编码器，降低VLM延迟
10. [Ripple-Pivot Search: Active Parallel Decoding for Diffusion Large Language Models](/202608/19/2608.11742v1-ripple-pivot-search-active-parallel-decoding-for-diffusion-large-language-models)  
   标签：评分：7.0/10、query:llm
   evidence：面向扩散LLM的并行解码调度方法，通过主动提交位置降低推理延迟。
11. [Beyond Tokens: A Survey on Decoding Methods for Large Language and Vision-Language Models](/202608/19/2608.14797v1-beyond-tokens-a-survey-on-decoding-methods-for-large-language-and-vision-language-models)  
   标签：评分：7.0/10、query:llm
   evidence：综述了解码方法，包括并行生成加速LLM和VLM推理


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
