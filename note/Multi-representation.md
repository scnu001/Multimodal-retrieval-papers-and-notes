## 📘 论文信息

- **标题（Title）**: Multimodality Representation Learning: A Survey on Evolution, Pretraining and Its Applications
- **作者（Authors）**: Shangsong Liang (corresponding author) and others
- **年份（Year）**: 2023
- **会议/期刊（Venue）**: ACM Transactions on Multimedia Computing, Communications and Applications 20.3 (2023)
- **arXiv 链接**: [arXiv:2302.00389](https://arxiv.org/abs/2302.00389)
- **关键词（Keywords）**: DropToken Strategy, Multiway Transformer, Cross-Attention Adapter, Image-Text Contrastive Loss, Masked "Language" Modeling, Two-stage Training, Pre-training Multi-task Training, Instruction Fine-tuning, Visual Question Answering (VQA), Multimodal Abstractive Summarization, Multimodal Information Retrieval, Hierarchical Attention Fusion
- **本地 PDF**: [📂 打开 PDF](paper/Multimodality Representation Learning.pdf)

---

## 🎯 核心贡献（Contributions）

1. 系统性地回顾了多模态表示学习的演进历程，从早期任务特定方法到现代大规模预训练-微调架构，提供了清晰的技术发展脉络 
2. 提出了多模态深度学习方法的统一分类框架，详细分析了任务特定方法与预训练-微调架构的优缺点及适用场景 
3. 全面综述了多模态预训练的关键技术，包括预训练任务设计、最先进的框架以及各种下游应用，为研究者提供了全面的技术参考 

---

## 🧠 方法概览（Method Overview）

- **模型结构**：
  - UniT[108]：201M参数，由ResNet-50+BERT组成，支持视觉和语言任务
  - ViT-BERT[107]：12层Transformer，768隐藏单元，3072 MLP
  - UNITER-large：303M参数，在多个基准测试中表现优异
  - VATT[109]：优于基于CNN的方法，在音频事件识别和视频动作识别任务中表现突出

- **输入输出**：
  - 输入：不同模态的数据（文本、图像、音频等）及其预处理后的特征表示
  - 输出：用于下游任务（如视觉问答、图像检索、多模态摘要等）的统一表示或任务特定输出

- **核心模块**：
  - Multiway Transformer：用于统一处理不同模态数据的转换器架构
  - DropToken策略：减少训练计算复杂度的采样技术，替代维度和分辨率降低 
  - Cross-Attention Adapter：连接视觉编码器和语言模型的适配器模块
  - Hierarchical Attention Fusion：用于多源多模态摘要的分层注意力融合网络

- **损失函数 / 训练策略**：
  - Image-Text Contrastive Loss：用于对齐图像和文本表示
  - Masked "Language" Modeling：用于图像、文本和图像-文本对的掩码语言建模
  - Image-Text Matching Loss：用于判断图像-文本对是否匹配
  - Two-stage Training：如MiniGPT-4中的两阶段训练策略（特征对齐和指令微调）

- **其他创新点**：
  - 提出了多模态表示学习的演进框架，阐明了从任务特定方法到预训练-微调架构的转变
  - 详细分析了预训练任务对下游任务性能的影响，为模型设计提供了理论指导
  - 探讨了多模态技术在实际应用中的挑战及潜在解决方案，包括数据质量和计算效率问题

---

## 📊 实验与结果（Experiments）

- **数据集**：
  - COCO、Flickr30k：用于图像字幕生成和跨模态检索任务
  - VQA2.0、VCR、RefCOCO：用于视觉问答和视觉常识推理任务
  - MNLI、QQP、SST-2：用于自然语言理解任务
  - SROIE、FUNSD：用于视觉丰富文档理解任务

- **对比方法**：
  - 任务特定方法：SegNet、FCN、PointFusion等特征级和模型级融合模型
  - 预训练-微调架构：VLP、VirTex、ViLBERT、ERNIE-ViL等
  - 统一架构：UNiT、ViT-BERT、UNITER等

- **性能指标**：
  - 准确率、F1分数：用于分类任务评估
  - BLEU、ROUGE、CIDEr：用于图像描述生成任务评估
  - mAP (mean Average Precision)：用于跨模态检索任务评估
  - F1分数：用于文档理解任务评估（如LayoutLMv2在SROIE上达到97%）

- **消融实验**：
  - 分析了不同预训练任务（如掩码语言建模、图像-文本对比学习）对下游任务性能的贡献
  - 验证了不同架构组件（如Multiway Transformer、Cross-Attention Adapter）的有效性
  - 测试了不同视觉编码器（ViT、ResNet等）和语言模型组合的效果差异
  - 评估了DropToken策略对模型性能和计算效率的影响，证明其在减少计算复杂度的同时保持了性能