
# 🛠️ Predictive Maintenance Analysis (设备预测性维护分析)

本项目基于工业传感器数据，构建机器学习模型以预测设备是否即将发生故障。目标是实现“预测性维护”，在故障发生前发出预警，从而减少停机时间、降低维修成本。

## 📊 数据集说明
- 包含日期、设备ID、9个传感器指标（metric1~metric9）、故障标签（failure: 0=正常, 1=故障）
- 数据严重不平衡：正常样本约12.4万条，故障样本仅106条（比例 ~1173:1）

## 🔍 主要工作
- 探索性数据分析（EDA）：分布可视化、异常值检测
- 特征工程：
  - 时间特征提取（年/月/日/星期/是否周末）
  - 类别编码（设备ID → 数值）
- 多模型对比：
  - Logistic Regression, KNN, Random Forest, Decision Tree, LightGBM, XGBoost, SVM
  - 所有模型均设置 `class_weight='balanced'` 应对不平衡问题
- 评估重点：**召回率（Recall）** —— 宁可误报，不可漏报！

## 📈 当前结果（测试集）
| 模型             | Recall (故障识别率) |
|------------------|---------------------|
| Logistic Regression | 0.56                |
| Decision Tree       | 0.56                |
| LightGBM            | 0.17                |
| 其他模型            | 0.00                |

> ⚠️ 注意：由于正样本极少（测试集仅18个），准确率高达96%+具有欺骗性，实际价值取决于能否抓住那少数几个故障点。

## 🚀 后续优化方向
- 使用 SMOTE 过采样或欠采样平衡训练集
- 调整分类阈值（如从0.5降至0.3）提升召回率
- 构造滑动窗口统计特征（均值、标准差等）捕捉趋势变化
- 引入 PR Curve / Confusion Matrix 更直观评估性能

## 📁 文件结构
```text
predictive_maintenance_dataset_0323.ipynb # 主分析 notebook
requirements.txt # 依赖包列表
README.md # 本文件
```  


## 💡 适用场景
- 工业物联网（IIoT）
- 智能制造
- 设备健康管理（PHM）
- 大数据分析师 / 预测性维护工程师求职作品集

---

📌 **作者**: tianzhensheng  
📅 最后更新: 2025-03-09  
📄 License: MIT