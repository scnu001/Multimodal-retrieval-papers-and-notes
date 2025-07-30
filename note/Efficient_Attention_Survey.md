## 📘 论文信息

- **标题（Title）**: Efficient Large Language Models: A Survey 
- **作者（Authors）**: Zhongwei Wan, Yu Zheng, and others (complete author list not fully visible in search results) 
- **年份（Year）**: 2023 (arXiv submission), 2024 (journal publication)
- **会议/期刊（Venue）**: Transactions on Machine Learning Research (TMLR) 
- **arXiv 链接**: [arXiv:2312.03863](https://arxiv.org/abs/2312.03863)
- **关键词（Keywords）**: Model Compression, Unstructured Pruning, Knowledge Distillation, Prompt Tuning, Memory-Efficient Fine-Tuning, Speculative Decoding, KV-Cache Optimization, Sharing-based Attention, MQA (Multi-Query Attention), GQA (Grouped-Query Attention), Performer, RFA (Random Features Attention), Low-Rank Approximation
- **本地 PDF**: [📂 打开 PDF](paper/Efficient_Attention_Survey.pdf)

---

## 🎯 核心贡献（Contributions）

1. 提供了高效大语言模型研究的系统性和全面性综述，将现有文献组织成一个包含三个主要类别的分类体系 
2. 详细分析了以模型为中心、以数据为中心和以框架为中心的LLM效率优化技术，为研究者提供了清晰的技术路线图 
3. 对各种高效LLM技术进行了深入比较，包括模型压缩、高效微调、推理加速等方向，并讨论了各种方法的优缺点和适用场景

---

## 🧠 方法概览（Method Overview）

- **模型结构**：
  - 作为综述论文，本文不提出新模型，而是系统分类现有高效LLM技术架构
  - 将高效注意力机制分为Sharing-based Attention、Kernelization/Low-Rank、Fixed Pattern Strategies和Learnable Pattern Strategies等类别
  
- **输入输出**：
  - 作为综述，本文不涉及具体输入输出，而是分析各类高效LLM方法的输入输出特性
  - 特别关注长上下文处理中的输入长度限制问题及解决方案

- **核心模块**：
  - MQA (Multi-Query Attention)和GQA (Grouped-Query Attention)作为共享式注意力代表 
  - Performer、RFA等基于随机特征的注意力近似方法
  - Speculative Decoding(推测解码)和KV-Cache Optimization(KV缓存优化)等推理加速技术
  - Model Compression(模型压缩)技术如Unstructured Pruning(非结构化剪枝)和Knowledge Distillation(知识蒸馏)

- **损失函数 / 训练策略**：
  - 分析了混合精度训练(AMP)、Brain Floating Point(BFLOAT16)等高效预训练技术
  - 讨论了参数高效微调方法如Prompt Tuning、LoRA等的训练策略
  - 介绍了ZeRO、FSDP等系统级预训练效率优化技术

- **其他创新点**：
  - 提出了高效LLM研究的三维分类框架：以模型为中心、以数据为中心和以框架为中心
  - 详细分析了各种技术的理论基础和实际应用限制
  - 为未来研究方向提供了系统性建议

---

## 📊 实验与结果（Experiments）

- **数据集**：
  - 作为综述论文，总结了各类高效LLM技术在标准NLP数据集上的表现
  - 包括GLUE、SuperGLUE、LAMBADA、WikiText等基准测试集
  - 长文本处理任务如PG-19、GovReport等用于评估长上下文模型

- **对比方法**：
  - 系统比较了各类模型压缩技术(结构化/非结构化剪枝、量化、低秩分解)
  - 对比了不同注意力机制变体(Performer、Linear Transformer、Routing Transformer等)
  - 分析了各种参数高效微调方法(Prompt Tuning、Adapter、LoRA等)的性能差异

- **性能指标**：
  - 模型大小(MB/GB)、参数量、计算复杂度(FLOPs)
  - 推理速度(tokens/s)、内存占用、能效比
  - 任务准确率、困惑度(perplexity)、与原始模型的性能差距

- **消融实验**：
  - 分析了不同压缩率对模型性能的影响
  - 研究了各种注意力近似方法中关键超参数(如随机特征数量)的影响
  - 评估了不同微调策略在少量样本场景下的有效性
  - 比较了系统级优化技术(如ZeRO)在不同规模模型上的加速效果