# [0026. mattpocock skills](https://github.com/tnotesjs/TNotes.github/tree/main/notes/0026.%20mattpocock%20skills)

<!-- region:toc -->

- [1. 本节内容](#1-本节内容)
- [2. 评价](#2-评价)
- [3. 请详细介绍一下 mattpocock/skills 这个项目【AI】](#3-请详细介绍一下-mattpocockskills-这个项目ai)
  - [3.1. 项目定位](#31-项目定位)
  - [3.2. 它解决的核心问题](#32-它解决的核心问题)
  - [3.3. 安装与初始化](#33-安装与初始化)
  - [3.4. 仓库结构](#34-仓库结构)
  - [3.5. 两类技能：User-invoked 与 Model-invoked](#35-两类技能user-invoked-与-model-invoked)
  - [3.6. 核心工程技能](#36-核心工程技能)
    - [`/ask-matt`](#ask-matt)
    - [`/grill-with-docs`](#grill-with-docs)
    - [`/domain-modeling`](#domain-modeling)
    - [`/tdd`](#tdd)
    - [`/diagnosing-bugs`](#diagnosing-bugs)
    - [`/codebase-design`](#codebase-design)
    - [`/improve-codebase-architecture`](#improve-codebase-architecture)
    - [`/to-prd` 与 `/to-issues`](#to-prd-与-to-issues)
    - [`/triage`](#triage)
  - [3.7. Productivity 与 Misc 技能](#37-productivity-与-misc-技能)
  - [3.8. 项目的工程思想](#38-项目的工程思想)
  - [3.9. 它适合谁？](#39-它适合谁)
  - [3.10. 注意点与局限](#310-注意点与局限)
  - [3.11. 总结](#311-总结)
- [4. 引用](#4-引用)

<!-- endregion:toc -->

## 1. 本节内容

- [mattpocock/skills][1] 项目简介

## 2. 评价

mattpocock/skills 在真实项目中有引入过这个项目中的 skills，感觉是有一些帮助的，常用的几个 skills 分别是：

- `/grill-with-docs` 通过不断地追问，帮你落地项目的说明文档。比如项目中的一些专业术语表达的具体含义啥的，每个功能模块的一些注意事项和详细说明啥的，这些都会落地到对应的文档中，后续 AI 会依据文档中的内容（相当于一个项目知识库）来理解你的需求。
- `/improve-codebase-architecture` 从一个更上层的视角来审视项目的架构，给出项目架构的优化方案。

关于如何集成到项目中，在 github 仓库 [mattpocock/skills][1] 中有说明。

## 3. 请详细介绍一下 mattpocock/skills 这个项目【AI】

下面按“它是什么、怎么用、核心技能、工作流思想、适合谁、局限”来介绍。

### 3.1. 项目定位

`mattpocock/skills` 是 Matt Pocock 公开的一组 **AI 编码 Agent 技能库**，主要面向 Claude Code、Codex 等支持 Agent Skills 的开发环境。它不是传统意义上的 JS/TS 库，也不是框架，而是一套可安装到编码 Agent 里的 **可复用提示词工作流 / slash command / 行为规范**。项目 README 里作者把它描述为“每天用于真实工程的 agent skills，不是 vibe coding”，并强调这些 skills 小、可改、可组合、适用于任意模型。([raw.githubusercontent.com](https://raw.githubusercontent.com/mattpocock/skills/main/README.md))

理解这个项目，先要理解 “Skill” 是什么。Claude Code 官方文档里说，Skill 本质上是一个带 `SKILL.md` 的目录，里面写着任务说明、流程、参考资料等；Claude 会在相关任务时加载它，用户也可以通过 `/skill-name` 直接调用。Skill 的好处是：长流程不会常驻塞进上下文，只有用到时才加载。([code.claude.com](https://code.claude.com/docs/en/skills))

所以，这个仓库可以理解为：**Matt Pocock 把自己做真实软件工程时希望 AI Agent 遵循的工作方法，封装成了一组可安装、可复用、可组合的技能。**

### 3.2. 它解决的核心问题

作者认为 AI 编码 Agent 常见失败点有四类：需求没对齐、输出太啰嗦、代码不能工作、代码库变成“大泥球”。README 对应给出的解决方向分别是：先通过 “grilling session” 反复追问需求；建立共享领域语言；用类型、浏览器反馈、自动化测试和 TDD 形成反馈环；持续关注代码设计和架构深度。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/README.md))

这也是这个项目和普通 prompt collection 的区别：它不是给你一堆“写 React 组件”“修 bug”的提示词，而是试图把工程实践拆成一套 Agent 可执行的流程。例如：先访谈澄清，再形成 PRD，再拆成垂直切片 issue，再让 Agent 分别实现；或者先构建可复现反馈环，再假设、插桩、修复、回归测试。

### 3.3. 安装与初始化

README 给出的快速安装方式是：

```bash
npx skills@latest add mattpocock/skills
```

安装时选择你需要的 skills 和目标编码 Agent；作者特别提醒要选择 `/setup-matt-pocock-skills`，然后在 Agent 里运行它。这个 setup skill 会询问项目使用的 issue tracker、triage 标签、文档保存位置等，完成之后其他工程类 skill 才能读取这些约定。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/README.md))

当前 `setup-matt-pocock-skills` 的实现并不是确定性脚本，而是“prompt-driven skill”：它会先探索仓库，再让用户逐项确认 issue tracker、triage label vocabulary、domain docs 布局，然后写入 `docs/agents/issue-tracker.md`、`docs/agents/triage-labels.md`、`docs/agents/domain.md` 等配置文档。它内置支持 GitHub、GitLab、本地 markdown，也允许记录 Jira、Linear 等“Other”工作流。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/skills/engineering/setup-matt-pocock-skills/SKILL.md))

### 3.4. 仓库结构

仓库的 `skills/` 目录按 bucket 分类，包含 `engineering`、`productivity`、`misc`，以及不对外主推的 `personal`、`in-progress`、`deprecated`。仓库自己的 `CLAUDE.md` 说明：`engineering` 是日常代码工作，`productivity` 是非代码工作流工具，`misc` 是偶尔使用的工具；只有 `engineering`、`productivity`、`misc` 里的技能需要出现在顶层 README 和 `.claude-plugin/plugin.json` 中。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/CLAUDE.md))

这里有个细节：skills.sh 页面显示该仓库索引了 44 个 skills、总安装量 4.8M；但当前仓库的 `.claude-plugin/plugin.json` 只注册了 17 个主要技能，这些才是当前插件清单中的核心技能。([skills.sh](https://skills.sh/mattpocock/skills))

### 3.5. 两类技能：User-invoked 与 Model-invoked

这个项目非常重视“技能何时被调用”。它把技能分成两类：

| 类型 | 含义 | 例子 |
| --- | --- | --- |
| User-invoked | 只有用户手动输入 `/skill-name` 才会触发 | `/grill-me`、`/to-prd`、`/triage` |
| Model-invoked | Agent 可以根据任务自动触发，也可由用户手动触发 | `/tdd`、`/diagnosing-bugs`、`/domain-modeling` |

仓库的 `docs/invocation.md` 说明：user-invoked skill 会设置 `disable-model-invocation: true`，因此只有人类能调用；model-invoked skill 则保留描述，让模型可以根据任务匹配自动使用。并且 user-invoked skill 可以调用 model-invoked skill，但不能调用另一个 user-invoked skill。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/docs/invocation.md))

这个设计很关键：它避免 Agent 自己乱触发高层流程。例如 `/to-prd`、`/triage` 这类会写 issue 或改变项目状态的技能，通常必须由人显式启动；而 `/tdd`、`/diagnosing-bugs` 这种方法论技能，可以由 Agent 在合适时自动套用。

### 3.6. 核心工程技能

#### `/ask-matt`

这是一个“路由器”技能：当你忘了该用哪个 skill，就用它。它描述了一条主流程：**idea → grill-with-docs → to-prd → to-issues → implement**；如果过程中有设计问题需要跑出来看，可以通过 `/handoff` 开新会话，再用 `/prototype` 做一次性原型，最后再 handoff 回主线。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/skills/engineering/ask-matt/SKILL.md))

#### `/grill-with-docs`

这是项目里最核心的需求澄清技能之一。它会运行 `/grilling`，同时使用 `/domain-modeling`，也就是一边追问你的设计，一边把形成的领域语言、ADR 等记录到项目文档中。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/skills/engineering/grill-with-docs/SKILL.md))

它解决的是“AI 以为懂了，其实没懂”的问题。作者的思路是：不要急着让 Agent 写代码，先让它像资深工程师/产品工程师一样反复追问，把需求树上的关键分支一个个定下来。

#### `/domain-modeling`

这个技能专门维护项目的领域模型。它会在用户使用模糊词、冲突词、过载词时立刻指出，并把最终确定的术语写进 `CONTEXT.md`；只有当决策“难以逆转、没有上下文会让未来读者困惑、且确实存在取舍”时，才建议创建 ADR。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/skills/engineering/domain-modeling/SKILL.md))

这对应 DDD 里的 ubiquitous language。它的目标不是写需求规格，而是让人和 Agent 对项目里的核心概念使用同一套语言，从而减少 token 浪费和误解。

#### `/tdd`

这是测试驱动开发技能。它强调测试应该通过公共接口验证行为，而不是测试实现细节；并且反对“一口气写完所有测试，再写所有实现”的水平切片方式，主张一个测试、一个实现、再下一个测试的垂直 tracer bullet 循环。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/skills/engineering/tdd/SKILL.md))

它的 TDD 流程大致是：先确认公共接口和最重要行为；写一个会失败的测试；写最少代码让它通过；继续下一个行为；全部 green 后再重构，并且永远不要在 red 状态下重构。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/skills/engineering/tdd/SKILL.md))

#### `/diagnosing-bugs`

这是调试技能，强调第一阶段不是读代码猜原因，而是先建立一个能捕捉当前 bug 的紧反馈环。它列举了可用方式：失败测试、curl/HTTP 脚本、CLI fixture、Playwright/Puppeteer 脚本、trace replay、throwaway harness、fuzz/property loop、git bisect harness 等。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/skills/engineering/diagnosing-bugs/SKILL.md))

它的完整流程是：建立反馈环 → 复现并最小化 → 生成 3–5 个可证伪假设 → 针对假设插桩 → 修复并加回归测试 → 清理和复盘。这个 skill 的风格非常“工程化”：没有 red-capable command，就不进入假设阶段。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/skills/engineering/diagnosing-bugs/SKILL.md))

#### `/codebase-design`

这是项目的架构词汇技能。它围绕 “deep modules” 建立一套统一语言：module、interface、depth、seam、adapter、leverage、locality。它主张好模块应该是“小接口 + 深实现”，让调用方用很少的接口知识获得很多行为，同时让维护者把变化和测试集中在清晰 seam 后面。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/skills/engineering/codebase-design/SKILL.md))

#### `/improve-codebase-architecture`

这个技能用于扫描代码库中的架构摩擦，找出“deepening opportunities”，也就是把浅模块变深的重构机会。它会读取 `CONTEXT.md` 和 ADR，探索代码库，然后生成一个自包含 HTML 架构报告，包含每个候选改造的文件、问题、方案、收益、before/after 可视化和推荐强度。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/skills/engineering/improve-codebase-architecture/SKILL.md))

#### `/to-prd` 与 `/to-issues`

`/to-prd` 会把当前对话和代码库理解综合成 PRD，并发布到项目 issue tracker；它明确要求不要再访谈用户，而是基于已有上下文综合。PRD 包括问题陈述、方案、用户故事、实现决策、测试决策、范围外事项等。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/skills/engineering/to-prd/SKILL.md))

