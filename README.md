# MyKnowledgeBase · 个人 Skills 知识库

## 仓库定位

本仓库有两个用途：

1. **管理个人 skills 集** —— 收录供 AI Agent 使用的技能指令（每个 skill 一个目录，含 `SKILL.md` 及配套脚本、参考资料）
2. **迭代个人 agents 使用经验总结** —— 在实际使用中沉淀的经验、规范与最佳实践，持续更新、持续迭代

## 安装方式（重要约定）

本仓库的所有 skills 都是**全局共享 skills**：无论下载还是克隆，请将内容统一存放到**当前用户主目录**下的 `.agents/skills/` 目录，作为所有 agents 共用的 skills：

| 操作系统 | 目标目录 |
|---|---|
| Windows | `C:\Users\<你的用户名>\.agents\skills\` |
| macOS / Linux | `~/.agents/skills/` |

```bash
# 克隆（或下载解压）后，将各 skill 目录复制到全局 skills 目录
git clone https://github.com/guol9180/MyKnowledgeBase.git

# Windows (PowerShell)
Copy-Item MyKnowledgeBase\* "$env:USERPROFILE\.agents\skills\" -Recurse -Force

# macOS / Linux
cp -r MyKnowledgeBase/*/ ~/.agents/skills/
```

> 说明：`README.md` 是仓库说明而非 skill（无 frontmatter），复制与否均无影响；各 skill 目录才是生效单元。

## Skills 列表

| Skill | 用途 |
|---|---|
| [init-project-docs](./init-project-docs/SKILL.md) | 新建开发项目时统一创建 README / AGENTS / DEVELOP_PLAN 三文档 |
| [executing-plans](./executing-plans/SKILL.md) | 作为执行者按实现计划落地任务 |
| [writing-plans](./writing-plans/SKILL.md) | 有规格 / 需求后，动手写代码前先写实现计划 |
| [test-driven-development](./test-driven-development/SKILL.md) | 测试驱动开发流程 |
| [systematic-debugging](./systematic-debugging/SKILL.md) | 遇到 bug / 测试失败的系统化排查 |
| [verification-before-completion](./verification-before-completion/SKILL.md) | 声称完成 / 通过之前先运行验证 |
| [requesting-code-review](./requesting-code-review/SKILL.md) | 完成功能后请求代码评审 |
| [receiving-code-review](./receiving-code-review/SKILL.md) | 收到评审意见后的严谨处理 |
| [finishing-a-development-branch](./finishing-a-development-branch/SKILL.md) | 实现完成后决定分支集成方式 |
| [using-git-worktrees](./using-git-worktrees/SKILL.md) | 用 git worktree 隔离特性开发 |
| [frontend-design](./frontend-design/SKILL.md) | 构建新 UI / 改版时的视觉设计指导 |
| [mcp-builder](./mcp-builder/SKILL.md) | 创建高质量 MCP（Model Context Protocol）服务器 |

## 维护约定

- **新增 skill**：在仓库根目录新建 `<skill-name>/SKILL.md`（YAML frontmatter 含 `name`、`description`），并同步更新上表
- **经验迭代**：使用中发现的问题与改进，直接修订对应 skill 后提交；跨 skill 的通用经验可新建 skill 沉淀
- **命名规范**：目录名与 `name` 字段一致，kebab-case，动宾或领域短语
