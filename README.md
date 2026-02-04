# Adult Income 数据治理项目

## 🎯 项目目标

通过对比实验证明**数据治理的价值**：
- Version A (Minimal): 最少处理
- Version B (Governance): 完整治理流程 ⭐
- Version C (Balanced): B + SMOTE平衡

## 📁 项目结构

```
adult_income/
├── notebooks/              # Jupyter notebooks
│   ├── 00_README.ipynb    # 项目总览和指南
│   ├── 01_data_profiling.ipynb
│   ├── 02_exploratory_data_analysis.ipynb
│   ├── 03_data_governance.ipynb
│   └── 04_model_validation.ipynb
├── data/
│   ├── raw/               # 原始数据
│   └── processed/         # 处理后的3个版本
├── outputs/
│   ├── figures/           # 所有可视化图表
│   └── models/            # 训练好的模型
├── requirements.txt       # Python依赖
└── README.md             # 本文件
```

## 🚀 快速开始

### 1. 环境配置

```bash
# 激活conda环境
conda activate your_env_name

# 安装依赖
conda install --classic -c conda-forge imbalanced-learn
pip install -r requirements.txt
```

### 2. 执行顺序

按数字顺序依次打开并运行notebooks：
1. `00_README.ipynb` - 阅读项目概览
2. `01_data_profiling.ipynb` - 数据画像
3. `02_exploratory_data_analysis.ipynb` - EDA找陷阱
4. `03_data_governance.ipynb` - 数据治理
5. `04_model_validation.ipynb` - 模型验证

### 3. 预期输出

- **19张图表** 保存在 `outputs/figures/`
- **3个模型文件** 保存在 `outputs/models/`
- **3个数据版本** 保存在 `data/processed/`
- **6个CSV报告** 保存在 `outputs/`

## 📊 主要发现

### 数据质量问题
- 缺失值: 3列，约5%
- 性别偏见: 67% Male
- 种族偏见: 85% White
- 类别不平衡: 24% vs 76%

### 模型性能对比
- **最佳准确率**: B: Governance - Random Forest (86.13%)
- **最佳稳健性**: B: Governance (CV Std = 0.0035)
- **最佳公平性**: C: Balanced (少数类性能提升)

### 核心结论
**数据治理的价值不仅在于提升准确率，更在于：**
- ✅ 提升模型稳健性（降低方差）
- ✅ 改善特征可解释性
- ✅ 减少模型偏见，提升公平性

## 🛠️ 技术栈

- **数据处理**: pandas, numpy
- **可视化**: matplotlib, seaborn
- **机器学习**: scikit-learn
- **类别平衡**: imbalanced-learn (SMOTE)
- **开发环境**: Jupyter Notebook

## 📚 关键技术

- IQR异常值检测与Winsorization
- Simpson's Paradox检测
- Label Encoding vs One-Hot Encoding
- Z-score标准化
- SMOTE合成少数类过采样
- 5-Fold交叉验证

## ⚖️ 伦理考虑

本项目特别关注AI公平性：
- 明确披露数据偏见（性别、种族）
- Version C专门优化少数类性能
- 讨论"收入≠成功"的标签偏见
- 强调模型仅用于教学，不应用于实际决策

## 📞 问题反馈

如遇问题，请检查：
1. Python环境是否正确配置
2. 所有依赖是否安装完整
3. 数据文件路径是否正确
4. 是否按顺序执行notebooks

---

**License**: Educational Use Only  
**Dataset**: UCI Adult Income Dataset (1994 Census)
