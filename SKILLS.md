# 技能索引 (Skills Index)

> SMC (Sumulige Claude) 技能库总览

@version: 1.1.0

## 目录

- [官方 Claude Skills](#官方-claude-skills)
- [SMC 内置 Agents](#smc-内置-agents)
- [工作流类](#工作流类)
- [示例技能](#示例技能)
- [技能模板](#技能模板)
- [创建新技能](#创建新技能)

---

## 官方 Claude Skills

> 由 Anthropic 官方维护的技能包，来自 https://github.com/anthropics/skills

### 文档处理类

| 技能 | 说明 | 用途 |
|------|------|------|
| [docx](./docx/) | Word 文档处理 | 创建和编辑 Word 文档 |
| [pdf](./pdf/) | PDF 文档处理 | 处理 PDF 文件 |
| [pptx](./pptx/) | PowerPoint 演示文稿 | 创建 PPT 幻灯片 |
| [xlsx](./xlsx/) | Excel 电子表格 | 处理 Excel 文件 |
| [doc-coauthoring](./doc-coauthoring/) | 文档协作 | 共同编辑文档 |

### 设计创意类

| 技能 | 说明 | 用途 |
|------|------|------|
| [algorithmic-art](./algorithmic-art/) | 算法艺术 | 生成算法艺术作品 |
| [canvas-design](./canvas-design/) | Canvas 设计 | HTML5 Canvas 设计 |
| [brand-guidelines](./brand-guidelines/) | 品牌指南 | 品牌规范管理 |
| [theme-factory](./theme-factory/) | 主题工厂 | 创建主题 |

### 开发工具类

| 技能 | 说明 | 用途 |
|------|------|------|
| [mcp-builder](./mcp-builder/) | MCP 构建器 | 构建 MCP 服务器 |
| [webapp-testing](./webapp-testing/) | Web 应用测试 | 测试 Web 应用 |
| [web-artifacts-builder](./web-artifacts-builder/) | Web 构建器 | 构建 Web 工件 |
| [skill-creator](./skill-creator/) | 技能创建工具 | 创建新技能 |

### 通信工具类

| 技能 | 说明 | 用途 |
|------|------|------|
| [slack-gif-creator](./slack-gif-creator/) | Slack GIF 创建 | 创建 Slack GIF |
| [internal-comms](./internal-comms/) | 内部沟通 | 团队沟通 |

---

## SMC 内置 Agents

> 5 个专用 Agent，实现 oh-my-opencode 同等能力

| Agent | 对应 oh-my-opencode | 核心能力 |
|-------|-------------------|----------|
| [conductor](./conductor/) | Sisyphus | 任务分解、并行协调、TODO 强制完成 |
| [architect](./architect/) | oracle | 系统设计、技术决策、深度分析 |
| [builder](./builder/) | frontend-ui-ux-engineer | 代码实现、测试、UI/UX |
| [reviewer](./reviewer/) | - | 代码质量、安全检查、最佳实践 |
| [librarian](./librarian/) | librarian | 文档查找、代码探索、知识管理 |

---

## 内置技能

### 工作流类

| 技能 | 说明 | 难度 |
|------|------|------|
| [manus-kickoff](./manus-kickoff/) | Manus 风格项目启动流程 | 中级 |

### 开发类

*(待补充)*

### 设计类

*(待补充)*

---

## 示例技能

| 技能 | 说明 | 难度 |
|------|------|------|
| [basic-task](./examples/basic-task.md) | 基础任务处理模板 | 初级 |
| [feature-development](./examples/feature-development.md) | 功能开发工作流 | 中级 |
| [bug-fix-workflow](./examples/bug-fix-workflow.md) | Bug 修复流程 | 中级 |

---

## 技能模板

### 标准技能结构

```
skill-name/
├── SKILL.md          # 技能定义（必需）
├── metadata.yaml     # 技能元数据（必需）
├── templates/        # 模板文件（可选）
│   └── default.md
└── examples/         # 示例文件（可选）
    └── basic.md
```

### SKILL.md 模板

参考 [template/SKILL.md](./template/SKILL.md)

### metadata.yaml 模板

```yaml
name: skill-name
version: 1.0.0
author: @username
description: 技能描述

tags:
  - category1
  - category2

triggers:
  - keyword1
  - keyword2

dependencies: []  # 依赖的其他技能

difficulty: beginner  # beginner | intermediate | advanced
```

---

## 创建新技能

### 使用 CLI 命令

```bash
oh-my-claude skill:create my-skill
```

### 手动创建

1. 复制模板：
```bash
cp -r .claude/skills/template .claude/skills/my-skill
```

2. 编辑 SKILL.md

3. 更新 metadata.yaml

4. 更新本索引

---

## 技能依赖管理

### 定义依赖

在 metadata.yaml 中声明：

```yaml
dependencies:
  - manus-kickoff
  - code-review
```

### 依赖解析

当使用技能时，系统会：
1. 检查依赖是否已安装
2. 按顺序加载依赖技能
3. 提示缺失的依赖

### 循环依赖检测

系统会自动检测并警告循环依赖。

---

## RAG 集成

技能会自动注册到 RAG 索引中 (`.claude/rag/skill-index.json`)，实现智能发现。

---

## 更新日志

### 1.0.0 (2026-01-11)
- 初始版本
- 添加 Manus Kickoff 技能
- 添加 3 个示例技能
- 添加技能模板
