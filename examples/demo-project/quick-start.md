# task-tracker 快速开始

新对话入口。

## 默认读取

每次新对话，Agent 优先读取以下热入口：

1. 根目录 `AGENTS.md`
2. `workspace-index.md`
3. `projects/task-tracker/quick-start.md`（本文件）
4. `projects/task-tracker/00-current-state.md`

## 开工检查

- 先看 `git status --short`
- 不修改 `package.json` 和 `tsconfig.json` 中的依赖版本，除非任务明确要求。
- 新增复杂逻辑时，补充必要注释，避免解释显而易见的代码。
- 不确定当前任务流程时，先回到根目录 `workflows/` 选择对应操作流程。

## 按需读取

根据任务类型，按需读取温层文档：

- 操作流程：`workflows/`
- 知识库治理规则：`standards/governance.md`
- 验证记录：`projects/task-tracker/verification/`
- 决策记录：`projects/task-tracker/decisions/`
- 错误记录：`projects/task-tracker/mistakes/`

## 冷文档

历史归档、外部参考资料默认不进入新对话读取链路。
