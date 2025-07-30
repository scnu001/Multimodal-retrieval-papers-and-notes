## 📘 论文信息

- **标题（Title）**: ALPS: Attention Localization and Pruning Strategy for Efficient Alignment of Large Language Models
- **作者（Authors）**: X Wang, L Gao, H Wang, Y Zhang, J Zhao
- **年份（Year）**: 2024
- **会议/期刊（Venue）**: 暂未查询到正式发表记录
- **arXiv 链接**: [arXiv:2505.18799](https://arxiv.org/abs/2505.18799)
- **关键词（Keywords）**: Task-specific attention heads localization, Attention head pruning, Parameter-efficient fine-tuning, Transferable task-specific heads, Knowledge forgetting mitigation, Layer consistency selection, QKV weight matrices
- **本地 PDF**: [📂 打开 PDF](paper/Attention_Localization_and_Pruning_Strategy.pdf)

---

## 🎯 核心贡献（Contributions）

1. 提出了Attention Localization and Pruning Strategy (ALPS)算法，能够定位最任务敏感的注意力头并进行剪枝，显著提高大型语言模型对齐效率 
2. 在微调过程中仅激活10%的注意力参数，同时在三个任务上比基线方法提高了2%的性能 
3. 识别出的任务特定注意力头可以在不同数据集之间转移，并有效减轻知识遗忘问题，为高效LLM对齐提供了新视角 

---

## 🧠 方法概览（Method Overview）

- **模型结构**：
  - 基于现有LLM的注意力机制进行优化，不改变原始模型架构
  - 通过分析注意力头对特定任务的敏感度，构建任务特定的注意力头子集

- **输入输出**：
  - 保持与原始LLM相同的输入输出格式和接口
  - 输入：标准文本序列；输出：与原始模型一致的预测结果

- **核心模块**：
  - Task-specific attention heads localization：识别对特定任务最关键的注意力头
  - Attention head pruning：冻结不重要的注意力头，只更新关键注意力头
  - Layer consistency selection (LC)：确保选定的注意力头在各层中均匀分布 

- **损失函数 / 训练策略**：
  - 参数高效微调策略，仅更新选定注意力头的QKV权重矩阵
  - 通过任务性能指标指导注意力头的选择过程
  - 采用渐进式剪枝策略，平衡模型性能与计算效率

- **其他创新点**：
  - 识别出的任务特定注意力头具有跨数据集转移能力
  - 证明了更少的注意力头可以避免知识遗忘问题
  - 提供了任务敏感注意力头的可视化分析方法

---

## 📊 实验与结果（Experiments）

- **数据集**：
  - IFEval、GPQA、GSM8K、MATH、HEval、HEval+、MBPP、MBPP+
  - 覆盖一般知识、数学和代码生成等多个任务领域

- **对比方法**：
  - Full fine-tuning：标准全监督微调，更新所有注意力参数
  - Random head selection：随机选择固定比例的注意力头进行训练
  - Layer consistency selection (LC)：在随机选择基础上确保各层注意力头均匀分布
  - LoRA：低秩适应方法 

- **性能指标**：
  - 多个任务上的准确率指标
  - 注意力参数激活比例(Attn%)
  - 与基线方法相比的性能提升百分比
  - 知识遗忘评估(MMLU和ARC-C基准测试)

- **消融实验**：
  - 不同比例的注意力头激活(10% vs 全参数)对性能的影响
  - 任务特定注意力头在不同数据集间的可转移性验证
  - 与Full fine-tuning相比在知识遗忘方面的优势分析
  - 各种选择策略(Random vs LC)的性能比较 