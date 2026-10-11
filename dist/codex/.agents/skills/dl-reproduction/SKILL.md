---
name: dl-reproduction
description: "复现指定论文或方法，运行作者实现、检查协议并诊断结果偏差。Use for paper reproduction and replication troubleshooting."
---

# 论文与方法复现

先读取[运行环境](references/library/packaging/runtime/portable.md)。从指定论文、已有仓库或用户的运行问题直接进入。

## 确定复现对象

明确要复现的是某张表、训练过程、推理结果、关键现象还是独立重实现；用户已说明就沿用。区分加载预训练权重后评估、重新训练和独立重实现，它们证明的事情不同。

记录决定结果含义的论文/代码版本、数据与划分、checkpoint、预处理、指标实现、训练预算和硬件。已有项目结构和日志可复用。缺少关键资料时先查正文、附录、配置和源码；无法确定的选择按影响说明。

## 执行与偏差诊断

1. 沿现有入口建立最短有效路径：真实样本 → 核心计算 → 指标/输出。检查实际标签、形状和损失，避免用占位结果证明复现成功。
2. 按用户授权的范围运行。环境或资源有限时可先验证推理/小规模路径，注明与完整目标的差别；必要检查见[实现参考](references/library/shared/implementation.md)。
3. 比较论文值、作者 checkpoint 值和本次结果，按[协议参考](references/library/shared/data-evaluation.md)对齐条件。保留运行失败及配置变化。
4. 结果偏差先查数据/指标/checkpoint，再查训练步数、有效 batch、精度、优化器与随机性。一次改变一个关键因素或采用能定位原因的对照；不静默调参直到“接近论文”。

## 交付

给出复现目标、实际命令/配置、运行状态、结果对照、差异及最有依据的诊断。运行成功、复现数值和复现机制分别判断。对随机波动按[统计参考](references/library/shared/statistics.md)解释；没有多次运行就不补造区间。

## 可选协作

可分工核查公式—代码、数据—指标、环境—运行条件，或独立复算关键值。并发执行前对齐 GPU 与输出目录，见[协作方法](references/library/shared/collaboration.md)。
