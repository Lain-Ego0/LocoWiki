# Go2 Backflip：Isaac Gym 后空翻训练与真机部署

> 类型：算法复现 / 四足机器人 / 强化学习 / Sim2Real

[uw-backflip](https://github.com/uwvwko-zzz/uw-backflip) 基于 Genesis-backflip，将后空翻训练迁移到 Isaac Gym，并完成 Unitree Go2 真机部署。仓库提供从训练、策略导出、MuJoCo Sim2Sim 到真机测试的流程。

- **机器人**：Unitree Go2。
- **训练与验证**：Isaac Gym 训练，MuJoCo Sim2Sim 验证。
- **部署**：导出 ONNX 策略，通过 Unitree SDK2 部署；项目报告已完成真机后空翻测试。

安装、训练和部署步骤及真机测试注意事项见[项目仓库](https://github.com/uwvwko-zzz/uw-backflip)。
