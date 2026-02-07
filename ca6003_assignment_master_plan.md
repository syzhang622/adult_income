# CA6003 数据治理与准备作业 - 高分作战计划

## 📋 作业核心要求解析

### 🎯 关键理念（必须理解！）
```
⚠️ 重点警告：这不是一个追求模型准确率的作业！
✅ 核心目标：证明数据准备的重要性，而非模型性能
✅ 评分重点：解释、推理、洞察 > 准确率
```

### 📊 评分标准拆解（总分90%）

| 维度 | 占比 | 核心要求 | 如何拿高分 |
|------|------|----------|-----------|
| **Appropriateness** | 25% | 选择合适的分析技术和可视化 | 在每个阶段都用**正确且多样**的方法 |
| **Correctness & Clarity** | 25% | 技术正确性 + 清晰表达 | 每个决策都有**明确的理由和证据** |
| **Data Interpretation** | 25% | 分析判断力（识别偏差、谬误） | 展示**深度分析**，抓住Simpson's paradox等 |
| **Novelty & Depth** | 25% | 原创性和深度洞察 | 选**有趣的数据集**，做**非常规分析** |

---

## 🚀 高分作业流程（7步走）

### **阶段1：数据集选择（Week 1，Day 1-2）**

#### 目标：选一个"有故事"的数据集

**❌ 避免选择：**
- Iris、Titanic等烂大街数据集
- 太干净的数据（没法展示清洗技巧）
- 太复杂的数据（理解成本高）

**✅ 推荐选择特征：**
1. **有现实意义**：医疗、金融、社会问题
2. **有明显问题**：缺失值、离群值、类别不平衡
3. **有潜在偏差**：性别、年龄、地域等bias
4. **中等规模**：5000-50000行，10-30列

**🎯 推荐数据集：**
```
优先级1（强烈推荐）：
- Credit Card Fraud Detection (Kaggle)
  → 极度不平衡，有明显离群值，现实意义强
  
- Adult Income Dataset (UCI)
  → 有性别/种族bias，缺失值多，社会意义强
  
- Healthcare/Medical datasets (Kaggle)
  → 缺失值多，偏态分布，伦理问题突出

优先级2（备选）：
- Singapore HDB Resale Prices (data.gov.sg)
  → 本地数据，时间序列，地域偏差
  
- Employee Attrition (Kaggle)
  → 类别不平衡，特征工程空间大
```

**选择标准清单：**
```python
✅ 数据集评估checklist：
□ 是否有>10%缺失值？
□ 是否有明显离群值？
□ 是否有类别不平衡问题？
□ 是否有潜在bias（性别/年龄/地域）？
□ 是否有现实意义和故事性？
□ 是否适合用简单模型（线性/逻辑/决策树）？
□ 数据量是否适中（5k-50k行）？

如果有5个以上✅ → 选这个！
```

---

### **阶段2：数据Profiling & EDA（Week 1-2，Day 3-7）**

#### 目标：全方位体检数据，找出所有问题

**📊 必做分析（拿满25%的Appropriateness分）：**

#### 2.1 基础Profiling
```python
必须包含的内容：
1. 数据集概览
   - 行数、列数、内存占用
   - 数据类型分布（数值/类别/日期）
   - 目标变量分布

2. 缺失值分析
   - 每列缺失率
   - 缺失模式可视化（missingno库）
   - 缺失值相关性分析（MCAR/MAR/MNAR判断）

3. 数值特征分析
   - 五数概括（min, Q1, median, Q3, max）
   - 偏度(skewness)和峰度(kurtosis)
   - 直方图 + 密度图

4. 类别特征分析
   - 类别数量和分布
   - 高基数问题识别
   - 稀有类别检测
```

#### 2.2 高级分析（拿Novelty分的关键！）
```python
进阶内容（展示深度）：

1. 离群值检测（多种方法对比）
   ✅ IQR方法
   ✅ Z-score方法
   ✅ Isolation Forest
   ✅ 箱型图可视化
   → 关键：解释为什么离群（像你PPT里的"whales"）

2. 相关性分析（识别谬误的机会！）
   ✅ Pearson相关矩阵热力图
   ✅ Spearman相关（非线性关系）
   ✅ 识别多重共线性（VIF）
   ⚠️ 强调：Correlation ≠ Causation！
   
3. 分布分析
   ✅ QQ Plot（检验正态性）
   ✅ 偏态识别（左偏/右偏/双峰）
   ✅ 对数变换前后对比

4. Bias检测（重点！）
   ✅ 按性别/年龄/地域分组统计
   ✅ 检验统计显著性（t-test/chi-square）
   ✅ 可视化群体差异（分组箱型图）
   
5. Simpson's Paradox检测
   ✅ 整体趋势 vs 分组趋势对比
   ✅ 用实例说明反转现象
   → 这是拿Novelty分的金矿！
```

#### 🎨 可视化要求
```
每个分析都要配图，且图要讲故事：

基础可视化（必须有）：
- 缺失值热力图
- 数值特征分布图（直方图+KDE）
- 相关矩阵热力图
- 箱型图（离群值检测）
- 类别特征柱状图

高级可视化（加分项）：
- QQ Plot
- Pair Plot（特征两两关系）
- Violin Plot（分布+箱型图结合）
- 分组对比图（显示bias）
- 时间序列图（如果有时间维度）

⚠️ 图表设计原则：
1. 每个图都要有标题、轴标签、图例
2. 使用色盲友好的配色
3. 图不要太密集（一页最多2-3个图）
4. 每个图后面都要有文字解释
```

---

### **阶段3：数据清洗与转换（Week 2，Day 1-3）**

#### 目标：展示数据准备的重要性

**🔧 必做步骤（要有Before/After对比！）：**

#### 3.1 缺失值处理
```python
必须展示多种方法的对比：

方法1：删除
- 适用场景：缺失率<5%
- 决策理由：简单且不影响分布
- Before/After对比：样本量变化

方法2：填补
- 均值/中位数填补（数值型）
- 众数填补（类别型）
- 前向/后向填充（时间序列）
- KNN填补（高级方法）
- 决策理由：保留样本量，填补值合理

方法3：标记缺失
- 创建is_missing指示变量
- 决策理由：缺失本身可能有信息

⚠️ 关键：每个决策都要justify！
```

