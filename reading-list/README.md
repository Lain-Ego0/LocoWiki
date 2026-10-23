# 论文学习清单（阅读清单 + 推荐论文）

> 中文 | [English](README.en.md)

本目录是论文功能的统一入口：负责技术方向索引、重点论文笔记与更新维护说明。论文正文不存储在本仓库，条目统一指向原始来源。

## 快速跳转
- [如何更新原文链接](#update)
- [按技术方向索引（快速查找）](#tech-index)
- [按来源/团队笔记（详细介绍）](#source-notes)
  - [ETH RSL](#eth-rsl)
  - [KAIST](#kaist)
  - [其他代表作](#other-works)
  - [人形](#humanoids)
  - [框架与工具](#frameworks)
  - [综述](#surveys)
  - [其他资料（暂无笔记）](#misc)

<a id="update" name="update"></a>
## 如何更新/抓取
1. 在 `reading-list/papers.json` 新增/更新条目（title / venue / year / notes / group）。
2. 解析原始链接并回写索引（`url` 字段，优先原始公开来源）：

```bash
python3 scripts/resolve_paper_links.py --update-index
```

3. README 只保留原始来源链接，不再添加本地 PDF 镜像。

说明：脚本会尽量从 arXiv/开放获取来源解析原始链接；若个别条目解析不到，可手动在 `papers.json` 里补 `url` 字段。

<a id="tech-index" name="tech-index"></a>
## 按技术方向索引（快速查找）
注：下方为快速索引；若某条目有笔记/简介，详见同文件后半部分「按来源/团队笔记（详细介绍）」。

### 综述 / 教材
- Learning-based legged locomotion: State of the art and future perspectives（IJRR 2025）— [原文 PDF](https://arxiv.org/pdf/2406.01152.pdf)
- Robot Dynamics Lecture Notes（2017）— [原文 PDF](https://rsl.ethz.ch/education-students/lectures/robotdynamics.html)

### 模型驱动控制 / 轨迹优化
- Dynamic Locomotion in the MIT Cheetah 3 Through Convex Model-Predictive Control — [原文 PDF](https://dspace.mit.edu/handle/1721.1/138000.2)
- DTC: Deep Tracking Control（Science Robotics 2024）— [原文 PDF](https://arxiv.org/pdf/2309.15462.pdf)

### 学习运控（本体感知为主）
#### 四足
- Learning agile and dynamic motor skills for legged robots（Science Robotics 2019）— [原文 PDF](https://arxiv.org/pdf/1901.08652.pdf)
- Learning Quadrupedal Locomotion over Challenging Terrain（Science Robotics 2020）— [原文 PDF](https://arxiv.org/pdf/2010.11251.pdf)
- Learning to Walk in Minutes Using Massively Parallel Deep Reinforcement Learning（CoRL 2021）— [原文 PDF](https://arxiv.org/pdf/2109.11978)
- Concurrent Training of a Control Policy and a State Estimator for Dynamic and Robust Legged Locomotion（RAL 2022）— [原文 PDF](https://arxiv.org/pdf/2202.05481.pdf)
- DreamWaQ: Learning Robust Quadrupedal Locomotion With Implicit Terrain Imagination via Deep Reinforcement Learning（ICRA 2023）— [原文 PDF](https://arxiv.org/pdf/2301.10602.pdf)
- Learning Quadrupedal Locomotion on Deformable Terrain（Science Robotics 2023）— [原文（期刊页）](https://doi.org/10.1126/scirobotics.ade2256)（暂无公开 PDF，可尝试作者预印本）
- Rapid Locomotion via Reinforcement Learning（RSS 2022）— [原文 PDF](https://arxiv.org/pdf/2205.02824.pdf)
- Trajectory-Level Automatic Curriculum Learning for Legged Locomotion on Unstructured Terrain（arXiv 2026）— [原文页面](https://arxiv.org/abs/2608.16164)
- TransCurriculum: Multi-Dimensional Curriculum Learning for Fast & Stable Locomotion（arXiv 2026）— [原文页面](https://arxiv.org/abs/2603.14156)
- Predictive Safety Curricula for Robust Legged Locomotion（arXiv 2026）— [原文页面](https://arxiv.org/abs/2609.37070)
- MoE-Loco: Mixture of Experts for Multitask Locomotion（2025）— [原文 PDF](https://arxiv.org/pdf/2503.08564.pdf)
- Scaling Rough Terrain Locomotion with Automatic Curriculum Reinforcement Learning（RAL 2026）— [原文 PDF](https://arxiv.org/pdf/2601.17428.pdf)

#### 双足
- Sim-to-Real Learning of All Common Bipedal Gaits via Periodic Reward Composition（ICRA 2021）— [原文 PDF](https://arxiv.org/pdf/2011.01387.pdf)

### Sim-to-Real / 适应
- Sim-to-Real: Learning Agile Locomotion for Quadruped Robots（2018）— [原文 PDF](https://arxiv.org/pdf/1804.10332.pdf)
- RMA: Rapid Motor Adaptation for Legged Robots（RSS 2021）— [原文 PDF](https://arxiv.org/pdf/2107.04034.pdf)
- Actuator Reality Shaping for Zero-Shot Sim-to-Real Robot Learning（2026）— [原文 PDF](https://arxiv.org/pdf/2607.02205.pdf)

### 感知 / 建图
- Learning robust perceptive locomotion for quadrupedal robots in the wild（Science Robotics 2022）— [原文 PDF](https://arxiv.org/pdf/2201.08117)
- Elevation Mapping for Locomotion and Navigation using GPU（IROS 2022）— [原文 PDF](https://arxiv.org/pdf/2204.12876)
- Experience-Driven Continual Learning of Terrain Traversability for Quadruped Robots（arXiv 2026）— [原文页面](https://arxiv.org/abs/2609.39755)
- DELTA: Deformable Elevation-Based Local Terrain Attention Encoder for Sparse-Terrain Quadrupedal Locomotion（arXiv 2026）— [原文页面](https://arxiv.org/abs/2608.22033)
- Agile and Generalized Legged Locomotion via Attention-Based Neural Map Encoding（T-RO 2026）— [原文 PDF](https://arxiv.org/pdf/2601.08485.pdf)

### 运动先验 / 模仿学习 / 风格奖励 / 生成模型
- Learning Agile Robotic Locomotion Skills by Imitating Animals（RSS 2020）— [原文 PDF](https://arxiv.org/pdf/2004.00784.pdf)
- Learning Agile Skills via Adversarial Imitation of Rough Partial Demonstrations — [原文 PDF](https://arxiv.org/pdf/2206.11693.pdf)
- AMP: Adversarial Motion Priors for Stylized Physics-Based Character Control（SIGGRAPH 2021）— [原文 PDF](https://arxiv.org/pdf/2104.02180.pdf)
- Adversarial Motion Priors Make Good Substitutes for Complex Reward Functions（ICRA 2022）— [原文 PDF](https://arxiv.org/pdf/2203.15103.pdf)
- Advanced Skills through Multiple Adversarial Motion Priors in Reinforcement Learning（ICRA 2023）— [原文 PDF](https://arxiv.org/pdf/2203.14912)
- Walk These Ways: Tuning Robot Control for Generalization with Multiplicity of Behavior（CoRL 2022）— [原文 PDF](https://arxiv.org/pdf/2212.03238.pdf)
- A Learning Framework for Diverse Legged Robot Locomotion Using Barrier-Based Style Rewards（ICRA 2025）— [原文 PDF](https://arxiv.org/pdf/2409.15780.pdf)
- Learning Robust, Agile, Natural Legged Locomotion Skills in the Wild（RAL 2023）— [原文 PDF](https://arxiv.org/pdf/2304.10888.pdf)
- Lifelike Agility and Play on Quadrupedal Robots using Reinforcement Learning and Generative Pre-trained Models（Nature Machine Intelligence 2023）— [原文 PDF](https://arxiv.org/pdf/2308.15143.pdf)
- KiRAS: Keyframe Guided Self-Imitation for Robust and Adaptive Skill Learning in Quadruped Robots（ICRA 2026）— [原文 PDF](https://arxiv.org/pdf/2603.15179.pdf)

### 跑酷 / 离散地形 / 高动态
- Learning Agile Locomotion on Risky Terrains（IROS 2024）— [原文 PDF](https://arxiv.org/pdf/2311.10484.pdf)
- ANYmal Parkour: Learning Agile Navigation for Quadrupedal Robots（Science Robotics 2024）— [原文 PDF](https://arxiv.org/pdf/2306.14874.pdf)
- Extreme Parkour with Legged Robots（ICRA 2024）— [原文 PDF](https://arxiv.org/pdf/2309.14341.pdf)
- Robot Parkour Learning（CoRL 2024）— [原文 PDF](https://arxiv.org/pdf/2309.05665.pdf)
- PIE: Parkour with Implicit-Explicit Learning Framework for Legged Robots（RAL 2024）— [原文 PDF](https://arxiv.org/pdf/2408.13740.pdf)
- Learning Highly Dynamic Skills Transition for Quadruped Jumping Through Constrained Space（arXiv 2026）— [原文页面](https://arxiv.org/abs/2608.19977)

### Loco-manipulation / Whole-body
- Deep Whole-Body Control: Learning a Unified Policy for Manipulation and Locomotion（CoRL 2022）— [原文 PDF](https://arxiv.org/pdf/2210.10044.pdf)
- Visual Whole-Body Control for Legged Loco-Manipulation（CoRL 2024）— [原文 PDF](https://arxiv.org/pdf/2403.16967.pdf)
- Curiosity-Driven Learning of Joint Locomotion and Manipulation Tasks（CoRL 2023）— [原文 PDF](https://proceedings.mlr.press/v229/schwarke23a/schwarke23a.pdf)（PMLR 开放获取）

### 人形（Whole-Body / 行为基础模型 / Teleop / Retargeting / 数据采集 / Getting-Up / 生成）
- Perpetual Humanoid Control for Real-time Simulated Avatars（ICCV 2023）— [原文 PDF](https://arxiv.org/pdf/2305.06456.pdf)
- Expressive Whole-Body Control for Humanoid Robots（RSS 2024）— [原文 PDF](https://arxiv.org/pdf/2402.16796.pdf)
- ExBody2: Advanced Expressive Humanoid Whole-Body Control（2024）— [原文 PDF](https://arxiv.org/pdf/2412.13196.pdf)
- Open-TeleVision: Teleoperation with Immersive Active Visual Feedback（CoRL 2024）— [原文 PDF](https://arxiv.org/pdf/2407.01512.pdf)
- Mobile-TeleVision: Predictive Motion Priors for Humanoid Whole-Body Control（2024）— [原文 PDF](https://arxiv.org/pdf/2412.07773.pdf)
- HOVER: Versatile Neural Whole-Body Controller for Humanoid Robots（ICRA 2025）— [原文 PDF](https://arxiv.org/pdf/2410.21229.pdf)
- HugWBC: A Unified and General Humanoid Whole-Body Controller for Fine-Grained Locomotion（2025）— [原文 PDF](https://arxiv.org/pdf/2502.03206)
- Learning Humanoid Standing-up Control across Diverse Postures（RSS 2025）— [原文 PDF](https://arxiv.org/pdf/2502.08378)
- Learning Getting-Up Policies for Real-World Humanoid Robots（RSS 2025）— [原文 PDF](https://arxiv.org/pdf/2502.12152)
- BeyondMimic: From Motion Tracking to Versatile Humanoid Control via Guided Diffusion（2025）— [原文 PDF](https://arxiv.org/pdf/2508.08241)
- BFM-Zero: A Promptable Behavioral Foundation Model for Humanoid Control Using Unsupervised Reinforcement Learning（2025）— [原文 PDF](https://arxiv.org/pdf/2511.04131.pdf)
- TWIST: Teleoperated Whole-Body Imitation System（CoRL 2025）— [原文 PDF](https://arxiv.org/pdf/2505.02833.pdf)
- Retargeting Matters: General Motion Retargeting for Humanoid Motion Tracking（ICRA 2026）— [原文 PDF](https://arxiv.org/pdf/2510.02252.pdf)
- TWIST2: Scalable, Portable, and Holistic Humanoid Data Collection System（2025）— [原文 PDF](https://arxiv.org/pdf/2511.02832.pdf)
- Global-Local Attention Decomposition for Terrain Encoding in Humanoid Perceptive Locomotion（arXiv 2026）— [原文页面](https://arxiv.org/abs/2606.00637)
- Extreme-RGMT: Continual Learning of Highly Dynamic Skills for Robust Generalist Humanoid Control（arXiv 2026）— [原文页面](https://arxiv.org/abs/2607.20110)
- PredActor: Predictive Action Diffusion for Steerable Onboard Humanoid Control（2026）— [原文 PDF](https://arxiv.org/pdf/2609.24840.pdf)

### 仿真 / 机器人学习框架
- mjlab: A Lightweight Framework for GPU-Accelerated Robot Learning（2026）— [原文 PDF](https://arxiv.org/pdf/2601.22074.pdf)

### 硬件 / 机构
- A Low Cost Modular Actuator for Dynamic Robots — [原文 PDF](https://dspace.mit.edu/handle/1721.1/118671)

### Others

<a id="source-notes" name="source-notes"></a>
## 按来源/团队笔记（详细介绍）

<a id="eth-rsl" name="eth-rsl"></a>
### ETH Robotics Systems Lab（RSL）

#### Learning Agile and Dynamic Motor Skills for Legged Robots（Science Robotics 2019）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/1901.08652.pdf) - 笔记：强化学习四足运控的奠基之作：用真实数据训练电机网络模型，并在仿真中进行补偿，结合 RL + dynamics randomization 训练策略；成功部署到 ANYmal，实现鲁棒 locomotion（速度跟踪、跌倒恢复等）。

#### Learning Quadrupedal Locomotion over Challenging Terrain（Science Robotics 2020）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2010.11251.pdf) - 笔记：首次提出两阶段教师-学生框架：教师策略利用模拟器里的“作弊信息”学习到好的运动策略，再通过在线模仿学习（DAgger）蒸馏给可部署（仅使用历史可观测数据）的学生策略（引入 encoder 估计隐式作弊信息）。同时提出地形课程，实现鲁棒的复杂连续地形行走。该阶段控制栈仍较复杂：网络用于辅助足端轨迹生成，还需 IK 求解得到最终 target joints；而后续主流更倾向策略直接输出 target joints。

#### Learning to Walk in Minutes Using Massively Parallel Deep Reinforcement Learning（CoRL 2021）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2109.11978) - 笔记：里程碑工作：推动 RL + Robotics 的后续发展。开发并验证 Isaac Gym 大规模并行训练 + domain randomization 的强化学习运控方案，并开源 `legged_gym` 项目。

#### Learning robust perceptive locomotion for quadrupedal robots in the wild（Science Robotics 2022）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2201.08117) - 笔记：集成本体感知与外部视觉信号的鲁棒 locomotion 策略，实现大规模户外甚至极端条件行走（楼梯、隧道、雪山、浓雾、森林、碎岩等）。给出了学习“带外感知策略”（估计高程图）的范例。

#### Elevation Mapping for Locomotion and Navigation using GPU（IROS 2022）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2204.12876) - 笔记：提出利用 GPU 高效构建高程图的方法：接收外部传感器点云与机器人位姿信息，快速构建周围地形高程图；复杂环境中里程计漂移仍是实时建图的最大挑战之一。代码已开源。

#### Advanced Skills through Multiple Adversarial Motion Priors in Reinforcement Learning（ICRA 2023）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2203.14912) - 笔记：增强版 AMP：允许多种可离散切换的风格，在轮腿四足机器人上展示躲避、行走，以及四足与双足模式（站立）之间的风格切换；其中从“反向站立（双足）序列”学习“趴下（四足）”的案例较有意思。

#### Curiosity-Driven Learning of Joint Locomotion and Manipulation Tasks（CoRL 2023）
- PDF：暂未找到可公开抓取的 PDF（可能在 OpenReview/作者主页）。
- 笔记：亮点：用轮腿四足学习把腿当作 manipulator 的 loco-manipulation 策略。

#### Learning Agile Locomotion on Risky Terrains（IROS 2024）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2311.10484.pdf) - 笔记：（@XueYeiii）有意思的工作之一：可能是较早的基于 RL 运控走离散地形的工作（虽非全向行走），demo 效果不错。

#### ANYmal Parkour: Learning Agile Navigation for Quadrupedal Robots（Science Robotics 2024）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2306.14874.pdf) - 笔记：多层级框架：感知模块重建环境信息，导航模块根据环境信息导航并驱动运动模块选择能力；运动模块具备跑酷基本技能。首篇实现四足动态跑酷的工作之一。

#### DTC: Deep Tracking Control（Science Robotics 2024）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2309.15462.pdf) - 笔记：结合 Model-based 与 Learning-based：上层 TO 根据环境与动力学实时优化机身轨迹与足端轨迹；底层 RL 严格跟踪优化轨迹，实现极端地形的精确运动（梅花桩、深沟、废墟等）。相较只做机身速度跟踪的方法，该分层框架更有利于落足点选择。

#### Agile and Generalized Legged Locomotion via Attention-Based Neural Map Encoding（T-RO 2026）
- 原文 PDF： https://arxiv.org/pdf/2601.08485.pdf
- 笔记：统一感知与控制的 RL 框架。注意力地图编码器从高程图中提取局部和全局特征，并关注稀疏落脚点等关键区域；配套学习式建图从深度观测估计带不确定性的局部高程图，再与里程计融合。方法在四足和双足机器人上验证了敏捷运动与跨地形泛化（前称 AME-2）。

#### Scaling Rough Terrain Locomotion with Automatic Curriculum Reinforcement Learning（RAL 2026）
- 原文 PDF： https://arxiv.org/pdf/2601.17428.pdf
- 笔记：提出基于学习进度的 LP-ACRL，根据 episode reward 在线估计任务学习进度并动态调整采样分布，无需预先知道任务难度顺序。ANYmal D 的单一策略可在楼梯、坡面、碎石和低摩擦平地等处保持 2.5 m/s 线速度与 3.0 rad/s 角速度，并迁移到真实机器人。

<a id="kaist" name="kaist"></a>
### KAIST（Raibo / Unitree 等）

#### Concurrent Training of a Control Policy and a State Estimator for Dynamic and Robust Legged Locomotion（RAL 2022）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2202.05481.pdf) - 笔记：一阶段非对称学习（非教师-学生）：策略网络联合训练关键状态估计器（线速度、足端高度、触地概率，输入为历史可观测数据）；仿真中 critic 直接使用关键状态真值，并引入 dynamics randomization，使用 PPO 训练后可部署并穿越多样连续复杂地形。

#### DreamWaQ: Learning Robust Quadrupedal Locomotion With Implicit Terrain Imagination via Deep Reinforcement Learning（ICRA 2023）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2301.10602.pdf) - 笔记：非对称强化学习结构：状态估计器从可观测信息中估计速度与隐式地形信息 z，z 通过 VAE 学习。在宇树 A1 上实现鲁棒的长距离多样户外地形行走，说明非对称 actor-critic 训练框架可在复杂环境获得很强的运动能力。

#### Learning Quadrupedal Locomotion on Deformable Terrain（Science Robotics 2023）
- PDF：暂未找到可公开抓取的 PDF（可能为期刊付费版；可优先找作者公开版/预印本）。
- 笔记：针对模拟器多为刚性接触动力学，修改 RaiSim 底层接触模型，建模颗粒介质（granular media）接触动力学，实现 Raibo 在沙滩/海绵垫等松软地形的敏捷与鲁棒运动；采用非对称训练框架，进一步验证其有效性。

#### A Learning Framework for Diverse Legged Robot Locomotion Using Barrier-Based Style Rewards（ICRA 2025）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2409.15780.pdf) - 笔记：引入松弛对数障碍函数，设计基于运动模式特征的软约束奖励机制，引导机器人趋向预设运动形态参数（周期步态、关节范围限制等）。未使用运动先验也生成多种仿生四足步态，其中四足站立的“仿人行走”与 gallop 奔跑步态令人印象深刻。

<a id="other-works" name="other-works"></a>
### 其他代表作（四足/双足/通用）

#### 四足 / 足式

##### Sim-to-Real: Learning Agile Locomotion for Quadruped Robots（Minitaur）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/1804.10332.pdf) - 笔记：较早的四足 sim2real 工作：RL + analytical 解析式电机模型 + dynamics randomization，基于 Ghost Robotics 的 Minitaur，启发了 ETH ANYmal 系列。

##### Learning Agile Robotic Locomotion Skills by Imitating Animals（RSS 2020）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2004.00784.pdf) - 笔记：在宇树早期的 Laikago 平台上，基于 motion retargeting + DeepMimic 的 motion tracking 方案，学习动物自然风格运动行为。代码已开源（UCB）。

##### RMA: Rapid Motor Adaptation for Legged Robots（RSS 2021）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2107.04034.pdf) - 笔记：Teacher-student + adaptation module（类似 ETH 的 encoder），随机采样地形 + domain randomization + RaiSim 并行训练，在宇树 A1 上实现无外感知的复杂连续地形穿越。代码已开源（CMU）。

##### Walk These Ways: Tuning Robot Control for Generalization with Multiplicity of Behavior（CoRL 2022）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2212.03238.pdf) - 笔记：在宇树 Go1 上实现可细粒度调参的鲁棒 locomotion：速度、步态（pronking/trotting/bounding/pacing/galloping）、步频、机身高度、俯仰角、触地时间、抬腿高度等。代码已开源（MIT）。

##### Rapid Locomotion via Reinforcement Learning（RSS 2022）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2205.02824.pdf) - 笔记：提出速度网格自适应采样课程，自动挖掘速度上限，减少手工速度课程与专家知识干预。代码已开源（MIT）。

##### Adversarial Motion Priors Make Good Substitutes for Complex Reward Functions（ICRA 2022）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2203.15103.pdf) - 笔记：首次将 AMP 应用于四足：仅任务奖励 + 风格奖励学习自然运动行为，推动后续四足模仿学习运控研究。代码已开源（UCB）。

##### Deep Whole-Body Control: Learning a Unified Policy for Manipulation and Locomotion（CoRL 2022）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2210.10044.pdf) - 笔记：在宇树 Go1 + WidowX 机械臂上验证 RL 运控实现臂-腿协同（基于遥操作），并提出 ROA 将环境隐变量 z 的两阶段估计改为一阶段在线估计；基于 Isaac Gym + rsl_rl 开发，代码已开源（CMU）。

##### Learning Robust, Agile, Natural Legged Locomotion Skills in the Wild（RAL 2023）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2304.10888.pdf) - 笔记：教师-学生框架 + AMP：仅本体感知即可在宇树 Go1 上实现鲁棒复杂连续地形行走；自然步态数据用轨迹优化在平地生成。注：期刊标题为 “Learning robust and Agile Legged Locomotion Using Adversarial Motion Priors”（SJTU）。

##### Lifelike Agility and Play on Quadrupedal Robots using Reinforcement Learning and Generative Pre-trained Models（Nature Machine Intelligence 2023）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2308.15143.pdf) - 笔记：利用生成模型：先在预训练阶段学习动物大规模运动数据，再在环境交互学习阶段复用技能；腾讯 Robotics X 代表作。

##### Learning Agile Skills via Adversarial Imitation of Rough Partial Demonstrations
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2206.11693.pdf) - 笔记：从不完整动作演示中学习四足动态运动：数据来自人为手工操作机器人收集，在低成本机器人上实现后空翻动作。

##### Extreme Parkour with Legged Robots（ICRA 2024）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2309.14341.pdf) - 笔记：domain randomization + 外感知将宇树 A1 连续地形 locomotion 能力推向极致，可跳箱、翻越、夹缝行走等（CMU/Stanford 等）。

##### Robot Parkour Learning（CoRL 2024）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2309.05665.pdf) - 笔记：与 Extreme Parkour 同期：通过 domain randomization + 外感知提升跑酷能力（CoRL 2024）。

##### Visual Whole-Body Control for Legged Loco-Manipulation（CoRL 2024）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2403.16967.pdf) - 笔记：在宇树 B1 + Z1 机械臂上验证视觉输入的双层策略（模仿学习 + 强化学习），通过 sim2real 实现自动移动抓取；基于 Isaac Gym + rsl_rl，代码已开源（UCSD）。

##### PIE: Parkour with Implicit-Explicit Learning Framework for Legged Robots（RAL 2024）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2408.13740.pdf) - 笔记：跑酷能力的增强版本：进一步提高动态能力，实现挑战环境高速运动并迁移到野外（ZJU）。

##### MoE-Loco: Mixture of Experts for Multitask Locomotion（2025）
- 原文 PDF： https://arxiv.org/pdf/2503.08564.pdf
- 笔记：将混合专家引入足式运动多任务强化学习。单一策略支持栏杆、坑、楼梯、坡面等复杂地形与四足/双足步态切换；不同专家自然形成行为分工，从而缓解梯度冲突并改善训练效率与性能。

##### KiRAS: Keyframe Guided Self-Imitation for Robust and Adaptive Skill Learning in Quadruped Robots（ICRA 2026）
- 原文 PDF： https://arxiv.org/pdf/2603.15179.pdf
- 笔记：用关键帧作为紧凑且通用的技能表示，通过关键帧引导自模仿在平地学习多种技能，再在复杂地形继续训练同一策略。技能熟练度初始化可缓解灾难性遗忘，在 Solo-8 与 Unitree Go1 上实现平滑技能切换和复杂地形适应。

#### Sim-to-Real / 通用

##### Actuator Reality Shaping for Zero-Shot Sim-to-Real Robot Learning（2026）
- 原文 PDF： https://arxiv.org/pdf/2607.02205.pdf
- 笔记：用二自由度前馈-反馈控制器塑造真实关节的闭环响应，使其匹配仿真中的理想二阶参考动力学。策略因此无需任务级微调和学习式执行器模型即可零样本迁移；论文在单关节、7-DOF 机械臂、轮腿机器人和人形机器人上进行了验证。

#### 双足 / 通用

##### Sim-to-Real Learning of All Common Bipedal Gaits via Periodic Reward Composition（ICRA 2021）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2011.01387.pdf) - 笔记：较早提出用概率周期函数定义足式步态（站立、行走、跳跃、跑步、单脚跳），在 Cassie 上测试；包含单步态策略与多步态切换策略，被后续工作参考。

##### AMP: Adversarial Motion Priors for Stylized Physics-Based Character Control（SIGGRAPH 2021）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2104.02180.pdf) - 笔记：非足式机器人论文，但框架迁移价值高：用 GAN 作为隐式 metric 获得风格引导奖励学习控制策略（UCB）。

<a id="humanoids" name="humanoids"></a>
### 人形（Whole-Body Control / 行为基础模型 / Teleop / Retargeting / 数据采集 / Getting-Up 等）

#### Perpetual Humanoid Control for Real-time Simulated Avatars（ICCV 2023）
- 原文 PDF： https://arxiv.org/pdf/2305.06456.pdf
- 笔记：提出渐进式乘法控制策略（PMCP），动态分配网络容量，从一万段量级的动作数据中学习。控制器无需外部稳定力，能处理姿态估计噪声和意外跌倒，并可持续、实时地模仿远距离参考动作用于模拟人物。

#### Expressive Whole-Body Control for Humanoid Robots（RSS 2024）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2402.16796.pdf) - 笔记：基于 motion sequence retargeting 学习人形运动序列（UCSD）。

#### ExBody2: Advanced Expressive Humanoid Whole-Body Control（2024）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2412.13196.pdf) - 笔记：Expressive Whole-Body Control 的后续工作（2024）。

#### Open-TeleVision: Teleoperation with Immersive Active Visual Feedback（CoRL 2024）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2407.01512.pdf) - 笔记：开源 VR 人形机器人遥操作框架（仅上半身）。

#### Mobile-TeleVision: Predictive Motion Priors for Humanoid Whole-Body Control（2024）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2412.07773.pdf) - 笔记：在 Mobile-TeleVision 工作中展示全身控制方式，其中 locomotion 控制器结合 ExBody 思路（2024）。

#### HOVER: Versatile Neural Whole-Body Controller for Humanoid Robots（ICRA 2025）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2410.21229.pdf) - 笔记：总结并统一多种人形全身控制方式（root velocity tracking、joint angle tracking、key-point tracking 等）（CMU）。

#### HugWBC: A Unified and General Humanoid Whole-Body Controller for Fine-Grained Locomotion（2025）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2502.03206) - 笔记：人形版 Walk These Ways：可细粒度调参的鲁棒连续地形 locomotion（步态、步频、机身高度、俯仰角、触地时间、抬腿高度等）；自然步态来自多项式足端轨迹引导奖励，并通过上肢介入课程实现上肢自由控制（SJTU/上海 AI Lab）。

#### Learning Humanoid Standing-up Control across Diverse Postures（RSS 2025）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2502.08378) - 笔记：效果很好的倒地起身控制（上海 AI Lab）。

#### Learning Getting-Up Policies for Real-World Humanoid Robots（RSS 2025）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2502.12152) - 笔记：同期起身策略工作（UIUC）。

#### BeyondMimic: From Motion Tracking to Versatile Humanoid Control via Guided Diffusion（2025）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2508.08241) - 笔记：高质量 motion tracking + guided diffusion：测试时可用简单 cost functions 做 task-specific control（Berkeley/Stanford）。

#### Trajectory-Level Automatic Curriculum Learning for Legged Locomotion on Unstructured Terrain（arXiv 2026）
- 原文页面： [原文链接](https://arxiv.org/abs/2608.16164) - 笔记：直接从非结构化地形图生成轨迹级课程；评估器学习任务难度，采样器根据策略能力持续提出下一轮训练轨迹。

#### TransCurriculum: Multi-Dimensional Curriculum Learning for Fast & Stable Locomotion（arXiv 2026）
- 原文页面： [原文链接](https://arxiv.org/abs/2603.14156) - 笔记：用 Transformer 教师联合调度速度、地形和域随机化三类课程，并在 Unitree Go1 上验证高速 locomotion 与 sim-to-real 转移。

#### Predictive Safety Curricula for Robust Legged Locomotion（arXiv 2026）
- 原文页面： [原文链接](https://arxiv.org/abs/2609.37070) - 笔记：用安全 critic 预测未来安全代价，优先训练罕见失败场景；在 ANYmal-D 等平台上降低小腿碰撞。

#### Experience-Driven Continual Learning of Terrain Traversability for Quadruped Robots（arXiv 2026）
- 原文页面： [原文链接](https://arxiv.org/abs/2609.39755) - 笔记：从接触前视觉和运动经验持续学习地形交互与可通行性，并用验证门控制模型更新。

#### Global-Local Attention Decomposition for Terrain Encoding in Humanoid Perceptive Locomotion（arXiv 2026）
- 原文页面： [原文链接](https://arxiv.org/abs/2606.00637) - 笔记：GLAD 将地形编码拆成全局环境理解和局部落足点细节，在 Unitree G1 上面向稀疏落足点与障碍地形实现感知运动。

#### Learning Highly Dynamic Skills Transition for Quadruped Jumping Through Constrained Space（arXiv 2026）
- 原文页面： [原文链接](https://arxiv.org/abs/2608.19977) - 笔记：分层策略结合动物动作模仿、视觉门检测和技能选择，实现四足机器人动态穿越狭窄通道。

#### Scaling Rough Terrain Locomotion with Automatic Curriculum Reinforcement Learning（arXiv 2026）
- 原文页面： [原文链接](https://arxiv.org/abs/2601.17428) - 笔记：LP-ACRL 在线估计学习进展并调整任务采样分布，使 ANYmal D 在多种粗糙地形上实现高速运动。

#### DELTA: Deformable Elevation-Based Local Terrain Attention Encoder for Sparse-Terrain Quadrupedal Locomotion（arXiv 2026）
- 原文页面： [原文链接](https://arxiv.org/abs/2608.22033) - 笔记：通过状态条件采样和固定数量的地形证据标记降低高分辨率地图编码成本，并在稀疏地形四足运动中验证 sim-to-real。

#### Extreme-RGMT: Continual Learning of Highly Dynamic Skills for Robust Generalist Humanoid Control（arXiv 2026）
- 原文页面： [原文链接](https://arxiv.org/abs/2607.20110) - 笔记：先训练通用运动跟踪策略，再通过难度感知采样和能力巩固学习后空翻等高动态人形技能，同时减少已掌握能力退化。

#### PredActor: Predictive Action Diffusion for Steerable Onboard Humanoid Control（arXiv 2026）
- 原文页面： [原文链接](https://arxiv.org/abs/2609.24840) - 笔记：动作扩散策略直接生成可执行动作，并预测未来状态轨迹以支持文本条件和测试时目标引导；在 Unitree G1 上完成实机验证。

#### BFM-Zero: A Promptable Behavioral Foundation Model for Humanoid Control Using Unsupervised Reinforcement Learning（2025）
- 原文 PDF：https://arxiv.org/pdf/2511.04131.pdf
- 笔记：使用 Forward-Backward 无监督强化学习构造共享潜变量空间，使同一 G1 策略可接受运动、目标或奖励提示，完成零样本推理和少样本优化适配。
- 开源项目：[BFM-Zero](../network-open-source/paper-reproductions/bfm-zero.md)

#### TWIST: Teleoperated Whole-Body Imitation System（CoRL 2025）
- 原文 PDF：https://arxiv.org/pdf/2505.02833.pdf
- 笔记：通过动作重定向与 RL+BC 教师-学生训练实现 G1 全身遥操作，单一控制器覆盖移动、全身操作和表现性动作。
- 开源项目：[TWIST](../network-open-source/paper-reproductions/twist.md)

#### Retargeting Matters: General Motion Retargeting for Humanoid Motion Tracking（ICRA 2026）
- 原文 PDF：https://arxiv.org/pdf/2510.02252.pdf
- 笔记：把重定向质量作为运动跟踪策略性能的关键变量进行系统对比，并提出 GMR；在减少奖励工程的设置下，其鲁棒性和动作保真度优于其他开源方法。
- 开源项目：[GMR](../network-open-source/paper-reproductions/gmr.md)

#### TWIST2: Scalable, Portable, and Holistic Humanoid Data Collection System（2025）
- 原文 PDF：https://arxiv.org/pdf/2511.02832.pdf
- 笔记：使用 PICO VR 构建便携、无光学动捕的全身遥操作与数据采集系统，并利用第一视角数据训练分层视觉运动策略。
- 开源项目：[TWIST2](../network-open-source/paper-reproductions/twist2.md)

#### PredActor: Predictive Action Diffusion for Steerable Onboard Humanoid Control（2026）
- 原文 PDF： https://arxiv.org/pdf/2609.24840.pdf
- 笔记：联合预测可执行动作与内部未来状态轨迹，仅使用本体感知，将文本条件生成和测试时状态目标引导统一到单一闭环策略中，无需独立运动跟踪器或特权全身状态。在 Jetson Orin NX 上满足 20 ms 控制周期，并在 Unitree G1 上实现文本指令、摇杆控制、语义插值和扰动响应。

<a id="frameworks" name="frameworks"></a>
### 框架与工具

#### mjlab: A Lightweight Framework for GPU-Accelerated Robot Learning（2026）
- 原文 PDF：https://arxiv.org/pdf/2601.22074.pdf
- 笔记：将 Isaac Lab 的 manager-based API 与 MuJoCo Warp GPU 仿真结合，提供轻量、可组合的训练环境以及速度跟踪、运动模仿和操作参考任务。
- 开源项目：[mjlab](../network-open-source/development-tools/mjlab.md)

<a id="surveys" name="surveys"></a>
### 综述

#### Learning-based legged locomotion: State of the art and future perspectives（IJRR 2025）
- 原文 PDF： [原文链接](https://arxiv.org/pdf/2406.01152.pdf) - 笔记：学习方法腿足式机器人运动控制综述：系统概括过去几年学术界与工业界相关成果并展望未来方向（佐治亚理工，Georgia Tech）。

<a id="misc" name="misc"></a>
### 其他资料（暂无笔记）
- Robot Dynamics Lecture Notes（2017）— [原文 PDF](https://rsl.ethz.ch/education-students/lectures/robotdynamics.html)
- Dynamic Locomotion in the MIT Cheetah 3 Through Convex Model-Predictive Control — [原文 PDF](https://dspace.mit.edu/handle/1721.1/138000.2)
- A Low Cost Modular Actuator for Dynamic Robots — [原文 PDF](https://dspace.mit.edu/handle/1721.1/118671)

返回总览：[README.md](../README.md)
