---
name: web-harness
description: 当用户希望把本插件中的 BANU 协作模板应用到 Web 代码仓库时使用，基于插件包内 templates 目录中的 AGENTS.md、CLAUDE.md、docs/ 和 tasks/ 模板文件。
---

# Web Harness

当一个仓库需要接入 BANU 协作脚手架时，使用这个 skill。

## 源模板

把本插件包中已有的这些文件视为源模板：

- `templates/AGENTS.md`
- `templates/CLAUDE.md`
- `templates/docs/architecture.md`
- `templates/docs/conventions.md`
- `templates/docs/api.md`
- `templates/docs/decisions.md`
- `templates/tasks/todo.md`
- `templates/tasks/lessons.md`
- `templates/tasks/review.md`

不要改写本插件包里的这些模板文件。应以它们为基线，复制或合并到目标仓库中。

## 工作流程

请阅读当前项目结构、配置文件、包管理文件、构建脚本和主要源码目录，帮我补全这套 AI 协作模板中的文档：

- `docs/architecture.md`
- `docs/conventions.md`
- `docs/api.md`

要求：

- 删除或替换所有占位内容，例如 [填写]、[路径]、[说明]。
- 补齐本地开发、测试、构建和发布命令。
- 补齐项目目录边界、共享模块边界和禁止改动项。
- 补齐请求封装、鉴权、错误处理和高风险业务边界。
- 不要编造无法从代码、配置或用户说明中确认的信息。
- 不确定的内容标记为“待确认”。