#### 3.2 离群值处理
```python
策略对比（这是重点！）：

策略A：保留
- 理由：代表真实高价值客户（像你PPT）
- 证据：业务分析 + 领域知识

策略B：删除
- 理由：极端值会影响模型
- 证据：统计检验（>3σ）

策略C：Winsorization（截尾）
- 理由：保留信息但减少影响
- 方法：替换为99th percentile

策略D：转换
- 理由：通过变换减少影响
- 方法：log变换、Box-Cox

⚠️ 每个策略都要实验，对比影响！
```

#### 3.3 特征工程
```python
基础工程：
1. 编码
   - One-Hot Encoding（低基数类别）
   - Label Encoding（有序类别）
   - Target Encoding（高基数类别）

2. 缩放
   - StandardScaler（正态分布）
   - MinMaxScaler（有界数据）
   - RobustScaler（有离群值）

3. 分箱（Binning）
   - 等宽分箱
   - 等频分箱
   - 自定义分箱（业务逻辑）

高级工程（加分项）：
4. 交互特征
   - 特征相乘/相加
   - 多项式特征

5. 时间特征
   - 提取年/月/日/周几
   - 周期性编码（sin/cos）

6. 领域知识特征
   - 如：BMI = weight / height^2
   - 收入负债比 = debt / income

⚠️ 每个特征都要解释为什么创建！
```

#### 3.4 Bias缓解
```python
必须展示的策略：

1. 重采样
   - Oversampling少数群体
   - Undersampling多数群体
   - SMOTE（但要说明为什么用/不用）

2. 重加权
   - 给不同群体不同权重
   - 平衡训练集

3. 公平性约束
   - 确保不同群体有相似结果
   - Demographic parity检验

⚠️ 关键：讨论trade-off（公平 vs 性能）
```

---

### **阶段4：创建对比版本（Week 2，Day 4）**

#### 目标：制造"戏剧性对比"

**📦 必须准备的数据版本：**

```python
版本1：Minimal Processing（基线）
- 只删除完全空行
- 不做任何填补
- 不处理离群值
- 不做特征工程
- 只做最基本编码
→ 目的：作为"坏例子"

版本2：Full Preparation（完整版）
- 合理处理缺失值
- 处理离群值（有理有据）
- 完整特征工程
- Bias缓解
- 所有转换优化
→ 目的：展示最佳实践

版本3：Over-processing（可选，加分项）
- 过度删除数据
- 激进处理离群值
- 过度特征工程
→ 目的：说明"过犹不及"

⚠️ 每个版本都要记录：
- 样本量变化
- 特征数量变化
- 分布变化
- 处理决策日志
```

---

### **阶段5：简单模型对比（Week 3，Day 1-3）**

#### 目标：用ML证明数据准备的重要性

**🤖 必须使用的模型（只能用简单模型！）：**

```python
场景1：分类问题
主模型：Logistic Regression
对比模型：Decision Tree（深度限制≤5）

场景2：回归问题
主模型：Linear Regression
对比模型：Decision Tree Regressor（深度限制≤5）

⚠️ 严格禁止：
- Random Forest
- XGBoost
- Neural Networks
- SVM（复杂核函数）
→ 用了会扣分！
```

**📊 对比实验设计：**

```python
实验1：基线 vs 完整准备
数据：Minimal vs Full
模型：相同模型（如Logistic Regression）
评估：准确率、精确率、召回率、F1、AUC

实验2：不同处理策略对比
例如：
- 删除离群值 vs 保留离群值
- 填补缺失 vs 删除缺失
- 有特征工程 vs 无特征工程

实验3：Bias影响
对比：
- 原始数据的群体差异
- 缓解后的群体差异
- Fairness metrics（Demographic Parity, Equal Opportunity）

⚠️ 评估重点：
✅ 解释性能差异的原因
✅ 特征重要性分析
✅ 错误案例分析
✅ 残差分析（回归问题）
✅ 混淆矩阵分析（分类问题）

❌ 不要：
- 盲目调参
- 追求最高准确率
- 使用复杂模型
```

**📈 必须的可视化：**
```
1. 性能对比柱状图
   - 不同版本的准确率对比
   - 不同指标（Precision/Recall/F1）对比

2. ROC曲线对比
   - Minimal vs Full的ROC曲线
   - AUC差异标注

3. 特征重要性图
   - 展示哪些新特征最有用
   - 原始特征 vs 工程特征

4. 学习曲线
   - 训练集 vs 验证集性能
   - 判断过拟合/欠拟合

5. 残差图（回归）/ 混淆矩阵（分类）
   - 展示预测错误的模式
   - 分析改进空间

6. Fairness对比图
   - 不同群体的性能差异
   - 缓解前后对比
```

---

### **阶段6：Jupyter Notebook撰写（Week 3，Day 4-7）**

#### 目标：制作一个"教科书级"的Notebook

**📓 Notebook结构（严格按此组织！）：**

```markdown
# 项目标题
Group X - [数据集名称] 数据准备与分析

## 目录
1. 项目概述
2. 数据获取与加载
3. 数据Profiling
4. 探索性数据分析（EDA）
5. 数据清洗与转换
6. 特征工程
7. Bias检测与缓解
8. 模型对比实验
9. 结果分析与洞察
10. 总结与反思

---

## 1. 项目概述

### 1.1 背景与目标
**业务背景：**
[用2-3段话描述数据集的现实意义]

**分析目标：**
- 目标1：...
- 目标2：...
- 目标3：...

**关键问题：**
1. 问题1：...
2. 问题2：...
3. 问题3：...

### 1.2 数据集描述
- **来源：** [链接]
- **样本量：** X行
- **特征数：** Y列
- **目标变量：** [名称及含义]
- **时间范围：** [如适用]

### 1.3 工具与库
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import classification_report, confusion_matrix, roc_auc_score

# 设置
plt.style.use('seaborn-v0_8')
sns.set_palette("husl")
pd.set_option('display.max_columns', None)
```

---

## 2. 数据获取与加载

### 2.1 数据加载
```python
# 加载数据
df = pd.read_csv('data.csv')

# 初步查看
print(f"数据集形状: {df.shape}")
df.head()
```

