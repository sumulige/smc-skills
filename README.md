# SMC Skills - Sumulige Claude Agent System

> 5 个专用 Agent 技能包，实现 oh-my-opencode 同等能力

## Agents

| Agent | 对应 oh-my-opencode | 核心能力 |
|-------|-------------------|----------|
| **conductor** | Sisyphus | 任务分解、并行协调、TODO 强制完成 |
| **architect** | oracle | 系统设计、技术决策、深度分析 |
| **builder** | frontend-ui-ux-engineer | 代码实现、测试、UI/UX |
| **reviewer** | (新增) | 代码质量、安全检查、最佳实践 |
| **librarian** | librarian | 文档查找、代码探索、知识管理 |

## 安装

```bash
# 复制到你的 SMC 配置目录
cp -r ~/.claude/skills/* ~/.claude/skills/
```

## 配置

在 `~/.claude/config.json` 中添加 agents 配置：

```json
{
  "agents": {
    "conductor": "任务协调与分解",
    "architect": "架构设计与决策",
    "builder": "代码实现与测试",
    "reviewer": "代码审查与质量检查",
    "librarian": "文档与知识管理"
  }
}
```

## 使用

```bash
# 使用 SMC
smc status

# 调用特定 agent
smc agent conductor "分析并实现这个任务"
smc agent architect "设计这个系统的架构"
smc agent librarian "查找 FastAPI JWT 认证文档"
```

## 核心能力

| 能力 | oh-my-opencode | SMC |
|------|---------------|-----|
| 并行 agents | ✅ | ✅ conductor 协调 |
| 背景任务 | ✅ | ✅ bash 支持 |
| TODO 强制完成 | ✅ | ✅ conductor 实现 |
| LSP 支持 | ✅ | ✅ 集成到工具链 |
| 文档搜索 | ✅ context7 | ✅ librarian |
| 代码搜索 | ✅ grep.app | ✅ librarian + webfetch |
| Git 集成 | ✅ git-master | ✅ builder bash |

## 项目结构

```
skills/
├── conductor/
│   └── SKILL.md    # 主协调器 - 任务分解、并行执行、TODO 强制
├── architect/
│   └── SKILL.md    # 架构师 - 系统设计、技术决策、深度分析
├── builder/
│   └── SKILL.md    # 构建者 - 代码实现、测试、UI/UX
├── reviewer/
│   └── SKILL.md    # 审查者 - 代码质量、安全检查、最佳实践
└── librarian/
    └── SKILL.md    # 图书馆员 - 文档查找、代码探索、知识管理
```

## 灵感来源

- [oh-my-opencode](https://github.com/code-yeongyu/oh-my-opencode) - Agent harness 设计
- [Claude Code](https://claude.ai/code) - 技能系统设计

## License

MIT
