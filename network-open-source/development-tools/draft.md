# Draft：参数化机器人设计与 MJCF 生成工具

> 类型：机器人设计 / MuJoCo / MJCF 生成 / 强化学习评估

## 项目简介

[Draft](https://github.com/davidhnguyen2000/draft) 是 MIT 的机器人设计探索工具（David Nguyen、Marcelo Coelho、Sangbae Kim）。它把一份简短的参数表、一棵带算术表达式的运动学树和根节点网格描述，直接编译成可用于物理仿真的 MuJoCo MJCF 模型，不需要先完成 CAD 装配再导出机器人描述文件。

生成器不预设具体机型：人形、四足以及其他由串联链组成的机器人共用同一套生成代码。论文报告在笔记本 CPU 上，12 自由度四足约 50 ms、29 自由度人形约 202 ms 即可生成一个通过校验的 MJCF。这样可以在控制训练开始前快速扫描腿长、站立姿态、执行器选型等设计变量。代码以 MIT 许可开源，仓库附带人形与四足两套示例规格。

为了避免生成“仿真里存在、现实中造不出来”的机器人，Draft 用 114 个集成执行器和 49 份公开机器人描述的统计趋势补全质量、减速比、体积、尺寸比例和转子惯量，并对设计做可制造性检查；论文还用四台现成商用机器人的孪生模型验证了质量趋势（几何平均倍误差 1.10×），并用同一套两阶段强化学习课程比较了三台四足设计。

## 核心机制

Draft 的输入可以理解为三部分：

1. **参数表**：给出连杆长度、密度、电机峰值扭矩与空载转速等自由参数；
2. **运动学树**：节点字段是引用参数表的算术表达式，因此半径、质量等可以由电机或父连杆尺寸推导，减少手工参数；
3. **根节点网格**：根连杆由截面多边形和平面放样成封闭网格，用来布置四肢。

模型由四类连杆基元拼装：basic link（结构圆柱 + 远端电机）、sphere link（点接触末端）、foot link（面接触足端）和 root link（自定义根部网格）。生成器把尺寸变化自动传导到视觉、碰撞和惯性属性，并借助 MuJoCo 的 `inertiafromgeom` 计算基元连杆的质量与惯量。关节采用峰值扭矩和空载转速描述的直流电机模型，位置增益按扭矩缩放，使不同关节的跟踪误差对应相近的可用扭矩比例。

参数补全依赖从真实硬件拟合的趋势：执行器质量随峰值扭矩约按 0.666 次幂增长，减速比由空载转速决定，体积由扭矩和减速比估计，转子惯量按半径四次方计算并折算为关节 armature。结构质量则按连杆类别分别拟合。生成器还会执行可行性检查，拒绝没有对应硬件可实现的设计。

## 快速开始

```bash
conda env create -f environment.yml && conda activate draft
export PYTHONNOUSERSITE=1
pip install -e ".[editor,twins,figures,dev]" -c constraints.txt

python scripts/robot_tuner.py                        # 浏览器参数编辑器
python scripts/generate_robot.py --robot quadruped   # 无界面生成，输出到 generated/
```

生成 MJCF 和做设计扫描只需要笔记本 CPU；训练内置的四足强化学习任务需要 CUDA GPU，安装 `.[rl]` 额外依赖后按 `docs/tasks.md` 运行。官方项目页提供基于 Pyodide 和 MuJoCo WebAssembly 的在线构建器，可以直接拖动滑杆生成人形或四足，并查看执行器趋势与可行性警告。

## 适用场景与边界

- 在控制训练前快速比较多组机构尺寸、站立构型和执行器方案；
- 为强化学习批量生成同一环境下的不同机器人模型，观察性能瓶颈落在哪个关节；
- 用公开硬件数据校准设计参数，避免完全不切实际的性能评估；
- 执行器统计只覆盖集成模块，不含未集成的定制转子-定子对；论文将其视为可辩护的保守基线，而不是性能上限；
- 作为设计探索的“中间层”，而不是完整 co-design 优化器或 CAD 替代品：论文明确不包含设计优化器，生成的是中等保真度模型，且当前连杆库不支持并联机构。

## 相关链接

- [GitHub 仓库](https://github.com/davidhnguyen2000/draft)
- [项目主页与在线构建器](https://davidhnguyen2000.github.io/draft-site/)
- [论文（arXiv）](https://arxiv.org/abs/2609.38405)
- [论文 PDF](https://arxiv.org/pdf/2609.38405)
- [项目视频](https://youtu.be/egzlEqfwwLU)