### 2.2 数据字典
| 列名 | 类型 | 描述 | 取值范围 |
|------|------|------|----------|
| ... | ... | ... | ... |

---

## 3. 数据Profiling

### 3.1 基础信息
```python
# 数据类型
df.info()

# 数值统计
df.describe()

# 缺失值统计
missing = df.isnull().sum()
missing[missing > 0]
```

### 3.2 缺失值分析
```python
import missingno as msno

# 缺失值可视化
msno.matrix(df)
plt.title('Missing Data Pattern')
plt.show()

# 缺失值相关性
msno.heatmap(df)
plt.title('Missing Data Correlation')
plt.show()
```

**分析结论：**
- 观察1：...
- 观察2：...
- 缺失机制判断：MCAR/MAR/MNAR？

---

## 4. 探索性数据分析（EDA）

### 4.1 目标变量分析
```python
# 分布
df['target'].value_counts()

# 可视化
plt.figure(figsize=(8, 6))
df['target'].value_counts().plot(kind='bar')
plt.title('Target Variable Distribution')
plt.xlabel('Class')
plt.ylabel('Count')
plt.show()
```

**关键发现：**
- 类别平衡情况：...
- 是否需要处理：...

### 4.2 数值特征分析
```python
# 选择数值列
numeric_cols = df.select_dtypes(include=[np.number]).columns

# 分布图
fig, axes = plt.subplots(nrows=3, ncols=3, figsize=(15, 12))
for idx, col in enumerate(numeric_cols[:9]):
    ax = axes[idx // 3, idx % 3]
    df[col].hist(bins=30, ax=ax, edgecolor='black')
    ax.set_title(f'{col} Distribution')
    ax.set_xlabel(col)
    ax.set_ylabel('Frequency')
plt.tight_layout()
plt.show()

# 偏度和峰度
skewness = df[numeric_cols].skew()
kurtosis = df[numeric_cols].kurtosis()
print("Skewness:\n", skewness[abs(skewness) > 1])
print("\nKurtosis:\n", kurtosis[abs(kurtosis) > 3])
```

**分析：**
- 高度偏态特征：[列举]
- 潜在离群值特征：[列举]
- 建议转换：[列举]

### 4.3 类别特征分析
```python
# 类别列
categorical_cols = df.select_dtypes(include=['object']).columns

# 唯一值统计
for col in categorical_cols:
    print(f"{col}: {df[col].nunique()} unique values")
    print(df[col].value_counts().head())
    print("-" * 50)

# 高基数检测
high_cardinality = [col for col in categorical_cols 
                    if df[col].nunique() > 10]
print(f"High cardinality features: {high_cardinality}")
```

### 4.4 离群值检测
```python
# 箱型图
fig, axes = plt.subplots(nrows=2, ncols=3, figsize=(15, 10))
for idx, col in enumerate(numeric_cols[:6]):
    ax = axes[idx // 3, idx % 3]
    df.boxplot(column=col, ax=ax)
    ax.set_title(f'{col} Boxplot')
plt.tight_layout()
plt.show()

# IQR方法检测
def detect_outliers_iqr(df, col):
    Q1 = df[col].quantile(0.25)
    Q3 = df[col].quantile(0.75)
    IQR = Q3 - Q1
    lower = Q1 - 1.5 * IQR
    upper = Q3 + 1.5 * IQR
    outliers = df[(df[col] < lower) | (df[col] > upper)]
    return outliers, lower, upper

# 检测每列
for col in numeric_cols:
    outliers, lower, upper = detect_outliers_iqr(df, col)
    print(f"{col}: {len(outliers)} outliers ({len(outliers)/len(df)*100:.2f}%)")
```

**离群值决策：**
| 特征 | 离群值% | 决策 | 理由 |
|------|---------|------|------|
| ... | ... | 保留/删除/转换 | ... |

### 4.5 相关性分析
```python
# 相关矩阵
corr_matrix = df[numeric_cols].corr()

# 热力图
plt.figure(figsize=(12, 10))
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm', center=0)
plt.title('Correlation Matrix')
plt.show()

# 高相关性检测
high_corr = []
for i in range(len(corr_matrix.columns)):
    for j in range(i+1, len(corr_matrix.columns)):
        if abs(corr_matrix.iloc[i, j]) > 0.8:
            high_corr.append((corr_matrix.columns[i], 
                            corr_matrix.columns[j], 
                            corr_matrix.iloc[i, j]))

print("High correlation pairs:")
for pair in high_corr:
    print(f"{pair[0]} vs {pair[1]}: {pair[2]:.3f}")
```

**⚠️ 相关性≠因果性警告**
[举例说明correlation vs causation]

### 4.6 QQ Plot（正态性检验）
```python
from scipy import stats

fig, axes = plt.subplots(nrows=2, ncols=3, figsize=(15, 10))
for idx, col in enumerate(numeric_cols[:6]):
    ax = axes[idx // 3, idx % 3]
    stats.probplot(df[col].dropna(), dist="norm", plot=ax)
    ax.set_title(f'{col} Q-Q Plot')
plt.tight_layout()
plt.show()
```

**正态性结论：**
- 符合正态：[列举]
- 需要转换：[列举]

### 4.7 Bias检测（重点！）
```python
# 假设有gender列
if 'gender' in df.columns:
    # 分组统计
    grouped = df.groupby('gender')[numeric_cols].mean()
    print(grouped)
    
    # 可视化对比
    fig, axes = plt.subplots(nrows=1, ncols=3, figsize=(15, 5))
    for idx, col in enumerate(['income', 'loan_amount', 'credit_score']):
        ax = axes[idx]
        df.boxplot(column=col, by='gender', ax=ax)
        ax.set_title(f'{col} by Gender')
    plt.tight_layout()
    plt.show()
    
    # 统计检验
    from scipy.stats import ttest_ind
    male_income = df[df['gender'] == 'Male']['income']
    female_income = df[df['gender'] == 'Female']['income']
    t_stat, p_value = ttest_ind(male_income, female_income)
    print(f"T-test: t={t_stat:.3f}, p={p_value:.3f}")
    if p_value < 0.05:
        print("⚠️ Significant difference detected - potential bias!")
```

