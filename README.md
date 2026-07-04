<p align="center">
  <strong>Agent KB Template</strong>
</p>

<h1 align="center">代理知识库模板</h1>

<p align="center">
  给 Codex、Claude、Hermes 等 AI Agent 使用的项目工作记忆模板。
  <br />
  让新对话先读正确上下文，遇到问题先找旧方案，工作结束后把经验沉淀下来。
</p>

<p align="center">
  <img alt="docs" src="https://img.shields.io/badge/docs-Markdown-0969da" />
  <img alt="agents" src="https://img.shields.io/badge/agents-Codex%20%7C%20Claude%20%7C%20Hermes-1a7f37" />
  <img alt="license" src="https://img.shields.io/badge/license-MIT-6e7781" />
</p>

---

## 这是什么

这是一个面向 AI Agent 的知识库模板。它不是业务项目仓库，也不是工具源码仓库，而是夹在“聊天记录”和“项目代码”之间的一层工作记忆。

它要解决的问题很具体：

- 新对话不知道项目当前状态。
- 旧方案散在聊天记录里，同类问题反复重查。
- 规则越写越多，Agent 启动时抓不住重点。
- 验证记录、错误复盘、交接信息没有固定位置。
- 文档越来越多之后，人和 Agent 都不知道该先看什么。

这个模板的核心不是“多写文档”，而是把文档分层，并给出可执行的操作流程。

## 适合谁

适合这些场景：

- 你经常用 Codex、Claude、Hermes 或其他 Agent 参与项目开发。
- 你有多个项目，希望 Agent 新对话能快速接上上下文。
- 你希望错误、验证、决策、交接不只停留在聊天里。
- 你愿意用 Markdown 和 Git 管理长期可复用的项目记忆。

不适合这些场景：

- 只想要一个自动化工具平台。
- 只做一次性聊天，不需要长期记忆。
- 不愿意维护任何项目状态或验证记录。

## 3 分钟快速开始

### 1. 复制模板

```bash
git clone https://github.com/wxk995/agent-kb-template.git my-agent-kb
cd my-agent-kb
```

### 2. 先读上手流程

```text
workflows/01-new-reader.md
```

这个文件会告诉你第一轮应该读什么，避免从整个仓库里猜入口。

### 3. 填写你的身份和偏好

- `AUTHOR.md`：给人看的说明，写这个知识库是谁维护的、为什么建。
- `global/profile.md`：给 Agent 看的用户画像，写你的表达习惯、决策偏好、边界和禁忌。

### 4. 创建第一个项目记忆

```bash
mkdir -p projects/my-app/{verification,mistakes,decisions,handoffs}
cp templates/quick-start.md projects/my-app/quick-start.md
cp templates/00-current-state.md projects/my-app/00-current-state.md
```

然后编辑：

- `projects/my-app/quick-start.md`：项目路径、技术栈、常用命令、受保护文件。
- `projects/my-app/00-current-state.md`：当前状态、当前阻塞、下一步。
- `workspace-index.md`：登记这个项目。

完整步骤见 `workflows/02-new-project.md`。

### 5. 新开 Agent 对话时这样说

```text
请先按本仓库的 AGENTS.md 和 workflows/03-start-agent-session.md 启动。
项目名：my-app。
```

Agent 应该先读取 5 个热入口，再开始执行任务。

## 按任务进入 workflow

`workflows/` 是这个模板的操作层。Markdown 负责保存知识，workflow 负责告诉人和 Agent 该怎么用这些知识。

| 你要做什么 | 先读 |
|------|------|
| 第一次使用本模板 | `workflows/01-new-reader.md` |
| 给新项目建立记忆 | `workflows/02-new-project.md` |
| 新开 Agent 对话 | `workflows/03-start-agent-session.md` |
| 更新、补充、纠正文档 | `workflows/04-update-knowledge.md` |
| 工作结束后沉淀结论 | `workflows/05-closeout.md` |
| 文档太多、重复、过期 | `workflows/06-prune-knowledge.md` |
| Agent 写完后复查 | `workflows/07-agent-review.md` |

