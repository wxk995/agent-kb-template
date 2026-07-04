# Workflow: 新增项目记忆

## When to use

为一个业务项目、学习项目或长期任务建立新的 Agent 记忆目录时使用。

## Read first

1. `AGENTS.md`
2. `workspace-index.md`
3. `templates/quick-start.md`
4. `templates/00-current-state.md`
5. `standards/governance.md`

## Steps

1. 确定项目名，使用短、稳定、不会频繁改名的目录名。
2. 创建目录：

   ```bash
   mkdir -p projects/<project>/{verification,mistakes,decisions,handoffs}
   ```

3. 复制热入口模板：

   ```bash
   cp templates/quick-start.md projects/<project>/quick-start.md
   cp templates/00-current-state.md projects/<project>/00-current-state.md
   ```

4. 填写 `projects/<project>/quick-start.md`：写项目路径、技术栈、常用命令、受保护文件和默认验证方式。
5. 填写 `projects/<project>/00-current-state.md`：只写当前状态、当前阻塞、下一步和不能重复犯的错误。
6. 在 `workspace-index.md` 的项目表里登记项目。
7. 如果项目有特殊规则，新增 `projects/<project>/project-rules.md`，并在 `quick-start.md` 中引用。

## Done when

- `workspace-index.md` 能找到新项目。
- 新项目有 `quick-start.md` 和 `00-current-state.md`。
- Agent 新对话能按热入口读到项目当前状态。
- 受保护文件和验证方式已经写清楚。
