# task-tracker 快速开始

> **这是虚构教学示例。** 所有项目名、路径、技术栈、数据和记录均为教学目的编造。
> 正式使用时，将内部路径 `examples/demo-project/` 替换为 `projects/<你的项目名>/`。

| 项目信息 | |
|---------|---|
| 路径 | `~/code/task-tracker`（业务代码仓库，非本知识库路径） |
| 用途 | 待办事项管理全栈应用（标签、优先级、到期提醒） |
| 技术栈 | Node.js + Express + SQLite / React + TypeScript / JWT + bcrypt |
| 启动 | `cd server && npm run dev` / `cd client && npm start` |
| 构建 | `cd client && npm run build` |
| 测试 | `npm test`（Vitest）/ `npm run test:e2e`（Playwright） |
| 验证 | `npm test` + 手动验证关键流程（登录→创建→编辑→删除） |
| 受保护文件 | `package.json`、`tsconfig.json`、`.github/workflows/`、`migrations/`（仅追加） |
| 项目规则 | API 先契约后实现；schema 变更入 decisions/；React Context 不引入额外状态库 |

## 热入口（每次新对话默认读取）

1. `AGENTS.md`
2. `workspace-index.md`
3. `global/agent-rules/agent.md`
4. `examples/demo-project/quick-start.md`（本示例文件）
5. `examples/demo-project/00-current-state.md`

## 开工检查

- `git status --short` → 确认并保留现有工作树状态
- 不修改受保护文件，除非任务明确要求
- 流程不确定 → 根目录 `workflows/` 选择对应操作流程

## 按需路由

| 场景 | 读取 |
|------|------|
| 操作流程 | `workflows/` |
| 治理规则 | `standards/governance.md` |
| 经验检索 | `global/experience-index.md` |
| 验证记录 | `examples/demo-project/verification/` |
| 决策记录 | `examples/demo-project/decisions/` |
| 交接记录 | `examples/demo-project/handoffs/` |
| 报错/复发/受保护文件 | `examples/demo-project/mistakes/`（按需，不全量读） |

冷文档默认不读。扩展文件 `active-work.md`、`project-index.md` 为可选，不列入默认最小结构。
