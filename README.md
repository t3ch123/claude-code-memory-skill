# Claude Code Memory

A lightweight memory layer for Claude Code, designed to persist context across sessions on long-running projects.

## Background

在长期项目中使用 Claude Code 时,每次新开会话都需要重新交代上下文——
当前进度、历史决策、已知问题、待办事项。这部分重复说明的成本会随项目周期增长。

本项目通过结构化的本地文件,让 Claude 自行维护会话间的状态,降低上下文重建成本。

## 工作机制

在项目根目录维护一个 `.claude/` 目录,包含一份 SKILL.md 和若干 markdown 备忘文件。

Claude Code 启动时自动读取 SKILL.md,SKILL.md 中定义了"读 / 写"两条强制流程:

- **启动流程**:读取当前状态、待办、已知问题、最近三次会话日志,向用户汇报
- **关闭流程**:在用户结束信号触发后,追加会话日志、更新当前状态、整理待办

## 目录结构

```
.claude/
├── SKILL.md
└── memory/
    ├── session_log.md      # 会话日志(追加,倒序)
    ├── current_state.md    # 项目当前状态(覆盖)
    ├── todo.md             # 待办事项
    ├── known_issues.md     # 已知问题与规避方案
    └── decisions.md        # 关键决策记录
```

## 接入方式

1. 复制本仓库 `.claude/` 至目标项目根目录
2. 启动 Claude Code

无需额外依赖或配置。

## 适用范围

适合具备以下特征的项目:

- 开发周期较长,涉及多次会话
- 存在需要持续追踪的决策与约束(技术选型、环境配置、业务规则)
- 多个工作流并行推进,容易遗忘进度

不建议用于一次性脚本或短期任务。

## 注意事项

- 记忆文件以 markdown 形式存储于本地,建议纳入版本控制
- 不应在记忆文件中记录密钥、密码或其他敏感信息
- 跨设备协作时,通过 git 同步 `.claude/` 目录即可

## License

MIT
