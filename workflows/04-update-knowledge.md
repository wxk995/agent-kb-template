# Workflow: 更新知识库

## When to use

用户要求更新、补充、纠正、合并、记录知识，或当前任务产生了稳定结论时使用。

## Read first

1. `AGENTS.md`
2. `standards/governance.md`
3. `workspace-index.md`
4. `global/experience-index.md`
5. 当前项目的 `quick-start.md` 和 `00-current-state.md`

## Steps

1. 先判断更新类型：
   - 当前状态变化：更新 `projects/<project>/00-current-state.md`
   - 新增项目：按 `02-new-project.md`
   - 新增可复用经验：更新 `global/experience-index.md` 或项目级经验文件
   - 做出技术取舍：新增或更新 `projects/<project>/decisions/`
   - 错误被解决：新增或更新 `projects/<project>/mistakes/`
   - 完成验证：新增或更新 `projects/<project>/verification/`
   - 需要交接：新增或更新 `projects/<project>/handoffs/`
2. 列出要改的文件和原因，让用户确认。
3. 修改正文文件，避免把聊天原文整段粘进去。
4. 如果新增了可检索经验，更新 `global/experience-index.md` 或项目索引。
5. 检查是否产生重复内容；如果重复，保留权威版本，其余改为引用或归档候选。
6. 运行最小验证：检查 Markdown 可读、路径存在、索引能路由到新内容。

## Done when

- 更新内容能被热入口或经验索引找到。
- 当前状态、验证、错误、决策、交接分别落在正确目录。
- 没有把一次性日志、临时输出或未验证猜测写成长期事实。
- 已说明修改了哪些文件和为什么。
