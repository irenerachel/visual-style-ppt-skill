# visual-style-ppt

English | [中文](README.zh-CN.md)

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
