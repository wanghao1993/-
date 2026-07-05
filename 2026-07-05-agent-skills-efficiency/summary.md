# 摘要：如何创建 Skills 来提高工作效率

## 核心观点

很多人用 AI 工具时仍然把重点放在 prompt 上，但当某类任务反复出现时，更有效的做法是把重复流程封装成 skill。

prompt 解决“这一次怎么说”，skill 解决“以后遇到同类任务，都按什么方法做”。

## 文章结构

1. 区分规则、记忆和 skill：
   - `AGENTS.md`、`CLAUDE.md`、`.cursor/rules` 更适合放长期约束。
   - 记忆适合保存项目事实。
   - skill 适合封装可重复执行的方法。

2. 说明 skill 的基础结构：
   - 一个 skill 通常是一个文件夹。
   - 至少包含 `SKILL.md`。
   - 可选包含 `scripts/`、`references/`、`assets/`。

3. 以 Codex 为例：
   - Codex 会按需加载 skill。
   - `AGENTS.md` 适合写项目规则。
   - skill 适合写具体工作流。

4. 以 Claude Code 为例：
   - skill 可以自动触发，也可以通过 `/skill-name` 手动调用。
   - 高风险流程可以设置为只允许手动触发。
   - 适合沉淀团队内部的审查、发布、复盘流程。

5. 以 Cursor 为例：
   - Rules 适合项目约定。
   - Skills 适合可执行工作流。
   - Cursor 会从 `.agents/skills/`、`.cursor/skills/`、用户级目录，以及部分 Claude/Codex skills 目录发现 skills。

## 推荐先做的三类 Skill

- 检查型：代码审查、发布前检查、文章润色、可访问性检查。
- 转换型：会议纪要转 action items、长文转公众号稿、PR diff 转 changelog。
- 排查型：线上错误排查、测试失败定位、性能问题分析。

## 关键建议

- 从一个 30 行以内的小 skill 开始。
- `description` 要具体，避免触发范围过宽。
- 能限制路径就限制路径。
- 高风险操作要求人工确认。
- 一定要写验证方式。
- 把长参考资料放进 `references/`，不要全塞进 `SKILL.md`。

## 可选金句

AI 提效的关键，不是把 prompt 写得更像咒语，而是把你的工作方法整理到足够清楚。
