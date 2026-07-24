# project-organization

项目文件组织与 AI 协作管理 Skill。

## 功能特性

- **自动触发**：当工作目录或其父目录中存在 `PROJECT.md` 文件时自动加载
- **目录结构**：统一管理 `.proj/` 目录（scripts/、archive/、temp/、work/）
- **任务队列**：基于 `task_plan.md` 进行里程碑式任务管理
- **待办事项**：细粒度待办清单，支持标签分类和优先级分区
- **进度追踪**：自动记录会话进度，自动归档完成的阶段
- **文件分类**：智能判断文件归属（核心交付物/工具脚本/归档/临时文件）

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
│   └── progress-template.md
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

1. 在项目根目录创建 `PROJECT.md` 文件（参考 `examples/sample-project/`）
2. Skill 自动检测并加载，创建 `.proj/` 目录结构
3. 通过自然语言与 AI 协作管理项目

### 快速开始

```bash
# 在你的项目根目录创建 PROJECT.md
touch PROJECT.md

# 然后像平常一样与 AI 对话，AI 会自动识别并启用项目管理技能
```

### 协作文件说明

| 文件 | 用途 | 生命周期 |
|------|------|---------|
| `PROJECT.md` | 项目身份证，放在项目根目录 | 项目全周期 |
| `task_plan.md` | 粗粒度里程碑任务队列 | 阶段性 |
| `todo.md` | 细粒度待办事项清单 | 持续流动 |
| `progress.md` | 会话进度记录 | 项目全周期 |
| `findings.md` | 调研/发现记录 | 可选 |

### 模板文件

`references/` 目录下提供了各类协作文件的模板：

| 模板文件 | 用途 |
|---------|------|
| `project-template.md` | `PROJECT.md` 模板 |
| `todo-template.md` | `todo.md` 模板 |
| `task-plan-template.md` | `task_plan.md` 模板 |
| `progress-template.md` | `progress.md` 模板 |

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
