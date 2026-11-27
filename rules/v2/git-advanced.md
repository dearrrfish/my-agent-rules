---
schemaVersion: 1
id: personal/git-advanced
title: 复杂工作区提交与清理
description: 在混合改动、分支隔离与工作树管理场景下安全隔离并清理本任务产物。
tags: [lean, git]
activation:
  mode: task
  instruction: 处理混合未提交改动、分 hunk 暂存、分支隔离或清理 worktree/构建产物时读取。
conflictsWith:
  - personal/git
---
- 修改前查看 `git status`，区分已有或并发改动；默认分支需要隔离时先建立任务分支或独立 worktree。
- 同文件混合用户与本任务改动时按 hunk 精确暂存，提交前审阅 staged diff；无法可靠分离时先说明具体冲突，不得将用户改动一并提交。
- 只读任务或无有效文件变化不创建空提交；凭据与临时产物不得进入提交，提交信息描述最终结果并遵循仓库格式与署名要求。
- 只清理确认归属本任务的 worktree、分支、预览服务与临时构建目录；删除前确认有效成果已安全保存在提交或约定位置，不删除含未归属改动的工作树。
