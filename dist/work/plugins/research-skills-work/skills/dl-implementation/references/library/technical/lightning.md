# Lightning 的研究实现边界

适用：已有 Lightning 项目的训练步骤、优化控制、指标或 checkpoint 问题。核对日期：2026-10-11；具体安装版本另查，本库未执行 Lightning 训练。

## 优化控制权

自动优化中 `training_step` 返回损失，框架负责反向与更新。自定义多优化器或特殊更新可用手动优化，明确管理清梯度、`manual_backward`、step、累积和 scheduler；不能两边同时更新。官方源文档说明这一区分及调度器行为。[Optimization 文档源码](https://raw.githubusercontent.com/Lightning-AI/pytorch-lightning/master/docs/source-pytorch/common/optimization.rst)

学习率调度的 step/epoch 单位、梯度累积和真正更新次数要一致。自定义 optimizer 步骤保留框架所需的 closure/精度/策略语义；绕过包装器可能改变行为，核对当前版本接口。

## 指标与保存

读取实际 `self.log` 与 metric 实现，检查 step/epoch 聚合、batch size 权重、分布式同步及状态重置。同步多个局部均值不能自动得到全局 macro F1 或其他非线性指标；需要聚合足够的统计量或预测。

明确 checkpoint 按哪个验证指标、方向与频率选取。区分最后一次与最佳 checkpoint，训练恢复包含哪些状态；更换 checkpoint 选择规则会改变比较含义。

## 现有项目优先

沿用项目实际使用的 `lightning.pytorch` 或 `pytorch_lightning` 版本与导入方式，不为组织代码自动迁移整仓库。检查 hooks、strategy、precision 与日志工具的当前语义；缺少对应 API 时查官方版本页，不批量添加兼容回退。

来源：AI-research-SKILLs/08-distributed-training/pytorch-lightning 的框架任务经重写。官方网页在本次抓取中仅返回跳转壳，关键优化语义改查官方仓库文档源码；其他具体 API 未声称完整核验。
