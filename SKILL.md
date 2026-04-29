---
name: visual-style-ppt
description: Create style-driven slide images with Image2, assemble those images into image-only PPTX decks, and manage reusable visual style libraries from documents or visual references. Use when the user asks for a "PPT Skill", "风格驱动 PPT", "提炼风格做 PPT", "调用某个风格做 PPT", "图片版 PPT", "保存 PPT 风格", "列出 PPT 风格", "文档生成 PPT", "文章生成 PPT", "把文档做成演示文稿", or wants to extract, save, reuse, and apply visual style keywords specifically for visual slide/image deck creation.
---

# Visual Style PPT

## Core Idea

Turn visual style into a reusable asset, then apply that asset to documents, outlines, image-only PPT decks, slide images, Xiaohongshu information graphics, and article illustrations.

Use this skill as an Image2-first visual slide workflow. The default deliverable is full-slide images; when the user wants a PPT, place the generated images into a PPTX as full-slide image pages. Do not implement or optimize editable PPTX content unless the user explicitly overrides this skill direction.

## Required References

- For the full operating workflow, read `references/workflow.md`.
- For PPTX vs image output rules, read `references/output-package.md`.
- For page type selection, read `references/page-types.md`.
- For post-generation revisions, read `references/revision-workflow.md`.
- For style extraction interviews, read `references/style-interview.md`.
- For the default terminal-tech magazine visual style, read `styles/terminal-tech-magazine.md`.
- When the user asks for a style library, list or read files in `styles/`.

## Default Behavior

- Default output type: Image2-generated slide images. If the user says "PPT", assemble those images into an image-only PPTX.
- Default aspect ratio: 16:9.
- Default image quality: Image2, 16:9, high-resolution, sharp text, clean edges.
- Default language: Chinese-first. Use Chinese for slide titles, section titles, module labels, captions, explanatory copy, and all generated support documents unless the user explicitly asks for another language. Keep proper nouns, product names, model names, code terms, and unavoidable domain terms in their original language when that is clearer.
- Default style: `styles/terminal-tech-magazine.md` when the user says "终端风格", "CodeBuddy 风格", "科技杂志风格", or does not specify another saved style.
- Default text density: low information by default, especially for PPT inner slides. Never create dense slides unless the user explicitly asks for a leave-behind, report page, or infographic. A normal inner slide should have one title, one short subtitle or takeaway, and at most 2-3 short information points.
- Default layout direction: cover pages may be visually expressive; inner slides must be information-first, calm, readable, and spacious, with imagery/backgrounds kept subordinate.
- Default style isolation: each deck must use exactly one selected style source and one `Style Lock`. Do not blend visual DNA from earlier tasks, previous reference images, or unrelated saved styles unless the user explicitly requests a hybrid.
- Default component consistency: across one deck, borders, cards, containers, dividers, arrows, footer metadata, corner radius, and line weights must use one repeated system. Variation may come from layout and emphasis, not from changing the frame/container style on every slide.
- Default slide header consistency: if a style uses small top titles with numbers, treat them as repeated content-section headers, not necessarily absolute slide/page numbers. Keep the same placement, size, spacing, and format across all applicable slides. If the style defines exceptions such as cover, contents, divider, or thank-you pages, preserve those exceptions deliberately; those exception pages do not consume a content-section number. The first applicable inner/content slide should usually start at `01` or `PART 1`.
- Default logo behavior: do not ask Image2 to generate logos, brand wordmarks, reusable deck marks, watermarks, or repeated English identity labels by default. If the user needs a logo, keep it out of generated slide images and add it later as a fixed post-production asset/layer, or let the user add it after delivery. A reference logo image may guide visual shape but is not reliable enough for cross-page text/logo consistency inside Image2 output.
- Default time/date behavior: do not add dates, times, timestamps, "today", export time, generated time, or current date to slides, prompts, metadata, footers, or visual elements by default. Include date/time only when the source article explicitly requires it, the user explicitly asks for it, or the slide topic itself is a timeline/schedule/date-sensitive report. A source document having a file timestamp, export timestamp, or local system date does not by itself justify visible date/time in the deck.
- Default page count: ask the user how many pages/slides they want unless they already provided a count or explicitly asked the skill to decide.
- Multiple outputs: keep one visual DNA while varying composition, page type, visual anchor, or emphasis.
- No outer border rule: generated slide images and thumbnail boards must not have black borders, dark strokes, or frame lines on the outer canvas edge. Internal grid lines, dividers, and module borders are allowed, but keep them inset from the image edge or let imagery/white space bleed naturally. Never create a full-page rectangular outline around the slide.
- Per-slide image rule: PPT pages must be generated and saved as separate single-slide image files, one image per slide. Do not request or deliver a multi-slide contact sheet, storyboard, PDF page, or collage as the final slide image output. Each final slide image must be independently usable as one full-bleed PPT page.
- Thumbnail-first option: for multi-page decks, prefer a two-pass visual workflow when style consistency matters: first generate one small "thumbnail board / contact sheet" that shows the whole deck as tiny slide thumbnails to lock visual rhythm, grid, palette, and page-to-page variation; then generate each approved slide as an individual full-size image using that thumbnail board as the visual continuity reference plus the page-specific prompt. The thumbnail board is a planning/reference artifact, not a final slide.
- Thumbnail grid rule: thumbnail board counts are flexible, but prefer stable grids with 4, 6, 9, or 16 slots. Choose the smallest preferred grid that can contain all planned slides, leaving any extra slot as a style/system/reference tile. Each thumbnail tile must use the same aspect ratio as the requested final slide output. For example, if the final deck is 16:9, every tiny slide in the thumbnail board should be composed as 16:9; if the user requests 3:4 vertical slides, every tiny slide in the thumbnail board should be composed as 3:4.
- Generation gate: before calling Image2 for a multi-page deck, always produce `outline.md` and `prompts.md` first, then ask the user to confirm or revise. `prompts.md` must include the selected style's full `Style Lock`.
- Final packaging gate: after Image2 generation, show or list the generated images and wait for the user to confirm that all images are approved. Only after that approval, assemble the image-only PPTX, collect all slide images plus `prompts.md`, `outline.md`, and style/reference docs, create a `.zip` package, and save it to the user's default save folder.

