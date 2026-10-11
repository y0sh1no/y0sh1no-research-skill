# PEFT / LoRA 的研究判断

适用：用户已经采用或正在比较 PEFT、LoRA、量化适配器。核对日期：2026-10-11。参考当前官方动态文档；具体模型、PEFT/Transformers/PyTorch/量化后端版本组合需在项目中核验，本库未训练模型。

## 参数与机制

查看实际模块名称和存储布局再选择 `target_modules`。标准 LoRA 更新可写为 ΔW = (α/r)BA；`use_rslora` 改变缩放，因此 rank 消融要同时考虑缩放规则。`modules_to_save` 指定额外训练/保存模块。核查冻结参数与 optimizer，不能只看“已插入 adapter”的日志。[LoRA 配置](https://huggingface.co/docs/peft/en/package_reference/lora)

rank、目标模块、初始化、缩放、dropout 和额外训练参数共同决定容量与优化。比较 rank 时说明保持了哪些条件；相同 rank 不保证跨结构相同参数量。默认初始化可保持初始函数不变，其他初始化应按实际方法检查。[LoRA 初始化](https://huggingface.co/docs/peft/en/package_reference/lora#initialization)

## 数据与量化

核查 causal LM 标签移位由谁负责、padding 和提示部分的 loss 掩码、截断/打包、tokenizer 与特殊 token。padding 与 EOS 共用 ID 时不能简单屏蔽所有同 ID token，否则可能把真实 EOS 监督也去掉。

QLoRA 同时改变存储、计算和训练参数；检查量化准备、计算 dtype、梯度及支持的保存/合并路径，按当前版本的官方[量化指南](https://huggingface.co/docs/peft/en/developer_guides/quantization)操作。显存可行性由模型、上下文、batch、激活和优化器决定，不使用“某大小模型必能放进某显卡”或固定质量损失百分比的保证。

## 实现与比较

检查目标层确实被命中、训练参数比例/梯度符合计划、实际损失有效。保存 adapter 时记录基座标识/修订、tokenizer、配置与额外训练模块；重新加载并比较预测，再判断产物是否可用。

对比全参微调、不同适配器或不同目标层时说明总参数、训练参数、预算、外部数据、选模和推理成本。不要仅凭参数更少推出质量更好或性能不损失。

来源：AI-research-SKILLs/03-fine-tuning/peft 的任务与关键配置经重写；原始示例未移植。正文涉及 API 已对照上述官方文档，运行状态与 API 核对状态分别记录。
