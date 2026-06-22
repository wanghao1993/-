# 别再只卷 Prompt 了：Loop Engineering 才是下半场，但你也不用慌

这两年聊 AI，最容易聊偏的一件事，就是大家总把注意力放在 prompt 上。

仿佛只要提示词写得够巧，模型就会突然开窍，工作也会自动完成。

但现在越来越多一线开发者已经换了视角。大家不再只问“这句话怎么说更有效”，而是开始问一个更像真实工作的题：

这件事，能不能交给 AI 自己往下做？

出了错怎么办？  
做到哪一步要停？  
什么时候该叫人来拍板？

这套思路，最近有个越来越常见的名字：`Loop Engineering`。

## Loop Engineering 到底是什么

如果用一句人话解释，loop engineering 研究的不是“怎么问”，而是“怎么把一份工作设计成一个闭环”。

这个闭环里，AI 不是只回你一句话，而是会按步骤往前推进：先理解任务，再看上下文，再动手，再验证，再修正，最后把结果交回来。

所以它关心的重点，天然就跟 prompt engineering 不一样。

`Prompt Engineering` 更像单轮沟通。  
`Loop Engineering` 更像流程编排。

前者在意的是一句话怎么写。后者在意的是整件事怎么跑。

这也是为什么现在很多人开始感觉到，单纯研究提示词已经不够了。模型会调工具、会读代码、会跑命令、会写文件之后，真正拉开差距的，已经不是谁更会写咒语，而是谁更会设计流程。

## 它和 Prompt、Harness 到底是什么关系

这里最容易混淆的，其实不是 prompt，而是 `harness`。

我更愿意把这三个词理解成三个不同层次。

`Prompt` 是沟通层。  
你要让模型知道目标是什么，约束是什么，输出长什么样。

`Harness` 是运行层。  
这个词通常不是某个单独功能名，而是一个更宽的工程说法。它指的是模型外面那层“执行骨架”：工具调用、权限控制、沙箱、日志、回滚、测试、规则文件、检查点，这些都算。没有 harness，模型顶多会说；有了 harness，它才有手有脚，也有护栏。

`Loop` 是编排层。  
它决定什么时候思考，什么时候查资料，什么时候执行，什么时候验证，什么时候停下来，什么时候把任务交给另一个 agent 或者交还给人。

所以这三者不是互相替代，也不是谁升级谁。

它们更像一套分层配合：

- prompt 负责把话说清楚
- harness 负责让系统能跑起来，而且别乱跑
- loop 负责把整件事串成闭环

你可以只有 prompt，没有 loop，那更像聊天。  
你可以有 harness，没有 loop，那只是工具箱。  
你也可以硬做一个 loop，但 prompt 和 harness 都很弱，结果通常不稳定。

真正好用的 agent 工作流，三层都得有。

## 一个具体例子：怎么在 Codex、Claude Code、Cursor 里做 loop engineering

拿一个很常见、也足够真实的任务举例：给一个现有 SaaS 项目接入 GitHub OAuth 登录。

这事不算大，但也绝对不是一句“帮我加个登录”就能稳稳做完的。它至少会牵涉后端鉴权、前端入口、环境变量、回调地址、异常处理、测试，最后还得有人 review。

如果只用 prompt，很多人的做法会是直接开口：

“帮我加 GitHub OAuth 登录。”

模型当然也能开始干，但这种做法很容易漂。它不知道你项目里有没有现成鉴权层，不知道你们测试怎么跑，不知道回调策略，也不知道哪些目录不能动。

loop engineering 的做法不一样。它会先把这件事拆成一个闭环。

### 第一步：先把长期上下文固定下来

这一层，说白了就是先把“默认工作方式”写进系统里。

