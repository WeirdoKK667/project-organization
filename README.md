# project-organization

AI 协作项目管理系统 — 自动组织项目结构、管理任务队列、同步 Git/GitHub。

## 功能特性

| 特性 | 说明 |
|------|------|
| **智能触发** | 检测 `PROJECT.md` 或用户明确意图（"初始化项目"、"需要项目管理"） |
| **项目结构** | 自动创建 `.proj/` 目录体系 |
| **任务队列** | 里程碑式任务管理，自动归档历史阶段 |
| **待办事项** | 细粒度清单，标签分类，优先级分区 |
| **进度追踪** | 会话进度自动记录，保留完整历史 |
| **Git 集成** | 智能版本标签（patch/minor/major 自动判断） |
| **GitHub 同步** | 会话开始自动拉取，结束自动推送，故障本地队列 |

## 快速开始

### 方式一：Skills CLI（推荐）

```bash
npx skills add WeirdoKK667/project-organization
```

### 方式二：手动安装

```bash
git clone https://github.com/WeirdoKK667/project-organization.git ~/.claude/skills/project-organization
```

## 使用方法

### 触发方式

| 方式 | 示例 |
|------|------|
| **自动检测** | 工作目录存在 `PROJECT.md` |
| **意图触发** | "初始化个项目"、"需要项目管理"、"帮我整理项目" |

### 初始化项目

```bash
# 在目标目录中告诉 AI：
$ "开个新项目" 或 "需要管理这个项目"

# AI 会自动询问并创建：
# - PROJECT.md
# - .proj/ 目录结构
# - .proj/config.yaml（若启用 GitHub）
```

### 目录结构

```
项目根目录/
├── PROJECT.md              ← 项目身份证
├── .proj/
│   ├── config.yaml        ← Git/GitHub 配置
│   ├── scripts/           ← 工具脚本
│   ├── archive/           ← 历史归档
│   ├── temp/              ← 临时文件
│   └── work/
│       ├── task_plan.md   ← 任务队列
│       ├── todo.md        ← 待办清单
│       ├── progress.md    ← 进度记录
│       └── findings.md    ← 调研记录
└── (项目文件...)
```

## 协作文件

| 文件 | 用途 |
|------|------|
| `PROJECT.md` | 项目元信息，放在根目录 |
| `task_plan.md` | 粗粒度里程碑，阶段性 |
| `todo.md` | 细粒度待办，持续流动 |
| `progress.md` | 会话进度历史 |
| `findings.md` | 调研/发现记录 |
| `.proj/config.yaml` | Git/GitHub 配置 |

## 模板文件

`references/` 目录提供所有协作文件的模板：

- `project-template.md` — PROJECT.md 模板
- `todo-template.md` — 待办事项模板
- `task-plan-template.md` — 任务队列模板
- `progress-template.md` — 进度记录模板
- `config-template.yaml` — 配置文件模板

## Git 版本标签

自动判断变更级别：

| 变更类型 | 示例 | 版本递增 |
|---------|------|---------|
| patch | 修复 bug、文档更新 | v0.1.0 → v0.1.1 |
| minor | 新增功能 | v0.1.0 → v0.2.0 |
| major | 架构重构 | v0.1.0 → v1.0.0 |

## 自动同步

| 时机 | 行为 |
|------|------|
| 会话开始 | `git pull` 拉取远程更新 |
| 会话结束 | `add → commit → push` 推送更改 |
| 每 N 次会话 | 强制同步（可配置） |
| 故障时 | 本地队列缓存，下次重试 |

## 示例项目

参考 `examples/sample-project/` 查看完整示例。

## 更新技能

```bash
npx skills update
```

## 许可证

MIT License
