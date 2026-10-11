# Claude Code 网页端部署

目标产品为 `claude.ai/code`。将本包 `.claude/skills/` 中需要的目录加入用户的科研仓库并随仓库提交；在网页端连接该仓库、选取包含这些文件的分支。skill 内容和相对资源随云端克隆提供。

云端访问不到本机个人 skills、未提交文件或本机符号链接目标。数据、依赖和计算资源按云端会话实际配置使用；指引文件不会提供 GPU、网络或凭据。不要把本机安装检查写成云端运行成功。

会话中显式使用技能名称或描述任务。原生子 agent 是否可调用以当前会话工具为准；可以调用时使用随包协作参考。多个网页会话并行和一个任务内的协作是不同运行方式，Agent Teams 不作为依赖。

此部署方式依据[项目级 Skills](https://code.claude.com/docs/en/skills)与[云端仓库运行](https://code.claude.com/docs/en/claude-code-on-the-web)组合，尚未在实际网页会话验证。用户自然使用时反馈发现/调用或资源问题即可。
