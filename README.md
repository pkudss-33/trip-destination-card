# Trip Destination Card

> 一个 Claude Code 技能：将行程目的地信息转化为精美的"电子杂志 × 电子墨水"风格对比卡片。

![Skill](https://img.shields.io/badge/Skill-Trip%20Destination-8B6C42?style=flat-square)
![Claude Code](https://img.shields.io/badge/Claude%20Code-Supported-6B5B95?style=flat-square)
![License](https://img.shields.io/github/license/pkudss-33/trip-destination-card?style=flat-square)

当你需要给老板或团队做**行程方案备选展示**时，告诉 Claude Code，它会自动调用这个技能，输出一份优雅、可翻页、可导出图片的单页 HTML 报告。

## 效果预览

- 暖色纸质感电子墨水风格，像 *Monocle* 杂志的旅行特辑
- 单酒店页面：左 1/3 信息 + 右 2/3 图片（横版/竖版分栏排列）
- 双酒店页面：左中右三栏（交通天气 | 酒店A+图 | 酒店B+图）
- 横向翻页（键盘 ← →）+ 纵向长图双模式，一键导出 PNG

## 快速安装

### 方式一：git clone（通用，零依赖）

```bash
mkdir -p ~/.claude/skills && git clone https://github.com/pkudss-33/trip-destination-card.git ~/.claude/skills/trip-destination-card
```

### 方式二：gh skill install（需要 GitHub CLI ≥ v2.90）

```bash
gh skill install pkudss-33/trip-destination-card trip-destination-card --agent claude-code --scope user
```

### 方式三：npx skills（需要 Node.js）

```bash
npx skills add pkudss-33/trip-destination-card
```

安装完成后，重启 Claude Code 或在新对话中使用。

## 触发方式

在 Claude Code 中提及以下关键词即可自动触发：

| 中文 | 英文 |
|---|---|
| 行程方案、目的地备选、出差方案 | trip plan, destination card |
| 旅行卡片、选点方案 | travel proposal |

**示例对话：**

> "帮我做一个7月出行的目的地备选方案，有乌鲁木齐、伊宁、拉萨三个地方"

> "老板要看这几个酒店的对比，做成卡片"

## 使用流程

1. **触发技能**后，Skill 会先返回一个问题清单
2. **按清单提供信息**：每个目的地的交通、天气、酒店、优缺点
3. **发送图片**：标注属于哪个目的地即可（横版/竖版自动识别）
4. Skill 自动生成 HTML，在浏览器中预览
5. 可切换翻页/长图模式，一键导出 PNG

## 信息格式（标准化）

无论你以什么格式提供信息（PDF、聊天、表格），Skill 会统一标准化为以下字段：

| 字段 | 示例 |
|---|---|
| 目的地 | 乌鲁木齐 · 北疆·天山北麓 |
| 交通 | 北京直飞 4h / 7/2 周四 20:55–01:15 首都→乌市 / 大飞机，无 WiFi |
| 天气 | 7月 20–30℃ / 温差大，紫外线强 |
| 酒店 | 希尔顿 / 2015年开业 / 希尔顿套房 / 110㎡ / 3200元/晚 / 无露台·禁烟 |
| 优点/注意 | 各 2-5 条 |

## 图片布局规则

- **单酒店**：横版图（宽>高）→ 右区左栏 60%，竖版图（高>宽）→ 右区右栏 40%
- **双酒店**：每个酒店下方等宽双图并排
- 图片保持原始比例，自动缩放到适配位置，不裁剪不变形

## 文件结构

```
trip-destination-card/
├── SKILL.md                    # 技能定义（触发词、标准化规范、工作流）
├── README.md                   # 本文件
├── assets/
│   └── template.html           # 完整设计系统模板（[[...]] 占位符）
└── references/
    └── layout-guide.md         # 布局参数、字体规格、响应式规则
```

## 许可证

MIT
