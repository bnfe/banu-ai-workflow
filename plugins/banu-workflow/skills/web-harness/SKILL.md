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

不要改写本插件包里的这些模板文件。应以它们为基线，复制、适配或合并到目标仓库中。

## 工作流程

1. 先检查目标仓库结构，以及是否已经存在 AI 协作相关文件。
2. 复用本插件包 `templates/` 目录中的 BANU 源模板。
3. 如果目标仓库已有同名或相近文件，按最小改动原则谨慎合并。
4. 项目事实放在 `docs/`，任务状态放在 `tasks/`，长期规则放在 `AGENTS.md`。
5. 不要编造目标仓库中不存在、也未被用户明确说明的项目事实。

## 验证

- 确认目标仓库在变更后具备预期的脚手架文件。
- 确认修改只发生在目标仓库，而不是本插件包中的模板文件。
