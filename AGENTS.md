# AGENTS.md

本仓库是项目共用的 Agent 工作记忆仓库。任何 Agent 在本仓库内工作时，必须先读取本文件。

## 新对话启动规则

每次新对话，Agent 默认读取以下热入口：

1. 根目录 `AGENTS.md`（本文件）
2. `workspace-index.md`
3. `projects/<当前项目>/quick-start.md`
4. `projects/<当前项目>/00-current-state.md`

开始工作前，用一句话确认：已读什么、当前任务、当前状态、下一步、禁止事项。

## 记忆更新规则

- 重要事实写入 Markdown，不留在聊天记录。
- 当前状态优先写 `00-current-state.md`。
- 长期规则沉淀到 `standards/`。
- 决策写 `decisions/`，错误写 `mistakes/`，验证证据写 `verification/`。
- 临时产物（截图、日志、临时脚本）不入库。

写入分层和升级条件见 `standards/governance.md`。

## 收口规则

工作结束或阶段性完成时，必须：

1. 更新 `00-current-state.md`
2. 重要结论写入对应目录（`decisions/`、`mistakes/`、`verification/`）
3. 确认临时产物已清理

## 防重复犯错

- 新任务先查 `mistakes/` 和 `decisions/` 是否有相关记录。
- 做完成声明前必须运行验证命令并报告结果。
