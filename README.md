# handonML
手写机器学习的练习仓库，围绕传统机器学习工具链展开，聚焦数据预处理、建模、评估与调优流程，力求将每一步的关键逻辑以精炼、教科书式的形式保留在笔记与脚本中。

---

## 一、项目目标
1. 完整梳理传统机器学习的预处理到评估流程，涵盖缺失值处理、特征工程、流水线搭建、模型训练与性能审视；
2. 以 UCI Adult、California Housing、MNIST 等公开数据集为练习对象，对比不同模型与调参手段的效果；
3. 将每日学习笔记（notebooks）与可复现脚本（scripts/ML）保持一致，便于复盘与复现。

---

## 二、目录结构
```
├── images/                # 训练/可视化示意图（如 sklearn 模型导航 ml_map.svg）
├── notebooks/             # 每日实验的 Jupyter 笔记，记录数据探索、建模与评估
│   ├── day1-2.ipynb
│   ├── day3-4.ipynb
│   ├── day5-6.ipynb
│   └── day7.ipynb
├── scripts/               # 可直接运行的流水线脚本
│   └── ML/
│       ├── day1-2.py
│       ├── day3-4.py
│       └── day7.py
├── LICENSE
├── README.md              # 本文件
```

---

## 三、笔记与脚本速览

- `day1-2`：UCI Adult 二分类——缺失值填充、分类特征独热编码、数值特征标准化，逻辑回归基线模型；`scripts/ML/day1-2.py` 为可直接运行的等价流水线。
- `day3-4`：California Housing 回归——ColumnTransformer 组合 PowerTransformer、标准化与 OneHot 编码，模型为 XGBoost 回归；使用随机搜索在测试集上校验 R² 表现，脚本为 `scripts/ML/day3-4.py`。
- `day5-6`：MNIST 手写数字的无监督学习——PCA 降维、KMeans/GMM/SpectralClustering 聚类，并用 t-SNE/PCA 可视化簇结构；notebook 记录评估指标（如 v-measure、ARI、silhouette）。
- `day7`：支持向量机对比实验——在 Adult 与 California Housing 上分别构建 SVC/SVR，与逻辑回归、XGBoost 进行效果对照；脚本 `scripts/ML/day7.py` 展示 SVR + 随机搜索的回归流水线。

每个 notebook 着重数据处理思路、参数选择与评估要点；`scripts/ML` 提供精炼、可复现的终端运行版本。

---

## 四、数据要求
所有脚本与笔记默认向上查找 `../data` 下相应子目录：

| 数据集 | 说明 | 路径示例 |
|--------|------|----------|
| Adult | 分类任务，需含 `X.csv` 与 `y.csv` | `data/Adult/X.csv`、`data/Adult/y.csv` |
| California Housing | 回归任务，需含 `housing.csv` | `data/California/housing.csv` |

本仓库不包含上述数据，运行前请根据原始 UCI/公开数据源自行下载并放置于上述路径，保证脚本中的相对路径能正确访问。

---

## 五、使用指南
1. 安装依赖（推荐在虚拟环境中）：
   ```bash
   pip install pandas numpy scikit-learn xgboost scipy
   ```
2. 运行脚本：以 day1-2 为例
   ```bash
   python scripts/ML/day1-2.py
   ```
3. 如果希望复现 notebook 中的探索过程，可直接在 `notebooks/` 中逐日执行，必要时参考脚本中更为精炼的流水线配置。

---

## 六、持续方向
该仓库仅包含传统机器学习部分，关于深度学习的学习与实践另存于 `handonDL`。在继续学习时，可将 multi-day notebook 中的经验迁移至其他模型（例如 transformer 微调或强化学习）以搭建完整的知识体系。
