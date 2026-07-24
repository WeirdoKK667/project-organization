# project-organization

项目文件组织与 AI 协作管理 Skill。

## 功能特性

- **智能触发**：检测 `PROJECT.md` 文件或用户关键词（"项目"、"初始化"、"这个目录"等）
- **目录结构**：统一管理 `.proj/` 目录（scripts/、archive/、temp/、work/）
- **任务队列**：基于 `task_plan.md` 进行里程碑式任务管理
- **待办事项**：细粒度待办清单，支持标签分类和优先级分区
- **进度追踪**：自动记录会话进度，自动归档完成的阶段
- **文件分类**：智能判断文件归属（核心交付物/工具脚本/归档/临时文件）
- **Git 集成**：自动标签管理（v1.0.0 等版本标签）
- **GitHub 同步**：会话开始自动拉取、结束自动推送、定期自动同步

## 目录结构

```
project-organization/
├── SKILL.md              # 技能主体
├── manifest.yaml         # 技能元数据
├── CHANGELOG.md          # 版本变更历史
├── README.md             # 本文件
├── references/           # 模板参考
│   ├── project-template.md
│   ├── todo-template.md
│   ├── task-plan-template.md
│   ├── progress-template.md
│   └── config-template.yaml
└── examples/             # 示例项目
    └── sample-project/
        ├── PROJECT.md
        └── .proj/work/
```

## 安装

### 方式一：使用 Skills CLI（推荐）

```bash
npx skills add WeirdoKK667/project-organization
```

### 方式二：手动安装

将本仓库克隆到 `~/.claude/skills/` 目录：

```bash
git clone https://github.com/WeirdoKK667/project-organization.git ~/.claude/skills/project-organization
```

## 使用方法

### 快速开始

只需在项目中和 AI 对话，提到"项目"、"初始化"、"需要管理"等词汇，AI 会自动询问是否初始化项目结构。

### 初始化项目

```
# 方式1：提到关键词时触发
$ AI: "我需要管理一下这个项目"
$ AI: "是否需要为此目录初始化项目结构？"

# 方式2：自动检测（已有 PROJECT.md）
$ AI: "检测到项目结构，自动加载项目管理功能..."
```

### 协作文件说明

| 文件 | 用途 | 生命周期 |
|------|------|---------|
| `PROJECT.md` | 项目身份证，放在项目根目录 | 项目全周期 |
| `task_plan.md` | 粗粒度里程碑任务队列 | 阶段性 |
| `todo.md` | 细粒度待办事项清单 | 持续流动 |
| `progress.md` | 会话进度记录 | 项目全周期 |
| `findings.md` | 调研/发现记录 | 可选 |
| `.proj/config.yaml` | Git/GitHub 配置 | 项目全周期 |

### 模板文件

`references/` 目录下提供了各类协作文件的模板：

| 模板文件 | 用途 |
|---------|------|
| `project-template.md` | `PROJECT.md` 模板 |
| `todo-template.md` | `todo.md` 模板 |
| `task-plan-template.md` | `task_plan.md` 模板 |
| `progress-template.md` | `progress.md` 模板 |
| `config-template.yaml` | `.proj/config.yaml` 模板 |

## Git 与 GitHub 功能

初始化项目时，AI 会询问是否启用以下功能：

| 功能 | 说明 |
|------|------|
| **Git 版本控制** | 自动标签管理（v1.0.0、v1.1.0 等） |
| **GitHub 同步** | 自动推送更新到远程仓库 |

### 自动同步机制

- **会话开始**：自动拉取远程更新
- **会话结束**：自动提交并推送所有更改
- **定期同步**：每 N 次会话自动执行（可配置）
- **故障处理**：推送失败时保存到本地队列，下次重试

## 示例项目

参考 `examples/sample-project/` 查看完整示例，包括：

- 典型的 `PROJECT.md` 配置
- 已填充的 `task_plan.md`
- 包含多个分区的 `todo.md`
- 包含多次会话历史的 `progress.md`

## 更新技能

```bash
# 更新到最新版本
npx skills update
```

## 许可证

MIT License
