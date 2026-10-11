# ChatGPT Work 插件包

本包在 `plugins/research-skills-work/` 提供 portable `plugin.json` 和 19 项自包含 skills，采用单 agent 科研辅助。它不发起子 agent，也不建议常规切换 Ultra。多视角请求由当前 agent 按不同问题与证据顺序分析。

## 使用入口

支持本地 marketplace 的桌面端可把本包作为项目目录：`.agents/plugins/marketplace.json` 已指向其中插件。进入该项目后，按插件界面提供的本地来源安装，再用 `@` 选择插件或其中的 skill。发现文件不等于插件已经安装或启用。

在 Work 网页端使用时，需要把插件接入该账户/工作区支持的插件分发入口。可向可用的 Plugin Creator 提供插件目录内容和参考材料，或采用工作区支持的 GitHub 分发。`ZIP` 是分发文件，本版不承诺网页端可直接上传 ZIP 安装；没有执行账号安装或发布。

用户使用时仍需提供当前任务的论文、代码或结果，或使用已连接的检索/文件工具。该插件不附带外部服务和额外访问权限。

## 核查范围

portable manifest、默认 `skills/` 布局与本地 marketplace 依据 OpenAI 官方 [Package your plugin](https://developers.openai.com/plugins/build/plugins)。Work 的插件选择与创建见 [Build plugins](https://learn.chatgpt.com/docs/build-plugins)。

本版只完成内容、路径、JSON 和归档完整性检查，尚未验证实际账户的插件安装、资源加载或工具可用性。用自然科研任务反馈即可，无需专门评测。
