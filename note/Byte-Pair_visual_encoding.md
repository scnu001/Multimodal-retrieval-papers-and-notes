## 📘 论文信息

- **标题（Title）**: Unified Multimodal Understanding via Byte-Pair Visual Encoding
- **作者（Authors）**: Wanpeng Zhang, Yicheng Feng, Hao Luo 
- **年份（Year）**: 2025
- **会议/期刊（Venue）**: 暂未查询到正式发表记录
- **arXiv 链接**: [arXiv:2506.23639](https://arxiv.org/abs/2506.23639)
- **关键词（Keywords）**: Priority-guided Visual Encoding, Unified Token Representation, Visual Byte Pair Encoding, Curriculum-driven Data Composition, RFD (Foundation Data Ratio), RPD (Perception Data Ratio), Embedding Alignment, Selective Fine-tuning, Stage-specific Parameter Freezing, Spatial Consistency Preservation
- **本地 PDF**: [📂 打开 PDF](paper/Byte-Pair_visual_encoding.pdf)

---

## 🎯 核心贡献（Contributions）

1. 提出了一个通过字节对编码应用于视觉token来统一多模态理解的框架，解决了多模态大语言模型中有效对齐不同模态的根本挑战 
2. 引入了优先级引导的编码方案(priority-guided encoding)，同时考虑频率和空间一致性，突破了传统仅依赖频率计数的简单视觉token编码限制 
3. 设计了基于课程驱动(curriculum-driven)的数据组成多阶段训练程序，通过精心设计的数据比例策略(RFD、RPD、RRD、RID)，系统性地解决了混合模态模型训练中的对齐和适应性问题 

---

## 🧠 方法概览（Method Overview）

- **模型结构**：
  - 基于统一token空间的混合模态架构，将文本和图像视为同一模型中的token进行处理
  - 三阶段训练流程：嵌入对齐(Embedding Alignment)、选择性微调(Selective Fine-tuning)和指令微调(Instruction Tuning)
  - 采用改进的Byte Pair Encoding技术处理视觉信息，实现图像token化

- **输入输出**：
  - 输入：原始图像和文本数据，通过视觉BPE编码转换为统一的离散token序列
  - 输出：能够理解并生成任意序列的文本和图像内容，实现真正的混合模态交互

- **核心模块**：
  - Priority-guided Visual Encoding：考虑频率和空间一致性的视觉token编码机制
  - Unified Token Space：将不同模态数据映射到共享表示空间的统一处理系统
  - Curriculum-driven Data Composition：动态调整基础数据、感知数据、推理数据和指令数据比例的管理系统
  - Stage-specific Parameter Freezing：在不同训练阶段冻结特定参数的策略

- **损失函数 / 训练策略**：
  - 课程学习方法，采用分阶段数据比例策略
  - 第一阶段(Embedding Alignment)：RFD ≫ RPD > RRD = RID = 0，主要关注基础数据
  - 第二阶段(Selective Fine-tuning)：RFD ≈ RPD > RRD > RID，增加对感知和推理数据的重视
  - 第三阶段(Instruction Tuning)：整合指令数据以提升任务执行能力

- **其他创新点**：
  - 视觉BPE编码保留了图像的结构信息，使Transformer模型能更有效地学习二维视觉数据
  - 优先级引导的编码方案超越了简单的频率计数，考虑了视觉元素的空间关系
  - 统一token表示方法避免了传统方法中模态特定编码器的限制

---

## 📊 实验与结果（Experiments）

- **数据集**：
  - Instruction Data(ID)：包括来自ShareGPT4o的57.3K条目、ALLaVA Inst的70K、LLaVA-OneVision的180K OCR相关条目和Infinity-MM的100K
  - 多模态基准测试集：用于评估模型理解和生成能力的多样化数据集

- **对比方法**：
  - 传统后期融合多模态模型
  - 分离的文本和视觉处理管道
  - 其他多模态基础模型如Unified-IO 2
  - 基于连续嵌入的方法

- **性能指标**：
  - 多模态理解和生成质量评估
  - 跨模态对齐准确性
  - 多模态基准测试上的任务性能
  - 模态间生成的连贯性和一致性

- **消融实验**：
  - 不同数据组成比例(RFD、RPD、RRD、RID)对模型性能的影响
  - 三阶段训练课程的有效性验证
  - 统一token方法与单独模态处理的对比分析
  - 视觉BPE编码对图像理解和生成质量的贡献评估