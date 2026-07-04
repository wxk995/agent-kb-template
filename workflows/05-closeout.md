# Workflow: 工作收口

## When to use

工作结束、用户要求总结/沉淀/记录、准备交接到新对话或其他 Agent 时使用。

## Read first

1. `AGENTS.md`
2. `standards/governance.md`
3. `projects/<project>/quick-start.md`
4. `projects/<project>/00-current-state.md`
5. 本次任务实际修改或产出的文件

## Steps

1. 列出本次任务的事实结果：完成了什么、验证了什么、没有完成什么。
2. 区分稳定结论和临时过程：
   - 稳定结论写入知识库。
   - 临时日志、测试输出、截图、缓存不长期保存。
3. 更新 `projects/<project>/00-current-state.md`，只保留当前状态和下一步。
4. 按类型写入温层：
   - 验证证据写 `verification/`
   - 错误和避免方式写 `mistakes/`
   - 技术取舍写 `decisions/`
   - 交接信息写 `handoffs/`
5. 如果形成跨项目经验，再更新 `global/experience-index.md`。
6. 检查热层文件是否超过 50 行；超过时进入 `06-prune-knowledge.md`。
7. 向用户报告：写入文件、验证结果、剩余风险、下一步。

## Done when

- 聊天里的重要结论已经落到 Markdown。
- 下一次新对话只读热入口也能继续。
- 临时内容已清理或明确不入库。
- 没有把未验证内容写成已完成事实。
