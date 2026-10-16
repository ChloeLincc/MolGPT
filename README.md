# MolGPT：基于 GPT-2 的分子生成

使用 GPT-2 架构的 Transformer 模型进行分子生成。

---

## 生成结果展示

### Top 16 分子（按 QED 排序）

![Top 16](results/p2_top16_molecules.png)

### 完整分子库（61 个有效分子）

![完整分子库](results/p2_all_molecules_grid.png)

### 3D 分子构象

![3D 构象](results/p2_molecules_3d_grid.png)

---

## 结果统计

| 指标 | 数值 |
|------|------|
| 生成分子数 | 100 |
| 有效分子数 | 61 |
| 有效比例 | 61% |
| 最高 QED | **0.929** |
| Top 16 平均 QED | **0.865** |

---

## 示例分子

| # | SMILES | QED | logP | MW |
|---|--------|-----|------|-----|
| 1 | `c1oc(=O)c(NCc2ccccc2)cc1C(F)(F)F` | 0.929 | 2.34 | 278.2 |
| 2 | `c1ccc(Nc2ncnc(N3CCOCC3)n2)cc1F` | 0.917 | 2.08 | 320.3 |
| 3 | `c1ccccc1NS(=O)(=O)c1cccs1` | 0.894 | 1.76 | 280.3 |
| 4 | `N(Cc1ccccc1)C(=O)c1ccccc1Cl` | 0.884 | 2.91 | 258.7 |
| 5 | `c1ccc(Oc2ccc(O)cc2O)c(C(F)(F)F)n1` | 0.879 | 3.24 | 298.2 |

---

## 模型配置

| 参数 | 值 |
|------|-----|
| Transformer 层数 | 4 |
| 隐藏层维度 | 512 |
| 注意力头数 | 8 |
| 参数量 | 12.7M |
| 训练数据 | 20,000 分子 |
| 训练轮数 | 20 epoch |

---

## 项目结构
```
MolGPT/
├── generation/ # 核心模块
│ ├── data_utils.py # 数据加载
│ ├── molgpt_dataset.py # 数据集 & 词汇表
│ ├── molgpt_model.py # GPT-2 模型定义
│ └── molgpt_trainer.py # 训练器
├── results/ # 生成结果
│ ├── p2_generated_molecules.csv # 分子数据
│ ├── p2_top16_molecules.png # Top 16 分子图
│ ├── p2_all_molecules_grid.png # 完整分子库
│ └── p2_molecules_3d_grid.png # 3D 构象
├── p2_train_molgpt.py # 训练入口
├── visualize_p2_3d.py # 3D 可视化
└── visualize_p2_molecules.py # 2D 可视化
```

---

## 快速开始
### 环境配置
```bash
python3.10 -m venv molgpt_env
source molgpt_env/bin/activate
pip install -r requirements.txt
```

### 训练模型
```bash
python p2_train_molgpt.py --data_path /path/to/data.csv --sample_size 20000
```

### 生成分子并可视化
```bash
python visualize_p2_molecules.py
python visualize_p2_3d.py
```