### 4.8 Simpson's Paradox检测（加分项！）
```python
# 示例：整体趋势 vs 分组趋势
# [根据你的数据集设计具体例子]

# 整体相关性
overall_corr = df[['feature1', 'feature2']].corr().iloc[0, 1]
print(f"Overall correlation: {overall_corr:.3f}")

# 分组相关性
for group in df['group_column'].unique():
    subset = df[df['group_column'] == group]
    group_corr = subset[['feature1', 'feature2']].corr().iloc[0, 1]
    print(f"Group {group} correlation: {group_corr:.3f}")

# 可视化
plt.figure(figsize=(10, 6))
sns.scatterplot(data=df, x='feature1', y='feature2', hue='group_column')
plt.title("Simpson's Paradox Illustration")
plt.show()
```

**Simpson's Paradox发现：**
[解释你发现的反转现象]

---

## 5. 数据清洗与转换

### 5.1 创建数据副本
```python
# 保留原始数据
df_original = df.copy()

# 创建处理版本
df_minimal = df.copy()  # 最小处理
df_full = df.copy()     # 完整处理
```

### 5.2 Minimal Processing Version
```python
# 只删除完全空行
df_minimal = df_minimal.dropna(how='all')

# 基础编码
from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
for col in categorical_cols:
    df_minimal[col + '_encoded'] = le.fit_transform(df_minimal[col].fillna('missing'))

print(f"Minimal processing: {df_minimal.shape}")
```

### 5.3 Full Preparation Version

#### 5.3.1 缺失值处理
```python
# 策略1：删除（缺失率<5%的列）
low_missing_cols = missing[missing / len(df) < 0.05].index
df_full = df_full.dropna(subset=low_missing_cols)

# 策略2：填补（缺失率5-20%的列）
medium_missing_cols = missing[(missing / len(df) >= 0.05) & 
                               (missing / len(df) < 0.20)].index

for col in medium_missing_cols:
    if col in numeric_cols:
        # 用中位数填补（对离群值鲁棒）
        df_full[col].fillna(df_full[col].median(), inplace=True)
    else:
        # 用众数填补
        df_full[col].fillna(df_full[col].mode()[0], inplace=True)

# 策略3：标记缺失（缺失率20-50%的列）
high_missing_cols = missing[(missing / len(df) >= 0.20) & 
                             (missing / len(df) < 0.50)].index

for col in high_missing_cols:
    df_full[col + '_is_missing'] = df_full[col].isnull().astype(int)
    df_full[col].fillna(df_full[col].median(), inplace=True)

# 策略4：删除列（缺失率>50%）
df_full = df_full.drop(columns=missing[missing / len(df) > 0.50].index)

print(f"After missing value treatment: {df_full.shape}")
```

**缺失值处理决策日志：**
| 列名 | 缺失率 | 策略 | 理由 |
|------|--------|------|------|
| ... | ... | ... | ... |

#### 5.3.2 离群值处理
```python
# 决策：保留高价值客户离群值，处理错误数据

# 示例：保留收入离群值（高收入客户）
# 但处理年龄离群值（可能是错误）

# 年龄离群值处理
age_outliers, lower, upper = detect_outliers_iqr(df_full, 'age')
print(f"Age outliers: {len(age_outliers)} ({lower:.1f}, {upper:.1f})")

# 截尾处理
df_full['age'] = df_full['age'].clip(lower=lower, upper=upper)

# 收入离群值保留
print("Income outliers retained - represent high-value customers")
```

**离群值处理决策：**
- 保留：[列举+理由]
- 删除：[列举+理由]
- 转换：[列举+理由]

#### 5.3.3 特征转换
```python
# 偏态特征log转换
skewed_features = ['income', 'loan_amount']
for col in skewed_features:
    df_full[col + '_log'] = np.log1p(df_full[col])
    
    # 前后对比
    fig, axes = plt.subplots(1, 2, figsize=(12, 4))
    df_full[col].hist(bins=30, ax=axes[0], edgecolor='black')
    axes[0].set_title(f'{col} - Original')
    df_full[col + '_log'].hist(bins=30, ax=axes[1], edgecolor='black')
    axes[1].set_title(f'{col} - Log Transformed')
    plt.tight_layout()
    plt.show()
```

---

## 6. 特征工程

### 6.1 编码
```python
# One-Hot Encoding（低基数）
low_cardinality = [col for col in categorical_cols 
                   if df_full[col].nunique() <= 5]
df_full = pd.get_dummies(df_full, columns=low_cardinality, prefix=low_cardinality)

# Target Encoding（高基数）
from category_encoders import TargetEncoder
high_cardinality = [col for col in categorical_cols 
                    if df_full[col].nunique() > 10]
te = TargetEncoder(cols=high_cardinality)
df_full[high_cardinality] = te.fit_transform(df_full[high_cardinality], df_full['target'])
```

### 6.2 交互特征
```python
# 基于领域知识创建
df_full['debt_to_income'] = df_full['debt'] / (df_full['income'] + 1)
df_full['credit_utilization'] = df_full['credit_used'] / (df_full['credit_limit'] + 1)

# 解释
print("创建交互特征：")
print("- debt_to_income: 衡量还款能力")
print("- credit_utilization: 信用使用率")
```

### 6.3 分箱
```python
# 年龄分箱
df_full['age_group'] = pd.cut(df_full['age'], 
                               bins=[0, 25, 35, 50, 100],
                               labels=['Young', 'Adult', 'Middle', 'Senior'])
```

---

## 7. Bias检测与缓解

### 7.1 Bias量化
```python
# 计算不同群体的目标变量分布
bias_analysis = df_full.groupby('gender')['target'].value_counts(normalize=True).unstack()
print(bias_analysis)

# 可视化
bias_analysis.plot(kind='bar', figsize=(10, 6))
plt.title('Target Distribution by Gender')
plt.ylabel('Proportion')
plt.show()
```

### 7.2 Bias缓解
```python
# 方法1：重采样
from imblearn.over_sampling import RandomOverSampler

# 分离特征和标签
X = df_full.drop('target', axis=1)
y = df_full['target']

# 对不同群体重采样
ros = RandomOverSampler(random_state=42)
X_resampled, y_resampled = ros.fit_resample(X, y)

print(f"Before: {len(y)}")
print(f"After: {len(y_resampled)}")

# 方法2：公平性约束
# [可选：使用fairlearn库]
```

