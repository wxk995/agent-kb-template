# Agent KB Template

一个从真实多 Agent 协作中长出来的知识库框架。不是AI生成的模板，是我和三个 Agent 磨合了几个月之后的"工作记忆系统"。

## 这不是又一个"最佳实践"文档

市面上的知识库模板大多是：列一堆目录 → 告诉你"把文档放进去" → 然后就没有然后了。

这个框架解决的是我在真实开发中踩过的坑：

### 坑 1：Agent 开新对话就失忆

每个 Agent 每次新对话都不知道当前项目状态、之前做了什么、踩过什么坑。我把这些写进 5 个"热入口"文件，Agent 启动时自动读取，不超过一屏——读完就知道当前状态。

### 坑 2：规则写太多 Agent 直接跳过

我试过写一个 100 行的规则文件。Agent 读过去就跳过了——太长。最后收敛到**每条规则不超过一句话，能执行的才算数**。热入口只放 5 个文件，现在 AGENTS.md 控制在 50 行以内。

### 坑 3：知识库没有"人"

所有文档都是 Agent 写的第三人称祈使句——"应该这样""禁止那样"。别人翻开仓库看不到是谁的、谁在主导。后来我加了 AUTHOR.md（给人看，这是谁的仓库）和 profile.md（给 Agent 看，这个人什么风格、讨厌什么、什么必须自己拍板）。Agent 在写总结、做判断时先读画像——产出开始有人的烙印了。

### 坑 4：Agent 不会主动查经验库

遇到问题时 Agent 倾向于自己分析，不会去查"上次怎么解决的"。我把它变成了硬规则：**先查后做**——遇到报错、方案设计、保护文件、用户说"之前遇到过"时，必须先查经验路由表，写检索回执（"已查 xxx，命中/未命中"），不写回执视为未检索。现在 Agent 没法绕过了。

### 坑 5：知识库只会长不会缩

每个条目都在往里加，从来不删。三个月后就是垃圾堆。后来加了瘦身规则：热层超过 50 行触发检查、温层 6 个月未碰归档、重复内容合并。收口时顺带检查——不是定时触发，是"感觉臃肿了就说一句"。

## 核心创新

### 1. 热/温/冷三层治理

| 层 | 什么时候读 | 放什么 |
|------|------|------|
| **热** | 每次启动 | 当前状态、下一步、硬规则（5个文件） |
| **温** | 按需 | 长期规范、验证记录、决策、错误库 |
| **冷** | 历史追溯 | 旧项目、参考资料、历史上下文 |

**设计理由**：Agent 的上下文窗口是有限的。热层必须短到 Agent 不会跳过——我定的是 50 行以内。如果启动链路太长，Agent 会选择性忽略，等于没写。

### 2. 用户画像

不是"Agent 使用手册"，是"Agent 理解用户的镜子"：

- 我是谁、我习惯怎么写、我会怎么写和不会怎么写
- 我的决策偏好（先小后大、先稳后新）
- 我讨厌的事（擅自修改、虚报完成度、闷头做完不给方案）
- 什么必须我拍板（最终方案、规则变更、受保护文件）

Agent 在写总结、做判断、调整规则时先读画像。定位是"参考我的偏好，不伪装成本人"。

### 3. 先查后做 + 检索回执

遇到问题 → 先查经验路由表 → 写回执 → 确认无现成方案 → 再自行分析。把这个流程从"建议"变成了 Agent 无法跳过的硬步骤。

### 4. 自瘦身闭环

收口时顺带检查热入口是否臃肿、温层是否有僵尸文件、是否有重复内容。不是自动化——是我说"瘦身"时才触发，避免 Agent 自作主张删重要内容。

## 快速开始

### 1. 复制模板

```bash
git clone https://github.com/wxk995/agent-kb-template.git my-project-kb
cd my-project-kb
```

### 2. 填写 AUTHOR.md 和 profile.md

这两个文件决定了 Agent 产出的"人味"：
- `AUTHOR.md`：告诉别人这是谁的仓库、为什么建
- `global/profile.md`：告诉 Agent 你是什么风格、讨厌什么、什么必须自己拍板

### 3. 创建项目记忆

```bash
mkdir -p projects/my-app/{verification,mistakes,decisions,handoffs}
cp templates/quick-start.md     projects/my-app/quick-start.md
cp templates/00-current-state.md projects/my-app/00-current-state.md
```

编辑 `00-current-state.md` 填入真实状态。在 `workspace-index.md` 登记项目。

### 4. 配置 Agent 全局入口

在每个 Agent 的全局配置里写入知识库路径和"先查后做"规则。详见 `global/agent-rules/agent.md` 模板。

## 目录结构

```
<WORKSPACE_ROOT>/
├── README.md
├── AUTHOR.md                   # 这是谁的仓库，为什么建
├── AGENTS.md                   # Agent 入口规则 + 硬约束
├── workspace-index.md          # 工作区与项目索引
├── LICENSE                     # MIT
│
├── global/
│   ├── profile.md              # 用户画像（Agent 写作/判断前必读）
│   ├── experience-index.md     # 经验路由表（按关键词查文件）
│   └── agent-rules/
│       └── agent.md            # Agent 角色规则模板
│
├── standards/
│   └── governance.md           # 三层治理 + 瘦身 + 经验升级规则
│
├── templates/                  # 文档模板
│   ├── decision.md
│   ├── handoff.md
│   ├── mistake.md
│   ├── verification.md
│   ├── quick-start.md
│   └── 00-current-state.md
│
├── examples/                   # 完整示例
│   └── demo-project/
│
└── projects/                   # 项目记忆
    └── <项目名>/
        ├── quick-start.md
        ├── 00-current-state.md
        ├── verification/
        ├── mistakes/
        ├── decisions/
        └── handoffs/
```

## 不做什么

- 不绑定特定 Agent 平台或编程语言
- 不替代项目本身的代码文档
- 不存 API 密钥、密码等敏感信息
- 不把聊天记录当事实源
- 不保留临时截图、日志、一次性测试输出
- 不加自动定时系统——手动触发够用，自动化越管越乱

## 许可

MIT
