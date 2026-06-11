# BANU Workflow

`BANU Workflow` 是一个面向 Codex 的仓库协作插件，用来把一套可复用的 AI 协作脚手架带进项目里。

它当前提供一个 `web-harness` skill，以及一组用于仓库初始化的模板文件，帮助团队在项目中建立统一的：

- `AGENTS.md` 协作规范入口
- `CLAUDE.md` 兼容入口
- `docs/` 项目事实文档
- `tasks/` 任务状态与复盘文档

## 1.安装

在任意本地仓库里执行：

```bash
codex plugin marketplace add bnfe/banu-ai-workflow
codex plugin add banu-workflow@banu-marketplace
```

第一步用于把 `banu-ai-workflow` 添加为本地 Codex 的 marketplace source，第二步才会真正安装 `banu-workflow` 插件。

安装后可用下面的命令确认状态：

```bash
codex plugin list --marketplace banu-marketplace
```

## 2.使用方式

安装插件后，可以直接在 Codex 中这样描述需求：

```text
把 BANU Workflow 的协作模板接入当前仓库
```

或者：

```text
告诉我 BANU Workflow 提供了哪些技能，并推荐适合当前仓库的用法
```

`web-harness` skill 会把 `templates/` 里的文件视为基线模板，并按目标仓库的现状进行复制或谨慎合并。
