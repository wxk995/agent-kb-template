# AGENTS.md

> 以下规则由用户制定和维护。任何修改须经本人确认。

本仓库是项目共用的 Agent 工作记忆仓库。任何 Agent 在本仓库内工作时，先读本文件，再按热入口继续。

## 启动链路

默认热入口顺序：
1. `AGENTS.md`
2. `workspace-index.md`
3. `global/agent-rules/agent.md`
4. `projects/<project>/quick-start.md`
5. `projects/<project>/00-current-state.md`

开工前用一句话确认：已读文件、任务、状态、下一步、禁止事项、不能重复犯的错误。

## 工作流路由

遇到操作类任务时先读 `workflows/README.md`，不要自己猜流程。
常用入口：新读者 `01-new-reader`；新项目 `02-new-project`；新对话 `03-start-agent-session`；更新知识 `04-update-knowledge`；收口 `05-closeout`；瘦身 `06-prune-knowledge`；自检 `07-agent-review`。

## 必读触发

- 涉及总结、说明、方案、对外分享、知识库规则、判断取舍或"我的风格"时，先读 `global/profile.md`；画像只作偏好参考，不伪装用户。
- 遇到报错、bug、异常、技术方案、受保护文件、关键配置，或用户提到"之前/又出现/上次"时，先查 `global/experience-index.md` → 对应经验文件，再分析。
- 回答上述问题时先写回执：`旧方案检索：已查 global/experience-index.md，命中：... / 未命中，自行分析如下。`

## 协作边界

默认角色由用户指定；同一批文件同一时间只允许一个 Agent 写入。多 Agent 文件化协作不是默认流程，仅在用户明确启用后使用。

## 硬规则

- 写知识库前列出文件清单和原因，等用户确认。
- 未经用户明确要求，不提交代码、推送或创建 PR。
- 受保护文件以项目 `project-rules.md` 为准。
- 完成声明前运行验证并说明结果；测试完成后删除临时内容。
- 外部工具不进默认流程；`archive/` 只作历史追溯。

## 知识库维护

分层、升级和瘦身见 `standards/governance.md`；重要事实写 Markdown，不留聊天。热状态优先写 `projects/<project>/00-current-state.md`，长期规则沉淀到 `standards/`。
