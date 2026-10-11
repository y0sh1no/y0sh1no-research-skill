---
name: dl-implementation
description: "实现、调试和执行当前深度学习研究任务，核对方法、训练与评估代码。Use for research implementation and experiment debugging."
---

# 科研实现与执行

先读取[运行环境](references/library/packaging/runtime/portable.md)。完成用户指定的方法改动、训练、评估或故障诊断，复用已有项目结构和授权。

## 实现判断

1. 从真实入口读相关模块、配置和调用点。确认输入/输出、关键公式、梯度路径、训练/推理差异，以及本次改动要验证什么。
2. 按[实现参考](references/library/shared/implementation.md)将方法对应到代码。对数据划分、指标、归一化、信息可用性等影响研究含义的选择查证或说明；常规代码组织直接合理决定。
3. 选择最小有效改动，保留可诊断失败。外部输入边界检查关键条件；内部遵循已有契约，兼容分支/重试/默认值对应真实需求。
4. 验证被改变的行为：可手算算子、梯度检查、真实小批数据、少量训练步骤、checkpoint 恢复或指标复算。按实际风险选择检查，不为低影响编辑建立完整测试体系。
5. 用户要求执行时运行当前授权范围，记录命令、有效配置、版本、日志和结果；训练/评估状态据实际输出判断。

## 技术资料按需加载

涉及对应内容时读取：

- [训练与复现配置](references/library/technical/training.md)：loss、梯度累积、精度、状态恢复、故障定位。
- [PEFT/LoRA](references/library/technical/peft.md)：目标模块、冻结、缩放、标签掩码与保存。
- [Accelerate](references/library/technical/accelerate.md)：分布式、累积、聚合及状态保存。
- [Lightning](references/library/technical/lightning.md)：优化控制权、日志与 checkpoint 语义。

先查当前安装版本及其官方文档，资料中的动态入口不代表某个依赖组合已经实测。

## 交付与协作

说明改了什么、影响哪些研究含义、实际运行了什么及尚未验证项。OOM 后调整精度/batch/样本过滤等需要记录其比较影响；失败不能返回伪造指标。

可按接口和文件边界分工，理论—实现核对可独立进行。并发 GPU、共享输出和整合责任按[协作方法](references/library/shared/collaboration.md)安排。
