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
项目根目录/
├── PROJECT.md              ← 项目身份证（唯一外露标记）
├── .proj/                  ← 统一收纳（隐藏目录）
│   ├── scripts/            ← 工具/辅助脚本
│   ├── archive/            ← 旧版本、备份、已完成阶段的归档
│   ├── temp/               ← 临时产物（定期清理）
│   └── work/               ← AI 协作文件（频繁读写）
│       ├── task_plan.md    ← 当前阶段的任务队列
│       ├── todo.md         ← 待办事项清单
│       ├── progress.md     ← 历次会话进度记录
│       └── findings.md     ← 调研/发现记录（可选）
└── (项目核心文件...)       ← 自由组织
```

## 安装

### 方式一：使用 Skills CLI

```bash
npx skills add <your-username>/project-organization
```

### 方式二：手动安装

将本仓库克隆到 `~/.claude/skills/` 目录：

```bash
git clone https://github.com/<your-username>/project-organization.git ~/.claude/skills/project-organization
```

## 使用方法

1. 在项目根目录创建 `PROJECT.md` 文件
2. Skill 自动检测并加载，创建 `.proj/` 目录结构
3. 通过自然语言与 AI 协作管理项目

### 示例 PROJECT.md

```markdown
# 我的项目

## 基本信息
- **根目录路径**：`/path/to/project`
- **创建时间**：2024-01-01
- **项目简介**：一个很棒的项目

## 目录结构
| 路径 | 用途 |
|------|------|
| `src/` | 源代码 |
| `docs/` | 文档 |

## 当前状态
- **当前任务**：完成核心功能开发
- **上次会话**：2024-01-15
```

## 协作文件说明

| 文件 | 用途 | 生命周期 |
|------|------|---------|
| `task_plan.md` | 粗粒度里程碑任务队列 | 阶段性 |
| `todo.md` | 细粒度待办事项清单 | 持续流动 |
| `progress.md` | 会话进度记录 | 项目全周期 |
| `findings.md` | 调研/发现记录 | 可选 |

## 许可证

MIT License