在 `Codex` 里，OpenAI 官方文档提到可以通过仓库中的 `AGENTS.md` 告诉 Codex 怎么理解代码库、该跑什么测试、遵守什么项目约定。Codex 的每个任务都在独立环境里跑，能读写文件，也能跑测试和命令。[OpenAI 官方介绍](https://openai.com/index/introducing-codex/)

在 `Claude Code` 里，这一层通常落在 `CLAUDE.md`。Anthropic 的文档明确建议把代码风格、测试命令、工作流规则写进去。它还区分了 `CLAUDE.md` 这种“建议性上下文”和 `hooks` 这种“必须执行的确定性动作”，比如每次改完文件都自动跑一次 eslint。[Claude Code 官方文档](https://code.claude.com/docs/en/best-practices)

在 `Cursor` 里，这一层更明显。它有 `.cursor/rules`、`AGENTS.md`、skills、subagents 这些机制。官方文档对 rules 的定义很直接：它们会作为持久上下文放进 agent 的前置提示里，保证模型每次都按同一套项目规则工作。[Cursor 官方文档](https://cursor.com/docs/rules.md)

这一步的重点不是“写更多字”，而是把反复要解释的东西前置掉。

比如：

- 优先复用现有 auth 模块
- 只跑和改动相关的测试
- 不要改动 `migrations/`
- UI 文案沿用现有登录页语气
- 提交前必须跑 typecheck

这一步做得好，后面每一轮都省心。

### 第二步：先侦察，不急着写

真正稳定的 loop，通常不会上来就改代码。

它会先让 agent 看清局面：项目里有没有现成鉴权中间件？OAuth 工具是否已有？前端登录页在哪？环境变量从哪里注入？测试是 Jest、Vitest 还是 Playwright？

在 `Claude Code` 和 `Cursor` 里，这类侦察特别适合交给 subagent。Anthropic 官方建议显式让 Claude 用 subagent 做代码探索和独立复查；Cursor 的 subagent 也支持独立上下文，甚至可以后台跑，避免主线程被一堆搜索结果塞满。[Claude Code 官方文档](https://code.claude.com/docs/en/best-practices) [Cursor 官方文档](https://cursor.com/docs/subagents.md)

`Codex` 这边的思路也类似，只是它更偏“把侦察任务本身当成一个独立 agent 任务”来做。OpenAI 官方写得很明确：Codex 支持把多项任务并行分发到独立环境里跑，然后给你日志和测试证据。[OpenAI 官方介绍](https://openai.com/index/introducing-codex/)

所以一个更像样的流程，不会是“直接做”，而是先分出一个发现阶段：

- 一个 agent 查现有 auth 结构
- 一个 agent 查前端登录入口和 UI 复用点
- 一个 agent 查测试和环境配置

先把图画出来，再动手。

### 第三步：执行时别只靠一个 agent 闷头干

很多人理解 loop engineering，会以为它就是“放手让 AI 自己跑很久”。

其实不是。

它更像有节奏地分工。

比如这个 OAuth 任务，完全可以拆成三段：

- 一个 agent 只管后端登录流和回调
- 一个 agent 只管前端入口和错误提示
- 一个 agent 只管补测试和检查回归风险

`Claude Code` 官方文档很鼓励这种并行会话和 worktree 式隔离；`Cursor` 的 agent 和 subagent 也支持前后台分工；`Codex` 更是从产品设计上就在强调多任务并行和异步委派。[Claude Code 官方文档](https://code.claude.com/docs/en/best-practices) [Cursor 官方文档](https://cursor.com/docs/agent/overview.md) [OpenAI 官方介绍](https://openai.com/index/introducing-codex/)

这一步真正改变的，不是“AI 更聪明了”，而是你的任务不再只有一条单线程。

## 第四步：验证，不是可选项，是 loop 的一部分

这一点非常关键。

很多人一提 agent，就容易想象成“它自己做完，我来收货”。实际不是。一个没验证环节的 loop，很容易稳定地产出错结果，而且错得很勤快。

这时候 harness 的价值就出来了。

`Codex` 会给出终端日志和测试输出，方便你检查它到底做了什么。  
`Claude Code` 有 checkpoints，可以在试错后回退，还可以再起一个 subagent 做独立复查。  
`Cursor` 有 checkpoints，也有 `Bugbot` 这种专门盯 PR diff 的审查流，甚至能在发现问题后继续拉起 cloud agent 做 autofix。[OpenAI 官方介绍](https://openai.com/index/introducing-codex/) [Claude Code 官方文档](https://code.claude.com/docs/en/best-practices) [Cursor 官方文档](https://cursor.com/docs/bugbot.md)

一个完整的 loop，到这里至少应该包括：

- 功能测试过没过
- 类型检查过没过
- 有没有超出任务范围的改动
- 有没有安全和边界问题
- 有没有人类必须拍板的地方

注意，review 不是对 agent 不信任。

而是因为你终于把 AI 当成真的执行者了。既然是执行者，就应该进正式流程，而不是靠“感觉差不多”。

## 第五步：人类不是被替代，而是被抬高了一层

这大概也是 loop engineering 最容易被误解的地方。

很多人一听这个词，就开始紧张：是不是以后不会写 prompt、不会写代码的人都要掉队？

我觉得没必要先把自己吓到。

因为 loop engineering 真正改变的，不是“人没用了”，而是“人做的那层事情变了”。

以前你可能更像操作员，一句一句盯着改。  
以后你更像负责人，决定目标、约束、节奏、验收和风险边界。

说得现实一点，团队里真正稀缺的能力，从来都不只是写出一段代码。

而是知道：

- 什么问题值得做
- 怎么拆才不会失控
- 哪些地方能自动化
- 哪些地方必须人工接管

这些能力，本来就是人的长项。

所以别把 loop engineering 理解成又一个必须立刻掌握的新名词。它更像是把很多你本来就在做的工程习惯，重新安到 AI 工作流里。

你以前会写文档、会分任务、会做 code review、会设测试门槛。现在只是多了一个执行者，而这个执行者需要你把流程讲清楚。

这不是把门槛抬到天上去。

这更像是把“会提问”往前推了一步，变成“会带活”。

## 最后一句

如果你现在还不擅长 loop engineering，真的不用焦虑。

因为它不是一门突然冒出来、完全陌生的新技术。它只是把老问题重新问了一遍：

你能不能把一件工作说清楚，拆清楚，盯清楚，收清楚？

prompt 当然还重要。  
harness 当然也重要。  
但真正让 AI 开始像同事，而不是像聊天机器人，靠的是 loop。

这才是下半场。
