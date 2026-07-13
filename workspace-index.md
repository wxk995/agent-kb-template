# 工作区索引

当前工作区路径：`<WORKSPACE_ROOT>`

## 设计理由

**为什么热入口要薄**：每个 Agent 新对话的上下文是有限的。启动时只读最少的必需信息（5 个热入口），遇到具体问题再按 experience-index 路由深读。不是为了省 token，是为了确保 Agent 每次启动真正读完必要信息——文档太多时 Agent 会选择性跳过。

**为什么业务仓库和知识库分离**：知识库的规则、实验、迭代频率远高于业务代码。混在一起会导致业务仓库的 git 历史被知识库提交污染，也让知识库不敢频繁变更。

**为什么按项目登记**：不同项目的技术栈、规则、受保护文件、当前状态都不同。按项目登记（workspace-index → projects/<项目>/）让 Agent 能一次性拿到"这个项目需要知道的所有上下文"。

## 全局资料

- `workflows/`：操作流程入口，告诉人和 Agent 遇到不同任务时该读什么、改什么、什么时候收口。
- `standards/`：跨项目长期规范。
- `global/experience-index.md`：经验路由表（按关键词路由到经验文件）。
- `global/profile.md`：用户画像（Agent 写作/判断前必读）。

## 常用操作入口

| 场景 | 读取 |
|------|------|
| 第一次使用本模板 | `workflows/01-new-reader.md` |
| 新增项目记忆 | `workflows/02-new-project.md` |
| 新开 Agent 对话 | `workflows/03-start-agent-session.md` |
| 更新知识库内容 | `workflows/04-update-knowledge.md` |
| 工作结束收口 | `workflows/05-closeout.md` |
| 知识库瘦身 | `workflows/06-prune-knowledge.md` |
| Agent 完成后自检 | `workflows/07-agent-review.md` |

## 已登记项目

| 项目名 | 类型 | 项目记忆路径 |
|--------|------|-------------|
| `<项目名>` | `<技术栈或项目类型>` | `projects/<项目名>/` |

> 上面这行是占位示例。首次使用时请替换为你的真实项目，或直接删除这行。

## 添加新项目

新增项目时不要临时猜目录，按 `workflows/02-new-project.md` 执行。
