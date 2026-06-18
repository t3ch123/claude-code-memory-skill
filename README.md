# Claude Code 项目记忆系统

让 Claude Code 在不同会话之间保持长期记忆的技能,不用每次重新解释项目背景。

## 适合谁

- 长期开发同一项目的人
- 容易忘记上次进度的人
- 经常切换 Claude Code 会话的人

## 怎么用

1. 下载本仓库的 SKILL.md
2. 放到你项目根目录下的 `.claude/` 文件夹里
3. 创建 `.claude/memory/` 子文件夹
4. 启动 Claude Code,它会自动读取 SKILL.md 并按记忆流程工作

## 文件结构

your-project/
└── .claude/
    ├── SKILL.md
    └── memory/
        ├── session_log.md
        ├── current_state.md
        ├── todo.md
        ├── known_issues.md
        └── decisions.md

## 效果

- 每次启动 Claude Code 自动汇报"上次做了什么"
- 关闭会话前自动保存进度
- 跨设备同步(把 .claude 目录提交到 git)

## License

MIT
