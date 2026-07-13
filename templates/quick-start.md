# <PROJECT_NAME> 快速开始

> 新对话入口。

| 项目信息 | |
|---------|---|
| 路径 | `<业务代码仓库的本地绝对路径>` |
| 用途 | `<一句话描述>` |
| 技术栈 | `<语言、框架、数据库、关键依赖>` |
| 启动 | `<启动命令>` |
| 构建 | `<构建命令>` |
| 测试 | `<测试命令>` |
| 验证 | `<每次修改后如何验证>` |
| 受保护文件 | `<文件1>、<文件2>（说明原因）` |
| 项目规则 | `projects/<PROJECT_NAME>/project-rules.md`（如有特殊规则） |

## 热入口（每次新对话默认读取）

1. `AGENTS.md`
2. `workspace-index.md`
3. `global/agent-rules/agent.md`
4. `projects/<PROJECT_NAME>/quick-start.md`（本文件）
5. `projects/<PROJECT_NAME>/00-current-state.md`

## 开工检查

- `git status --short` → 确认并保留现有工作树状态
- 确认受保护文件和禁止事项
- 流程不确定 → 根目录 `workflows/` 选择对应操作流程

## 按需路由

| 场景 | 读取 |
|------|------|
| 操作流程 | `workflows/` |
| 治理规则 | `standards/governance.md` |
| 经验检索 | `global/experience-index.md` |
| 验证记录 | `projects/<PROJECT_NAME>/verification/` |
| 决策记录 | `projects/<PROJECT_NAME>/decisions/` |
| 交接记录 | `projects/<PROJECT_NAME>/handoffs/` |
| 报错/复发/受保护文件 | `projects/<PROJECT_NAME>/mistakes/`（按需，不全量读） |

冷文档默认不读。
