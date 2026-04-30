# visual-style-ppt

Style-driven Codex Skill for turning documents, articles, and visual references into image-first presentation decks.

## Highest Priority Rule

This skill must use the Image 2 model for every generated slide image, thumbnail board, visual page, infographic, article illustration, and PPT page image. HTML output is forbidden: do not use HTML/CSS, browser screenshots, SVG/HTML mockups, canvas renders, PIL, or local scripts as final or intermediate image outputs. If Image 2 is unavailable, stop and state that Image 2 access is required.

<details open>
<summary>中文</summary>

一个用于「风格驱动 PPT」的 Codex Skill。

它把视觉风格当成可复用资产：先提炼或选择一个视觉风格，再基于文档、文章、提纲或主题生成图片版幻灯片提示词，并在需要时把逐页图片组装成 image-only PPTX。

## 仓库简介

`visual-style-ppt` 适合把内容策划、视觉风格提炼、Image2 生图提示词和图片版 PPT 打包流程串成一套稳定 SOP。它不追求可编辑 PPT 排版，而是把每页幻灯片视为一张高完成度视觉图片，再用 PPTX 作为最终交付容器。

推荐 GitHub About 简介：

```text
Style-driven Codex Skill for creating image-first PPT decks from documents, articles, and visual references.
```

推荐 Topics：

```text
codex-skill, ppt, presentation, image2, visual-style, prompt-engineering, slide-deck, markdown-to-ppt
```

## 适合做什么

- 把文章、Markdown、文档内容转成图片版 PPT
- 从截图、参考图、网页、已有 deck 中提炼视觉风格
- 保存、复用、维护一套 PPT 视觉风格库
- 用指定风格生成 `outline.md` 和 `prompts.md`
- 生成逐页幻灯片图片，并最终打包成 PPTX 和 zip
- 做小红书信息图、文章配图、视觉化报告页等风格统一的页面资产

## 核心原则

- **Image 2 only**：所有幻灯片图片、缩略图板、信息图和配图都必须由 Image 2 模型生成，严禁 HTML 出图或任何等价替代路线。
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

## 使用前提

- 已安装并可使用 Codex Skills。
- 需要生成图片时，当前环境必须具备可调用的 Image 2 模型；没有 Image 2 时不得用 HTML 或其它图像生成/本地渲染能力替代。
- 需要组装 PPTX 时，环境应具备 PPTX 创建能力；本 Skill 默认生成 image-only PPTX。
- 如果输入是 PDF、Word、Markdown 或网页内容，先确保 Codex 能读取对应文件或链接。

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

## 什么时候不适合用

- 需要高度可编辑的 PPT 源文件，例如每个文本框、图表和形状都要可单独修改。
- 需要严格品牌 Logo 复现，并要求模型在每页图片中稳定绘制相同 Logo。
- 需要大量表格、长段落、报告正文堆叠在单页里。
- 需要自动加入今天日期、导出时间或时间戳，但来源没有明确要求。

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

| 风格文件 | 适合内容 | 视觉气质 |
| --- | --- | --- |
| `terminal-tech-magazine.md` | AI、开发者工具、技术产品、深色视觉报告 | 终端科技杂志风格 |
| `impact-grid-editorial.md` | 观点型内容、趋势判断、强标题页面 | 冲击力网格编辑风格 |
| `french-editorial-commerce.md` | 品牌、消费、生活方式、审美型商业内容 | 法式编辑商业风格 |

## 新增风格规范

新增风格时，在 `styles/` 下创建一个稳定命名的 Markdown 文件，例如：

```text
styles/minimal-founder-deck.md
```

每个风格至少包含：

- 风格定位和适用场景
- 颜色系统，最好包含 hex 色值
- 字体气质与标题/正文层级
- 页面网格、留白、页眉页脚规则
- 卡片、边框、分割线、装饰元素规则
- `## Style Lock`
- Image2 negative constraints

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

## 命名约定

- 风格文件使用 kebab-case，例如 `terminal-tech-magazine.md`。
- 生成图片使用两位数序号，例如 `slide-01.png`。
- 中间文档使用稳定文件名，例如 `outline.md`、`prompts.md`、`revision-log.md`。
- 同一个项目的最终交付建议放入独立目录，避免不同 deck 的图片混在一起。

## 维护建议

