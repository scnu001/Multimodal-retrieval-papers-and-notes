## 📘 论文信息

- **标题（Title）**: RAPTOR: RECURSIVE ABSTRACTIVE PROCESSING FOR TREE-ORGANIZED RETRIEVAL
- **作者（Authors）**: Parth Sarthi, Salman Abdullah, Aditi Tuli, Shubh Khanna, Anna Goldie, Christopher D. Manning
- **年份（Year）**: 2024
- **会议/期刊（Venue）**: The Twelfth International Conference on Learning Representations. 2024（ICLR）
- **arXiv 链接**: [arXiv:2401.18059](https://arxiv.org/abs/2401.18059)
- **关键词（Keywords）**: Tree-Organized Retrieval, Recursive Clustering, Hierarchical Summarization, Multi-level Abstraction, Chunk Embedding, Context-aware Retrieval, Abstract Node Generation, Bottom-up Tree Construction, Query-adaptive Retrieval, Long Document Understanding
- **本地 PDF**: [📂 打开 PDF](paper/RAPTOR.pdf)

---

## 🎯 核心贡献（Contributions）

1. 提出了RAPTOR（Recursive Abstractive Processing for Tree-Organized Retrieval）框架，通过递归嵌入、聚类和总结文本块构建树状结构，解决了传统检索增强语言模型中只能检索短文本片段而难以获取全局信息的局限性 
2. 设计了自下而上的树结构构建方法，使系统能够检索不同抽象级别的信息，从而更好地回答需要全局理解的复杂问题 
3. 在QASPER等数据集上验证了该方法的有效性，证明RAPTOR在F-1分数上比BM25和DPR等基线方法高出至少1.8个百分点，展示了其在长文本理解和检索任务中的优势 

---

## 🧠 方法概览（Method Overview）

- **模型结构**：
  - 树状层次结构：从底层文本块到高层抽象摘要的多级表示
  - 递归构建机制：通过迭代聚类和摘要生成构建树状结构
  - 分层索引系统：不同层级的节点存储不同抽象级别的信息

- **输入输出**：
  - 输入：长文本文档（如科学论文、书籍章节等）
  - 输出：针对查询的多级检索结果，包含具体细节和全局概要信息

- **核心模块**：
  - Recursive Clustering：将文本块聚类形成更高层次的节点 
  - Abstract Node Generation：为每个聚类生成摘要表示的抽象节点
  - Bottom-up Tree Construction：从原始文本块开始，自下而上构建树状结构 
  - Query-adaptive Retrieval：根据查询特性动态选择合适的抽象级别进行检索

- **损失函数 / 训练策略**：
  - 摘要质量评估：使用LLM评估生成摘要的相关性和信息量
  - 多级检索优化：优化不同抽象级别节点的嵌入表示
  - 层次一致性约束：确保树中不同层级的表示保持语义一致性

- **其他创新点**：
  - 消除了传统基于连续分块的检索方法的局限性，解决了技术或科学文档中上下文缺失的问题 
  - 通过递归摘要机制，使检索结果更加相关和全面，从而在下游任务中实现更好的性能 
  - 提供了可解释的检索路径，使用户能够理解系统如何从不同抽象级别获取信息

---

## 📊 实验与结果（Experiments）

- **数据集**：
  - QASPER：科学论文问答数据集，用于评估长文本理解能力 
  - 2600字故事数据集：包含叙事和主题相关问题的自定义评估集
  - BEIR检索数据集套件：用于多领域检索任务评估

- **对比方法**：
  - BM25：经典的基于词频的检索方法
  - DPR：密集段落检索器，当前主流的单向量检索方法
  - Title+Abstract：仅使用论文标题和摘要作为上下文的基线方法

- **性能指标**：
  - F-1分数：用于评估问答任务的准确性和完整性 
  - MRR@10 (Mean Reciprocal Rank)：评估检索结果的相关性排序
  - 人工评估：通过定性分析评估检索结果的质量和相关性

- **消融实验**：
  - 不同语言模型对比：在GPT-3、GPT-4和UnifiedQA 3B上验证RAPTOR的通用性 
  - 树深度影响：分析不同层次树结构对检索性能的影响
  - 聚类算法比较：评估不同聚类方法对树构建质量的影响
  - 摘要生成策略：测试不同摘要生成方法对最终检索效果的贡献 