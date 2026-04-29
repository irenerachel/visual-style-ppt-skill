# visual-style-ppt

<details open>
<summary>中文</summary>

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

</details>

<details>
<summary>English</summary>

A Codex Skill for style-driven visual presentation creation.

This skill treats visual style as a reusable asset: extract or select a visual style first, then use documents, articles, outlines, or topics to create image-based slide prompts. When needed, it assembles the generated slide images into an image-only PPTX deck.

## What It Is For

- Turn articles, Markdown files, and documents into image-based presentations
- Extract visual style from screenshots, reference images, webpages, or existing decks
- Save, reuse, and maintain a visual style library for PPT creation
- Generate `outline.md` and `prompts.md` from a selected style
- Generate one slide image per page and package the result as PPTX and zip
- Create Xiaohongshu-style infographics, article visuals, visual reports, and consistent page assets

## Core Principles

- **Image2-first**: Generate complete slide images by default, instead of editable PPT elements.
- **One image per slide**: Each final slide should be saved as an individual image, such as `slide-01.png` or `slide-02.png`.
- **Style isolation**: Each deck uses exactly one selected style and one `Style Lock`, avoiding visual DNA from past tasks or unrelated references.
- **Low text density**: Inner slides stay calm by default: one title, one short takeaway, and at most 2-3 information points.
- **Chinese-first by default**: Slide titles, section labels, and support documents default to Chinese; product names, model names, and API terms stay in English when clearer.
- **No automatic dates**: Dates and timestamps are not added unless the source or the user explicitly requires them.

## Structure

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

## Installation

Place this repository under your Codex skills directory:

```bash
cd ~/.codex/skills
git clone https://github.com/irenerachel/visual-style-ppt-skill.git visual-style-ppt
```

If you already have a local copy, update it with:

```bash
cd ~/.codex/skills/visual-style-ppt
git pull
```

## Example Prompts

```text
Use the terminal-tech style and turn this article into an 8-slide PPT.
```

```text
Use the CodeBuddy-like tech magazine style to turn this Markdown file into a 16:9 image-based presentation.
```

```text
Extract the style from this image and save it as a reusable PPT style.
```

```text
List the available PPT styles.
```

```text
Use the saved terminal-tech-magazine style. Give me the outline and prompts first, then wait for confirmation before generating images.
```

## Standard Workflow

1. Classify the task: style extraction, style application, document-to-PPT, image-only PPT revision, or style library management.
2. Select or create a visual style file.
3. Extract the story arc, audience, page count suggestion, and key visual moments from the source.
4. Generate `outline.md` and `prompts.md` first.
5. For multi-page decks, generate a thumbnail board first to lock the visual rhythm.
6. After user confirmation, generate each final slide image one by one.
7. After all images are approved, assemble an image-only PPTX.
8. Package the final images, PPTX, prompts, outline, style file, and revision log.

## Style Library

Reusable styles live in the `styles/` directory. Each style is a Markdown file.

Every style file should include a `## Style Lock` section that controls the deck's font mood, layout grid, color ratios, border system, headers and footers, text density, logo handling, and Image2 negative constraints.

Built-in styles:

- `terminal-tech-magazine.md`: Terminal tech magazine style for AI, developer tools, technical products, and dark visual reports.
- `impact-grid-editorial.md`: High-impact editorial grid style for opinion pieces, trend analysis, and strong title pages.
- `french-editorial-commerce.md`: French editorial commerce style for brand, consumer, lifestyle, and aesthetic business content.

## Output Convention

Recommended output files include:

- `outline.md`
- `prompts.md`
- `style-used.md`
- `thumbnail-board.png`
- `slide-01.png`
- `slide-02.png`
- `deck.pptx`
- `revision-log.md`
- final `.zip`

The PPTX is a delivery container, not the editable layout source. The final visual result is defined by the per-slide images.

## Maintenance

- Update `SKILL.md` and `references/` when changing the workflow.
- Add new visual styles as `styles/*.md`; do not rewrite `SKILL.md` just to change a style.
- Make sure every style includes a clear `Style Lock`.
- Keep style files reusable and avoid embedding too much one-off project content.

## License

Personal skill repository. Add a license if you plan to distribute or accept external contributions.

</details>
