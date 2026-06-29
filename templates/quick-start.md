# <PROJECT_NAME> 快速开始

新对话入口。

## 默认读取

每次新对话，Agent 优先读取以下热入口：

1. 根目录 `AGENTS.md`
2. `workspace-index.md`
3. `projects/<PROJECT_NAME>/quick-start.md`（本文件）
4. `projects/<PROJECT_NAME>/00-current-state.md`

## 开工检查

- 先看 `git status --short`
- 确认当前项目边界和禁止事项
- 检查 `mistakes/` 是否有和当前任务相关的历史错误

## 按需读取

根据任务类型，按需读取：

- 知识库治理规则：`standards/governance.md`
- 验证记录：`projects/<PROJECT_NAME>/verification/`
- 决策记录：`projects/<PROJECT_NAME>/decisions/`
- 错误记录：`projects/<PROJECT_NAME>/mistakes/`

## 冷文档

历史归档、外部参考资料默认不进入新对话读取链路。