---

## 8. 模型对比实验

### 8.1 数据分割
```python
# Minimal版本
X_minimal = df_minimal.select_dtypes(include=[np.number])
y_minimal = X_minimal.pop('target')
X_train_min, X_test_min, y_train_min, y_test_min = train_test_split(
    X_minimal, y_minimal, test_size=0.2, random_state=42)

# Full版本
X_full = df_full.select_dtypes(include=[np.number])
y_full = X_full.pop('target')
X_train_full, X_test_full, y_train_full, y_test_full = train_test_split(
    X_full, y_full, test_size=0.2, random_state=42)
```

### 8.2 模型训练
```python
# Logistic Regression（简单模型）
from sklearn.linear_model import LogisticRegression

# Minimal数据
lr_minimal = LogisticRegression(random_state=42, max_iter=1000)
lr_minimal.fit(X_train_min, y_train_min)
y_pred_min = lr_minimal.predict(X_test_min)

# Full数据
lr_full = LogisticRegression(random_state=42, max_iter=1000)
lr_full.fit(X_train_full, y_train_full)
y_pred_full = lr_full.predict(X_test_full)
```

### 8.3 性能对比
```python
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score, roc_auc_score

# 计算指标
metrics_minimal = {
    'Accuracy': accuracy_score(y_test_min, y_pred_min),
    'Precision': precision_score(y_test_min, y_pred_min, average='weighted'),
    'Recall': recall_score(y_test_min, y_pred_min, average='weighted'),
    'F1': f1_score(y_test_min, y_pred_min, average='weighted'),
    'AUC': roc_auc_score(y_test_min, lr_minimal.predict_proba(X_test_min), multi_class='ovr')
}

metrics_full = {
    'Accuracy': accuracy_score(y_test_full, y_pred_full),
    'Precision': precision_score(y_test_full, y_pred_full, average='weighted'),
    'Recall': recall_score(y_test_full, y_pred_full, average='weighted'),
    'F1': f1_score(y_test_full, y_pred_full, average='weighted'),
    'AUC': roc_auc_score(y_test_full, lr_full.predict_proba(X_test_full), multi_class='ovr')
}

# 对比表格
comparison_df = pd.DataFrame({
    'Minimal Processing': metrics_minimal,
    'Full Preparation': metrics_full,
    'Improvement': [metrics_full[k] - metrics_minimal[k] for k in metrics_minimal.keys()]
})
print(comparison_df)

# 可视化
comparison_df[['Minimal Processing', 'Full Preparation']].plot(kind='bar', figsize=(10, 6))
plt.title('Model Performance Comparison')
plt.ylabel('Score')
plt.xticks(rotation=0)
plt.legend(loc='lower right')
plt.show()
```

### 8.4 ROC曲线对比
```python
from sklearn.metrics import roc_curve, auc

# 计算ROC
fpr_min, tpr_min, _ = roc_curve(y_test_min, lr_minimal.predict_proba(X_test_min)[:, 1])
fpr_full, tpr_full, _ = roc_curve(y_test_full, lr_full.predict_proba(X_test_full)[:, 1])

# 绘图
plt.figure(figsize=(10, 6))
plt.plot(fpr_min, tpr_min, label=f'Minimal (AUC={metrics_minimal["AUC"]:.3f})')
plt.plot(fpr_full, tpr_full, label=f'Full Prep (AUC={metrics_full["AUC"]:.3f})')
plt.plot([0, 1], [0, 1], 'k--', label='Random')
plt.xlabel('False Positive Rate')
plt.ylabel('True Positive Rate')
plt.title('ROC Curve Comparison')
plt.legend()
plt.show()
```

### 8.5 特征重要性
```python
# 获取系数
feature_importance = pd.DataFrame({
    'Feature': X_train_full.columns,
    'Coefficient': lr_full.coef_[0]
}).sort_values('Coefficient', key=abs, ascending=False)

# 可视化Top 15
top_features = feature_importance.head(15)
plt.figure(figsize=(10, 6))
plt.barh(top_features['Feature'], top_features['Coefficient'])
plt.xlabel('Coefficient')
plt.title('Top 15 Feature Importance')
plt.gca().invert_yaxis()
plt.show()
```

### 8.6 混淆矩阵
```python
from sklearn.metrics import confusion_matrix
import seaborn as sns

# Minimal
cm_min = confusion_matrix(y_test_min, y_pred_min)
# Full
cm_full = confusion_matrix(y_test_full, y_pred_full)

# 可视化
fig, axes = plt.subplots(1, 2, figsize=(12, 5))

sns.heatmap(cm_min, annot=True, fmt='d', cmap='Blues', ax=axes[0])
axes[0].set_title('Minimal Processing')
axes[0].set_xlabel('Predicted')
axes[0].set_ylabel('Actual')

sns.heatmap(cm_full, annot=True, fmt='d', cmap='Greens', ax=axes[1])
axes[1].set_title('Full Preparation')
axes[1].set_xlabel('Predicted')
axes[1].set_ylabel('Actual')

plt.tight_layout()
plt.show()
```

---

## 9. 结果分析与洞察

### 9.1 性能改进分析
```markdown
**关键发现：**

1. **整体性能提升**
   - 准确率提升：+X%
   - AUC提升：+Y
   - 主要原因：[具体分析]

2. **哪些数据准备步骤最有影响？**
   - 缺失值处理：[影响]
   - 离群值处理：[影响]
   - 特征工程：[影响]
   - 证据：通过消融实验验证

3. **意外发现**
   - 发现1：[描述+解释]
   - 发现2：[描述+解释]
```

### 9.2 错误案例分析
```python
# 找出预测错误的样本
errors = X_test_full[y_test_full != y_pred_full]
print(f"错误预测数量: {len(errors)}")

# 分析错误样本的特征
error_analysis = errors.describe()
correct_analysis = X_test_full[y_test_full == y_pred_full].describe()

# 对比
comparison = pd.concat([error_analysis.loc['mean'], correct_analysis.loc['mean']], axis=1)
comparison.columns = ['Errors', 'Correct']
comparison['Difference'] = comparison['Errors'] - comparison['Correct']
print(comparison.sort_values('Difference', key=abs, ascending=False).head(10))
```

