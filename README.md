# Agent KB Template

一个面向 AI Agent 协作的文件化知识库模板。用 Markdown + Git 管理 Agent 的工作记忆，
按"热/温/冷"三层按需读取，避免上下文膨胀。

不绑定任何特定 Agent 平台、编程语言或业务领域。

## 解决什么问题

- **Agent 每次新对话都要重新解释项目背景** → 热入口文件一次写清楚
- **Agent 重复犯同样的错误** → 错误库 + 经验路由表
- **多 Agent 同时改文件互相覆盖** → 同一时间一个 writer
- **上下文窗口被历史信息塞满** → 热/温/冷三层按需读取
- **重要决策和验证结果散落在聊天记录里** → 结构化落盘

## 快速开始

### 1. 复制模板

```bash
git clone https://github.com/your-org/agent-kb-template.git my-project-kb
cd my-project-kb
```

### 2. 创建你的第一个项目记忆

```bash
mkdir -p projects/my-app/verification projects/my-app/mistakes projects/my-app/decisions projects/my-app/handoffs

cp templates/quick-start.md     projects/my-app/quick-start.md
cp templates/00-current-state.md projects/my-app/00-current-state.md
```

### 3. 填写内容并告诉 Agent

编辑 `projects/my-app/00-current-state.md`，填入项目路径、当前状态和下一步。
在 `workspace-index.md` 中登记新项目。

在你的 Agent 入口文件（如项目根目录的 AGENTS.md）中加入：

```
开始工作前先读取：
<WORKSPACE_ROOT>/projects/my-app/00-current-state.md
<WORKSPACE_ROOT>/projects/my-app/quick-start.md
```

### 4. 开始使用

每次新对话，Agent 先读热入口，确认当前状态后再开始工作。
工作结束后，重要结论写到对应目录。

## 目录结构

```
<WORKSPACE_ROOT>/
├── AGENTS.md                  # Agent 入口规则
├── workspace-index.md         # 工作区与项目索引
├── README.md                  # 本文件
├── LICENSE                    # MIT
│
├── templates/                 # 文档模板（复制即用）
│   ├── decision.md            # 决策记录
│   ├── handoff.md             # 交接记录
│   ├── mistake.md             # 错误记录
│   ├── verification.md        # 验证记录
│   ├── quick-start.md         # 项目快速开始
│   └── 00-current-state.md    # 当前热状态
│
├── standards/                 # 框架规范
│   └── governance.md          # 知识库治理规则
│
├── examples/                  # 完整示例
│   └── demo-project/          # task-tracker 示例项目
│
└── projects/                  # 项目记忆（按项目创建）
    └── <项目名>/
        ├── quick-start.md
        ├── 00-current-state.md
        ├── verification/
        ├── mistakes/
        ├── decisions/
        └── handoffs/
```

## 核心概念

### 热层 — 每次新对话必读

新对话启动时，Agent 默认只读 3-4 个热入口文件，不翻全库。

- `AGENTS.md`：Agent 行为规则
- `workspace-index.md`：有哪些项目、全局资料在哪
- `projects/<项目>/quick-start.md`：项目快速入口
- `projects/<项目>/00-current-state.md`：当前热状态

热层只写当前状态和下一步，不堆砌历史。

### 温层 — 按需读取

根据任务类型选择性读取：

- `standards/`：长期规范
- `verification/`：验证记录
- `decisions/`：决策记录
- `mistakes/`：错误库
- `handoffs/`：交接记录

温层保存规范、验证、交接等内容；新对话不默认全读。

### 冷层 — 历史追溯

旧项目快照、外部参考资料、阶段性上下文等仅历史追溯时读取。
默认不进入新对话读取链路。

## 模板说明

| 模板 | 用途 | 什么时候创建 |
|------|------|------------|
| `quick-start.md` | 项目快速入口 | 项目初始化时 |
| `00-current-state.md` | 当前热状态 | 项目初始化时，每次收口更新 |
| `decision.md` | 记录重要决策及原因 | 做出影响后续工作的选择时 |
| `handoff.md` | 交接当前工作状态 | 暂停/转交工作时 |
| `mistake.md` | 记录错误和避免方式 | 发生可复现的错误时 |
| `verification.md` | 记录验证命令和结果 | 完成功能/修复后 |

## 不做什么

- 不绑定特定 Agent 平台或编程语言
- 不替代项目本身的文档体系
- 不存储 API 密钥、密码等敏感信息
- 不把聊天记录当事实源
- 不保留临时截图、日志、一次性测试输出

## 许可

MIT
