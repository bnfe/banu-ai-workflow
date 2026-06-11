# AI 工程协作体系

这是一套可复制到任意项目中的 AI 工程协作体系，借鉴 Harness Engineering 思路，将 AI 协作所需的规则、项目知识、任务状态和复盘反馈结构化管理。目标是把“长期有效的协作规则”和“项目实时上下文”拆开，减少 token 浪费，同时让 AI 在处理复杂任务时有稳定的工作流、任务记录和复盘入口。

## 1.文件结构

```text
.
├── AGENTS.md                 # 主协作规范，Codex 可直接读取
├── CLAUDE.md                 # Claude Code 入口，指向 AGENTS.md
├── docs/
│   ├── architecture.md       # 项目结构、技术栈、运行入口
│   ├── conventions.md        # 编码规范、文件组织、测试要求
│   ├── api.md                # API、SDK、外部服务与业务边界
│   └── decisions.md          # 重要架构决策记录
└── tasks/
    ├── todo.md               # 当前任务状态
    ├── lessons.md            # 历史经验与踩坑规则
    └── review.md             # 任务复盘归档
```

## 2.使用方式

1. 将这些文件复制到目标项目根目录。
2. 按目标项目实际情况补充 `docs/architecture.md`、`docs/conventions.md` 和 `docs/api.md`。
3. 使用 Codex 时，保留根目录的 `AGENTS.md` 作为主协作规范入口。
4. 使用 Claude Code 时，保留根目录的 `CLAUDE.md`，让它指向并遵循 `AGENTS.md`。
5. 遇到长期影响架构、边界或技术路线的判断时，记录到 `docs/decisions.md`。
6. 开始非琐碎任务前，在 `tasks/todo.md` 写清目标、假设、计划和验证方式。
7. 任务完成后，把复盘追加到 `tasks/review.md`；用户纠正或踩坑经验沉淀到 `tasks/lessons.md`。

## 3.设计原则

### 3.1分层信息注入，控制 token 成本

```text
AGENTS.md  -> 每次对话注入，只放长期有效的高优先级规则
docs/      -> 按需阅读，存放项目事实和稳定约定
tasks/     -> 按需阅读，存放当前任务、复盘和经验
```

`AGENTS.md` 不应该塞满具体项目细节。项目越复杂，越需要把事实拆到 `docs/` 中，让 AI 在需要时读取，而不是每次对话都背着整本手册走。

### 3.2todo 不累积，管理上下文窗口

```text
todo.md     -> 只保留当前任务和最近一次调整
review.md   -> 结构化归档，使用 Review ID 追踪历史
lessons.md  -> 只保留提炼后的可复用规则
```

这样 AI 每次读到的都是干净的当前状态；需要历史时再按 Review ID 回查，不让旧任务污染当前判断。

### 3.3规则少而硬，事实按需补

- `AGENTS.md` 写“必须遵守”的协作规则。
- `docs/` 写“这个项目是什么样”的事实。
- `tasks/` 写“现在正在做什么”和“过去学到了什么”。

如果某条信息只对一个任务有效，放进 `tasks/todo.md` 或本次对话；如果会长期影响协作，再沉淀进 `docs/` 或 `tasks/lessons.md`。

## 4.迁移检查

复制到新项目后，至少检查这些占位内容：

- `docs/architecture.md`：技术栈、目录结构、运行命令、模块边界。
- `docs/conventions.md`：格式化、lint、测试、文件命名、依赖管理。
- `docs/api.md`：请求封装、鉴权、错误处理、外部 SDK、业务高风险边界。
- `docs/decisions.md`：清空示例决策，保留真实的架构判断。
- `tasks/todo.md`：清空旧任务，只保留当前任务模板。
- `tasks/review.md`：清空示例索引，或替换为当前项目真实复盘。
- `tasks/lessons.md`：删除不适用于当前项目的经验。

## 5.初始化 checklist

- [ ] 删除或替换所有占位内容，例如 `[填写]`、`[路径]`、`[说明]`。
- [ ] 补齐本地开发、测试、构建和发布命令。
- [ ] 补齐项目目录边界、共享模块边界和禁止改动项。
- [ ] 补齐请求封装、鉴权、错误处理和高风险业务边界。
- [ ] 不要编造无法从代码、配置或用户说明中确认的信息。
- [ ] 不确定的内容标记为“待确认”。

## 6.维护建议

- 不要把临时结论长期写进 `AGENTS.md`。
- 不要让 `tasks/todo.md` 变成历史垃圾桶。
- 每次用户纠正 AI 后，都把可复用规则补进 `tasks/lessons.md`。
- 每次完成非琐碎任务后，都在 `tasks/review.md` 追加结构化复盘。
- 当目录、架构或依赖策略发生变化时，同步更新 `docs/`。
