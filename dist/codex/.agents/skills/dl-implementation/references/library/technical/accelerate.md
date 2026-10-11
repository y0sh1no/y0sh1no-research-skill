# Accelerate 的训练语义

适用：当前项目的 Accelerate 训练、梯度累积、分布式指标或恢复问题。核对日期：2026-10-11；参考动态文档，项目版本及执行结果另行核验。

## 更新与累积

明确谁拥有设备放置、包装模型/优化器/loader、loss 缩放和更新。标准路径使用 `Accelerator`、`prepare`、`accumulate` 与 `backward`；框架处理累积时不要再次手动缩放同一 loss。尾批与 dataloader 同步行为会影响最后一次更新。[梯度累积](https://huggingface.co/docs/accelerate/en/usage_guides/gradient_accumulation)

对于变长序列，先明确目标是样本均值还是有效 token 均值。各 micro-batch 均值再简单平均一般不等于总 token loss；需要核对跨累积步和进程的分子/分母。学习率调度按实际 optimizer 更新及框架配置核查，而非仅看循环迭代次数。

## 聚合与状态

分布式评估注意采样补齐造成的重复样本、尾批和非等大小 batch；选择适合当前数据的聚合。`gather_for_metrics` 为指标聚合提供处理路径，`save_state`/`load_state` 用于训练状态恢复；模型权重导出与继续训练状态不是同一交付物。[Accelerator API](https://huggingface.co/docs/accelerate/en/package_reference/accelerator)

多进程只由约定进程写共享报告/最终产物，所有需要集体参与的操作保持进程一致。不能让每个进程都无意识地重复保存、评估或启动其他任务。

## 故障与研究比较

先查启动命令、配置、进程/设备分配及实际 strategy，再判断是否为模型问题。移到分布式后核对有效 batch、数据顺序、loss 与指标定义变化；“代码运行了”不代表单卡与多卡协议等价。

来源：AI-research-SKILLs/08-distributed-training/accelerate 经重写。去除“若干行即可处理所有场景”的泛化描述；未复制或运行上游训练脚本。
