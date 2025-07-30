## 📘 论文信息

- **标题（Title）**: MoCa: Modality-aware Continual Pre-training Makes Better Bidirectional Multimodal Embeddings
- **作者（Authors）**: Haonan Chen, Hong Liu, Yuping Luo, Liang Wang, Nan Yang, Furu Wei, Zhicheng Dou
- **年份（Year）**: 2025
- **会议/期刊（Venue）**: 暂未查询到正式发表记录
- **arXiv 链接**: [arXiv:2506.23115](https://arxiv.org/abs/2506.23115)
- **关键词（Keywords）**: Modality-aware Continual Pre-training, Bidirectional Multimodal Embeddings, Text-aligned Visual Tokenization, Multi-stage Contrastive Learning, Cross-modal Alignment, Multimodal Retrieval Optimization, Synthetic Data Augmentation, Modality-specific Adaptation, Embedding Space Harmonization, Weakly-supervised Contrastive Learning
- **本地 PDF**: [📂 打开 PDF](paper/Modality-aware_Continual_Pre-training.pdf)

---

## 🎯 核心贡献（Contributions）

1. 提出了MoCa (Modality-aware Continual Pre-training)框架，通过模态感知的持续预训练策略，显著提升了双向多模态嵌入的质量，解决了传统方法中模态间表示不一致的问题 
2. 设计了文本对齐的视觉标记化(Text-aligned Visual Tokenization)技术，使视觉特征与文本语义空间更好地对齐，增强了跨模态检索的准确性 
3. 引入了多阶段对比学习策略，通过合成高质量多模态数据，有效缓解了多模态数据稀缺问题，并在多个跨模态检索基准测试中实现了最先进的性能 

---

## 🧠 方法概览（Method Overview）

- **模型结构**：
  - 基于多模态LLM的双向嵌入架构，支持从文本到图像和从图像到文本的双向检索
  - 采用模态感知的持续预训练框架，分阶段优化不同模态的表示能力
  - 整合了文本编码器和视觉编码器，形成统一的嵌入空间

- **输入输出**：
  - 输入：原始文本和图像数据
  - 输出：统一嵌入空间中的向量表示，支持跨模态检索和理解

- **核心模块**：
  - Modality-specific Adaptation Layer：针对不同模态特性进行特定适应的模块 
  - Text-aligned Visual Tokenization：将视觉特征与文本语义对齐的标记化机制 
  - Embedding Space Harmonization：协调不同模态嵌入空间的统一表示模块
  - Synthetic Data Augmentation：生成高质量合成多模态数据以扩展训练集 

- **损失函数 / 训练策略**：
  - 多阶段对比学习损失，包括模态内对比和跨模态对比
  - 弱监督对比预训练损失，利用弱标签数据增强表示学习 
  - 持续预训练策略，逐步增加任务复杂度和数据多样性
  - 模态感知的课程学习，根据模态特性动态调整训练难度

- **其他创新点**：
  - 提出了一种解决多模态嵌入中"模态鸿沟"问题的新方法
  - 实现了无需任务特定微调的通用多模态表示
  - 通过模态感知的持续学习，有效缓解了多模态模型中的灾难性遗忘问题

---

## 📊 实验与结果（Experiments）

- **数据集**：
  - 多模态检索基准：BEIR (Heterogenous Benchmark for Zero-shot Evaluation) 
  - 多语言多模态数据集：mme5 (Multimodal Multilingual Embeddings) 
  - 通用视觉-语言数据集：Janus-pro数据集 
  - 合成多模态数据：通过高质量合成技术生成的补充数据集

- **对比方法**：
  - MM-Embed：通用多模态检索的多模态LLM方法 
  - Text Embeddings by Weakly-supervised Contrastive Pre-training 
  - Janus：用于统一多模态理解和生成的解耦视觉编码 
  - Colpali：高效的基于视觉语言模型的文档检索系统 

- **性能指标**：
  - 跨模态检索准确率(NDCG@10, Recall@K)
  - 零样本迁移性能
  - 多语言支持能力评估
  - 训练效率和模型大小指标

- **消融实验**：
  - 不同预训练阶段对最终性能的贡献分析
  - 模态感知组件的有效性验证
  - 合成数据质量与数量对性能的影响
  - 文本对齐视觉标记化技术与传统方法的对比分析