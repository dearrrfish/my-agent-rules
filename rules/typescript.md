---
schemaVersion: 1
id: personal/typescript
title: TypeScript 的类型与边界
description: 保持类型可信，按现有工具链验证 TypeScript 变更。
activation:
  mode: path
  paths: ['**/*.ts', '**/*.tsx', '**/*.mts', '**/*.cts']
---
遵循项目 tsconfig、模块格式和公共导出约定。为边界和公开接口表达明确类型；在外部输入进入系统时做运行时校验，不用 any 或双重断言代替验证。

异步资源有明确生命周期，处理实际可能失败的路径，保留原始错误。类型和实现共同约束允许状态，避免散落的非空断言掩盖遗漏。

修改后使用项目现有的类型检查和相关行为测试；没有脚本时先查工具链，不猜测固定 npm/pnpm 命令，也不为了个人偏好换包管理器。
