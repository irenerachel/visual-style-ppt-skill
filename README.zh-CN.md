# visual-style-ppt

[English](README.en.md) | 中文

一个用于「风格驱动 PPT」的 Codex Skill。

它把视觉风格当成可复用资产：先提炼或选择一个视觉风格，再基于文档、文章、提纲或主题生成图片版幻灯片提示词，并在需要时把逐页图片组装成 image-only PPTX。

## 适合做什么

- 把文章、Markdown、文档内容转成图片版 PPT
- 从截图、参考图、网页、已有 deck 中提炼视觉风格
- 保存、复用、维护一套 PPT 视觉风格库
- 用指定风格生成 `outline.md` 和 `prompts.md`
- 生成逐页幻灯片图片，并最终打包成 PPTX 和 zip
- 做小红书信息图、文章配图、视觉化报告页等风格统一的页面资产

## 核心原则

- **Image2-first**：默认生成完整的幻灯片图片，而不是可编辑 PPT 元素。
- **一页一图**：每一页最终幻灯片都应保存为单独图片，例如 `slide-01.png`、`slide-02.png`。
- **风格隔离**：一个 deck 只使用一个选定风格和一个 `Style Lock`，避免混入历史任务或无关参考图的视觉 DNA。
- **低信息密度**：默认内页保持克制，一页一个主标题、一个简短 takeaway，最多 2-3 个信息点。
- **中文优先**：默认使用中文标题、中文模块名和中文支持文档；产品名、模型名、API 等保留英文。
- **不自动加日期**：除非来源或用户明确要求，否则不在页面、脚注或元数据中添加日期和时间。

## 目录结构

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── output-package.md
│   ├── page-types.md
│   ├── revision-workflow.md
│   ├── style-interview.md
│   └── workflow.md
└── styles/
    ├── french-editorial-commerce.md
    ├── impact-grid-editorial.md
    └── terminal-tech-magazine.md
```

## 安装

把这个仓库放到 Codex 的 skills 目录下：

```bash
cd ~/.codex/skills
git clone https://github.com/irenerachel/visual-style-ppt-skill.git visual-style-ppt
```

如果你已经有本地目录，也可以直接更新：

```bash
cd ~/.codex/skills/visual-style-ppt
git pull
```

## 使用示例

```text
调用终端风格，把这篇文章做成 8 页 PPT
```

```text
用 CodeBuddy 那种科技杂志风格，把这个 Markdown 做成图片版 PPT，16:9
```

```text
提炼这张图的风格，保存成一个可复用 PPT 风格
```

```text
列出现在可用的 PPT 风格
```

```text
用保存的 terminal-tech-magazine 风格，先给我 outline 和 prompts，我确认后再生成图片
```

## 标准工作流

1. 判断任务类型：提炼风格、调用风格、文档转 PPT、图片版 PPT 修订，或风格库管理。
2. 选择或创建一个视觉风格文件。
3. 从内容中抽取故事线、受众、页数建议和关键视觉时刻。
4. 先生成 `outline.md` 和 `prompts.md`。
5. 多页 deck 优先生成 thumbnail board，用于锁定整体节奏。
6. 用户确认后，再逐页生成最终幻灯片图片。
7. 用户确认全部图片后，组装 image-only PPTX。
8. 打包最终图片、PPTX、提示词、提纲、风格文件和修订记录。

## 风格库

可复用风格放在 `styles/` 目录，每个风格是一个 Markdown 文件。

每个风格文件都应该包含 `## Style Lock`，用于控制整套 deck 的字体气质、布局网格、色彩比例、边框系统、页眉页脚、文本密度、Logo 处理和 Image2 negative constraints。

当前内置风格：

- `terminal-tech-magazine.md`：终端科技杂志风格，适合 AI、开发者工具、技术产品和深色视觉报告。
- `impact-grid-editorial.md`：冲击力网格编辑风格，适合观点型内容、趋势判断和强标题页面。
- `french-editorial-commerce.md`：法式编辑商业风格，适合品牌、消费、生活方式和审美型商业内容。

## 生成物约定

推荐输出文件包括：

- `outline.md`
- `prompts.md`
- `style-used.md`
- `thumbnail-board.png`
- `slide-01.png`
- `slide-02.png`
- `deck.pptx`
- `revision-log.md`
- final `.zip`

PPTX 是交付容器，不是可编辑排版源文件。真正的视觉结果以逐页图片为准。

## 维护建议

- 修改工作流时更新 `SKILL.md` 和 `references/`。
- 新增视觉风格时只添加 `styles/*.md`，不要为了改风格重写 `SKILL.md`。
- 每个风格都要写清楚自己的 `Style Lock`。
- 避免在风格文件里写过多一次性项目内容，保持它可复用。

## License

Personal skill repository. Add a license if you plan to distribute or accept external contributions.
