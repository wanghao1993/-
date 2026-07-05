# 公众号排版稿：别再收藏 Prompt 了，真正提效的是 Skills

## 标题备选

1. 别再收藏 Prompt 了，真正拉开差距的是 Skills
2. 我劝你别再迷信提示词了：AI 提效的关键，已经换了
3. AI 用得累的人，通常都缺一个 Skill
4. Codex、Claude Code、Cursor 都在做的事：把你的工作方法变成 Skills
5. 未来会用 AI 的人，不是 prompt 写得好，而是会写 Skills
6. 你每天重复说给 AI 听的话，都该变成一个 Skill
7. 真正会用 AI 的人，已经开始训练自己的工作流了

## 推荐标题

别再收藏 Prompt 了，真正拉开差距的是 Skills

![封面图：别再收藏 Prompt 了](./images/cover-skills-workbench.png)

## 导语

过去一年，很多人都在收藏 prompt。

“万能提示词 100 条”

“让 AI 秒变专家的咒语”

“程序员必备 prompt 模板”

看起来很热闹。

但我越来越觉得，继续卷 prompt，可能卷错方向了。

因为真正让 AI 提效的，不是你这次问得多巧，而是你能不能把一套重复发生的工作，变成 AI 下次自己会执行的流程。

这个东西，就叫 skill。

---

## 正文

先说一个很扎心的场景。

你让 AI 帮你改代码。

第一次，你说：

“按我们项目风格来，先看现有实现，不要乱造新抽象，改完跑测试。”

第二次，你又说：

“按我们项目风格来，先看现有实现，不要乱造新抽象，改完跑测试。”

第三次，你还是说：

“按我们项目风格来，先看现有实现，不要乱造新抽象，改完跑测试。”

这时候问题就来了。

到底是 AI 不够聪明，还是你把自己活成了复读机？

很多人所谓“AI 用得不顺”，其实不是模型能力不行，而是工作流没有沉淀。

你每天都在重复交代背景、重复讲规则、重复补充边界、重复提醒它别犯同一个错。

这不是协作。

这是人肉配置文件。

所以我现在越来越建议一件事：

别只收藏 prompt。

开始创建 skills。

---

prompt 和 skill 的区别，其实一句话就能讲明白。

prompt 是这一次怎么问。

skill 是以后遇到同类事情，都按什么方法做。

prompt 像临时交代。

skill 像工作 SOP。

prompt 解决的是“我现在要你做什么”。

skill 解决的是“这类事在我这里应该怎么做”。

这也是为什么 Codex、Claude Code、Cursor 都开始提供类似 skills 的机制。

不是大家突然想发明新名词。

而是 AI 工具已经不只用来聊天，它们开始真的接活了。

聊天时，prompt 很重要。

干活时，流程更重要。

![Prompt 和 Skill 的差别](./images/prompt-vs-skill.png)

---

先别急着想技术细节。

我们先看一个普通人每天都会遇到的问题。

比如你经常让 AI 帮你写公众号文章。

你可能每次都要补充：

- 用简体中文
- 段落短一点，适合手机阅读
- 别写得像说明书
- 要给标题备选
- 要有导语
- 要有金句
- 涉及事实要列参考
- 图片放到文章目录下

这些东西难吗？

不难。

烦吗？

很烦。

因为它们不是创作本身，而是每次创作前都要重新铺一遍的地垫。

如果你把这套要求写成一个 skill，下次只要说“把这篇改成公众号稿”，AI 就更容易按你的结构走。

它不用每次都从一张白纸开始猜。

这就是 skills 最朴素的价值：

把重复说明，变成默认动作。

---

一个 skill 长什么样？

不用想复杂。

它通常就是一个文件夹，里面有一个 `SKILL.md`。

像这样：

```text
article-wechat-ready/
  SKILL.md
  references/
    style-guide.md
```

`SKILL.md` 负责告诉 AI：

这个 skill 什么时候用。

使用时先做什么、后做什么。

输出要长什么样。

哪些事情不能擅自做。

怎么判断做完了。

比如一个公众号 skill，可以写成这样：

```markdown
---
name: article-wechat-ready
description: Use when turning a draft into a WeChat public-account article.
---

## Workflow

1. Read the draft and notes first.
2. Produce title options, recommended title, lead-in, body copy, closing quote, and references.
3. Use Simplified Chinese.
4. Keep paragraphs short for mobile reading.
5. Remove stiff AI-like phrasing.
6. Keep all files inside the article package folder.
```

