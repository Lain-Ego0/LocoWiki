# Go2 / Go2W SuperMimic：基于世界模型的四足控制

> 类型：算法复现 / 四足机器人 / 世界模型 / mjlab

这两个项目将 SuperMimic 的世界模型训练思路用于四足机器人控制，并使用 mjlab 和 MuJoCo Warp 进行仿真。

## Go2：追逐与躲避

[go2-supermimic](https://github.com/Zhengtianjin/go2-supermimic) 面向 Unitree Go2，提供追逐目标和躲避障碍的仿真任务，包括平地、障碍物和复杂地形。项目使用学习得到的世界模型及想象轨迹上的反向传播训练策略，并提供训练代码和预训练策略。

## Go2W：轮足地形控制

[go2w-supermimic](https://github.com/uwvwko-zzz/go2w-supermimic) 基于 Go2-SuperMimic，面向 Unitree Go2W 轮足机器人训练速度控制策略，包含平地、楼梯、平台、斜坡和碎石地形。策略不接收地形扫描，训练时世界模型和 critic 使用特权信息；项目目前在仿真中验证。

人形机器人全身动作跟踪的相关复现，包括 [supermimic_vibed](https://github.com/zita-ch/supermimic_vibed)，见 [SuperMimic 复现](supermimic.md)。