## Workflow

1. Classify the request:
   - Style extraction from images, screenshots, decks, webpages, or descriptions.
   - Style library operation: save, list, rename, update, or call a style.
   - Document-to-PPT or document-to-image creation.
   - Image-only PPT revision or visual redesign with a saved style.
   - Post-generation revision of one slide, one image, or one section.
2. If extracting a style, produce a concise style keyword profile and ask whether to save it as a Markdown file under `styles/`. Save style assets as style files, not as `SKILL.md`.
3. If applying a style, select the saved style:
   - Use explicit names first.
   - Treat "终端风格", "CodeBuddy 那种风格", and "科技杂志风格" as `terminal-tech-magazine`.
   - If multiple plausible styles exist, ask one short clarifying question.
   - Every saved style must provide its own `Style Lock`. Use that style-specific lock as the shared prefix for all Image2 prompts in the same deck.
   - Style isolation is mandatory: after selecting a style, ignore visual DNA from earlier user-provided references and previous deck attempts unless the user explicitly asks to combine styles.
4. If creating from a document path, read the document, extract the story arc, audience, page count suggestion, and visual moments before creating prompts or slides.
5. Before generating images or PPTs, confirm only missing production parameters that materially affect the result: page count, ratio, non-Chinese language requirements, text density, whether the user wants visible dates when the source calls for them, and whether the user wants image files only or an image-only PPTX package. Do not ask whether PPTX must be editable. If the user does not specify language, default to Chinese-first, especially Chinese slide titles. Do not include logos, brand wordmarks, repeated deck identity labels, or watermarks in Image2 prompts unless the user explicitly asks; if they ask, recommend post-production placement instead of model-rendered logos.
6. Do not add date/time by default. If the output must contain any date, time, "today", publication date, log date, report date, or timestamp because the user or source explicitly requires it, verify the date first using the source, conversation environment, local system date, or a reliable time source. Do not invent dates.
7. Select page types from `references/page-types.md` and map each slide to one page type.
8. Generate `outline.md` and `prompts.md` before any Image2 generation. `outline.md` contains the slide plan and page roles. `prompts.md` contains the full style-specific `Style Lock` plus every page prompt. For multi-page decks, `prompts.md` should also include a thumbnail-board prompt before the per-slide prompts unless the user asks to skip it. Page titles and visible text should be Chinese-first by default, with English retained only for names or terms that should not be translated. Stop and ask the user to confirm these two documents before generating images, unless the user explicitly says to skip confirmation.
9. For multi-page visual slide output, use this preferred two-pass generation sequence when feasible:
   - Pass A: generate one thumbnail board/contact sheet containing all planned slides as small thumbnails. The thumbnail count is flexible but should prioritize 4, 6, 9, or 16 slots. Use the smallest stable slot count that fits the slide count; for 8 slides, use 9 slots and make the extra tile a style/system/reference tile. The board should show only enough readable text to identify each slide and should prioritize layout, color, rhythm, image placement, grid structure, and overall visual consistency.
   - The thumbnail tile aspect ratio must match the final requested output ratio. Default final output is 16:9, so default thumbnail tiles are 16:9. If the user asks for 3:4, 4:5, 1:1, or another output ratio, compose every thumbnail tile in that same ratio before generating full-size slides.
   - Review the thumbnail board with the user when possible. If the user already said to proceed, use it directly as the visual continuity reference.
   - Pass B: generate every slide one by one as a separate full-size image file in the requested final output ratio. Each Image2 call or output unit must target exactly one final slide. Include the approved thumbnail board, the selected `Style Lock`, and that slide's page-specific prompt as guidance.
