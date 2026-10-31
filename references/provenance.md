# 来源与取舍

研究日期：2026-10-31。

结构模板：agent-rules 的 templates/ruleset-proj-sample；保留 schemaVersion、namespace、rules/profiles 清单与独立 references 结构。namespace 使用 personal，未修改 agent-rules 的 builtin。

参考项目：BaoCut，固定 revision d96a1a9c2e366e47e28b41616d2b5e3abea736f5：

- https://github.com/JimLiu/baocut/blob/d96a1a9c2e366e47e28b41616d2b5e3abea736f5/AGENTS.md
- https://github.com/JimLiu/baocut/blob/d96a1a9c2e366e47e28b41616d2b5e3abea736f5/docs/development-workflow.md
- https://github.com/JimLiu/baocut/blob/d96a1a9c2e366e47e28b41616d2b5e3abea736f5/docs/repo-conventions.md
- https://github.com/JimLiu/baocut/blob/d96a1a9c2e366e47e28b41616d2b5e3abea736f5/LICENSE

借鉴组织思想：短入口、按任务下钻、单一事实源、验证与影响相称、工作区成果归属清晰。本文库正文原创，没有复制参考项目的规则段落。

BaoCut 固定版本采用 Community License v1.0，含商业分发等限制；不将其许可当作 MIT，不将其项目代码、文档或模板移入本库。没有对本库选择新的公开分发许可证。

个人确认的取舍：

- 自主完成已授权目标，仅遇阻或重大取舍提问。
- 不强制逐次独立评审，不为 low advisory 重开审计循环。
- 完成目标或阶段任务后自动本地 commit，push 仍需明确要求。
- 工程、界面、语言规则按需启用，三条通用规则常驻。
- 不照搬固定目录、Electron/Web 多端、英文字符串禁令或特定包管理器。

本库不写入个人真实用户配置，不内置本会话的专用交互 wrapper；使用环境自己的交互机制与优先级约定。
