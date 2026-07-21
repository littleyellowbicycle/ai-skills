# AI Skills

可复用的 AI Agent 技能包。每个 skill 是一个自包含的 `SKILL.md`，定义 agent 在特定场景下的完整工作流。

## 使用方式

```bash
# 克隆到你的 agent skills 目录
git clone https://github.com/littleyellowbicycle/ai-skills.git ~/.agents/skills/

# 或只拉取需要的 skill
cp -r ai-skills/competitive-research ~/.agents/skills/
```

## Skills

| Skill | 说明 | 触发短语 |
|-------|------|----------|
| competitive-research | 竞品调研 → 差异化分析 → 自媒体文案生成 | "调研 {topic}" |

## 设计原则

- 零代码依赖，纯 agent 指令 + MCP 工具
- MCP 工具可替换，不绑定特定服务
- 搜索策略由 agent 自主决定