10. For visual slide output, create full-slide Image2 prompts and generate complete slide images only after the user confirms `outline.md` and `prompts.md`. The image itself may contain the final short slide text, but normal inner slides must stay sparse: one main title, one short subtitle or takeaway, and at most 2-3 short points. Each prompt must include the selected style's `Style Lock` so fonts, hierarchy, layout grid, ornaments, color ratios, footer behavior, border/container system, and avoid rules stay consistent across the deck. Separate cover and inner-slide behavior: the cover can carry a strong visual concept; inner slides should prioritize text and information hierarchy, using images and background as quiet support.
11. Final slide image output is always page-by-page: save and present each slide as its own image file using a stable ordered naming pattern such as `slide-01.png`, `slide-02.png`, etc. Do not rely on a single combined image as the deliverable for a PPT deck. If Image2 returns a combined image, treat it only as a draft/reference and regenerate or crop into approved single-page images before PPT assembly.
12. After images are generated, present the image set for review and ask the user to confirm whether all images are approved or which pages need revision. Do not create the final zip before this approval.
13. For revision requests, identify the target slide/image, preserve unchanged pages, and update only the affected asset. Repeat image review until the user confirms all images.
14. After the user confirms all images, assemble each generated image as a full-bleed slide in an image-only PPTX. The PPTX is a delivery container, not an editable deck.
15. Final package: collect all final images, `deck.pptx`, `prompts.md`, `outline.md`, `style-used.md` if present, the thumbnail board if used, and any revision log into a single `.zip`. Save the zip to the user's default save folder; on macOS, use `~/Downloads` unless the user specified another default folder or the environment clearly provides one.
16. After generating the prompt set, ask whether the user wants to save the style as a reusable template under `styles/`. If the user says yes, save the style file with its `Style Lock` so future decks can start by choosing this saved style instead of extracting from images again.
17. Run a final quality check: style consistency, readable Chinese, clean alignment, no overcrowding, unified border/container system, no black outer canvas border, no mixed historical style, no fake date, no model-rendered logo/wordmark drift, one-image-per-slide output, and output parameters respected.

## Invocation Examples

- "调用终端风格，把这篇文章做成 PPT"
- "用 CodeBuddy 那种风格，把这个文档做成 PPT"
- "提炼这张图的风格，保存成一个可复用风格"
- "列出现在可用的 PPT 风格"
- "用保存的 terminal-tech-magazine 风格生成 10 页 PPT"
- "把这份 Markdown 做成 8 页图片版 PPT，16:9，Image2"
- "先给我 outline 和 prompts，我确认后再生成图片"

## Language Rule

Default to Chinese-first decks and Chinese-first support documents. Titles are especially important: unless the user explicitly requests English or bilingual output, write slide titles, section headers, module labels, and conclusion lines in Chinese. Generated documents such as `outline.md`, `prompts.md`, `style-used.md`, `revision-log.md`, and final delivery notes should also be written mainly in Chinese. Preserve English only for proper nouns, product names, model names, code/API terms, brand names, quoted source terms, and compact labels where translation would reduce clarity, such as `Claude`, `Image2`, `API`, `Opus 4.6`, or XML tag names. For bilingual decks, Chinese should usually lead and English should be secondary.

## Date Rule

Dates and times are off by default. Do not add visible dates, times, timestamps, "today", export time, generated time, or current date unless the user explicitly asks for them, the source article explicitly requires them, or the slide topic itself is date-sensitive. A source file's export timestamp, filename date, filesystem modified time, or the local current date should not appear in the deck unless it is content-relevant.

When date/time is required, verify it before use. If the source provides the required date, use the source date. If the date is relative or operational and the environment date is available, verify with the conversation environment, local system date, or a reliable time source. Do not invent dates. The preferred Chinese date format is `YYYY年M月D日`; the preferred technical log format is `YYYY-MM-DD`.

## Replaceable Styles

The reusable style library lives in `styles/`. Add new styles as individual Markdown files with stable names such as:

- `terminal-tech-magazine.md`
- `warm-editorial-report.md`
- `minimal-founder-deck.md`

Do not overwrite this skill's workflow to change a visual style. Update or add a style file instead.

Each style file must include a `## Style Lock` section. This section is the cross-page control system for that style and should specify:

- Font family mood and title/body hierarchy.
- Language behavior: Chinese-first visible text and Chinese-first support documents, especially titles, with rules for retaining English terms and product names.
- Relative font scale rules, not exact pixels.
- Layout grid, safe margins, page rhythm, and repeated page structures.
- Reusable decorative elements and how often to use them.
- Style isolation rules: what must not be imported from previous references, previous tasks, or unrelated saved styles.
- Specific color palette with hex values for background, primary, secondary, accent, text, muted text, border, and shadow/glow colors, plus approximate color ratios.
- Border and container rules: one consistent stroke color, stroke thickness mood, corner radius style, card/panel material, divider shape, and line geometry reused across the deck.
- Footer/header metadata behavior.
- Logo/wordmark behavior: default to no generated logos or repeated brand marks; if needed, reserve a quiet empty area for a later fixed asset rather than asking Image2 to draw the logo.
- Text density limits: strict maximum visible text for cover pages and inner slides; normal inner slides should be low-density, not report-dense.
- Cover vs inner-slide rules: how expressive the cover can be, and how restrained inner pages must be.
- Image2 negative constraints.