就这么简单。

别小看这几行。

很多人的效率，就是被这些“每次都要重复说一遍”的小规则吃掉的。

---

再看 Codex。

Codex 里有一个很重要的文件：`AGENTS.md`。

你可以把它理解成项目里的“工作说明书”。

比如这个仓库是干什么的，文件应该怎么命名，测试怎么跑，哪些目录不能随便动。

但 `AGENTS.md` 更适合写长期规则。

skill 更适合写具体流程。

举个例子：

`AGENTS.md` 可以写：

```text
文章必须放在 YYYY-MM-DD-topic-slug/ 目录下。
公众号稿使用 wechat-ready.md。
图片放在 images/ 目录。
默认使用简体中文。
```

而 skill 可以写：

```text
当用户要求写公众号文章时：
1. 先创建文章包。
2. 再写 full-article.md。
3. 再写 summary.md。
4. 最后写 wechat-ready.md。
5. 公众号稿必须包含标题备选、推荐标题、导语、正文、金句、参考资料。
```

这两者搭配起来，Codex 就不再只是“听你说一句，回你一段”。

它会更像一个知道你工作习惯的执行者。

你不用每次从目录结构开始解释。

它也不会把草稿散落在根目录里。

这才叫提效。

---

Claude Code 也是类似思路。

它有 `CLAUDE.md`，也有 skills。

如果某些说明你经常复制粘贴，Claude Code 官方文档本身也建议把它们做成 skill。

项目级 skill 通常可以放在：

```text
.claude/
  skills/
    review-pr/
      SKILL.md
```

个人常用 skill 可以放在：

```text
~/.claude/skills/
```

Claude Code 的一个实用点是：skill 可以自动触发，也可以手动触发。

比如你写一个“发布前检查”skill：

```markdown
---
description: Run a pre-release checklist before deploying or merging important changes.
disable-model-invocation: true
---

## Checklist

1. Summarize what changed.
2. Identify risky files.
3. Run standard tests.
4. Check whether docs or release notes need updates.
5. Report blockers separately.
```

注意这里的 `disable-model-invocation: true`。

意思是：不要让模型自己决定什么时候用，必须我手动叫你用。

这对高风险任务很重要。

比如发布、删库、迁移、改生产配置。

AI 可以帮你检查，可以帮你整理，可以帮你执行一部分动作。

但什么时候真按下按钮，最好还是人说了算。

好的 skill 不是让 AI 放飞。

好的 skill 是让 AI 在该稳的地方稳下来。

---

Cursor 的情况也很有意思。

很多 Cursor 用户熟悉的是 Rules。

比如 `.cursor/rules`。

Rules 很适合写长期约束和项目约定：

- 这个目录下的组件怎么写
- API 入参怎么校验
- 命名规则是什么
- 什么时候必须补测试

但当你要表达的不是单条约束，而是一套可重复执行的动作，skills 往往更顺手。

Cursor 的 skills 会从这些位置自动发现：

```text
.agents/skills/
.cursor/skills/
~/.agents/skills/
~/.cursor/skills/
```

它还兼容一些 Claude 和 Codex 的 skills 目录。

这件事非常值得重视。

因为 skills 正在变成一种跨工具的工作流资产。

你今天写给 Cursor 的 skill，明天可能也能被别的 agent 工具读懂。

以后真正值钱的，可能不是你收藏了多少 prompt。

而是你沉淀了多少高质量工作流。

![Codex、Claude Code、Cursor 的 skill 入口](./images/tools-skill-locations.png)

---

那什么东西最适合先做成 skill？

我建议从三类开始。

第一类，检查型。

比如代码审查、发布前检查、文章润色、可访问性检查。

这类任务风险低，收益高。

AI 不一定要替你做决定，但很适合帮你查漏补缺。

第二类，转换型。

比如把会议纪要转成 action items，把长文转成公众号稿，把 PR diff 转成 changelog，把产品需求转成测试用例。

这类任务格式稳定，重复率高。

做成 skill，马上省时间。

第三类，排查型。

比如线上错误排查、测试失败定位、性能问题分析。

这类 skill 要特别注意顺序。

不要让 AI 上来就改。

应该让它先复现、先找证据、先列假设，再做最小修改。

可以写成这样：

