请你阅读我上传的论文 PDF（arXiv 预印本），并输出一份格式规范、信息完整的 Markdown 学术笔记。请严格按以下要求执行：

---

🎯 输出要求：

1. 提取论文的完整信息，包括标题、作者、年份、PDF 本地链接、DOI 和 arXiv 链接；
2. 请根据标题与作者，**联网查询该论文是否已被正式接收/发表**（如 NeurIPS、CVPR、ACL、IEEE TSP 等），如果查不到，请注明“暂未查询到正式发表记录”；
3. 请在 “关键词” 字段中提取 **具体的技术关键词**，不要泛泛写 “Multimodal Learning” 或 “LLMs”，而应根据论文中提出的方法、模块、损失函数、核心机制等提取，如：
   - 方法名：Contrastive Fusion Token、Prompt-based Retrieval、Scene-aware Filtering；
   - 模块结构：Cross-modal Graph Matching、Wasserstein Robust Estimator、OCR-Text Graph；
   - 技术细节：Token-level Alignment、AdapterFusion、Score-based Fusion；
4. 输出内容请严格遵循以下 Markdown 模板格式，**模块名不得删除或改动顺序**；
5. “本地 PDF”链接请使用 `[📂 打开 PDF](paper/XXX.pdf)` 格式，文件名替换为上传文件名；
6. “arXiv链接”请填入真实地址，若查不到 arXiv ID 请写“未知”。

---

📝 Markdown 输出格式如下：

## 📘 论文信息

- **标题（Title）**: 
- **作者（Authors）**: 
- **年份（Year）**: 
- **会议/期刊（Venue）**: 请尽可能联网查找是否正式发表，若未收录请注明“暂未查询到正式发表记录”
- **arXiv 链接**: [arXiv:xxxx.xxxxx](https://arxiv.org/abs/xxxx.xxxxx)
- **关键词（Keywords）**: 
- **本地 PDF**: [📂 打开 PDF](paper/XXX.pdf)

---

## 🎯 核心贡献（Contributions）

1. 
2. 
3. 

---

## 🧠 方法概览（Method Overview）

- **模型结构**：
  - 
- **输入输出**：
  - 
- **核心模块**：
  - 
- **损失函数 / 训练策略**：
  - 
- **其他创新点**：
  - 

---

## 📊 实验与结果（Experiments）

- **数据集**：
  - 
- **对比方法**：
  - 
- **性能指标**：
  - 
- **消融实验**：
  - 

---





