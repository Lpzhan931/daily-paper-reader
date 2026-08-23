<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-23
- 运行时间：2026-08-23 20:20:06 UTC
- 运行状态：成功
- 本次总论文数：10
- 精读区：6
- 速读区：4

### 今日简报（AI）
今日精读6篇、速读4篇，核心聚焦边缘端MoE自推测解码与长上下文稀疏注意力优化。最值得关注《S2-MoE》与《Learning how to Forget》，前者提升边缘设备解码效率，后者用遗忘机制改进稀疏注意力。建议下一步深入MoNe模块化记忆和FlashQuant异常感知推理，兼顾效率与内存。
- 详情：[/202608/23/README](/202608/23/README)

### 精读区论文标签
1. [S2-MoE: Enabling Efficient Self-Speculative Decoding for Mixture-of-Experts on Edge Devices](/202608/23/2608.15018v2-s2-moe-enabling-efficient-self-speculative-decoding-for-mixture-of-experts-on-edge-devices)  
   标签：评分：9.0/10、query:llm-sd
   evidence：面向边缘设备MoE大语言模型的自投机解码与验证效率优化
2. [Learning how to Forget: Fine-tuning for Long-Context Sparse Attention](/202608/23/2608.19920v1-learning-how-to-forget-fine-tuning-for-long-context-sparse-attention)  
   标签：评分：9.0/10、query:llm
   evidence：通过稀疏注意力进行KV缓存选择与压缩，并支持任意KV缓存策略的微调
3. [S2-MoE: Enabling Efficient Self-Speculative Decoding for Mixture-of-Experts on Edge Devices](/202608/23/2608.15018v1-s2-moe-enabling-efficient-self-speculative-decoding-for-mixture-of-experts-on-edge-devices)  
   标签：评分：8.0/10、query:llm
   evidence：针对MoE大语言模型的推理高效自投机解码，减少验证开销并提高专家复用，属于LLM投机解码加速
4. [Dynamic Multi-Byte Prediction With Hierarchical Language Models](/202608/23/2608.15454v1-dynamic-multi-byte-prediction-with-hierarchical-language-models)  
   标签：评分：8.0/10、query:llm
   evidence：通过并行多字节预测加速层次语言模型推理，与多令牌投机预测同属并行生成加速技术
5. [DeltaLog: Deferred Materialization of Recurrent States for Linear Attention Decoding](/202608/23/2608.15533v1-deltalog-deferred-materialization-of-recurrent-states-for-linear-attention-decoding)  
   标签：评分：8.0/10、query:llm
   evidence：线性注意力模型的高效解码，减少循环状态物化开销
6. [FluxBin: Flexible LUT-based Ultra-low-bit LLM Inference by Algorithm-Kernel Synergy](/202608/23/2608.15602v1-fluxbin-flexible-lut-based-ultra-low-bit-llm-inference-by-algorithm-kernel-synergy)  
   标签：评分：8.0/10、query:llm
   evidence：通过算法-内核协同设计实现超低位宽大语言模型推理加速

### 速读区论文标签
1. [MoNe: Modular Neural Memory for Efficient Long Context Inference](/202608/23/2608.17616v1-mone-modular-neural-memory-for-efficient-long-context-inference)  
   标签：评分：8.0/10、query:llm
   evidence：模块化神经记忆支持长上下文推理，使推理成本与上下文长度解耦
2. [FlashAttention for Scalable Vector Architectures](/202608/23/2608.18656v1-flashattention-for-scalable-vector-architectures)  
   标签：评分：8.0/10、query:llm
   evidence：面向向量架构的FlashAttention高效注意力机制，契合大模型高效推理主题
3. [FlashQuant: Sparse-Dense Fusion for Memory-Efficient Outlier-Aware LLM Inference](/202608/23/2608.15531v1-flashquant-sparse-dense-fusion-for-memory-efficient-outlier-aware-llm-inference)  
   标签：评分：7.0/10、query:llm
   evidence：面向LLM推理加速的内存高效离群值感知量化方法
4. [RecurrentGPT: Expressive Depth through Recurrent Modulation in Transformers](/202608/23/2608.15062v2-recurrentgpt-expressive-depth-through-recurrent-modulation-in-transformers)  
   标签：评分：6.0/10、query:llm
   evidence：提出共享核心的循环深度Transformer以减少内存占用并保持表达力，与大模型高效推理相关


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
