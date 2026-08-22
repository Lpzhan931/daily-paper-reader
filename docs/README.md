<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-22
- 运行时间：2026-08-22 20:24:40 UTC
- 运行状态：成功
- 本次总论文数：8
- 精读区：6
- 速读区：2

### 今日简报（AI）
今日共处理8篇论文，精读6篇、速读2篇，重点聚焦大模型解码优化与边缘端推理效率。

最值得关注的是两篇9.0分精读：《Beyond Tokens》系统梳理LLM与VLM解码方法，以及《S2-MoE》实现边缘设备上MoE的高效自推测解码。

建议普通读者优先从解码方法综述入手建立全局认知，再结合S2-MoE了解实用优化方向。
- 详情：[/202608/22/README](/202608/22/README)

### 精读区论文标签
1. [Beyond Tokens: A Survey on Decoding Methods for Large Language and Vision-Language Models](/202608/22/2608.14797v1-beyond-tokens-a-survey-on-decoding-methods-for-large-language-and-vision-language-models)  
   标签：评分：9.0/10、query:vlm-spec
   evidence：综述涵盖并行解码等加速视觉语言模型推理的解码方法
2. [S2-MoE: Enabling Efficient Self-Speculative Decoding for Mixture-of-Experts on Edge Devices](/202608/22/2608.15018v1-s2-moe-enabling-efficient-self-speculative-decoding-for-mixture-of-experts-on-edge-devices)  
   标签：评分：9.0/10、query:llm
   evidence：面向MoE的自投机解码框架，降低验证开销并提升推理效率
3. [S2-MoE: Enabling Efficient Self-Speculative Decoding for Mixture-of-Experts on Edge Devices](/202608/22/2608.15018v2-s2-moe-enabling-efficient-self-speculative-decoding-for-mixture-of-experts-on-edge-devices)  
   标签：评分：9.0/10、query:llm
   evidence：面向混合专家模型的自投机解码，提升边缘设备上的推理效率
4. [Learning how to Forget: Fine-tuning for Long-Context Sparse Attention](/202608/22/2608.19920v1-learning-how-to-forget-fine-tuning-for-long-context-sparse-attention)  
   标签：评分：9.0/10、query:llm
   evidence：通过微调适配稀疏注意力实现KV缓存压缩，直接支持LLM高效推理与KV缓存优化
5. [FlashQuant: Sparse-Dense Fusion for Memory-Efficient Outlier-Aware LLM Inference](/202608/22/2608.15531v1-flashquant-sparse-dense-fusion-for-memory-efficient-outlier-aware-llm-inference)  
   标签：评分：8.0/10、query:llm
   evidence：面向内存高效LLM推理的量化与稀疏-稠密融合
6. [MoNe: Modular Neural Memory for Efficient Long Context Inference](/202608/22/2608.17616v1-mone-modular-neural-memory-for-efficient-long-context-inference)  
   标签：评分：8.0/10、query:llm
   evidence：高效长上下文推理；降低Transformer的计算和显存开销

### 速读区论文标签
1. [DeltaLog: Deferred Materialization of Recurrent States for Linear Attention Decoding](/202608/22/2608.15533v1-deltalog-deferred-materialization-of-recurrent-states-for-linear-attention-decoding)  
   标签：评分：7.0/10、query:llm
   evidence：通过循环状态内存优化实现高效大模型解码
2. [Dynamic Multi-Byte Prediction With Hierarchical Language Models](/202608/22/2608.15454v1-dynamic-multi-byte-prediction-with-hierarchical-language-models)  
   标签：评分：6.0/10、query:llm
   evidence：并行多字节预测以加速分层语言模型推理


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
