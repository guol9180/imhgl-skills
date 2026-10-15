---
name: init-project-docs
description: 新建开发项目时统一创建 README.md（项目熟悉）、AGENTS.md（开发规范）、DEVELOP_PLAN.md（计划与验收）三个文档，严格分类、交叉引用、禁止冗余。Use when initializing a new dev project, or when project docs are missing / being restructured.
---

# 初始化项目文档（三件套）

## Overview

新建开发项目时，统一创建三个 Markdown 文档。三个文件职责互斥、严格分类，同一信息只写一处，其余位置用引用：

| 文件 | 职责 | 回答的问题 | 读者 |
|---|---|---|---|
| `README.md` | **项目熟悉** | 这是什么？为什么存在？怎么跑起来？ | 第一次接触项目的人（含未来的自己） |
| `AGENTS.md` | **开发规范** | 改代码必须遵守什么？ | 所有参与开发的 agent 与人 |
| `DEVELOP_PLAN.md` | **计划与验收** | 做什么？做到哪了？怎么算完成？ | 任务执行者与验收者 |

**Announce at start:** "我正在使用 init-project-docs skill 初始化项目三文档。"

## 内容分类规则（严格归属）

写入任何内容前，先对照下表确定唯一归属文件：

| 内容类型 | 归属 | 示例 |
|---|---|---|
| 项目定位、功能清单、架构概览 | README | "这是一个 XX 系统，包含 A / B 模块" |
| 环境要求、安装、启动、常用命令 | README | `pnpm install`、`pnpm dev` |
| 技术选型及理由 | README | "用 SQLite，因为单机零依赖" |
| 代码风格、目录约定、命名规范 | AGENTS | "组件放 `src/components/`，PascalCase" |
| 分支 / 提交 / 测试 / 验证流程 | AGENTS | "提交前必须跑 `pnpm test`" |
| 禁止事项、红线 | AGENTS | "禁止直接改 `migrations/` 中已应用的文件" |
| 任务拆解、优先级、状态 | DEVELOP_PLAN | "- [ ] P0: 用户登录接口" |
| 里程碑与时间安排 | DEVELOP_PLAN | "M1（第 1 周）：跑通核心链路" |
| 验收标准（每条可验证） | DEVELOP_PLAN | "输入错误密码返回 401，提示语为 X" |

**判断口诀：** 换个人接手项目要看的 → README；改代码要守的 → AGENTS；这件事做完没、对不对 → DEVELOP_PLAN。

## 不冗余原则：引用而非复制

- 同一信息**只允许存在一处**（写在其归属文件中）；其他文档需要时，用相对链接引用，禁止复制粘贴：

  ```markdown
  提交前请先跑测试，流程见 [AGENTS.md · 验证流程](./AGENTS.md#验证流程)。
  环境安装见 [README.md · 安装](./README.md#安装)。
  ```

- 链接用 `./文件名.md#锚点` 精确到小节；锚点为标题原文（空格换 `-`，中文标题直接可用）
- 一条信息在多处出现即视为冗余缺陷：修订时只改归属文件，引用处自动生效
- 临时讨论、单次决策过程不进三文档；结论若需长期遵守，归入 AGENTS；若是任务范畴，归入 DEVELOP_PLAN 对应条目

## 最小骨架

初始化时创建三个文件，只填已知信息，未知项留 `TODO`：

```markdown
<!-- README.md -->
# <项目名>
<一句话定位>
## 功能
- TODO
## 快速开始
## 环境要求 / 安装 / 启动
## 架构概览
（开发规范见 [AGENTS.md](./AGENTS.md)，当前计划见 [DEVELOP_PLAN.md](./DEVELOP_PLAN.md)）
```

```markdown
<!-- AGENTS.md -->
# 开发规范
## 目录约定
## 代码风格
## 流程要求（分支 / 提交 / 测试 / 验证）
## 禁止事项
（项目背景见 [README.md](./README.md)，勿在此重复）
```

```markdown
<!-- DEVELOP_PLAN.md -->
# 开发计划与验收
## 任务清单
- [ ] P0: <任务>（验收标准：<可验证的条目>）
## 里程碑
## 验收清单
（技术背景见 [README.md](./README.md)，改码规则见 [AGENTS.md](./AGENTS.md)，勿在此重复）
```

## 执行步骤

1. 按最小骨架创建 `README.md`、`AGENTS.md`、`DEVELOP_PLAN.md`
2. 填入当前已知信息，未确定项写 `TODO`，不编造
3. 自检两条：① 逐条核对内容是否写在归属文件（对照分类规则表）；② 检索是否存在重复内容，有则删掉副本改为引用