- 修改工作流时更新 `SKILL.md` 和 `references/`。
- 新增视觉风格时只添加 `styles/*.md`，不要为了改风格重写 `SKILL.md`。
- 每个风格都要写清楚自己的 `Style Lock`。
- 避免在风格文件里写过多一次性项目内容，保持它可复用。
- 如果生成流程、包装方式或修订规则变化，同步更新 `references/` 中对应文档。

## 授权与使用

当前仓库按个人 Skill 仓库维护。若后续计划公开分发、接受外部贡献或作为模板复用，建议再补充正式开源协议，例如 MIT License。

</details>

<details>
<summary>English</summary>

A Codex Skill for style-driven visual presentation creation.

This skill treats visual style as a reusable asset: extract or select a visual style first, then use documents, articles, outlines, or topics to create image-based slide prompts. When needed, it assembles the generated slide images into an image-only PPTX deck.

## Repository Summary

`visual-style-ppt` connects content planning, visual style extraction, Image2 prompt writing, and image-first PPT packaging into a reusable workflow. It does not aim to create fully editable PowerPoint layouts. Instead, it treats each slide as a polished visual image and uses PPTX as the final delivery container.

Suggested GitHub About description:

```text
Style-driven Codex Skill for creating image-first PPT decks from documents, articles, and visual references.
```

Suggested topics:

```text
codex-skill, ppt, presentation, image2, visual-style, prompt-engineering, slide-deck, markdown-to-ppt
```

## What It Is For

- Turn articles, Markdown files, and documents into image-based presentations
- Extract visual style from screenshots, reference images, webpages, or existing decks
- Save, reuse, and maintain a visual style library for PPT creation
- Generate `outline.md` and `prompts.md` from a selected style
- Generate one slide image per page and package the result as PPTX and zip
- Create Xiaohongshu-style infographics, article visuals, visual reports, and consistent page assets

## Core Principles

- **Image 2 only**: Every slide image, thumbnail board, infographic, and illustration must be generated with the Image 2 model; HTML image output and equivalent substitute routes are forbidden.
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

## Requirements

- Codex Skills should be installed and available.
- Image generation requires the Image 2 model in the current environment; HTML and other image-generation or local-rendering substitutes are not allowed.
- PPTX assembly requires an environment capable of creating PPTX files; this skill defaults to image-only PPTX.
- If the input is a PDF, Word document, Markdown file, or webpage, make sure Codex can access the file or link.

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

## When Not To Use It

- You need a highly editable PPT source file where every text box, chart, and shape must remain separately editable.
- You need strict logo reproduction and expect the image model to redraw the same logo consistently on every page.
- You need dense tables, long paragraphs, or report-style body copy packed into a single slide.
- You need automatic dates, export times, or timestamps when the source does not explicitly require them.

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

| Style file | Best for | Visual mood |
| --- | --- | --- |
| `terminal-tech-magazine.md` | AI, developer tools, technical products, dark visual reports | Terminal tech magazine |
| `impact-grid-editorial.md` | Opinion pieces, trend analysis, strong title pages | High-impact editorial grid |
| `french-editorial-commerce.md` | Brand, consumer, lifestyle, aesthetic business content | French editorial commerce |

## Adding A New Style

Create a stable Markdown file under `styles/`, for example:

```text
styles/minimal-founder-deck.md
```

Each style should include:

- Style positioning and suitable use cases
- Color system, preferably with hex values
- Font mood and title/body hierarchy
- Page grid, spacing, header, and footer rules
- Card, border, divider, and decorative element rules
- `## Style Lock`
- Image2 negative constraints

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

## Naming Conventions

- Use kebab-case for style files, such as `terminal-tech-magazine.md`.
- Use two-digit numbering for generated images, such as `slide-01.png`.
- Use stable names for intermediate documents, such as `outline.md`, `prompts.md`, and `revision-log.md`.
- Keep each final project in its own output directory to avoid mixing images from different decks.

## Maintenance

- Update `SKILL.md` and `references/` when changing the workflow.
- Add new visual styles as `styles/*.md`; do not rewrite `SKILL.md` just to change a style.
- Make sure every style includes a clear `Style Lock`.
- Keep style files reusable and avoid embedding too much one-off project content.
- If the generation flow, packaging rules, or revision workflow changes, update the matching document in `references/`.

## License And Usage

This repository is currently maintained as a personal skill repository. If you plan to distribute it publicly, accept external contributions, or use it as a reusable template, consider adding a formal open source license such as the MIT License.

</details>
