# 我的 Agent 规则库

面向个人开发的原创规则，使用 agent-rules 的 ruleset schema v1。它独立于工具源码维护；借鉴 BaoCut 的短入口和任务路由思想，规则正文按个人约定重新编写。

默认风格：自主推进已授权目标，验证随影响变化，保护已有工作；完成目标或阶段任务后自动本地 commit，push 另行授权。不为 low advisory 反复开启审计。

## 选择 Profile

### v0.2 精简系列（推荐用于现代前沿/均衡模型）

| Profile | 适用范围 |
| --- | --- |
| personal/lean-core | 单屏精简常驻微内核（含自主推进、安全边界、实证沟通、最小抽象与阶段本地提交） |
| personal/lean | **推荐默认**；lean-core + 按需加载的复杂 Git、视觉自检 UI、契约与风险验证、阶段交接 |
| personal/lean-ops | lean + 按需加载的跨平台与外部依赖安全边界 |

v0.2 针对现代前沿模型精简了常驻上下文与通用工程常识（淘汰 `navigation`/`architecture`/`debugging`/`typescript`/`python`/`localization` 独立规则），将阶段本地 commit 升格为常驻微内核要点，强化了界面真实渲染的多模态自检与阶段 `handoff.md` 交接，并通过 `conflictsWith` 防止同一 Profile 混选 v0.1 与 v0.2 等价规则。

### v0.1 经典系列（保留用于向后兼容与 A/B 对比）

| Profile | 适用范围 |
| --- | --- |
| personal/core | 三条精简常驻规则与按任务读取的 Git 阶段提交规则 |
| personal/engineering | core + 定位、契约、测试、调试、架构、跨平台和依赖 |
| personal/ui | engineering + 界面验收、文案和本地化 |
| personal/typescript | engineering + TypeScript 路径规则 |
| personal/python | engineering + Python 路径规则 |

日常新项目优先用 `personal/lean`（最小可用可选 `personal/lean-core`）；需要对比或兼容旧工作区时可继续使用 v0.1 Profile。条件规则的加载取决于宿主能力；portable 模式可能生成“先读取”指引，这依赖 agent 遵循指引，不是自动加载保证。

## 本地使用

在 agent-rules CLI 所在目录执行（先审阅预览）：

```sh
node bin/ar.mjs ruleset add ~/codes/my-agent-rules --name personal
node bin/ar.mjs install --scope project --profile personal/engineering --tool codex --dry-run --json
```

规则注册会建立内容快照；编辑本库后需显式 ruleset update personal，再安装时使用 --update-sources 接受新内容，先 dry-run 审阅。真实用户目录安装和外部发布由独立任务授权，本库创建不隐含安装。

Claude 可使用 --tool claude；共享 AGENTS.md 的目标须选同一 Profile。Claude 默认独立 CLAUDE.md，可使用 --tool-profile claude=personal/typescript 选择不同 Profile。--claude-instructions agents|both 会将 Claude 加入共享入口组，要求 Profile 一致。

## 维护方式

每条规则包含触发条件、具体行为和适用边界；长示例放 references。避免同一正文在多个位置维护，不将机器路径、凭据、固定测试命令或项目专用目录写进通用规则。

编辑后使用 agent-rules 的 loadCatalog / resolveProfile / compile 验证全部 Profile，确认项目和用户 scope、入口预算、引用资源及适配诊断。不要通过测试伪装成真实宿主验收。

本库未选择公开分发许可证，manifest 故意不含 license。不要因参考项目或模板可读而推断其授权；来源与原创边界见 [参考记录](references/provenance.md)。
