---
schemaVersion: 1
id: personal/ops-security
title: 跨平台与外部依赖安全边界
description: 隔离平台差异与不可信外部资源，严控路径、命令执行与许可证边界。
tags: [lean, ops, security]
activation:
  mode: task
  instruction: 涉及跨平台路径/进程、系统集成、引入依赖、外部规则库或许可证边界时读取。
conflictsWith:
  - personal/platforms
  - personal/dependencies
---
- 列出实际受影响的平台与宿主，查证路径大小写、权限、换行与进程信号差异；平台专有逻辑通过清晰边界隔离，不用当前机器通过推断其他平台通过，未实测平台在交付中注明。
- 路径操作使用项目路径接口并处理空格与非 ASCII 名称，校验规范路径与根目录边界，拒绝逃逸符号链接与不支持的资源类型；系统命令使用安全参数数组（argv），不拼接不可信 shell 文本。
- 区分文档证据、编译 fixture、模拟测试与真实宿主加载；未知宿主能力明确拒绝或走已声明降级，不向猜测的用户配置目录写入。
- 优先复用项目已有能力；新增依赖说明具体需求并同步 lockfile，核查版本、来源与许可证（仓库可读不代表正文可重新分发）。只读研究外部仓库时不执行来源 hooks、过滤器或未知脚本；凭据仅走现有认证机制，不嵌入 URL、锁文件、生成物或日志。