如果不知道该看什么，不要全仓库乱翻，先看 `workflows/README.md`。

## 核心设计

### 1. 热/温/冷三层

| 层 | 什么时候读 | 放什么 |
|------|------|------|
| 热层 | 每次新对话默认读 | 当前状态、下一步、硬规则 |
| 温层 | 按任务需要读 | 验证、决策、错误、交接、长期规范 |
| 冷层 | 历史追溯时读 | 旧资料、参考资料、归档内容 |

热层要短。它的目标是让 Agent 每次都能读完，而不是把所有背景都塞进去。

### 2. 先查后做

遇到报错、方案设计、关键配置、受保护文件，或用户提到“上次/之前/又出现”，Agent 必须先查：

```text
global/experience-index.md
```

查完要写检索回执，说明命中哪个文件，或者确认未命中后再自行分析。

### 3. 用户画像

`global/profile.md` 不是让 Agent 模仿用户口吻，而是让 Agent 知道：

- 用户是谁，做什么项目。
- 用户习惯什么表达方式。
- 用户讨厌什么行为。
- 哪些事情必须用户本人拍板。

它的定位是：参考偏好，不伪装成本人。

### 4. 收口沉淀

工作结束时不要只在聊天里说“完成了”。稳定结论应该写回对应位置：

- 当前状态：`projects/<project>/00-current-state.md`
- 验证记录：`projects/<project>/verification/`
- 错误复盘：`projects/<project>/mistakes/`
- 技术取舍：`projects/<project>/decisions/`
- 交接信息：`projects/<project>/handoffs/`

具体步骤见 `workflows/05-closeout.md`。

### 5. 瘦身规则

知识库只会增长是不行的。这个模板默认规则是：

- 热层文件超过 50 行，触发瘦身检查。
- 温层文件长期不用，考虑归档。
- 同一规则重复出现，只保留一个权威版本。
- 删除或归档前先列清单确认。

具体步骤见 `workflows/06-prune-knowledge.md`。

## 目录结构

```text
<WORKSPACE_ROOT>/
├── README.md
├── AUTHOR.md                   # 给人看的作者和维护说明
├── AGENTS.md                   # Agent 入口规则和硬约束
├── workspace-index.md          # 工作区与项目索引
├── LICENSE
│
├── workflows/                  # 操作流程：读什么、改什么、什么时候收口
│   ├── README.md
│   ├── 01-new-reader.md
│   ├── 02-new-project.md
│   ├── 03-start-agent-session.md
│   ├── 04-update-knowledge.md
│   ├── 05-closeout.md
│   ├── 06-prune-knowledge.md
│   └── 07-agent-review.md
│
├── global/
│   ├── profile.md              # 用户画像
│   ├── experience-index.md     # 经验路由表
│   └── agent-rules/
│       └── agent.md            # Agent 通用行为规则
│
├── standards/
│   └── governance.md           # 三层治理、瘦身、经验升级规则
│
├── templates/                  # 项目文档模板
│   ├── decision.md
│   ├── handoff.md
│   ├── mistake.md
│   ├── verification.md
│   ├── quick-start.md
│   └── 00-current-state.md
│
├── examples/
│   └── demo-project/           # 示例项目记忆
│
└── projects/
    └── <project>/
        ├── quick-start.md
        ├── 00-current-state.md
        ├── verification/
        ├── mistakes/
        ├── decisions/
        └── handoffs/
```

## 不做什么

- 不绑定特定 Agent 平台或编程语言。
- 不替代业务项目自己的代码文档。
- 不保存 API 密钥、密码等敏感信息。
- 不把聊天记录原文当事实源。
- 不长期保留临时截图、日志、一次性测试输出。
- 不强依赖某个平台的 skill 系统；`workflows/` 是平台无关操作流程。
- 不默认引入自动定时系统；先把手动流程跑顺。

## 许可证

MIT
