# Skill: Competitive Research

自媒体竞品调研与文案生成。引用外部 MCP 服务做数据归档，其余环节由 agent 自主完成。

## 依赖

需要以下 MCP 工具可用（来自 `my-knowledge-base` 或任何兼容服务）：

| 工具 | 用途 |
|------|------|
| `ingest_url(url)` | 归档竞品文章到原料层 |
| `ingest_text(text)` | 手动录入无法抓取的内容 |
| `process_pending()` | 加工原料为结构化笔记 |
| `list_processed(tag, keyword)` | 查询已加工的笔记 |
| `generate_copy(topic, context)` | 生成文案（可选，也可自己写） |

## 触发短语

- `调研 {topic}`
- `写一篇关于 {topic} 的文案`
- `这个选题怎么样：{topic}`

## 流程

### Step 1: 搜索竞品

用你的 web search 搜索以下平台：

```
site:xiaohongshu.com {topic}
site:bilibili.com {topic}
site:zhihu.com {topic}
site:juejin.cn {topic}
site:mp.weixin.qq.com {topic}
```

### Step 2: 归档

- 对可抓取的 URL → 调 `ingest_url(url)` 归档
- 对无法抓取的页面 → 自己阅读总结 → 调 `ingest_text(text)` 手动录入
- 调 `process_pending()` 加工为笔记

### Step 3: 分析差距

调 `list_processed(tag=topic)` 查看竞品笔记，分析：

- 已覆盖角度 vs 空白机会
- 受众情绪诉求（焦虑/好奇/求快等）
- 差异化切入方向

### Step 4: 输出报告

生成两份文件（用你的 LLM 能力直接写，不需要调工具）：

1. `research_{topic}.md` — 竞品分析报告（覆盖矩阵 + 差异化建议 + 推荐选题）
2. `copy_{topic}.md` — 文案成品（AIDA 结构：标题 → Hook → 正文 → 结尾）

保存到当前工作目录。

### Step 5: 汇报

在回复中展示：
- 竞品分析结论
- 差异化角度
- 文案预览（前 500 字）

## 设计原则

- 不引入任何 Python 代码依赖，纯 agent + MCP 工具完成
- MCP 服务可替换——只要提供同名工具就能跑
- 搜索策略由 agent 自主决定，不绑定固定来源