`/to-issues` 则把计划、spec 或 PRD 拆成独立可领取的 issue。它强调使用 “vertical slices / tracer bullets”：每个 issue 应该端到端穿过 schema、API、UI、测试等层，而不是按“先数据库、再 API、再 UI”的水平层拆分。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/skills/engineering/to-issues/SKILL.md))

#### `/triage`

`/triage` 用来处理外部 issue 或 PR。它定义了两个类别角色：`bug`、`enhancement`，以及五个状态角色：`needs-triage`、`needs-info`、`ready-for-agent`、`ready-for-human`、`wontfix`。它会读取 issue/PR 上下文、检查代码库是否已有实现、确认 bug 是否可复现、必要时进行 grilling，最后贴上合适标签或生成 agent-ready brief。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/skills/engineering/triage/SKILL.md))

### 3.7. Productivity 与 Misc 技能

`/grill-me` 是不依赖代码库的需求追问技能，本质上运行 `/grilling`；`/grilling` 要求 Agent 一次只问一个问题，沿着设计决策树逐个分支追问，并在每个问题中给出推荐答案。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/skills/productivity/grill-me/SKILL.md))

`/handoff` 用于把当前会话压缩成交接文档，保存到系统临时目录，并在文档中建议下一轮 Agent 应该调用哪些 skills；它还要求不要重复已有 PRD、ADR、issue、commit、diff，而是引用路径或 URL，并且要移除敏感信息。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/skills/productivity/handoff/SKILL.md))

