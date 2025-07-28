## 📘 论文信息

- **标题（Title）**: End-to-end Knowledge Retrieval with Multi-modal Queries
- **作者（Authors）**: Man Luo, Zhiyuan Fang, Tejas Gokhale, Yezhou Yang, Chitta Baral
- **年份（Year）**: 2023
- **会议/期刊（Venue）**: ACL 2023 (Association for Computational Linguistics) 
- **arXiv 链接**: [arXiv:2306.00424](https://arxiv.org/abs/2306.00424)
- **关键词（Keywords）**: ReViz Model, ReMuQ Dataset, Multi-modal Queries, End-to-end VL-Retriever, Multimodal Retrieval Pre-training Task, Cross-modal Semantic Alignment, Image-Text Query Processing, Knowledge Corpus Retrieval, VL-ICT Pretraining
- **本地 PDF**: [📂 打开 PDF](paper/ReViz Multi-modal Queries.pdf)

---

## 🎯 核心贡献（Contributions）

1. 提出了ReViz模型，一种能够直接处理多模态查询（包含跨图像和文本输入的信息）进行端到端知识检索的系统，无需依赖中间模块如对象检测器或字幕生成器 
2. 创建了新的基准数据集ReMuQ，包含8418个训练样本和3609个测试样本，用于评估多模态查询知识检索系统的性能 
3. 设计了创新的多模态检索预训练任务（VL-ICT），有效解决了查询和知识编码器在不同语义空间中的对齐难题，显著提升了检索性能 

---

## 🧠 方法概览（Method Overview）

- **模型结构**：
  - 多模态转换器：处理图像和文本查询输入的编码器
  - 语言转换器：处理知识库文本的编码器
  - 端到端架构：直接连接多模态查询和知识检索，消除中间处理步骤

- **输入输出**：
  - 输入：图像-文本对构成的多模态查询（例如，一张图片加上相关问题）
  - 输出：从大型知识库中检索到的相关知识描述

- **核心模块**：
  - Multimodal Retrieval Pre-training Task：创建(input-image, input-text, output-knowledge)三元组进行预训练 
  - Cross-modal Semantic Alignment：解决不同模态编码器产生的嵌入在不同语义空间的问题
  - VL-Retriever架构：直接处理多模态输入的端到端检索系统，无需中间转换模块

- **损失函数 / 训练策略**：
  - 对比学习损失：拉近相关查询-知识对的嵌入距离，推远不相关对
  - 三元组损失：基于(input-image, input-text, output-knowledge)三元组的预训练任务
  - 两阶段训练：先进行多模态检索预训练，再在下游任务上进行微调

- **其他创新点**：
  - 消除了传统方法中需要先将图像转换为语言表示（如字幕或对象标签）的中间步骤，避免了信息损失 
  - 提出的预训练任务不仅提高了检索性能，还改善了下游任务的表现 
  - 通过端到端训练实现了查询和知识表示之间的更好对齐，解决了不同模态编码器的语义空间差异问题

---

## 📊 实验与结果（Experiments）

- **数据集**：
  - ReMuQ：新构建的多模态查询数据集，包含8418个训练样本和3609个测试样本，知识库包含约195,837个知识描述 
  - OKVQA：用于评估多模态问答任务的基准数据集
  - GS-112K：包含112,000个知识描述的检索知识库

- **对比方法**：
  - CLIP-IMG+Q：使用CLIP图像编码器结合文本查询
  - BM25(GenCap)：基于生成字幕的传统检索方法
  - DPR(GenCap)：基于生成字幕的密集段落检索器
  - TRiG：使用GPT-3生成知识的检索方法 

- **性能指标**：
  - MRR@5：平均倒数排名（前5个结果）
  - P@5：前5个结果的精确率
  - R@5, R@10, R@20, R@50, R@100：不同召回率指标
  - F-1分数：精确率和召回率的调和平均数

- **消融实验**：
  - 预训练任务有效性：验证了多模态检索预训练任务(VL-ICT)对模型性能的提升 
  - 模型组件分析：测试了不同架构组件对最终性能的贡献
  - 知识库大小影响：评估了不同规模知识库对检索性能的影响
  - 多模态查询分析：研究了不同类型和复杂度的多模态查询对系统表现的影响 