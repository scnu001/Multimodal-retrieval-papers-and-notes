## 📘 论文信息

- **标题（Title）**: ViSTA: Vision and Scene Text Aggregation for Cross-Modal Retrieval
- **作者（Authors）**: Mengjun Cheng, Yipeng Sun, Longchao Wang, Xiongwei Zhu, Kun Yao, Jie Chen, Guoli Song, Junyu Han, Jingtuo Liu, Errui Ding, Jingdong Wang
- **年份（Year）**: 2022
- **会议/期刊（Venue）**: CVPR 2022 (IEEE/CVF Conference on Computer Vision and Pattern Recognition) 
- **arXiv 链接**: [arXiv:2203.16778](https://arxiv.org/abs/2203.16778)
- **关键词（Keywords）**: Scene Text Aware Cross-modal Retrieval, Vision and Scene Text Aggregation, Full Transformer Architecture, Scene Text Semantics Integration, Cross-modal Entity Alignment, Text-Visual Feature Fusion, Scene Text Graph, Text-guided Attention Mechanism, Multi-granularity Text Representation, OCR-Text Graph
- **本地 PDF**: [📂 打开 PDF](paper/ViSTA.pdf)

---

## 🎯 核心贡献（Contributions）

1. 提出了ViSTA框架，首次系统性地将场景文本信息整合到跨模态检索中，解决了传统方法仅依赖视觉外观而忽略图像中文字信息的局限性 
2. 设计了完整的Transformer架构，统一处理场景文本感知和传统无场景文本的跨模态检索任务，实现了单一模型处理多种检索场景 
3. 提出了场景文本语义与视觉特征的聚合机制，通过有效整合场景文本信息，显著提升了跨模态检索性能，特别是在包含文字信息的图像检索任务中 

---

## 🧠 方法概览（Method Overview）

- **模型结构**：
  - 全Transformer架构：统一处理视觉特征和场景文本特征
  - 双流编码器：分别处理图像视觉特征和OCR提取的文本特征
  - 跨模态融合模块：实现视觉和文本特征的深度交互

- **输入输出**：
  - 输入：图像及其通过OCR提取的场景文本信息
  - 输出：与查询文本匹配的跨模态表示，用于计算相似度和检索

- **核心模块**：
  - Scene Text Graph：构建场景文本的语义关系图，捕获文本间的上下文关系
  - Text-Visual Feature Fusion：将OCR提取的文本特征与视觉特征进行多层次融合
  - Text-guided Attention Mechanism：利用场景文本指导视觉特征的注意力分布
  - Multi-granularity Text Representation：从字符级到句子级的多粒度文本表示 

- **损失函数 / 训练策略**：
  - 对比学习损失：拉近匹配的图像-文本对，推开不匹配对
  - 场景文本感知损失：专门针对包含场景文本的样本设计的损失函数
  - 两阶段训练策略：先在大规模数据上预训练，再在特定任务上微调
  - 多任务学习：同时优化场景文本感知和传统无场景文本的检索任务

- **其他创新点**：
  - 提出了统一框架处理有无场景文本的跨模态检索任务，避免了为不同场景设计专门模型的复杂性
  - 通过场景文本语义与视觉外观的聚合，解决了仅依赖视觉信息导致的语义缺失问题
  - 设计了轻量级但有效的文本-视觉特征融合机制，显著提升了检索性能而不大幅增加计算复杂度

---

## 📊 实验与结果（Experiments）

- **数据集**：
  - Flickr30K：用于常规跨模态检索任务评估
  - CTC-1K和CTC-5K：专门用于场景文本感知检索任务的数据集 
  - MSCOCO：大规模图像-文本对数据集，用于常规检索任务评估
  - VG (Visual Genome)：用于预训练的数据集，包含丰富的场景文本信息

- **对比方法**：
  - 传统无场景文本方法：基于SBU、GCC、VG和MSCOCO预训练的基线模型
  - Scene Text Aware方法：仅处理包含场景文本的检索任务的专门模型
  - 其他跨模态检索方法：包括基于场景图和对象检测的最新方法 

- **性能指标**：
  - Recall@K：评估前K个检索结果中包含相关样本的比例
  - R@1, R@5, R@10：不同召回率指标
  - 文本到图像检索和图像到文本检索的对称评估指标
  - 场景文本感知任务的专门评估指标

- **消融实验**：
  - 场景文本模块有效性：验证了场景文本信息对检索性能的贡献
  - 不同融合策略比较：测试了多种视觉-文本特征融合方法的效果
  - OCR质量影响：分析了OCR提取质量对最终检索性能的影响
  - 预训练数据规模影响：评估了不同规模预训练数据对模型性能的贡献 