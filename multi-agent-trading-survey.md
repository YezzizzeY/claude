# 基于多智能体（Multi-Agent）的交易系统：文献综述与开放问题

> 检索时间：2026-09-26。覆盖范围：经典已发表工作（1993–2022）、LLM 多智能体交易（2023–2025）、2026 年以来的最新论文（截至 2026-09）。
>
> **可信度说明**：所有条目均通过网络搜索确认过标题与出处（arXiv ID / 会议 / 期刊）。由于检索环境无法直接打开 arXiv 全文，部分作者列表、实验细节和 "局限" 一栏来自摘要或搜索摘要，属于"作者声明或从实验设置可见"的归纳，而非原文逐字引用。标注 **[待核实]** 的条目请在正式引用前到 arxiv.org / 出版方页面二次确认。

---

## 目录

1. [经典工作（1993–2022）](#1-经典工作19932022)
   - 1.1 基于智能体的市场仿真（ABM）
   - 1.2 多智能体强化学习（MARL）交易 / 做市 / 执行
   - 1.3 多智能体 / 分层 / 集成组合管理
   - 1.4 交易智能体竞赛（TAC）与连续双向拍卖
2. [LLM 多智能体交易（2023–2025）](#2-llm-多智能体交易20232025)
   - 2.1 交易与组合框架
   - 2.2 选股、因子挖掘与投研智能体
   - 2.3 LLM 智能体市场仿真
   - 2.4 基准、实盘竞技场与批判性评测
3. [2026 年以来的论文](#3-2026-年以来的论文)
   - 3.1 LLM 多智能体交易 / 组合框架
   - 3.2 基准、评估方法与生产环境证据
   - 3.3 安全与鲁棒性
   - 3.4 LLM 智能体市场仿真
   - 3.5 MARL 与学习型智能体
   - 3.6 2026 年综述 / SoK
4. [仍存在的 Research Problems](#4-仍存在的-research-problems)

---

## 1. 经典工作（1993–2022）

### 1.1 基于智能体的市场仿真（Agent-Based Market Simulation）

| 年份 | 论文 | 出处 | 贡献 | 主要局限 |
|---|---|---|---|---|
| 1993 | Gode & Sunder, *Allocative Efficiency of Markets with Zero-Intelligence Traders* | J. Political Economy 101(1) | 预算约束下的随机 "ZI-C" 交易者在双向拍卖中即可达到接近人类的配置效率 —— 市场结构本身承担了大部分"理性" | 只研究配置效率，不学习，实验室式简单市场 |
| 1994 | Palmer, Arthur, Holland, LeBaron, Tayler, *Artificial Economic Life: A Simple Model of a Stockmarket* | Physica D 75 | 圣塔菲人工股票市场（SF-ASM）：GA 演化预测规则，出现泡沫、崩盘与波动聚集 | 单一风险资产、做市商式出清、结果对参数敏感 |
| 1997 | Arthur et al., *Asset Pricing Under Endogenous Expectations in an Artificial Stock Market* | *The Economy as an Evolving Complex System II*; SSRN 2252 | 异质、归纳式预期下的资产定价，解释技术交易与波动聚集 | 依赖 GA 探索率，难以标定与验证 |
| 1997 | Cliff, *Minimal-Intelligence Agents for Bargaining Behaviors (ZIP)* | HP Labs TR HPL-97-91 | ZIP 交易者：简单自适应利润率即可实现类人均衡 | 技术报告；只在程式化双向拍卖中测试 |
| 1999 | Lux & Marchesi, *Scaling and Criticality in a Stochastic Multi-Agent Model of a Financial Market* | Nature 397 | 基本面 / 图表派切换模型，复现肥尾与波动聚集 | 规则型、无学习；仅部分参数区间成立 |
| 2001 | Raberto et al., *Agent-Based Simulation of a Financial Market (Genoa ASM)* | Physica A 299; arXiv cond-mat/0103600 | 现金守恒 + 真实出清机制 | 随机交易者，单资产 |
| 2002 | Chiarella & Iori, *A Simulation Analysis of the Microstructure of Double Auction Markets* | Quantitative Finance 2(5) | 限价订单簿 ABM，研究价差、深度、tick size | 交易规则外生、无适应 |
| 2005 | Farmer, Patelli, Zovko, *The Predictive Power of Zero Intelligence in Financial Markets* | PNAS 102(6) | 零智能订单流模型拟合 LSE，单参数解释 ~96% 价差方差 | 订单流外生（泊松），忽略策略行为 |
| 2006 | LeBaron, *Agent-Based Computational Finance* | Handbook of Computational Economics Vol. 2 | 该领域的标准综述 | 指出验证、标定、设计自由度过多等开放问题 |
| 2013 | Wah & Wellman, *Latency Arbitrage, Market Fragmentation, and Efficiency* | ACM EC '13 | 双交易所 ABM：延迟套利降低总剩余，周期性集合竞价可消除 | 单证券、背景交易者为固定 ZI 策略 |
| 2015 | Masad & Kazil, *Mesa: An Agent-Based Modeling Framework* | SciPy 2015 | 通用 Python ABM 框架，常用于市场模型 | 无金融 / 订单簿组件，规模受 Python 性能限制 |
| 2019 | Byrd, Hybinette, Balch, *ABIDES: Towards High-Fidelity Market Simulation for AI Research* | arXiv 1904.12066（后发表于 SIGSIM-PADS 2020） | 基于离散事件与 NASDAQ ITCH/OUCH 协议的高保真仿真器，支持上万智能体 | 背景智能体手工设计，逼真度验证仍是开放问题 |
| 2019 | Byrd, *Explaining Agent-Based Financial Market Simulation* | arXiv 1909.11650 | ABIDES 设计的教程式说明 | 非实证 |
| 2020 | Vyetrenko et al., *Get Real: Realism Metrics for Robust Limit Order Book Market Simulations* | ICAIF '20; arXiv 1912.04941 | 订单簿仿真"逼真度"典型事实指标体系 | 作者自述仿真与真实市场仍有较大差距 |
| 2020 | Maeda et al., *Deep Reinforcement Learning in Agent Based Financial Market Simulation* | J. Risk & Financial Mgmt 13(4) | 在 ABM 人工市场中训练 DRL，使市场冲击可见 | 人工市场程式化，迁移性存疑 |
| 2021 | Lussange et al., *Modelling Stock Markets by Multi-agent Reinforcement Learning* | Computational Economics 57 | 所有智能体都用 RL 学习，并用 LSE 2007–2018 数据标定 | 简单 RL、单资产，只标定部分微观结构指标 |
| 2021 | Amrouni et al., *ABIDES-Gym* | ICAIF '21; arXiv 2110.14771 | 将 ABIDES 封装为 Gym 环境（JPMorgan） | 单学习者 vs 固定背景智能体 |
| 2021 | Coletta et al., *Towards Realistic Market Simulations: a GAN Approach* | ICAIF '21; arXiv 2110.13287 | 用条件 GAN "世界智能体" 替代手工背景智能体 | 历史数据有限；逼真度仍仅用典型事实评估 |

### 1.2 多智能体强化学习（MARL）：交易、做市、执行

| 年份 | 论文 | 出处 | 贡献 | 主要局限 |
|---|---|---|---|---|
| 2007 | Lee et al., *A Multiagent Approach to Q-Learning for Daily Stock Trading (MQ-Trader)* | IEEE Trans. SMC-A 37(6) | 买入信号 / 买单 / 卖出信号 / 卖单四个协作 Q-learning 智能体 | 手工特征、仅韩国市场日频 |
| 2018 | Patel, *Optimizing Market Making using Multi-Agent RL* | arXiv 1812.10252 | 宏观（方向）+ 微观（挂单）双层 MARL 做市 | 仅比特币，简化成交模型 |
| 2019 | Bao & Liu, *Multi-Agent Deep RL for Liquidation Strategy Analysis* | arXiv 1906.11046（ICML'19 AI in Finance WS） | Almgren–Chriss 清算扩展到多智能体，研究合作 / 竞争奖励 | 基于程式化冲击模型 |
| 2019 | Ganesh et al., *RL for Market Making in a Multi-agent Dealer Market* | arXiv 1911.05892（NeurIPS'19 WS，JPMorgan） | 多交易商 OTC 市场中 RL 做市商学习对手定价与库存管理 | 竞争者策略固定，并非完全 MARL |
| 2019 | Buehler et al., *Deep Hedging* | Quantitative Finance 19(8) | 摩擦条件下的深度对冲（后续 MARL 对冲的基础） | 单智能体、依赖市场生成器 |
| 2020 | Spooner & Savani, *Robust Market Making via Adversarial RL* | IJCAI-20 | 做市商与对手的零和博弈，得到对模型误设鲁棒的策略 | 对手控制参数少、程式化模型 |
| 2020 | Karpe et al., *Multi-Agent RL in a Realistic Limit Order Book Market Simulation* | ICAIF '20; arXiv 2006.05574 | 在 ABIDES 历史订单簿仿真中训练 DDQN 执行智能体 | 学习智能体少、资产与日期窄 |
| 2021 | Ardon et al., *Towards a Fully RL-based Market Simulator* | ICAIF '21; arXiv 2110.06829 | 流动性提供者 / 需求者群体同时学习（共享策略） | 程式化交易商市场 |
| 2022 | Vadori et al., *Towards MARL driven Over-The-Counter Market Simulations* | arXiv 2210.07184 | 外汇式 OTC 博弈，奖励族 + 共享策略产生涌现行为并标定 | 设计空间受限 |
| 2022 | Shavandi & Khedmati, *A Multi-Agent Deep RL Framework for Algorithmic Trading* | Expert Systems with Applications 208 | 多时间尺度分层 DQN，长周期向短周期传递知识 | 标的少、简化成本 |

### 1.3 多智能体 / 分层 / 集成组合管理

| 年份 | 论文 | 出处 | 贡献 | 主要局限 |
|---|---|---|---|---|
| 2019 | Wang et al., *AlphaStock* | KDD '19 | 跨资产注意力 RL 的多空选股（常用基线） | 单策略，并非真正多智能体 |
| 2020 | Yang et al., *Deep RL for Automated Stock Trading: An Ensemble Strategy* | ICAIF '20 | PPO / A2C / DDPG 按滚动 Sharpe 切换 | 事后选择易回测过拟合，仅 Dow 30 |
| 2020 | Lee et al., *MAPS: Multi-Agent RL-based Portfolio Management System* | IJCAI-20 | 多"投资者"智能体 + 多样性损失，实现组合分散 | 离散动作、成本与冲击简化 |
| 2020 | Liu et al., *FinRL* | arXiv 2011.09607（NeurIPS'20 WS） | 开源 DRL 交易库 | 历史回放，无市场冲击 |
| 2021 | Wang et al., *Commission Fee is not Enough: HRPM* | AAAI-21 | 高层组合 + 低层执行的分层 RL，建模滑点 | 执行仍基于历史回放，训练成本高 |
| 2021 | Wang et al., *DeepTrader* | AAAI-21 | 资产打分（图网络）+ 市场打分（回撤奖励）控制多空比例 | 依赖估计的图结构，仅回测 |
| 2022 | Huang & Tanaka, *MSPM: A Modularized and Scalable Multi-Agent RL-based System for Portfolio Management* | PLOS ONE 17(2); arXiv 2102.03502 | 每资产 DQN 信号模块 + PPO 战略模块，模块化可扩展 | 资产池小、仅回测 |
| 2022 | Liu et al., *FinRL-Meta* | NeurIPS 2022 D&B; arXiv 2211.03107 | 数百个 Gym 式市场环境与基准（含多智能体环境） | 作者明确指出低信噪比、幸存者偏差、回测过拟合 |

### 1.4 交易智能体竞赛（TAC）与连续双向拍卖（CDA）

| 年份 | 论文 | 出处 | 贡献 | 主要局限 |
|---|---|---|---|---|
| 2001 | Wellman et al., *Designing the Market Game for a Trading Agent Competition* | IEEE Internet Computing 5(2) | TAC Classic（旅行套餐同时拍卖）基准设计 | 非金融市场，结论依赖规则 |
| 2001 | Das, Hanson, Kephart, Tesauro, *Agent-Human Interactions in the Continuous Double Auction* | IJCAI-01 | GD / ZIP 型智能体在 CDA 中稳定胜过人类 | 小样本实验；结论后被 De Luca & Cliff (2011) 部分质疑 |
| 2001 | Tesauro & Das, *High-Performance Bidding Agents for the Continuous Double Auction* | ACM EC '01 | 改进 GD 出价智能体，在多种规则下表现强 | 短文，程式化环境 |
| 2005 | Stone & Greenwald, *The First International Trading Agent Competition* | Electronic Commerce Research 5(2) | 总结 TAC-2000 智能体策略 | 场次少、方差大 |
| 2005 | Arunachalam & Sadeh, *The Supply Chain Trading Agent Competition (TAC SCM)* | ECRA 4(1) | 供应链谈判竞赛 | 规则漏洞影响早期比赛 |

**经典时期的共性局限**：仿真器逼真度与标定难（LeBaron 2006 即列为核心问题）；RL 组合方法普遍在历史回放上回测，无市场冲击；"多智能体"常只是单一决策者的协作模块，或"一个学习者 vs 固定对手"，很少研究共同学习下的稳定性 / 均衡；证据局限于单一市场、短周期。

---

## 2. LLM 多智能体交易（2023–2025）

标注：**[MAS]** 明确多智能体；**[单体/相关]** 单智能体但为常用基线或被广泛对比；**[Sim]** 市场仿真；**[Bench]** 基准 / 批判性评测。

### 2.1 交易与组合框架

| 论文 | 出处 | 架构 / 贡献 | 评测 | 局限 |
|---|---|---|---|---|
| **TradingAgents** (Xiao et al.) [MAS] | arXiv 2412.20138 (2024) | 模拟交易公司：基本面 / 情绪 / 新闻 / 技术分析师 + 多空研究员辩论 + 交易员 + 风控团队 + 基金经理 | 2024-01-01 至 03-29，AAPL、GOOGL、AMZN 等；Sharpe 约 5.6–8.2 | 约 3 个月、标的少、牛市；测试期在 LLM 训练窗口内；调用成本高 |
| **FinCon** (Yu et al.) [MAS] | NeurIPS 2024; arXiv 2407.06567 | 经理–分析师层级；"概念化语言强化"更新信念；CVaR 风控 | 训练 2022-01 至 10，测试 2022-10 至 2023-06；8 只股票 + 小组合 | 测试约 8 个月、存在泄漏风险、依赖 GPT-4 |
| **FinMem** (Yu et al.) [单体/相关] | arXiv 2311.13743; AAAI Symposium / IEEE TBD | 分层记忆（短 / 中 / 长期）+ 角色设定 | 测试 2022-10 至 2023-04，5 只股票 | FINSABER 显示长周期下优势消失 |
| **TradingGPT** (Li et al.) [MAS] | arXiv 2309.03736 (2023) | 多个分层记忆 + 不同风险性格的智能体辩论 | 以框架提出为主 | 定量证据少 |
| **FinAgent** (Zhang et al.) [单体/相关] | KDD 2024; arXiv 2402.18485 | 多模态（数字 / 文本 / K 线图）+ 双层反思 + 工具 | 2023-06 至 2024-01，6 个数据集 | 约 7 个月、标的窄 |
| **FinVision** (Fatemi & Hu) [MAS] | ICAIF 2024; arXiv 2411.08899 | 新闻、K 线视觉、反思三类智能体 | 3 只股票；AMZN 上未超越买入持有 | 标的极少，对 FinAgent 无明显优势 |
| **HedgeAgents** (Li et al.) [MAS] | WWW 2025 Companion; arXiv 2502.13165 | 基金经理 + 股票 / 外汇 / BTC 对冲专家，三类"会议"机制 | 3 年测试，年化 71.6% | 收益过高，疑似回测乐观 |
| **QuantAgents** (Li et al.) [MAS] | Findings of EMNLP 2025; arXiv 2510.04643 | 模拟交易分析师 + 风控 + 新闻 + 经理；真实盘与模拟双奖励 | 3 年约 300% | 成本与泄漏控制不明 |
| **TradingGroup** [MAS] | ICAIF 2025; arXiv 2508.17565 | 新闻 / 财报 / 趋势 / 风格 / 决策智能体 + 动态止盈止损 + 数据合成后训练 | 5 个股票数据集 | 合成数据后训练存在过拟合风险 |
| **ContestTrade** (Zhao et al.) [MAS] | arXiv 2508.00554 | 内部竞赛机制：持续给智能体打分，只采用排名靠前者的输出 | A 股 2025-01 至 06，Sharpe 3.12 | 6 个月、单市场 |
| **ATLAS** (Papadakis et al.) [MAS] | arXiv 2510.15949 | 分析师 + 中心交易员；Adaptive-OPRO 每 5 天优化提示词 | 7 个骨干模型、多市场状态；发现反思常常有害 | 窗口短，提示优化易过拟合 |
| **QuantAgent（高频）** (Xiong et al.) [MAS] | arXiv 2509.09995 | 仅用 OHLC 的指标 / 形态 / 趋势 / 风险智能体 | 10 个标的，1h / 4h；方向准确率约 48–64% | 接近随机、成本敏感、基线弱 |
| **QuantAgent（自改进）** (Wang et al.) [单体/相关] | arXiv 2402.03755 | 内外双循环自我改进的 alpha 挖掘 | 信号层面 | 组合层结果有限 |
| **FLAG-Trader** (Xiong et al.) [单体/相关] | Findings of ACL 2025 | LLM 作为策略网络 + PPO 微调 | InvestorBench 环境 | 按资产分别训练 |
| **TradExpert** (Ding et al.) [MAS] | ICLR 2025 FinAI WS; arXiv 2411.00782 | 新闻 / 行情 / 因子 / 基本面四专家 LLM 的混合专家 | 2023 年回测 | 1 年牛市、可能泄漏 |
| **MM-DREX** [MAS] | arXiv 2509.05080 | VLM 路由器按 K 线图给趋势 / 反转 / 突破等专家分配权重 | 股票 / 期货 / 加密 | 训练重，成本处理未确认 |
| **P1GPT** (Lu et al.) [MAS] | arXiv 2510.23032 | 分层多模态分析流水线 | 美股回测 | 样本小 |
| **TiMi: Trade in Minutes!** (Song et al., MSRA 等) [MAS] | arXiv 2510.04787; **ICLR 2026** | 不做角色扮演；LLM 负责策略开发，分钟级执行交给程序化机器人，并做"数学化反思" | 200 多个股指 / 加密交易对实盘 | 需离线仿真预热，流动性风险 |
| **ElliottAgents** (Chudziak & Wawer) [MAS] | PACLIC 2024 | 艾略特波浪 + RAG + DRL 回测 | 预测准确率 | 无风险调整指标，理论本身存争议 |

### 2.2 选股、因子挖掘与投研智能体

| 论文 | 出处 | 贡献 | 评测 / 局限 |
|---|---|---|---|
| **MarketSenseAI** (Fatouros et al.) [MAS] | arXiv 2401.03737；2.0 版 arXiv 2502.00415 | 新闻 / 基本面 / 价格 / 宏观 / 信号智能体 + SEC 文件 RAG | S&P 100，2023–24，累计 125.9% vs 指数 73.5%；AI 牛市、GPT-4 自评、可能有幸存者偏差 |
| **AlphaAgents** (BlackRock) [MAS] | arXiv 2508.11152 | 基本面 / 情绪 / 估值智能体辩论达成共识 | 约 15 只科技股、4 个月；作者自认是探索性工作 |
| **MASS** (Guo et al.) [MAS] | arXiv 2505.10278 | 将异质投资者智能体扩展到 512 个，观察到"规模效应" | 仅 A 股、约 2 年、推理成本高 |
| **Enhancing Investment Analysis** (Han et al.) [MAS] | ICAIF 2024; arXiv 2411.04788 | 研究智能体组规模与协作结构 | **简单任务上单智能体优于多智能体**；只评估分析质量，不评估 PnL |
| **FinRobot** (Yang et al.; Zhou et al.) [MAS] | arXiv 2405.14767; 2411.08804 | 开源金融智能体平台 / 股票研报生成 | 缺乏严格定量回测 |
| **Alpha-GPT / 2.0** (Wang et al.) | arXiv 2308.00016; 2402.09746 | 人机交互式公式化 alpha 挖掘 | 竞赛成绩不等于样本外证据 |
| **AlphaAgent** (Tang et al.) [MAS] | KDD 2025; arXiv 2502.16789 | 想法 / 因子 / 评估智能体 + AST 原创性约束，对抗 alpha 衰减 | CSI 500 与 S&P 500，2021–2024，**计入交易成本**；是较严谨的一篇 |
| **R&D-Agent-Quant** (Li et al., MSRA) [MAS] | arXiv 2505.15155 | 研究 + 开发智能体在 Qlib 中联合优化因子与模型 | CSI 300，测试期 2017–2020（在 LLM 知识范围内）；单次实验成本低于 10 美元 |
| **CryptoTrade** (Li et al.) [单体+反思] | EMNLP 2024 | 链上 + 链下信息 + 反思 | 常仅与买入持有相当 |

### 2.3 LLM 智能体市场仿真

| 论文 | 出处 | 贡献 | 局限 |
|---|---|---|---|
| **StockAgent** (Zhang et al.) [Sim/MAS] | arXiv 2407.18957 | 用虚构股票避免泄漏，研究宏观 / 政策 / 事件冲击 | 玩具市场、轮次少 |
| **ASFM** (Gao et al.) [Sim] | arXiv 2406.19966 | 价格–时间优先撮合的订单簿 + LLM 交易者 | 仅做定性验证 |
| **TwinMarket** (Yang et al.) [Sim] | NeurIPS 2025; arXiv 2502.01506 | BDI 投资者 + 社交网络，用 639 个雪球真实用户标定，复现典型事实 | 仅中国散户数据，扩展成本高 |
| **Can LLMs Trade?** (Lopez-Lira) [Sim] | arXiv 2504.10789 | 持续订单簿 + 价值 / 动量 / 做市 LLM 智能体 | **同一模型的智能体行为高度相关（羊群）**；智能体少 |
| **EconAgent** (Li et al.) [Sim] | ACL 2024 | 宏观家庭智能体，复现菲利普斯曲线、奥肯定律 | 无资产市场 |
| **Agent Trading Arena** (Ma et al.) [Sim/Bench] | Findings of EMNLP 2025; arXiv 2502.17967 | 零和虚拟股市；LLM 读图表比读数字更好 | 合成市场 |

### 2.4 基准、实盘竞技场与批判性评测

| 论文 | 出处 | 核心发现 |
|---|---|---|
| **FINSABER** (Li, Kim, Cucuringu, Ma) | arXiv 2505.07078; **KDD 2026** | 2000–2024 年、100 多个标的、滚动窗口回测：FinMem / FinAgent 等的优势基本消失；LLM 策略**牛市过度保守、熊市过度激进** |
| **Profit Mirage / FinLake-Bench** (Li et al.) | arXiv 2510.07920 | 测试期移到模型知识截止之后，主流智能体 Sharpe **下降 51–62%**；提出反事实修正 FactFin |
| **InvestorBench** (Li et al.) | ACL 2025 | 股票 / 加密 / ETF，13 个骨干模型 |
| **StockBench** (Chen et al.) | arXiv 2510.02209 | 模型知识截止后的 82 个交易日：多数智能体跑不赢买入持有；静态金融问答能力 ≠ 交易能力 |
| **Agent Market Arena (AMA)** (Qian et al.) | arXiv 2510.11695; **WWW 2026** | 实盘多市场：**智能体架构比骨干模型更重要** |
| **LiveTradeBench** (Yu, Li, You) | arXiv 2511.03628 | 21 个 LLM 实盘 50 天：LMArena 排名高不代表交易好 |
| **AI-Trader** | arXiv 2512.10971 | 实时、无污染；美股 / A 股 / 加密 |
| **FinSearchComp** (ByteDance Seed) | arXiv 2509.13160 | 金融搜索与推理（不直接评测交易） |

**2023–2025 的共性弱点**：(1) 前视偏差与模型记忆 —— 测试期落在预训练窗口内；(2) 回测窗口短（3–12 个月）、标的少（1–30 只大盘科技股）、多为牛市，导致 Sharpe 5–8、多年 300–400% 这类不可信结果；(3) 忽略交易成本 / 滑点 / 冲击，基线弱，缺少显著性检验；(4) 成本高、不可复现（闭源 API 版本漂移）；(5) 多智能体本身的增益未被隔离（缺少"同等信息下的单智能体"消融）；(6) 仿真主要靠"复现典型事实"验证。

---

## 3. 2026 年以来的论文

> arXiv ID 前四位为 YYMM（如 2602 = 2026 年 2 月）。作者或日期未确认的条目标注 **[待核实]**。

### 3.1 LLM 多智能体交易 / 组合框架

| arXiv / 出处 | 论文 | 贡献 | 评测 / 局限 |
|---|---|---|---|
| 2602.23330 | **Toward Expert Investment Teams: A Multi-Agent LLM System with Fine-Grained Trading Tasks** (Miyazaki, Kawahara, Roberts, Zohren) | 将分析拆成细粒度任务，而不是宽泛的角色提示；风险调整收益更优 | 日本 TOPIX 100；有粒度消融；仅回测、单一市场 |
| 2605.05580 | **AlphaCrafter** (Yuan et al., 南京大学) | 用可编程策略规范（流程 / 约束 / 校验）包裹每个智能体的全栈多智能体流水线 | CSI 300 与 S&P 500 回测 + **实盘**；回测强的基线在实盘中崩溃（MACD 实盘年化 −38.7%） |
| 2604.02279 | **The Self Driving Portfolio** (Ang, Azimbayev, Kim) | 约 50 个智能体做资本市场假设与 20 多种组合方法，互评投票；元智能体根据实现收益改写代码与提示；受投资政策声明约束 | 机构战略资产配置；评测细节 [待核实] |
| 2606.08283 | **Macro Economists in the Machine** (Wang, Dai, Ma, Geng) | 鹰派 / 鸽派 / 辩论 LLM 智能体 vs 确定性 z-score 规则，输入相同，以隔离 LLM 的增量贡献 | 2023–2025 年 124 次周度调仓的商品 ETF；样本短 |
| 2605.24490 | **Market Regime Council (MRC)** (Pei, Ge, Zheng, Cartlidge) | 精确 Shapley 值做智能体信用分配 + 贝叶斯冷启动 + 按市场状态调整权重 | 13 个加密资产、1,037 个交易日、5 个随机种子，Sharpe 1.51 |
| 2603.22567 | **TrustTrade** (Li et al.) | 选择性共识：按智能体间语义 / 数值一致性加权 | 评测细节 [待核实] |
| 2606.00939 | **FinCom** [作者待核实] | "要么反驳要么承诺"式审议，对抗附和式共识 | LLM 评审打分，不是 PnL |
| 2609.29701 | **Multi-Agent Debate for Explainable Trading** (Huang et al.) [日期待核实] | 辩论式组合分配 | 210 次仿真：推理质量从 0.72 提高到 0.84，但与 Sharpe 的相关系数 **r = 0.07** —— 推理变好 ≠ 赚钱 |
| 2609.17632 | **EvolveTrade** [作者待核实] | 策略智能体每 5 天根据决策轨迹和 PnL 改写交易智能体的提示 | 股票回测 |
| 2601.08641 | **Resisting Manipulative Bots in Meme Coin Copy Trading** (Luo et al.); WWW 2026 | 多智能体多模态跟单系统，抵御抢跑 / 假情绪机器人 | 考虑真实摩擦 |
| 2604.26747 | **From Hypotheses to Factors: Constrained LLM Agents in Crypto** (Huang et al.) [是否多智能体待核实] | 受约束 LLM 智能体把假设转为因子 | 样本外（2024–26）Sharpe 1.55 |
| 2603.20247 | **AlphaLogics** (Weng et al.) | 以"市场逻辑"驱动的多智能体因子生成，并由回测反馈精炼 | CSI 500、S&P 500 |
| 2608.12841 | **AQuA** [作者待核实] | 封闭沙箱中的递归自改进量化研究循环，防止泄漏实验被当作先例复用 | IC 0.0843；因果 walk-forward 下 Sharpe 约 2.0；作者承认仅为模拟 |
| 2604.18500 | **QRAFTI** (Lim, Muthuraman, Sury) | 基于 MCP 工具的多智能体"量化研究团队" | 初步评测 |
| 2605.27864 | **FundaPod** (Zhu, Zheng, Chen) | 多人格智能体 + 知识图谱记忆，保留分歧并交由人类基金经理裁决 | 平台论文 |
| 2604.11477 | **OOM-RL** [作者待核实] | 以实盘资金耗尽作为不可博弈的奖励，对齐构建交易系统的多智能体 | 20 个月实盘的单系统案例 |

另有首发于 2025 年、在 2026 年被会议接收的论文：TiMi（ICLR 2026）、AMA（WWW 2026）、FINSABER（KDD 2026）。QuantAgent、StockBench、MASS 出现在 ICLR 2026 投稿中，是否被接收 [待核实]。

### 3.2 基准、评估方法与生产环境证据

| arXiv / 出处 | 论文 | 核心发现 |
|---|---|---|
| 2605.28359 | **KTD-Fin: From Knowing to Doing** (Zhu et al.) | 在数据侧遮蔽代码和日期，把模型记忆与决策分离，并做 Barra 归因：10 个前沿 LLM 智能体在 CSI 300 上的收益**主要来自市场与风格暴露**，几乎没有持续的选股 alpha |
| 2606.29771 | **CLQT** (Qu, Chen) | 闭环、计入成本、检查策略一致性的诊断式基准；认为"固定窗口收益排名"是很弱的代理指标 |
| 2608.11232 | **Backtrader-Bench** (Zhao, Raissi); FinLLM@IJCAI 2026 | 从回测自动生成的选择题；考察交易知识，而不是交易表现 |
| 2601.13770 | **Look-Ahead-Bench** (Benhenda) | 用跨市场状态的 alpha 衰减度量前视偏差；Llama 3.1、DeepSeek 3.2 偏差显著，point-in-time 模型没有 |
| 2605.24564 | **FinCAD: Summoning the Oracle to Slay It** (Li, Wang, Ma); EMNLP 2026 | 解码阶段抑制模型对历史结果的记忆 |
| 2608.02985 | **Temporal Leakage in LLM Backtesting** (Zhang, Stadie) | 时间泄漏的系统研究 |
| 2609.05663 | **What LLM Trading Agents Actually Do in Production** (Barton et al., DXRG) | 两支实盘智能体舰队、共 750 万次调用：平台运营层（风险滑块、排行榜）比策略文本更能决定行为；仓位不随波动率调整；49.3% 曾盈利 300 bps 以上的仓位最终亏损平仓；**没有方向性优势**（作者即平台方） |
| 2605.28850 | **TradeArena: Representation Signatures and Risk-Feedback Alignment** (Xue) | 回撤发生前，规划嵌入漂移、有效秩收缩，可作为预警 |
| 2606.08285 | **Beyond Agent Architecture: Execution Assumptions and Reproducibility** (Yao, Zheng) | 审计 30 项研究：论文对架构写得详细，对评估假设写得少；理想化执行显著抬高结果 |
| 2603.27539 | **Toward Reliable Evaluation of LLM-Based Financial MAS** (Nguyen, Pham) | 四维分类法；提出"协调优先假设"（协调协议比模型规模更重要），但因缺少评估基础设施尚未验证 |

### 3.3 安全与鲁棒性

| arXiv / 出处 | 论文 | 核心发现 |
|---|---|---|
| 2601.13082 | **Adversarial News and Lost Profits** (Rizvani, Apruzzese, Laskov); IEEE SaTML | 单日标题操纵（包括人眼不可见内容）造成的损失可以量化 |
| 2608.24069 | **Poisoning Agentic Alpha** (Na, …, Lopez-Lira, …) | 对 TradingAgents 类流水线按角色攻击（分析师投毒、研究员说服、交易员目标劫持、风控越狱）：**没有天然鲁棒的架构，对抗信号能穿过审议** |
| 2609.19789 | **Contagion on the Trading Floor** (Sua et al.); ECML PKDD 2026 | 社交媒体投毒在分析师层与协调层之间"传染"的度量 |
| 2609.19705 | **SoK: Trading Agents or Market Crashers?** (Wang, Saxena) | 审计 15 个学术方案：80% 至少一项市场鲁棒性不达标，100% 有安全缺陷；止损几乎从未被强制执行；提示 / 工具 / 记忆未隔离；TradingAgents 决策延迟超过 240 秒 |

### 3.4 LLM 智能体市场仿真

| arXiv / 出处 | 论文 | 核心发现 |
|---|---|---|
| 2602.07023 | **Behavioral Consistency Validation for LLM Agents** (Li et al.); Findings of ACL 2026 | LLM 交易风格切换只**部分**符合行为金融理论 |
| 2604.18602 | **Machine Spirits** (Saxena, Pangallo, Hommes, Caccioli, del Rio-Chanona) | 15 个 LLM 在"学习预测"实验中：5 个产生泡沫，7 个非理性，3 个接近理性预期；混合市场中强模型剥削弱模型，可能放大波动 |
| 2609.02580 | **Competitive Market Behavior of LLMs** (Struski et al.) | 双向拍卖中，LLM 市场比人类市场收敛更慢、配置效率更低 |
| 2601.11369 | **Institutional AI: Governing LLM Collusion** (Bracale Syrnikov et al.) | 治理图把严重合谋从 50% 降到 5.6%（古诺市场） |
| 2604.17774 | *Prompt Optimization Enables Stable Algorithmic Collusion in LLM Agents* | 提示优化可导致稳定的算法合谋（仅核实了标题与 ID） |
| 2609.18357 | *Market Signal Injection: Adversarial Context Manipulation of LLM Pricing Agents* | 定价智能体的上下文注入攻击（仅核实了标题与 ID） |

### 3.5 MARL 与学习型智能体

| arXiv / 出处 | 论文 | 核心发现 |
|---|---|---|
| 2605.20348 | **Memory-Induced Supra-Competitive Outcomes Between Deep RL Agents in Optimal Trade Execution** (Koulouris, Campajola) | 带记忆的 DRL 执行智能体会出现类合谋的超竞争结果 |
| 2601.17008 | **Bayesian Robust Financial Trading with Adversarial Synthetic Market Data** (Xia et al., NTU); KDD 2026 | 宏观扰动对手与交易者构成两人贝叶斯马尔可夫博弈，提升对宏观变化的鲁棒性 |
| 2608.18195 | **Multi-Level Market Making with RL** (Cheridito, Weiss) | 多档位 RL 做市（单智能体，相邻方向） |
| 2608.23706 | **Do LLMs Understand Limit Order Book Dynamics?** (Chen, Glasserman) | LLM 能生成合法的事件序列，但没有学到订单簿状态 → 出现伪可预测性 |
| 2511.02136 / 2510.25929 | JaxMARL-HFT；*MARL for Market Making: Competition without Collusion* | 2025 年末的 MARL 背景工作 |

2026 年的 MARL 交易论文明显少于 LLM 方向。

### 3.6 2026 年综述 / SoK

| arXiv / 出处 | 综述 | 列出的开放问题 |
|---|---|---|
| 2608.31041 | **Agentic Quantitative Trading: A Survey of Workflows, Systems, and Evaluation** (Hua et al.) | 研究集中在信号发现，与组合构建、执行、风控的端到端集成罕见；多智能体大多只是"聚合输出"；预测能力难以转化为实盘表现 |
| 2605.19337 | **Agentic Trading: When LLM Agents Meet Financial Markets** (Xia et al.) | 77 项研究中的核心 19 项：仅 2 项有时间一致的数据划分，1 项有显式成本模型，1 项处理幸存者偏差，15 项未发布可运行代码；搜索式策略生成（MCTS / ToT）存在多重检验与数据窥探问题 |
| 2609.19705 | SoK: Trading Agents or Market Crashers? | 闪崩鲁棒性、止损执行、组件隔离、决策延迟 |
| 2603.27539 | Toward Reliable Evaluation of LLM-Based Financial MAS | 五类评估失败（前视、幸存者、过拟合、成本、状态变化）可能让收益符号反转 |
| 2606.08285 | Beyond Agent Architecture | 执行逼真度与评估假设的报告规范 |
| 2609.04917 | **AI in Equity and Crypto Markets: Progress, Profitability Evidence, and the Limits of Automated Investing** (Zhu, Cai) | 覆盖截至 2026-08 的公开研究 |
| SSRN 7493756 | **From Agent-Based Models to LLM-Based Financial Agents: A PRISMA-Based Systematic Review** (Khoukhi, Slimani) [日期待核实] | 93 项研究的系统综述；MARL 与 LLM-MAS 占主导 |

---

## 4. 仍存在的 Research Problems

下面综合三个时期的证据，按"问题 → 现有证据 → 可能方向"组织。

### P1. 评估有效性：前视偏差、模型记忆与时间泄漏（最核心）
- **证据**：Profit Mirage 显示测试期移到知识截止之后，Sharpe 下降 51–62%；KTD-Fin 遮蔽代码和日期后，收益主要是 beta 与风格暴露；Look-Ahead-Bench 显示开源模型普遍存在前视偏差；Xia et al. 2026 统计核心 19 篇中仅 2 篇的数据划分时间一致。
- **开放问题**：如何对闭源 LLM 做真正的 point-in-time 评估？是否需要"时间截断预训练"的金融基座模型？解码期去记忆（FinCAD）或反事实改写（FactFin）能在多大程度上替代截断？如何在不泄漏的前提下利用长历史做研究？

### P2. 统计显著性与实盘证据不足
- **证据**：2023–2025 的主流框架通常只回测 3–12 个月、不超过 30 只股票；实盘基准（StockBench、AMA、LiveTradeBench、AI-Trader）只有 50–120 天；AlphaCrafter 发现回测强的基线在实盘崩溃；DXRG 的生产数据显示没有方向性优势。
- **开放问题**：多长的实盘 / 前向测试才足以区分技能与运气（Deflated Sharpe、多重检验校正）？如何构建持续运行、公开、防作弊的"终身"竞技场，并统一成本、执行与市场状态划分？

### P3. 执行真实性：交易成本、滑点、市场冲击与延迟
- **证据**：经典 RL 与 LLM 框架大多在历史回放上回测，无冲击；Xia et al. 核心 19 篇中仅 1 篇有显式成本模型；Yao & Zheng 指出理想化执行显著抬高结果；SoK 指出 TradingAgents 决策延迟超过 240 秒。
- **开放问题**：LLM 决策层如何与微观结构执行层耦合（TiMi 的"策略–执行分离"是一个方向）？如何在考虑自身冲击的仿真器（ABIDES 类）中评估 LLM 多智能体？延迟与成本约束下，高频或日内场景是否还适合用 LLM？

### P4. "多智能体"本身的增益尚未被证明
- **证据**：Han et al. 发现简单任务上单智能体更好；2609.29701 发现推理质量与 Sharpe 的相关系数只有 0.07；AMA 发现架构比骨干模型重要；"协调优先假设"尚未验证；2026 年综述指出多数系统只是聚合输出；Miyazaki et al. 发现任务粒度比角色设定更关键。
- **开放问题**：
  - 需要标准化消融：同等信息、同等 token 预算下单智能体与多智能体的对比。
  - 哪些协调机制真正有效（辩论、投票、竞赛、层级、Shapley 信用分配），在什么条件下有效？
  - 角色扮演式"交易公司"隐喻是否只是提示工程？

### P5. 信用分配、在线学习与非平稳性
- **证据**：MRC 用 Shapley 值做动态信用分配并处理冷启动；ATLAS 发现反思常常有害；EvolveTrade 与 ATLAS 按收益改写提示存在对噪声过拟合的风险；FINSABER 显示 LLM 策略牛市过度保守、熊市过度激进；Xia et al. 2026 指出市场状态切换是典型的评估失败。
- **开放问题**：
  - 在低信噪比奖励下，如何在智能体之间做可靠的信用分配？
  - 如何做出有统计保证的"自我进化"（提示 / 代码 / 记忆更新），而不是对近期 PnL 追涨杀跌？
  - 如何识别市场状态并做风险自适应（例如仓位随波动率调整：DXRG 发现各波动率档位的中位杠杆都是 5 倍）？

### P6. 风险管理与约束执行
- **证据**：SoK 统计止损几乎从未被强制执行、80% 的方案未通过市场鲁棒性测试；DXRG 发现 49.3% 曾盈利 300 bps 以上的仓位最终亏损平仓；HedgeAgents、QuantAgents 等宣称的超高收益缺少风险披露。
- **开放问题**：把硬约束（仓位、杠杆、止损、授权范围）从 LLM 软推理中剥离出来，做成可验证的确定性层；把形式化验证或运行时监控用于多智能体交易系统；为风控建立可审计的决策追踪（MRC 的因果追踪、TradeArena 的表征预警）。

### P7. 安全：投毒、提示注入与对抗传播
- **证据**：Poisoning Agentic Alpha 显示没有天然鲁棒的架构；Contagion 研究了信念在层级之间的传染；Adversarial News 量化了标题操纵造成的损失；meme 币机器人会操纵跟单者。
- **开放问题**：
  - 多智能体审议如何从"放大器"变成"防火墙"（交叉验证、来源可信度、隔离）？
  - 对抗鲁棒的检索与记忆机制。
  - 智能体作为攻击者（操纵市场）的检测与治理。

### P8. 系统性风险：同质化、羊群与合谋
- **证据**：Lopez-Lira 发现同一模型的智能体行为高度相关；Machine Spirits 发现部分模型会形成泡沫，强模型剥削弱模型并放大波动；DRL 执行智能体会出现超竞争结果；提示优化可导致稳定合谋；治理图能降低古诺市场中的合谋。
- **开放问题**：
  - 大量机构使用相同基座模型时的市场稳定性（闪崩、流动性枯竭）。
  - 监管视角下 LLM 合谋的检测与机制设计。
  - 异质性应如何注入（模型、数据、目标的多样性），MAPS 的多样性损失能否迁移到 LLM 时代？

### P9. 市场仿真的逼真度与标定
- **证据**：从 LeBaron（2006）到 Get Real（2020）再到 TwinMarket（2025），验证手段主要是"复现典型事实"；LLM 市场在双向拍卖中收敛慢于人类；LLM 没有学到订单簿状态；行为一致性只部分成立。
- **开放问题**：
  - 超越典型事实的定量验证，例如对真实订单流、对政策冲击的反事实预测。
  - 仿真规模、成本与保真度的权衡。
  - 把 LLM 智能体（认知 / 叙事）与 ABIDES 类高保真撮合结合的混合仿真器。
  - 用仿真做可信的策略压力测试和监管沙盒。

### P10. 经典 MARL 与 LLM 智能体的融合
- **证据**：FLAG-Trader 用 RL 微调 LLM 策略；Bayesian Robust Trading 采用对抗博弈训练；QuantAgents 使用模拟与真实双奖励；2026 年纯 MARL 交易论文明显减少。
- **开放问题**：
  - 多个 LLM 智能体之间的博弈论分析（均衡、稳定性、可学习性），这在经典 MARL 中已有工具，但 LLM-MAS 中几乎空白。
  - 用 RL 训练协调策略，而不是手写流程。
  - LLM 负责高层语义，RL 负责低层执行 / 做市的分层混合架构。

### P11. 可复现性、成本与开放基础设施
- **证据**：核心 19 篇中有 15 篇未发布可运行代码；闭源 API 版本漂移；每次决策要调用几十次 LLM；只有少数论文报告 token 成本（R&D-Agent-Quant、AlphaAgent）；报告中描述架构多、描述评估假设少。
- **开放问题**：
  - 统一的报告清单（数据截止、成本、执行语义、股票池、搜索预算）。
  - 开源小模型能否在成本受限下达到可比效果。
  - 把成本当作一等指标：单位 token 收益、延迟–收益曲线。

### P12. 市场与资产覆盖面窄
- **证据**：绝大多数工作集中在美股大盘科技股、A 股或加密；少数工作覆盖日本（TOPIX 100）、商品 ETF、外汇、永续合约；期权、固收、跨资产与低流动性市场几乎空白。
- **开放问题**：跨市场泛化；小盘 / 新兴市场的数据稀疏问题；衍生品定价与对冲中的多智能体协作（Deep Hedging 与 LLM 的结合）。

### P13. 人机协作与治理
- **证据**：FundaPod 把分歧留给人类基金经理；Self Driving Portfolio 受投资政策声明约束；DXRG 显示运营层（排行榜、风险滑块）比策略文本更能决定行为。
- **开放问题**：人在回路的最佳介入点；把可解释性（而不是事后叙事）作为决策依据；合规、问责与审计（谁对智能体的交易负责）。

---

### 一句话总结

多智能体交易从 ABM / MARL 走到 LLM-MAS 之后，**"架构创新"远多于"可信证据"**。2026 年的研究重心已明显转向评估有效性（泄漏、成本、实盘）、安全（投毒与传染）和系统性风险（羊群与合谋）。最有价值的方向是：在严格的 point-in-time、计入成本、长周期或实盘的评估下，**证明多智能体协调本身带来可归因的风险调整超额收益**，并把风控与安全做成可验证的确定性层。
