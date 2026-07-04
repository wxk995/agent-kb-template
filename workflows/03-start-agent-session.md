# Workflow: 新开 Agent 对话

## When to use

每次新开 Codex、Claude、Hermes 或其他 Agent 对话，准备继续某个项目时使用。

## Read first

1. `AGENTS.md`
2. `workspace-index.md`
3. `global/agent-rules/<agent>.md`
4. `projects/<project>/quick-start.md`
5. `projects/<project>/00-current-state.md`

## Steps

1. 确认当前 Agent 名称和目标项目名。
2. 按热入口顺序读取 5 个文件。
3. 如果任务涉及总结、方案、规则调整或判断取舍，再读 `global/profile.md`。
4. 如果任务涉及报错、方案设计、受保护文件、关键配置，或用户提到"上次/之前/又出现"，先查 `global/experience-index.md`。
5. 用一句话向用户回执：已读文件、当前任务、当前状态、下一步、禁止事项、不能重复犯的错误。
6. 只有在任务需要历史追溯时，才继续读取温层或冷层文件。

## Done when

- Agent 已知道当前项目状态和边界。
- 不需要全量翻库也能开始当前任务。
- 如果触发先查后做规则，已经给出检索回执。
