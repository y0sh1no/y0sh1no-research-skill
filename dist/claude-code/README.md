# Claude Code 本地安装与使用

将本包 `.claude/skills/` 中需要的完整目录复制到科研项目的 `.claude/skills/`，或个人 `~/.claude/skills/`。保留每项 skill 内的参考和许可文件。

在会话中使用 `/dl-paper-reading` 等项目 skill 命令，或直接描述科研任务。示例：`使用 dl-baseline-selection 比较这些仓库，帮我选择开发基座和论文比较对象。`

可使用当前会话的原生子 agent；委派时附相关 skill 或必要参考，确认它可访问的文件和上下文。独立评阅先用共同稿件和量表，再核查关键分歧。需要更强隔离时检查实际历史继承方式，不把新角色名称当成独立判断保证。无需开启 Agent Teams。

安装规则见 [Skills](https://code.claude.com/docs/en/skills)，子 agent 能力见 [Sub-agents](https://code.claude.com/docs/en/sub-agents)。本版完成文件检查，未启动 Claude Code 客户端验收。