`/teach` 是一个状态化教学工作区技能。它会在当前目录维护 `MISSION.md`、`reference/*.html`、`learning-records/*.md`、`lessons/*.html`、`assets/*` 等文件，用于跨多轮教学；最新版本还强调 lesson 应复用 `./assets/` 里的组件，如样式表、quiz widget、simulator、diagram helper。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/skills/productivity/teach/SKILL.md))

`misc` 里还有偏工程杂项的工具，例如 `git-guardrails-claude-code` 会给 Claude Code 设置 PreToolUse hook，阻止 `git push`、`git reset --hard`、`git clean -f`、`git branch -D` 等危险命令；`setup-pre-commit` 则会帮项目配置 Husky、lint-staged、Prettier、typecheck 和 test。([GitHub](https://raw.githubusercontent.com/mattpocock/skills/main/skills/misc/git-guardrails-claude-code/SKILL.md))

### 3.8. 项目的工程思想

这个项目背后的核心思想可以总结成四句话：

第一，**Agent 不应该直接“开写”**。复杂需求需要先被反复追问，直到人和 Agent 对目标、约束、边界有共同理解。

第二，**文档不是交付物，而是 Agent 的长期记忆接口**。`CONTEXT.md`、ADR、issue tracker、triage label 这些不是官僚流程，而是为了让后续 Agent 会话能少猜、多复用。

第三，**代码质量来自反馈环**。无论是 TDD 还是 debug，项目都强调可运行、可复现、可验证的反馈，而不是让模型凭语感修代码。

第四，**Agent 会加速熵增，所以架构纪律更重要**。因为 Agent 写代码速度很快，坏抽象、浅模块、无测试 seam 也会更快堆积；所以项目把 deep modules、seam、interface、locality 这些设计语言放到了核心位置。

### 3.9. 它适合谁？

它特别适合已经在用 Claude Code、Codex、Cursor 等 Agent 做真实项目的人，尤其是多人协作、长期维护、issue 驱动、希望让 Agent 参与 PRD/triage/实现/debug 的团队或个人。

它不太适合只想要“一个 prompt 让 AI 秒写应用”的用户。这个项目的取向恰好相反：它会让 Agent 慢下来，先澄清、记录、测试、拆分，再开始实现。

### 3.10. 注意点与局限

首先，这不是一个传统 npm 库。仓库的 `package.json` 标记为 `private: true`，主要只有 changeset/version 脚本和 MIT license 元数据；安装命令里的 `skills` 是 skills.sh 的 CLI，而不是这个仓库本身发布成了 npm runtime 包。([GitHub](https://github.com/mattpocock/skills/blob/main/package.json))

其次，这些技能会影响 Agent 的行为，某些还会写文件、发 issue、改标签、配置 hooks，因此最好先阅读对应 `SKILL.md`，特别是涉及 issue tracker、git hook、pre-commit、triage 的技能。Claude Code 官方文档也提醒，项目 skills 可以携带工具权限，信任仓库前应先审查。([Claude Code](https://code.claude.com/docs/en/skills))

最后，它的价值取决于你的执行方式。如果你只是装了但仍然让 Agent 跳过访谈、跳过测试、跳过 issue 拆分，那收益会很有限。它真正强的地方，是把“资深工程师会坚持做但 Agent 容易偷懒的流程”显式化，并让 Agent 每次都按这个流程工作。

### 3.11. 总结

一句话说：**`mattpocock/skills` 是一套面向真实软件工程的 Agent 工作流技能库**。它不是教 AI “更快写代码”，而是教 AI **更像工程师一样工作**：先澄清需求，沉淀领域语言，形成 PRD，拆成垂直切片，用 TDD 和紧反馈环实现，遇到 bug 先复现再假设，定期检查架构是否变浅、变乱。对于认真使用 AI 编码 Agent 的开发者来说，这个项目的价值主要不在某个单独 skill，而在它把一整套工程纪律模块化、可安装、可组合地放进了 Agent 的工作方式里。

## 4. 引用

- [github mattpocock/skills][1]

[1]: https://github.com/mattpocock/skills
