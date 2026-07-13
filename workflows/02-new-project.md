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

2. 创建目录和温层子目录：

   **PowerShell：**
   ```powershell
   $project = "<project>"
   New-Item -ItemType Directory -Force -Path "projects/$project/verification"
   New-Item -ItemType Directory -Force -Path "projects/$project/mistakes"
   New-Item -ItemType Directory -Force -Path "projects/$project/decisions"
   New-Item -ItemType Directory -Force -Path "projects/$project/handoffs"
   ```

   **Bash：**
   ```bash
   PROJECT="<project>"
   mkdir -p "projects/$PROJECT"/{verification,mistakes,decisions,handoffs}
   ```

3. 复制热入口模板：

   **PowerShell：**
   ```powershell
   Copy-Item templates/quick-start.md "projects/$project/quick-start.md"
   Copy-Item templates/00-current-state.md "projects/$project/00-current-state.md"
   ```

   **Bash：**
   ```bash
   cp templates/quick-start.md "projects/$PROJECT/quick-start.md"
   cp templates/00-current-state.md "projects/$PROJECT/00-current-state.md"
   ```

4. 填写 `projects/<project>/quick-start.md`：
   - 业务项目路径
   - 项目用途
   - 技术栈
   - 常用启动/构建/测试命令
   - 默认验证方式
   - 受保护文件
   - 项目特殊规则入口（如有）

5. 填写 `projects/<project>/00-current-state.md`：只写当前状态、当前阻塞、下一步和不能重复犯的错误。

6. 在 `workspace-index.md` 的项目表里登记项目（替换或删除占位行后添加）。

7. 如果项目有特殊规则，新增 `projects/<project>/project-rules.md`，并在 `quick-start.md` 中引用。

## Done when

- `workspace-index.md` 能找到新项目。
- 新项目有 `quick-start.md` 和 `00-current-state.md`。
- 四个温层子目录（verification、mistakes、decisions、handoffs）已创建。
- Agent 新对话能按 5 个热入口读到项目当前状态。
- 受保护文件和验证方式已经写清楚。
