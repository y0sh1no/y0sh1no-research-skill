# Codex 安装与使用

本包包含 18 项独立科研能力和数学支持，资源已随每项 skill 提供。把本包 `.agents/skills/` 中需要的目录复制到科研项目的 `.agents/skills/`，或个人 `~/.agents/skills/`。不要只复制 `SKILL.md`。

可以在 CLI/IDE 使用 `$dl-paper-reading` 等名称显式选择，也可描述任务让 Codex 匹配。示例：`$dl-diagnostic-experiments 根据这些失败样本，设计能区分数据覆盖与目标函数问题的实验。`

任务内协作按实际子 agent 工具和随包参考开展。独立判断应明确原始材料、上下文继承和返回证据；无需预先配置固定模型或外部 reviewer 服务。缺少委派工具时顺序完成多视角分析。

安装路径及发现方式见 [Build skills](https://learn.chatgpt.com/docs/build-skills)，协作入口见 [Subagents](https://learn.chatgpt.com/docs/agent-configuration/subagents)。本版完成静态打包检查，尚未验证你的客户端实际加载。