```markdown
## Debugging protocol

1. Reproduce or locate the failure before changing code.
2. List the top 2-3 hypotheses.
3. Gather evidence for the most likely hypothesis.
4. Make one minimal fix.
5. Run the failing test again.
6. Report what changed and what remains uncertain.
```

这几行看起来普通。

但它能把 AI 从“猜一个答案”拉回到“按工程流程排查”。

这就是差距。

---

写 skill 时，最容易犯的错误，是写得太大。

很多人一上来就想做一个“超级全能工作流”：

项目背景、代码规范、产品原则、设计系统、发布流程、故障手册、老板偏好，全都塞进去。

结果就是 AI 看完以后也不知道重点在哪。

skill 不是公司百科。

skill 是一套可重复执行的动作。

所以最好的开始方式，是选一个你这周已经重复做过三次的小流程。

比如：

- 每次提交前总结 diff
- 每次改 UI 后检查可访问性
- 每次修 bug 先写复现路径
- 每次写文章都整理成公众号格式
- 每次发布前跑固定 checklist

先写一个 30 行以内的 skill。

用一周。

看它哪里误触发，哪里不够清楚，哪里还需要你补话。

然后再改。

skills 的维护方式，应该像维护测试用例。

不是一次写完就供起来。

而是在每次出错后，补一条更具体的规则。

AI 总是忘记跑测试，就加：

```markdown
Always report the exact verification command and result. If verification was not run, explain why.
```

AI 总是乱抽象，就加：

```markdown
Prefer existing project patterns. Add a new abstraction only when it removes repeated complexity in at least two places.
```

AI 写中文太像说明书，就加：

```markdown
For Chinese copy, use short paragraphs and natural spoken rhythm. Avoid slogan-like phrasing.
```

不要一次写一百条。

每次补一两条，反而更有效。

![创建 Skill 的生命周期](./images/skill-lifecycle.png)

---

最后，给一个可以直接抄走的通用模板。

不管你用 Codex、Claude Code，还是 Cursor，都可以从它改起。

```markdown
---
name: your-skill-name
description: Use when [具体任务场景]. Do not use for [不适用场景].
---

# Your Skill Name

## Goal

Describe the outcome this skill should produce.

## When to Use

- Use when...
- Do not use when...

## Before Acting

1. Read the relevant files or context.
2. Identify constraints, risks, and unknowns.
3. Ask the user only if a decision cannot be safely inferred.

## Workflow

1. Step one.
2. Step two.
3. Step three.

## Output Format

- Summary:
- Changes made:
- Verification:
- Open questions:

## Guardrails

- Do not make unrelated changes.
- Do not invent facts.
- Do not run high-risk actions without explicit approval.
- Prefer existing project patterns.

## Verification

- Run the relevant check if available.
- If verification cannot be run, explain the reason.
- Report exact command names and results.
```

你可以先把它改成一个“公众号文章整理”skill。

也可以改成“PR review”skill。

或者“bug 排查”skill。

关键不是模板本身。

关键是你开始把脑子里的工作方法写出来。

写到 AI 能执行。

写到同事能复用。

写到你下次不用再重复解释。

这才是 AI 提效真正进入日常工作的方式。

不是天天找新的神级 prompt。

而是把你已经验证过的工作方法，一点点变成 skills。

到那时候，AI 不再只是一个聊天窗口。

它更像一张工作台。

你常用的工具都在上面。

每一把都知道什么时候用，怎么用，用完怎么检查。

而你终于不用每天把同一句话，再说一遍。

## 可选金句

1. 你每天重复说给 AI 听的话，都该变成一个 skill。
2. prompt 是临时交代，skill 是工作 SOP。
3. 真正会用 AI 的人，不是在训练模型，而是在训练自己的工作现场。
4. AI 提效的关键，不是少打几个字，而是少解释、少返工、少踩同一个坑。

## 参考资料

1. OpenAI Developers, Codex: Agent Skills  
https://developers.openai.com/codex/skills

2. OpenAI Developers, Codex: Custom instructions with AGENTS.md  
https://developers.openai.com/codex/guides/agents-md

3. Anthropic, Claude Code Docs: Overview  
https://code.claude.com/docs/en/overview

4. Anthropic, Claude Code Docs: Extend Claude with skills  
https://code.claude.com/docs/en/skills

5. Cursor Docs: Agent Skills  
https://cursor.com/docs/skills.md

6. Cursor Docs: Rules  
https://cursor.com/docs/rules.md
