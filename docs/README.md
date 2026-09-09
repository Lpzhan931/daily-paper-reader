<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-09
- 运行时间：2026-09-09 21:23:03 UTC
- 运行状态：成功
- 本次总论文数：13
- 精读区：6
- 速读区：7

### 今日简报（AI）
今日精读6篇、速读7篇，重点聚焦长上下文KV缓存管理与多模态高效推理。最值得看的是《HeadWiseKV》与《CONDUIT》，分别提出按头预算缓存分配和残差流恢复框架，显著提升混合长上下文及视觉语言模型的缓存效率。若想快速跟进，可从KV缓存压缩与边缘-云协同推理（如AceSpec）入手。
- 详情：[/202609/09/README](/202609/09/README)

### 精读区论文标签
1. [HeadWiseKV: Budgeted Per-Head Cache Residency for Hybrid Long-Context Language Models](/202609/09/2609.02029v1-headwisekv-budgeted-per-head-cache-residency-for-hybrid-long-context-language-models)  
   标签：评分：9.0/10、query:llm
   evidence：面向混合长上下文语言模型，在预算下按KV头分配历史窗口以压缩全局缓存，直接对应KV缓存优化与LLM高效推理。
2. [CONDUIT: A Unified Residual-Stream Restoration Framework for KV Cache Reuse in Vision-Language Models](/202609/09/2609.05821v1-conduit-a-unified-residual-stream-restoration-framework-for-kv-cache-reuse-in-vision-language-models)  
   标签：评分：9.0/10、query:vlm-spec
   evidence：面向VLM的KV缓存复用，避免重复编码视觉前缀，直接加速VLM推理
3. [DFlow: Enabling Verifier Information Flow in Block Diffusion Speculative Decoding](/202609/09/2609.06498v1-dflow-enabling-verifier-information-flow-in-block-diffusion-speculative-decoding)  
   标签：评分：9.0/10、query:llm
   evidence：面向大语言模型的高效投机解码方法，契合综合高效推理主题
4. [ECOKV: Geometry-Aware KV Cache Eviction via Complementary Diversity Metrics](/202609/09/2609.06663v1-ecokv-geometry-aware-kv-cache-eviction-via-complementary-diversity-metrics)  
   标签：评分：9.0/10、query:vlm-spec
   evidence：面向多模态大模型的几何感知KV缓存淘汰方法，降低显存与计算开销以加速VLM推理
5. [Online Draft Co-Training for Speculative Decoding in Large-Scale, Long-Context RL Post-Training](/202609/09/2609.07108v1-online-draft-co-training-for-speculative-decoding-in-large-scale-long-context-rl-post-training)  
   标签：评分：9.0/10、query:llm
   evidence：直接面向投机解码加速大模型推理，属于大语言模型高效推理组合主题。
6. [SFAD: Speculative Factuality-Aware Decoding](/202609/09/2609.00796v1-sfad-speculative-factuality-aware-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：面向大语言模型的投机解码框架，在改进事实性的同时避免推理降速，属于高效推理相关检索主题

### 速读区论文标签
1. [AceSpec: An Asymmetric Edge-Cloud Collaborative Framework for Communication-Efficient LLM Inference](/202609/09/2609.02514v1-acespec-an-asymmetric-edge-cloud-collaborative-framework-for-communication-efficient-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：面向LLM边缘-云协作的投机解码与云端验证，契合大模型高效推理主题
2. [Don't Drop Dropout: Optimizing Layer Sparsity for Efficient LLM Training and Inference](/202609/09/2609.05275v1-dont-drop-dropout-optimizing-layer-sparsity-for-efficient-llm-training-and-inference)  
   标签：评分：8.0/10、query:llm
   evidence：研究层稀疏化（随机深度）以提升大模型训练与推理效率，并通过零样本剪枝鲁棒性对应高效推理中的剪枝主题。
3. [STAR-Pro: Stage-Wise Token Adaptive Reduction with Progressive Refinement for Efficient Large Vision-Language Models](/202609/09/2609.05916v1-star-pro-stage-wise-token-adaptive-reduction-with-progressive-refinement-for-efficient-large-vision-language-models)  
   标签：评分：8.0/10、query:vlm-spec
   evidence：通过分阶段词元自适应缩减与渐进精炼降低大型视觉-语言模型的推理计算开销。
4. [OUTLETS: Output-Length Prediction from Speculative Decoding Backbones](/202609/09/2609.01068v1-outlets-output-length-prediction-from-speculative-decoding-backbones)  
   标签：评分：7.0/10、query:llm
   evidence：利用投机解码骨干中的草稿表示预测输出长度以服务LLM调度与资源供给，契合大模型高效推理主题
5. [Jina-OCR-v1: Efficient Document Parsing with Speculative Decoding and Dense Verifiable Rewards](/202609/09/2609.03181v1-jina-ocr-v1-efficient-document-parsing-with-speculative-decoding-and-dense-verifiable-rewards)  
   标签：评分：7.0/10、query:vlm-spec
   evidence：文档解析模型结合压缩视觉编码器、MoE解码器与FastMTP投机解码头，展示了面向视觉解码的投机加速
6. [hLLM: Single Pass Decoding for Generative Reranking](/202609/09/2609.01807v1-hllm-single-pass-decoding-for-generative-reranking)  
   标签：评分：6.0/10、query:llm
   evidence：面向大模型重排序的高效非自回归解码
7. [SPD: Single Pass Decoding for Generative Reranking](/202609/09/2609.01807v2-spd-single-pass-decoding-for-generative-reranking)  
   标签：评分：6.0/10、query:llm
   evidence：面向LLM的高效解码技术，与高效推理主题相关


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
