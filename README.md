# 🔋 电池衰减与使用场景数据仓库

<p align="center">
  <img alt="status" src="https://img.shields.io/badge/Status-Data%20Ready-2ea44f">
  <img alt="theme" src="https://img.shields.io/badge/Theme-Battery%20Health-1f6feb">
  <img alt="mood" src="https://img.shields.io/badge/Mood-稳中带梗-f59e0b">
</p>

> 这个仓库主要用于 MCM/ICM 相关建模数据整理：
> 一边研究电池怎么“优雅变老”，一边观察人类如何把手机“高强度服役”。

---

## ✨ 项目亮点

- 数据来源覆盖 **内因**（电芯老化机制）与 **外因**（真实使用行为）
- 同时包含 `.mat` 与 `.csv` 两类常见建模数据格式
- 文件结构分区明确，适合快速上手做 EDA / 特征工程 / 寿命预测
- 轻量、直给、可复现：主打一个“打开就能干活”

---

## 🧭 目录导航

```text
.
├── 2026_MCM-ICM_Problems/
│   └── 2026_MCM-ICM_Problems/
│       ├── 2026_MCM_Problem_C_Data.csv
│       └── MCM-ICM_Summary.tex
├── 内因（电池寿命衰减）/
│   ├── BIT_Nature_degradation_voltage_capacity_long.csv
│   └── 5.+Battery+Data+Set/
│       └── 5. Battery Data Set/
│           ├── 1. BatteryAgingARC-FY08Q4/
│           ├── 2. BatteryAgingARC_25_26_27_28_P1/
│           ├── 3. BatteryAgingARC_25-44/
│           ├── 4. BatteryAgingARC_45_46_47_48/
│           ├── 5. BatteryAgingARC_49_50_51_52/
│           └── 6. BatteryAgingARC_53_54_55_56/
└── 外因（人为使用手机、不同场景）/
    ├── Figure4_data_combined_Xiaomi_Samsung.csv
    ├── MCM_A_clean_static_app_usage.csv
    ├── Dynamic_Selected_Samples_Clean_1min/
    └── MCM_A_clean_battery_timeseries_split_by_imei/
```

---

## 📦 数据分区说明

### 1) 内因：电池寿命衰减

重点关注电池在循环过程中的容量衰减、电压变化等物理特征：

- NASA ARC 系列 `.mat` 数据：适合做 SOH/RUL 建模
- 长表格式衰减数据 `.csv`：适合统计分析与可视化

适合任务：

- 容量衰减曲线拟合
- 退化阶段识别
- 剩余寿命（RUL）预测

### 2) 外因：人为使用与场景差异

重点关注真实手机使用环境中，行为模式对耗电与衰减的影响：

- 静态 App 使用画像
- 1 分钟粒度放电时序样本
- 按设备 IMEI 拆分的电池时序

适合任务：

- 使用行为聚类
- 场景化耗电建模
- 跨用户泛化分析

---

## 🚀 快速开始

### Step 1. 准备环境

推荐 Python 3.10+，并安装常用数据分析库：

```bash
pip install pandas numpy scipy matplotlib seaborn scikit-learn
```

### Step 2. 读取示例数据

```python
import pandas as pd

df = pd.read_csv("外因（人为使用手机、不同场景）/MCM_A_clean_static_app_usage.csv")
print(df.head())
```

### Step 3. 开始你的建模流程

你可以从这三件事开始：

1. 数据清洗与字段标准化
2. 构建特征（循环特征 / 使用行为特征）
3. 建立基线模型（回归、时序模型、树模型）

---

## 🧪 建议分析路线

- 路线 A（稳健型）：先做外因统计分析，再和内因数据做关联验证
- 路线 B（模型型）：直接做 RUL 预测，后续加入外因特征看增益
- 路线 C（竞赛型）：先跑可解释基线，再迭代复杂模型

一句话总结：

> 先让模型跑起来，再让模型跑得更明白。

---

## 😄 适度玩梗区

- 电池：我还能再撑一会儿。  
  你：导航+视频+热点+游戏同时开。  
  电池：……

- 建模人日常：
  - 上午：这个特征一定有用
  - 下午：这个特征怎么还不如随机数
  - 晚上：先加进来再说（不是）

- 当你看到容量曲线突然“反弹”时：
  > 恭喜你，遇到了数据世界的“量子电池”。

---

## 📌 注意事项

- 部分数据集体量较大，建议按需加载
- `.mat` 文件可用 `scipy.io.loadmat` 或 `h5py`（视文件版本而定）
- 建议统一时间字段与单位（分钟、循环次数、容量单位）

---

## 🤝 使用建议

如果你用于 MCM/ICM 建模，推荐输出至少包括：

- 数据预处理流程图
- 特征重要性/敏感性分析
- 模型误差与泛化能力对比

这样评委一看就知道：

你不只是“把模型跑通了”，你是“把问题讲明白了”。

---

## 📮 维护说明

当前仓库以数据组织与建模支持为主，后续可继续补充：

- 字段字典（Data Dictionary）
- 标准化预处理脚本
- 基线模型与可复现实验配置

欢迎后续迭代，把这个仓库打造成“电池研究快乐老家”。
