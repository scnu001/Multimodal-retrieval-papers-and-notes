## 📘 论文信息

- **标题（Title）**: An Image is Worth More Than 16×16 Patches: Exploring Transformers on Individual Pixels  
- **作者（Authors）**: Duy-Kien Nguyen, Mahmoud Assran, Unnat Jain, Martin R. Oswald, Cees G. M. Snoek, Xinlei Chen  
- **年份（Year）**: 2025  
- **会议/期刊（Venue）**: 已发表于 ICLR 2025  
- **arXiv 链接**: [arXiv:2410.12345](https://arxiv.org/abs/2410.12345)  
- **关键词（Keywords）**: 像素作为token（Pixels-as-tokens）、无局部性偏置（Locality-free）、位置嵌入（Learned Position Embedding）、对比学习优化（Contrastive Learning）、注意力机制（Self-Attention）、块化设计（Patchification）、像素置换（Pixel Permutation）、多尺度分析（Multi-scale Analysis）  
- **本地 PDF**: [📂 打开 PDF](paper/XXX.pdf)  

---

## 🎯 核心贡献（Contributions）

1. **挑战局部性偏置的必要性**：通过实验证明，Transformer 可以直接将每个像素作为 token 处理，无需依赖传统 Vision Transformer（ViT）中的 16×16 块化设计，从而质疑局部性偏置在视觉任务中的必要性。  
2. **跨任务有效性验证**：在监督学习（分类与回归）、自监督学习（掩码自编码）和图像生成（扩散模型）任务中，验证了无局部性偏置的 Transformer 架构的有效性。  
3. **揭示 ViT 局部性设计的局限性**：通过像素置换实验发现，ViT 中的块化设计（Patchification）对局部性偏置的依赖远强于位置嵌入，且完全移除局部性偏置仍能取得优异性能。  

---

## 🧠 方法概览（Method Overview）

- **模型结构**：  
  - **像素级 Transformer 架构**：将图像视为无序的像素集合，每个像素作为独立 token，通过线性投影映射到隐藏维度，并附加可学习的位置嵌入。  
  - **无局部性偏置设计**：完全移除 ViT 中的块化步骤（16×16 块投影），直接处理像素级 token，避免局部性假设。  

- **输入输出**：  
  - **输入**：RGB 图像（如 32×32 或 224×224 分辨率）。  
  - **输出**：根据任务类型生成分类结果、重建图像或生成新图像。  

- **核心模块**：  
  - **像素投影层**：将每个像素（R, G, B）线性映射为隐藏维度向量。  
  - **位置嵌入**：通过可学习的嵌入层为每个像素分配位置信息，不依赖 2D 网格结构。  
  - **Self-Attention 模块**：通过全局注意力机制捕捉像素间的长距离依赖关系。  
  - **MLP 块**：用于非线性变换和特征融合。  

- **损失函数 / 训练策略**：  
  - **监督学习**：交叉熵损失（分类）或均方误差（回归）。  
  - **自监督学习（MAE）**：掩码重建损失（像素级回归）。  
  - **图像生成**：扩散模型的负对数似然损失。  

- **其他创新点**：  
  - **字典化 ViT 变体**：利用像素强度值的有限词汇量（256³）设计非参数嵌入，减少词汇量。  
  - **像素置换实验**：通过随机置换像素验证局部性偏置对性能的影响。  

---

## 📊 实验与结果（Experiments）

- **数据集**：  
  - **CIFAR-100**：32×32 分辨率，100 类图像分类。  
  - **ImageNet**：224×224 分辨率，1000 类图像分类。  
  - **Oxford-102-Flowers**：细粒度分类任务。  
  - **NYU-v2**：深度估计回归任务。  
  - **ImageNet（生成任务）**：基于扩散模型的图像生成。  

- **对比方法**：  
  - **ViT 基线**：使用 2×2 或 16×16 块化的标准 ViT 变体（ViT-T/2, ViT-S/2, ViT-B/2）。  
  - **无局部性偏置 ViT**：像素级 Transformer（ViT-T/1, ViT-S/1, ViT-B/1）。  
  - **扩散模型基线**：DiT-L/2（块化设计）与 DiT-L/1（像素级设计）。  

- **性能指标**：  
  - **分类任务**：  
    - **CIFAR-100**：ViT-T/1 达到 85.1% Acc@1，优于 ViT-T/2 的 83.6%。  
    - **ImageNet**：ViT-S/1 达到 74.1% Acc@1，优于 ViT-S/2 的 72.9%。  
  - **深度估计**：ViT-S/1 的 RMSE 为 0.72，优于 ViT-S/2 的 0.80。  
  - **图像生成**：DiT-L/1 在 FID 指标上达到 4.05，优于 DiT-L/2 的 4.16。  

- **消融实验**：  
  - **位置嵌入影响**：移除位置嵌入后，ViT-B/1 的 Acc@1 仅下降 1.5%（82.8% → 81.2%）。  
  - **像素置换实验**：当置换 25K 像素对时，ViT-B 的 Acc@1 下降至 57.6%，表明块化设计对局部性偏置的强依赖。  
  - **字典化 ViT**：非参数嵌入的 ViT-B/1 在 ImageNet 上达到 76.6% Acc@1，优于默认 ViT-B/1 的 76.1%。  

---