**错误模式：**
- 模式1：[描述]
- 模式2：[描述]
- 改进方向：[建议]

### 9.3 Fairness评估
```python
# 不同群体的性能差异
for group in df_full['gender'].unique():
    mask = X_test_full['gender'] == group  # 假设gender在特征中
    group_acc = accuracy_score(y_test_full[mask], y_pred_full[mask])
    print(f"{group} Accuracy: {group_acc:.3f}")

# Demographic Parity
# [计算并可视化]
```

---

## 10. 总结与反思

### 10.1 主要贡献
```markdown
1. **数据准备策略**
   - 创新点：[描述]
   - 效果：[量化]

2. **Bias缓解方法**
   - 方法：[描述]
   - 改进：[量化]

3. **分析洞察**
   - Simpson's Paradox发现：[描述]
   - 业务含义：[解释]
```

### 10.2 学到的教训
```markdown
**成功经验：**
- 经验1：...
- 经验2：...

**挑战与解决：**
- 挑战1：... → 解决方案：...
- 挑战2：... → 解决方案：...

**如果重做：**
- 改进1：...
- 改进2：...
```

### 10.3 未来方向
```markdown
- 方向1：尝试更高级的填补方法（如MICE）
- 方向2：深入分析特定子群体
- 方向3：纳入更多领域知识
```

---

## 附录

### A. 完整代码
[提供完整可运行的代码]

### B. 数据字典
[完整的特征说明]

### C. 参考文献
[引用的论文、文档]
```

---

**📝 Markdown写作规范：**

```markdown
优秀的Markdown应该：

1. **结构清晰**
   - 使用#标题层级
   - 每个section有明确目的
   - 逻辑流畅连贯

2. **代码块规范**
   - 每个代码块都有注释
   - 输出结果紧跟代码
   - 重要输出用Markdown表格展示

3. **可视化标注**
   - 每个图都有标题
   - 图后都有文字解释
   - 指出关键发现

4. **决策记录**
   - 用表格记录重要决策
   - 说明理由和证据
   - 对比不同选择

5. **避免冗余**
   - 不要重复代码
   - 不要过度可视化
   - 保持简洁有力

⚠️ 常见错误：
- ❌ 代码没有注释
- ❌ 图表没有解释
- ❌ 决策没有理由
- ❌ 结构混乱跳跃
- ❌ 输出太多不重要信息
```

---

## **阶段7：视频制作（Week 4，Day 1-5）**

### 目标：做一个"TED Talk级"的演示

**🎬 视频结构（12分钟，严格分配）：**

```
时间分配（总计12分钟）：

00:00 - 01:00  开场介绍（1分钟）
01:00 - 02:30  数据集背景与问题（1.5分钟）
02:30 - 04:30  EDA关键发现（2分钟）
04:30 - 06:30  数据清洗与转换（2分钟）
06:30 - 08:00  Bias分析（1.5分钟）
08:00 - 10:00  模型对比实验（2分钟）
10:00 - 11:30  关键洞察与结论（1.5分钟）
11:30 - 12:00  团队贡献与Q&A（0.5分钟）

⚠️ 严格控制时间！超过12分钟会被截断！
```

**📹 视频制作要求：**

```markdown
技术要求：
1. **录制工具**
   - Zoom（推荐）
   - Microsoft Teams
   - OBS Studio（高级）

2. **视频质量**
   - 分辨率：至少1080p
   - 声音清晰（用耳机麦克风）
   - 光线充足（脸部可见）
   - 背景整洁专业

3. **展示形式**
   - 画中画：人像+PPT
   - 所有人都要出镜
   - 切换流畅自然

4. **PPT设计**
   - 简洁清晰（每页<50字）
   - 大字体（标题≥32pt）
   - 高对比度配色
   - 关键数字突出显示
   - 图表清晰可读

内容要求：
1. **开场（1分钟）**
   - 自我介绍（每人5-10秒）
   - 项目背景简介
   - 核心问题陈述
   
   示例脚本：
   "大家好，我是XX。今天我们要展示的是关于[数据集名称]的数据准备分析。
   这个数据集涉及[领域]，包含[X]行数据和[Y]个特征。
   我们的核心问题是：[问题陈述]。
   我们将展示数据准备如何显著影响模型性能。"

2. **数据探索（3.5分钟）**
   - 用1-2个最震撼的可视化
   - 讲清楚最重要的发现
   - 强调问题（缺失、离群、偏差）
   
   关键点：
   - 不要展示所有图！只展示最有说服力的
   - 每个图都要有"故事"
   - 用数字说话（"30%的数据有缺失"）

3. **数据准备（3.5分钟）**
   - Before/After对比要震撼
   - 每个决策都要justify
   - 展示处理过程的可视化
   
   脚本示例：
   "我们发现[特征名]有严重偏态。左图是原始分布，右图是log转换后。
   可以看到转换后更接近正态分布，这将帮助线性模型更好地学习。"

4. **模型对比（2分钟）**
   - 用清晰的对比图
   - 强调性能提升
   - 解释为什么提升
   
   重点强调：
   - "数据准备使准确率提升了X%"
   - "最重要的改进来自[具体步骤]"
   - "这证明了[数据准备原则]的重要性"

5. **洞察与总结（2分钟）**
   - 3个最重要的发现
   - 学到的教训
   - 团队分工
   
   脚本示例：
   "通过这个项目，我们得出三个关键洞察：
   第一，[洞察1]。第二，[洞察2]。第三，[洞察3]。
   最重要的是，我们证明了高质量的数据准备比复杂的模型更重要。"

表达技巧：
1. **语速控制**
   - 不要太快（120-150词/分钟）
   - 关键点要放慢强调
   - 数字要清楚念出

2. **肢体语言**
   - 手势指向PPT关键点
   - 眼神看镜头（不要只看屏幕）
   - 表情自然微笑

3. **过渡流畅**
   - "接下来我们来看..."
   - "更有意思的是..."
   - "这导致了一个重要发现..."

4. **团队协作**
   - 提前排练3-5次
   - 每人负责自己擅长的部分
   - 交接要自然（"现在请XX继续讲解..."）

