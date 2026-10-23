# SuperMimic：可微世界模型人形全身控制的两份复现

> 类型：论文复现 / 人形机器人 / 世界模型 / BPTT / Unitree G1

## 论文与任务

[SuperMimic](https://arxiv.org/abs/2610.28480)（Qiayuan Liao 等，CoRL 2026 Oral）用一个可微世界模型摊销大规模人形全身动作跟踪的学习成本。世界模型从仿真日志拟合，和策略在同一个循环里训练；策略在短视野 imagined rollout 上做 BPTT，奖励、观测和终止信号由解析头计算。

论文在 Unitree G1 上验证 LAFAN1 40 条动作和 BONES-SEED 约 12.95 万条动作，并报告单卡 3 小时超过 128 卡 7 天基线、9.8 小时双卡零失败。截至 2026-10-24，项目页未列出官方训练代码；目前已有两份公开复现。

## 两份复现对照

| 项目 | 论文数据 | zita-ch | CuboiLeo |
| :--- | :--- | :--- | :--- |
| 数据 | LAFAN1 40 条；BONES-SEED 129,514 条 | LAFAN1 40 条 | LAFAN1 40 条；BONES-SEED 129,943 条 |
| 硬件 | 1×H100 | 1×RTX PRO 6000 | 1×/4×RTX 5090 |
| 观测口径 | 93 维本体 | 99 维（+6） | 93 维；e3 为 93+9 |
| LAFAN1 最高回报 | 0.82 @1.2h | 0.829 @1.47h，0/40（+6） | 0.904 @3.3h，3/40（+9） |
| 严格论文观测 | 0.82 @1.2h | 未报告 | e2：0.56，9/40，1.8 h |
| BONES-SEED | >0.90 @3h，25/129,514 失败 | 未实现 | 0.934/0.935（2000 子集，+9） |

数字为作者报告；zita 和 Cuboi 的最高回报都使用了额外观测，且 Cuboi 的评测分母不同，不能直接排名。Cuboi 的论文口径正式结果 e6/e7 仍在进行中。

## 主要差异

两份都实现了 71 维世界模型、2048×3 MLP、H=32 BPTT 和解析奖励/观测头，差异主要在以下四点。

### Actor 输入与 Goal

| 输入 | zita-ch | CuboiLeo 论文口径 | CuboiLeo e3 |
| :--- | :--- | :--- | :--- |
| 单帧本体观测 | 99 | 93 | 93 |
| 10 帧本体历史 | 990 | 930 | 930 |
| 每帧参考 Goal | 73 | 68 | 68 |
| 当前额外 Goal 特征 | 0 | 0 | +9 |
| Actor Goal Encoder 输入 | 730 | 680 | 689 |
| Actor 潜变量 | 32 | 32 | 32 |

zita 在本体观测中加了 6 维 `R^T R_ref` 相对根部朝向，并进入 10 帧历史；它包含相对 yaw，真机部署仍需要航向估计。zita 的 Goal 每帧 73 维，主要是未来参考根部的相对位姿、速度、关节位置和关节速度。

Cuboi 的 93 维本体观测对应论文 Table A.1 的口径，e3 另在 Goal 组加 9 维 BeyondMimic 风格 anchor 相对位姿，Goal Encoder 输入从 680 变成 689。它的 68 维 Goal 由关节位置、关节速度、投影重力、角速度、线速度和根部高度组成。论文未完整披露 Goal 组成，不能把分数差异直接归因于世界模型或 BPTT。

### 评测归一化

zita 用 `ret / ((clip_len - 1) * MAX_STEP_REWARD)`，分母是完整参考动作长度；Cuboi 用 `ret / (max_reward * max(steps, 1))`，分母是实际执行步数。提前摔倒时 Cuboi 的分母会缩短，失败片段可能被高估，因此 `0.829 / 0/40` 和 `0.904 / 3/40` 不能直接比较。公平对比应按完整 clip 长度重算。

### 动作噪声

按论文设定，Actor 是确定性的，噪声用于扩展世界模型拟合的数据分布。Cuboi 把 clean action 留给上一动作观测和动作变化惩罚，把含噪动作送入仿真和世界模型；zita 在 `env.step` 前加噪，含噪动作会成为下一帧的 `a_prev`。两种做法都能训练，但会改变观测和奖励分布，对比时应固定口径。

### 世界模型与工程范围

两份世界模型都是 71 维状态、2048×3 MLP。zita 直接预测状态增量；Cuboi 预测速度增量并显式积分，最后一层零初始化。

工程上，zita 是轻量 Isaac Lab 3 Docker 实现，关闭自碰撞、加入 500 次仅更新世界模型的预热、MLP 使用 bf16；作者自述为 AI 快速实现、未经充分审查。Cuboi 提供 BONES-SEED 全量数据管线、多卡数据并行、可微 FK 数值对拍、PAPER_SPEC 和实验日志，世界模型使用学习的终止头。这些差异影响训练稳定性和工程成本，但不足以单独判断哪套世界模型更好。

## 相关链接

- [论文 arXiv](https://arxiv.org/abs/2610.28480)
- [SuperMimic 项目主页](https://supermimic.github.io)
- [zita-ch/supermimic_vibed](https://github.com/zita-ch/supermimic_vibed)
- [CuboiLeo/SuperMimic-Reproduced](https://github.com/CuboiLeo/SuperMimic-Reproduced)
- [CuboiLeo PAPER_SPEC](https://github.com/CuboiLeo/SuperMimic-Reproduced/blob/main/docs/PAPER_SPEC.md)
- [CuboiLeo 实验日志](https://github.com/CuboiLeo/SuperMimic-Reproduced/blob/main/docs/EXPERIMENTS.md)
- [zita-ch MILESTONES](https://github.com/zita-ch/supermimic_vibed/blob/main/MILESTONES.md)
- [LAFAN1 Retargeting Dataset](https://huggingface.co/datasets/lvhaidong/LAFAN1_Retargeting_Dataset)
