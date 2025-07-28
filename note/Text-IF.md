## 📘 论文信息

- **标题（Title）**: Text-IF: Leveraging Semantic Text Guidance for Degradation-Aware and Interactive Image Fusion
- **作者（Authors）**: Xunpeng Yi, Han Xu, Hao Zhang, Linfeng (and others) 
- **年份（Year）**: 2024
- **会议/期刊（Venue）**: Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition. 2024.
- **arXiv 链接**: [arXiv:2403.16387](https://arxiv.org/abs/2403.16387)
- **关键词（Keywords）**: Semantic Interaction-guided Module, Degradation-aware Processing, Text-guided Image Restoration, Text Semantic Encoder, Semantic Interaction Fusion Decoder, Interactive Flexible Fusion, Text-to-Fusion Mapping, Degradation Specification, Multi-modal Image Fusion, Object Detection Enhancement
- **本地 PDF**: [📂 打开 PDF](paper/Text-IF Leveraging Semantic Text Guidance for Degradation-Aware and.pdf)

---

## 🎯 核心贡献（Contributions）

1. 提出了Text-IF框架，解决了图像融合和退化感知的综合问题，突破了传统图像融合质量提升的限制，实现了更适应复杂退化条件的图像处理 
2. 引入了语义交互引导模块，利用文本指定图像退化的类型，实现了退化感知融合，使系统能够根据不同的退化条件动态调整融合策略 
3. 通过文本语义编码器和语义交互融合解码器，实现了全能红外和可见图像的退化感知处理和交互式灵活融合，不仅提升了融合质量，还增强了下游任务（如目标检测）的性能 

---

## 🧠 方法概览（Method Overview）

- **模型结构**：
  - 两阶段架构：首先进行退化感知的图像修复，然后进行语义引导的图像融合
  - 文本语义编码器：将文本描述转换为语义指导向量
  - 语义交互融合解码器：根据文本指导生成高质量融合图像

- **输入输出**：
  - 输入：退化图像对（如低光可见光图像和红外图像）以及描述退化类型或期望输出的文本提示
  - 输出：高质量融合图像，保留源图像的关键信息并修复退化问题

- **核心模块**：
  - Semantic Interaction-guided Module：利用文本指定图像退化类型，实现退化感知融合 
  - Degradation-aware Processing：针对不同类型的图像退化（低光、低对比度、噪声、过曝等）进行自适应处理
  - Text-to-Fusion Mapping：将文本语义信息映射到融合过程的关键参数，指导融合决策

- **损失函数 / 训练策略**：
  - 多任务损失函数：结合图像质量评估指标（如NIQE、MUSIQ）和结构相似性
  - 退化感知训练：使用多种退化类型的数据进行训练，提高模型的泛化能力
  - 交互式微调：允许用户通过文本提示调整融合结果，实现个性化输出

- **其他创新点**：
  - 消除了传统方法中需要针对特定退化类型设计专门算法的局限性，实现了统一框架处理多种退化条件
  - 通过文本指导实现了用户与融合过程的交互，使融合结果更符合用户期望
  - 在提升图像融合质量的同时，显著改善了下游任务（如目标检测）的性能，验证了方法的实用性 

---

## 📊 实验与结果（Experiments）

- **数据集**：
  - MSRS：多光谱遥感数据集，用于评估低光可见光图像融合
  - LLVIP：低光可见光-红外视频数据集，包含低光条件下的可见光和红外图像对
  - MFNet：多模态融合数据集，包含低对比度红外图像
  - DN-MSRS：添加噪声的MSRS数据集，用于评估噪声图像处理能力
  - RoadScene：道路场景数据集，包含过曝的可见光图像

- **对比方法**：
  - UMF-CMGR、TarDAL、ReCoNet、MURF：现有的图像融合方法
  - U2Fusion、MetaFusion、DDFM：先进的多模态图像融合算法
  - eir.+XXX：现有图像修复方法与融合方法的组合

- **性能指标**：
  - EN (Entropy)：评估图像信息量
  - NIQE (Natural Image Quality Evaluator)：评估图像自然度
  - MUSIQ：基于深度学习的图像质量评估指标
  - SD (Structural Distortion)：评估结构失真
  - mAP@0.50、mAP@0.75：目标检测任务的平均精度

- **消融实验**：
  - 文本指导有效性：验证了不同文本提示对融合质量的影响
  - 退化感知模块贡献：分析了退化感知处理对不同类型退化图像的改进效果
  - 语义交互融合解码器分析：测试了不同设计选择对最终性能的贡献
  - 下游任务性能评估：在目标检测任务上验证了Text-IF融合结果的实用性，证明其优于现有方法 