⚠️ 避免的错误：
- ❌ 读PPT（要conversational）
- ❌ 过度技术术语
- ❌ 没有eye contact
- ❌ 语速太快
- ❌ 背景噪音
- ❌ 时间超时
```

---

## 🎯 高分检查清单

### **提交前最终检查（必做！）**

```markdown
Jupyter Notebook检查：
□ 所有代码都能运行
□ 没有错误或警告
□ 所有图表都能正常显示
□ Markdown解释清晰完整
□ 每个决策都有理由
□ 代码有详细注释
□ 结构清晰有逻辑
□ 文件大小<100MB
□ 文件名包含组号

视频检查：
□ 时长≤12分钟
□ 所有成员都出镜
□ 声音清晰无杂音
□ PPT清晰可读
□ YouTube链接可访问
□ 视频设为公开
□ 标题包含组号
□ 字幕准确（可选但推荐）

内容检查：
□ 包含所有4个学习目标
□ 展示了Minimal vs Full对比
□ 识别了analytical fallacies
□ 检测并缓解了bias
□ 只用了简单模型
□ 强调了数据准备而非准确率
□ 有原创洞察
□ 引用了数据来源

团队协作：
□ 分工明确记录
□ 每人贡献清晰
□ 准备好peer evaluation
□ 所有人都理解全部内容

提交：
□ 在deadline前提交
□ YouTube链接有效
□ .ipynb格式正确
□ 组长确认提交成功
```

---

## 📅 详细时间规划（4周）

### Week 1（数据选择 + 初步EDA）
```
Day 1-2: 选择数据集
- 浏览推荐网站
- 筛选候选数据集
- 组内投票决定
- 下载并初步查看

Day 3-4: 数据Profiling
- 基础统计
- 缺失值分析
- 分布分析
- 类型检查

Day 5-7: 深度EDA
- 相关性分析
- 离群值检测
- Bias检测
- QQ Plot
- Simpson's Paradox探索
```

### Week 2（数据清洗 + 特征工程）
```
Day 1-2: 数据清洗
- 缺失值处理
- 离群值处理
- 重复值检查
- 数据验证

Day 3-4: 特征工程
- 编码
- 缩放
- 转换
- 交互特征
- 分箱

Day 5-7: 创建对比版本
- Minimal版本
- Full版本
- 记录所有决策
- 验证数据质量
```

### Week 3（建模 + Notebook撰写）
```
Day 1-3: 模型实验
- 训练简单模型
- 性能对比
- 特征重要性
- 错误分析
- Fairness评估

Day 4-7: Notebook撰写
- 整理所有代码
- 添加Markdown解释
- 创建可视化
- 完善文档
- 内部review
```

### Week 4（视频制作 + 提交）
```
Day 1-2: PPT制作
- 设计slides
- 精简内容
- 美化图表
- 排练脚本

Day 3-4: 视频录制
- 第一次录制
- Review并改进
- 第二次录制
- 最终版本

Day 5: 提交
- 上传YouTube
- 检查链接
- 提交Notebook
- 确认提交成功
- 准备peer evaluation
```

---

## 💎 加分技巧（从80分到95分+）

### 1. 数据集选择加分项
```
✨ 选一个有社会意义的数据集
   → 例：医疗公平、贷款歧视、就业bias
   
✨ 选一个有明显ethical concerns的
   → 容易展示bias分析深度
   
✨ 选一个有时间维度的
   → 可以做时间序列分析
```

### 2. 分析深度加分项
```
✨ 找到真实的Simpson's Paradox案例
   → 这是很少有人能做到的
   
✨ 用统计检验支持结论
   → t-test, chi-square, ANOVA
   
✨ 做消融实验（ablation study）
   → 逐个移除数据准备步骤，看影响
   
✨ 分析模型的decision boundary
   → 可视化模型学到了什么
```

### 3. 可视化加分项
```
✨ 交互式可视化（Plotly）
   → 但notebook里要能正常显示
   
✨ 创新的可视化方式
   → 不只是bar/line chart
   → Sankey diagram, TreeMap等
   
✨ Before/After对比动画
   → 用matplotlib animation
```

### 4. 洞察深度加分项
```
✨ 连接到现实世界影响
   → "这个bias会导致XX群体被拒贷"
   
✨ 提出可行的改进建议
   → "建议收集XX数据来减少偏差"
   
✨ 讨论ethical implications
   → "虽然性能提升了，但公平性下降了"
   
✨ 引用学术文献
   → 支持你的数据准备决策
```

### 5. 演示技巧加分项
```
✨ 讲一个完整的故事
   → 有起承转合，不是罗列结果
   
✨ 用类比帮助理解
   → "Simpson's Paradox就像..."
   
✨ 展示失败案例
   → "我们最初尝试了XX，但失败了，因为..."
   
✨ 提问互动（如果是live）
   → "大家觉得这个离群值应该保留还是删除？"
```

---

## ⚠️ 常见陷阱与避免方法

### 陷阱1：追求模型准确率
```
❌ 错误做法：
"我们调参到了98%准确率！"

✅ 正确做法：
"通过合理的数据准备，我们使准确率从75%提升到82%。
这7%的提升主要来自于[具体的数据准备步骤]，
证明了[数据准备原则]的重要性。"
```

### 陷阱2：使用复杂模型
```
❌ 错误做法：
使用XGBoost, Random Forest等

✅ 正确做法：
只使用Logistic Regression, Linear Regression, Decision Tree
明确说明："我们刻意使用简单模型，因为重点是数据而非算法"
```

### 陷阱3：没有justify决策
```
❌ 错误做法：
"我们用中位数填补了缺失值"

✅ 正确做法：
"我们用中位数而非均值填补缺失值，原因是：
1. 数据有离群值，中位数更鲁棒
2. 特征分布偏态，中位数更能代表中心趋势
3. 对比实验显示中位数填补效果更好（AUC提升0.03）"
```

### 陷阱4：忽略bias分析
```
❌ 错误做法：
只做技术分析，不谈伦理

✅ 正确做法：
专门一个section分析bias
展示不同群体的差异
讨论公平性trade-off
提出缓解策略
```

### 陷阱5：PPT过于密集
```
❌ 错误做法：
一页PPT放3个图+大段文字

