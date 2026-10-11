# 深度学习科研能力库

版本：0.1.0。提供 18 项科研能力和 1 项数学支持能力，由用户安排当前科研任务。Work 版默认单 agent。

本仓库分发可直接加载的 skills 和插件包。维护源与构建工具位于原本地 `research-skills` 工程；这里保留全部四端 `dist`，并增加网页安装入口。

## Claude 账号安装：跨项目使用

1. 在 Claude 的 **Settings → Capabilities** 开启代码执行与文件创建。团队账号也需要组织允许使用及创建 skills。
2. 打开 **Customize → Skills → ＋ → Create skill → Upload a skill**。
3. 从 [claude-upload](claude-upload/) 下载需要的单 skill ZIP，上传后启用。每个 ZIP 包含一个完整 skill 文件夹及其参考材料；不要上传整套平台 ZIP 到单 skill 上传入口。
4. 使用同一账号开始新的 `claude.ai/code` 会话，账号启用的 skills 会同步加载。可运行 `/skills` 查看，再描述科研任务。

官方说明：[上传 skills](https://support.claude.com/en/articles/12512180-use-skills-in-claude)、[云端账号同步](https://code.claude.com/docs/en/skills#use-skills-in-cowork-and-cloud-sessions)。

## Claude Code 网页端：仓库级使用

本仓库根目录已包含 [.claude/skills](.claude/skills/)。在 `claude.ai/code` 连接本仓库，并选择包含这些文件的分支后，新会话可发现项目 skills。

如果要在自己的科研代码仓库中使用，将需要的完整 skill 文件夹复制到那个仓库的 `.claude/skills/`，提交并推送，或使用上面的账号安装方式跨项目加载。

## ChatGPT Work 网页端：GitHub marketplace 导入

需要工作区管理员使用 **Admin → Plugins → Add → Import marketplace**：

| 字段 | 值 |
|---|---|
| Source | `https://github.com/y0sh1no/y0sh1no-research-skill` |
| Path | 留空：marketplace 位于仓库根目录 |
| Branch | `main` |

导入后为 `research-skills-work` 配置可用范围，用户从 Plugins 安装，在 Work 对话输入 `@` 选择插件。

根目录 [.agents/plugins/marketplace.json](.agents/plugins/marketplace.json) 指向 [Work 插件](dist/work/plugins/research-skills-work/)。也可使用 `Path = dist/work` 导入该目录已有的独立 marketplace；两种方式选择一种即可。

如果当前账号没有管理员入口，但可以使用 `@Plugin Creator`，可提供技能文件和参考材料，通过对话创建个人插件。此方式不代表整套 ZIP 可以一键导入。

官方说明：[GitHub 导入](https://learn.chatgpt.com/docs/enterprise/plugin-management)、[插件创建与使用](https://learn.chatgpt.com/docs/build-plugins)。

## ChatGPT Work 桌面端

克隆本仓库，选择仓库根目录作为项目目录，重启 ChatGPT 桌面客户端。在 Plugins Directory 中选择本地来源“科研能力库”，安装 `research-skills-work`，再在 Work 对话中通过 `@` 选择插件。

也可下载 [Work 整包](dist/research-skills-work-0.1.0.zip)，解压后将含 `.agents` 和 `plugins` 的目录作为项目目录。

官方说明：[本地 marketplace 与安装](https://developers.openai.com/plugins/build/plugins#install-a-local-plugin-manually)。

## 其他平台与下载

- [Codex 分发包](dist/codex/)：完整复制需要的 skill 到项目 `.agents/skills/` 或个人 `~/.agents/skills/`。
- [Claude Code 本地分发包](dist/claude-code/)：完整复制需要的 skill 到项目 `.claude/skills/` 或个人 `~/.claude/skills/`。
- [全部平台分发文件](dist/)：包含四端整包 ZIP、资源、来源记录及许可。
- [单 skill 上传 ZIP](claude-upload/)：用于 Claude 的账号上传入口。

覆盖文献调研、方向与前沿、精读、复现、基线、问题发现、诊断、创新性核查、方法构思、实验设计、实现、分析、论文叙事、写作、审稿、修改、rebuttal、交付及数学支持。协作方式依当前宿主工具选择；Work 版默认单 agent。

发布前验证了资源引用、插件路径、许可和归档完整性；未运行模型评测，也未验证实际账号安装。后续以使用反馈改进。

## 许可与来源

新编内容采用 [MIT](LICENSE)。保留的第三方归属和许可见 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) 与 [LICENSES](LICENSES/)。
