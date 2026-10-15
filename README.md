# imhgl-skills · 个人 Skills 知识库

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
git clone https://github.com/guol9180/imhgl-skills.git

# Windows (PowerShell)
Copy-Item imhgl-skills\* "$env:USERPROFILE\.agents\skills\" -Recurse -Force

# macOS / Linux
cp -r imhgl-skills/*/ ~/.agents/skills/
```

> 说明：`README.md` 是仓库说明而非 skill（无 frontmatter），复制与否均无影响；各 skill 目录才是生效单元。

## Skills 列表

| Skill | 用途 | 来源 |
|---|---|---|
| [init-project-docs](./init-project-docs/SKILL.md) | 新建开发项目时统一创建 README / AGENTS / DEVELOP_PLAN 三文档 | 自研 |
| [executing-plans](./executing-plans/SKILL.md) | 作为执行者按实现计划落地任务 | [obra/superpowers](https://github.com/obra/superpowers) · MIT |
| [writing-plans](./writing-plans/SKILL.md) | 有规格 / 需求后，动手写代码前先写实现计划 | [obra/superpowers](https://github.com/obra/superpowers) · MIT |
| [test-driven-development](./test-driven-development/SKILL.md) | 测试驱动开发流程 | [obra/superpowers](https://github.com/obra/superpowers) · MIT |
| [systematic-debugging](./systematic-debugging/SKILL.md) | 遇到 bug / 测试失败的系统化排查 | [obra/superpowers](https://github.com/obra/superpowers) · MIT |
| [verification-before-completion](./verification-before-completion/SKILL.md) | 声称完成 / 通过之前先运行验证 | [obra/superpowers](https://github.com/obra/superpowers) · MIT |
| [requesting-code-review](./requesting-code-review/SKILL.md) | 完成功能后请求代码评审 | [obra/superpowers](https://github.com/obra/superpowers) · MIT |
| [receiving-code-review](./receiving-code-review/SKILL.md) | 收到评审意见后的严谨处理 | [obra/superpowers](https://github.com/obra/superpowers) · MIT |
| [finishing-a-development-branch](./finishing-a-development-branch/SKILL.md) | 实现完成后决定分支集成方式 | [obra/superpowers](https://github.com/obra/superpowers) · MIT |
| [using-git-worktrees](./using-git-worktrees/SKILL.md) | 用 git worktree 隔离特性开发 | [obra/superpowers](https://github.com/obra/superpowers) · MIT |
| [frontend-design](./frontend-design/SKILL.md) | 构建新 UI / 改版时的视觉设计指导 | [anthropics/skills](https://github.com/anthropics/skills) · Apache 2.0 |
| [mcp-builder](./mcp-builder/SKILL.md) | 创建高质量 MCP（Model Context Protocol）服务器 | [anthropics/skills](https://github.com/anthropics/skills) · Apache 2.0 |

## 第三方 skill 引入规范

除 `init-project-docs` 外，其余 skills 均借鉴自上游开源项目（见上表来源列）。**引入新 skill 或同步上游更新时**，必须逐项过一遍以下审查清单：

1. **去除单一 agent 绑定**：删除或改写绑定特定 agent 产品的表述（专有 CLI 名称、专有工作流、特定产品提示语等），改写为通用 agent 指令；只剥离绑定，不改动原 skill 的方法论
2. **去除上游命名空间**：`superpowers:` 之类的项目前缀一律去除，改为本仓库内的平铺 skill 名引用；若引用的本仓库未收录的上游 skill（如 `subagent-driven-development`、`writing-skills`），保留原名并在首次出现处注明「上游 skill，本仓库未收录」
3. **保留许可证**：上游 `LICENSE.txt` 原样保留，各 skill 目录内的版权声明不得删除
4. **结构对齐本仓库规范**：目录名 = frontmatter `name`（kebab-case），必须含 `SKILL.md`
5. **登记来源**：在上表「来源」列登记上游仓库与许可证；同步上游新版本时先 diff 上游变更，再按本清单重新过一遍

## 维护约定

- **新增 skill**：在仓库根目录新建 `<skill-name>/SKILL.md`（YAML frontmatter 含 `name`、`description`），并同步更新上表
- **经验迭代**：使用中发现的问题与改进，直接修订对应 skill 后提交；跨 skill 的通用经验可新建 skill 沉淀
- **命名规范**：目录名与 `name` 字段一致，kebab-case，动宾或领域短语