✅ 正确做法：
一页PPT一个重点
大字体大图表
用口头解释细节
```

### 陷阱6：时间分配不当
```
❌ 错误做法：
前8分钟介绍数据，后4分钟匆忙讲模型

✅ 正确做法：
严格按照时间分配
每个部分都重要
提前排练计时
```

### 陷阱7：分工不清
```
❌ 错误做法：
peer evaluation时说不清谁做了什么

✅ 正确做法：
在notebook和视频里明确标注
"这部分由XX完成"
保留工作日志
```

---

## 🏆 标杆示例（想象中的满分作业）

### 项目：Healthcare Bias in Diabetes Prediction

**为什么是满分：**

1. **数据集选择（10/10）**
   - 医疗数据，有社会意义
   - 包含种族、性别等敏感特征
   - 明显的类别不平衡（糖尿病患者<10%）
   - 有缺失值、离群值等问题

2. **EDA深度（10/10）**
   - 发现了Simpson's Paradox：整体上feature X与糖尿病正相关，但分种族看是负相关
   - 识别了sampling bias：某些种族群体严重underrepresented
   - 用QQ Plot展示了血糖值的非正态分布
   - 检测到年龄-BMI的multicollinearity（VIF>10）

3. **数据准备（10/10）**
   - 缺失值：用MICE而非简单填补，并解释为什么
   - 离群值：保留极高血糖值（真实病例），删除年龄>120（错误数据）
   - 创建了BMI categories, age groups等领域知识特征
   - 对偏态特征做了Box-Cox转换，展示了QQ plot改善

4. **Bias缓解（10/10）**
   - 量化了不同种族的误诊率差异（高达15%）
   - 使用重采样使各种族样本平衡
   - 对比了公平性指标：Demographic Parity, Equal Opportunity
   - 讨论了accuracy-fairness trade-off

5. **模型对比（10/10）**
   - Minimal版本：只删除空行 → Accuracy 0.80, AUC 0.82
   - Full版本：完整准备 → Accuracy 0.86, AUC 0.91
   - 做了消融实验：逐步添加数据准备步骤，看增益
   - 分析了哪个步骤贡献最大（特征工程 +0.08 AUC）

6. **洞察深度（10/10）**
   - 发现高BMI患者被over-diagnosed，低收入患者被under-diagnosed
   - 解释了为什么：数据收集bias（医院主要在富裕社区）
   - 提出改进：需要收集更多低收入社区数据
   - 伦理讨论：模型可能加剧医疗不平等

7. **演示质量（10/10）**
   - 开场用病人故事引入
   - PPT极简，每页一个重点
   - 展示了一个震撼的可视化：同样症状的黑人和白人预测概率差异
   - 11分58秒，完美利用时间
   - 所有成员表达清晰，过渡自然

8. **Notebook质量（10/10）**
   - 结构清晰，像一本教科书
   - 每个决策都有详细解释和证据
   - 代码优雅，注释充分
   - Markdown写得像论文
   - 所有图表都能复现

9. **原创性（10/10）**
   - 自己设计了一个"Fairness Score"
   - 创新地可视化了bias propagation
   - 引用了相关医疗公平性文献
   - 提出了数据收集改进方案

**总分：95/100**（扣5分因为...总得找点小瑕疵吧😄）

---

## 📚 推荐资源

### 数据集网站（按推荐度排序）
```
1. ⭐⭐⭐⭐⭐ Kaggle
   - 数据质量高，文档完整
   - 有现成的kernel可以参考
   - 推荐datasets：
     * Credit Card Fraud
     * Adult Income
     * Heart Disease

2. ⭐⭐⭐⭐ UCI ML Repository
   - 经典数据集，有论文支持
   - 推荐：Adult, German Credit, COMPAS

3. ⭐⭐⭐⭐ Data.gov.sg
   - 本地数据，有现实意义
   - 推荐：HDB Resale, Healthcare

4. ⭐⭐⭐ Our World in Data
   - 社会问题数据，有故事性
   - 推荐：COVID, Inequality, Education
```

### 学习资源
```
EDA & Visualization:
- Seaborn Gallery: https://seaborn.pydata.org/examples/index.html
- Matplotlib Tutorials: https://matplotlib.org/stable/tutorials/index.html

Statistics:
- Simpson's Paradox: https://en.wikipedia.org/wiki/Simpson%27s_paradox
- Statistical Tests: https://www.statsmodels.org/

Fairness in ML:
- Fairlearn: https://fairlearn.org/
- AI Fairness 360: https://aif360.mybluemix.net/

Presentation Skills:
- TED Talk tips: https://www.ted.com/playlists/574/how_to_make_a_great_presentation
```

---

## 🎉 最后的鼓励

```
记住：

1. 这不是一个比拼模型准确率的作业
   → 你的洞察和解释比数字更重要

2. 教授想看到的是你的思考过程
   → 展示你如何做决策，而非完美结果

3. Bias和公平性是加分重点
   → 这是AI Ethics的核心，多花时间在这上面

4. 团队协作很重要
   → 分工明确，互相review，共同进步

5. 提前开始，避免deadline压力
   → Week 1就要选好数据集！

6. 享受这个过程
   → 你在学习AI从业者最重要的技能之一

Good luck! 你们一定能拿高分！💪
```

---

## 附录：快速参考

### 评分分布提醒
- Appropriateness (25%): 方法选择是否合适
- Correctness (25%): 技术正确性+表达清晰度
- Interpretation (25%): 分析判断力（识别谬误）
- Novelty (25%): 原创性和深度洞察

### 禁止使用的模型
❌ Random Forest
❌ XGBoost / LightGBM
❌ Neural Networks
❌ SVM (复杂核函数)
❌ Ensemble methods

### 允许使用的模型
✅ Logistic Regression
✅ Linear Regression
✅ Decision Tree (深度≤5)

### Deadline
- Video + Notebook: Week 5 (Feb 8, 12:00)
- Peer Evaluation: Week 6 (Feb 14, 12:00)

### 提交清单
□ YouTube公开链接（标题含组号）
□ .ipynb文件（文件名含组号）
□ 视频≤12分钟
□ 所有成员出镜
□ 代码可运行
