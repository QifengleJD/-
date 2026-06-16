# 电商用户价值分层：从传统 RFM 到 RFM-I 增强模型

基于电商用户行为数据（1000 用户 × 14 特征），在统一 Min-Max 归一化体系下构建传统 RFM 基线模型，通过数据洞察驱动模型改进，最终构建 RFM-I 增强模型，并通过 ROI 对比验证改进效果。

## 项目背景

传统 RFM 模型存在两个关键盲区：
- **盲区一**：无法识别"逛而不买"的高意向潜力用户——他们停留时间长、浏览页面多，但 RFM 只看交易结果，将其归为低价值
- **盲区二**：一刀切看待消费金额——同样消费 1000 元，月薪 5 万和月薪 5 千的用户价值背景完全不同

本项目通过引入行为数据维度修正传统 RFM，让每一分营销预算花在"最需要推一把"的人身上。

## 核心方法论

| 阶段 | 内容 | 关键决策 |
|------|------|---------|
| EDA | 用户画像 + 行为分析 + 相关性矩阵 | 发现"逛≠买"、"有钱≠花"两个核心洞察 |
| 实验 | 评分方法 × 权重方案 × I 指标集成 | 多组对照实验选出最优组合 |
| 基线 | 传统 RFM 8 类分层 | 为改进提供对比基准 |
| 缺陷诊断 | 量化三个盲区用户规模 | 每个改进方向有数据支撑 |
| 增强 | RFM-I 15 类分层 | 新识别 7 个独特群体 |
| 验证 | ROI 对比 + 敏感性分析 | 四种场景下结论稳健 |

## 核心创新

- **I 指标（意向度）**：用停留时长 + 浏览页数识别"想买但没买"的潜伏用户
- **Friction 指标（转化摩擦度）**：量化"看很多页才买一次"的纠结程度
- **L 指标（行为忠诚度）**：从"是否订阅"升级到"实际行为"衡量忠诚
- **D 维度（购买力背景）**：基于收入水平修正消费价值判断
- **ROI 闭环验证**：边际增量思维 + 敏感性分析，量化改进效果

## 项目结构

```
├── user_personalized_features.csv          # 数据集（1000用户 × 14特征）
├── 电商用户价值分层_RFM到RFM-I_完整项目.py  # 完整项目脚本
├── 电商用户价值分层_RFM到RFM-I.ipynb        # 主分析 Notebook
├── 电商用户价值分层_RFM到RFM-I_分析报告.ipynb # 分析报告 Notebook
├── RFM评分方法与权重方案实验.ipynb           # 评分方法与权重实验
├── rfm_analysis/                           # 可视化输出
│   ├── correlation_matrix.png              # 特征相关性矩阵
│   ├── eda_distributions.png               # EDA 分布图
│   ├── segment_distribution.png            # 用户分层分布
│   ├── segment_radar.png                   # 群体雷达图
│   └── roi_comparison.png                  # ROI 对比图
├── RFM-1/                                  # RFM-1 增强模型
│   ├── RFM-1模型.ipynb
│   └── RFM-1模型.docx
└── 电商平台用户行为分析与 RFM 价值分层体系搭建.doc  # 项目文档
```

## 数据字段

| 类别 | 字段 |
|------|------|
| 用户属性 | Age, Gender, Location, Income, Interests |
| 行为数据 | Last_Login_Days_Ago, Time_Spent_on_Site_Minutes, Pages_Viewed, Newsletter_Subscription |
| 消费数据 | Purchase_Frequency, Average_Order_Value, Total_Spending, Product_Category_Preference |

## 环境依赖

- Python 3.8+
- pandas / numpy
- matplotlib / seaborn
- scipy

## 快速开始

```bash
# 安装依赖
pip install pandas numpy matplotlib seaborn scipy

# 运行完整项目脚本
python 电商用户价值分层_RFM到RFM-I.ipynb
```

或者按顺序运行 Jupyter Notebook：
1. `RFM评分方法与权重方案实验.ipynb` — 确定评分方法、权重和 I 指标集成方式
2. `电商用户价值分层_RFM到RFM-I.ipynb` — 主分析流程
3. `电商用户价值分层_RFM到RFM-I_分析报告.ipynb` — 完整分析报告

## 运营策略输出

RFM-I 将用户分为 15 类，每类对应差异化运营策略：

| 优先级 | 群体 | 策略方向 |
|--------|------|---------|
| S | 核心VIP、重要价值用户 | VIP 专属服务、交叉销售 |
| A | 纠结土豪、高潜沉睡/流失用户 | 精准推荐、限时大促唤醒 |
| B | 犹豫型潜力用户、隐形活跃者 | 降低决策门槛、社交裂变 |
| C-E | 一般/低价值用户 | 低成本自动化运营 |

## License

MIT
