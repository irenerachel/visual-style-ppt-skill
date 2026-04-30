# impact-grid-editorial

## Style Summary

高端咨询报告、可持续金融、社会影响力机构网页和编辑型长报告混合出来的图片版 PPT 风格。核心气质是：理性、克制、昂贵、机构化、带一点纪录片感。它适合 AI 方法论、商业战略、ESG、金融科技、研究摘要、创始人/管理层简报，以及需要显得可靠而不是花哨的内容。

关键词：`consulting editorial`、`impact report`、`strict black-line grid`、`warm white`、`deep teal`、`documentary photography`、`oversized condensed title`、`thin divider`、`modular report layout`。

## When To Use

- 需要“高级咨询公司 / 机构报告 / 研究简报”质感的 PPT。
- 内容偏方法论、行业观察、技术策略、工作系统、模型框架、政策/金融/可持续主题。
- 用户给了类似 BCG、Mastercard、impact report、气候金融、机构网站截图作为参考。
- 需要跨页统一视觉，而不是每页都很炫的视觉实验。

## Style Lock

Use a high-end consulting editorial style inspired by sustainability finance reports and premium institutional web design. Build every slide on a strict black-line grid with generous warm-white space, thin dividers, hard-edged image blocks, and restrained report-like typography.

Language behavior: Chinese-first by default. Use Chinese for slide titles, section headers, module labels, captions, and explanatory copy. Preserve product names, model names, brand names, code/API terms, XML/JSON labels, and technical proper nouns in English when clearer. English may appear as tiny metadata, vertical labels, or compact institutional captions.

Typography: use oversized condensed sans-serif titles, thin-weight compact Chinese, and small precise editorial body text. Cover pages may use very large multi-line titles. Inner slides should keep one dominant title, one short takeaway, and at most 2-3 short content blocks unless the page is intentionally a table or report extract. Avoid decorative display fonts, playful type, handwritten type, and generic startup pitch typography.

Layout system: use visible grid logic. Prefer thin black horizontal and vertical rules, modular blocks, split screens, hard rectangular image crops, catalog-like lists, compact tables, big-number metric layouts, plus-sign list markers, and tiny footnotes aligned to the grid. Use generous negative space. Variation comes from page type and image placement, not from changing the whole visual language each slide.

Canvas edge rule: do not place black borders, dark strokes, or frame lines on the outer canvas edge. Internal grid lines and dividers are allowed, but they should be inset from the edge or interrupted by image/white-space modules. The slide must never look like it has a full-page rectangular black outline.

Slide header system: use this only on normal inner/content slides. Do not use it on cover pages, contents/目录 pages, divider pages, or closing/thank-you pages. The header number is a content-section number, not the absolute slide/page number. Cover, contents, divider, and thank-you pages do not consume a header number. The first normal inner/content slide should start at `01`, or use `PART 1` if that better fits the deck. Format for numbered headers: two-digit content-section number, two spaces, short slide title, for example `01  先选对模型`. Keep this header small, black, horizontally aligned, and placed at the same top margin on every applicable slide. Do not vary it into a large title, vertical label, tag, pill, or decorative caption.

Aspect ratio behavior: default final output is 16:9. If the user requests another output ratio such as 3:4, 4:5, or 1:1, compose both thumbnail-board tiles and final slide images in that requested ratio. Never let thumbnail tiles use a different ratio from the final output.

Thumbnail-board behavior: for multi-page decks, prefer a two-pass workflow. First generate a thumbnail board/contact sheet to lock deck rhythm. Thumbnail slot counts are flexible, but prefer 4, 6, 9, or 16 slots. Choose the smallest preferred grid that fits the planned slide count; extra slots can become style/system/reference tiles. Then generate each final slide one by one as a separate full-size image using the thumbnail board as continuity reference.

Color palette:
- Dominant background: warm white `#F4F2EF`
- Primary text and grid lines: near-black `#111111`
- Deep charcoal: `#2B2F2E`
- Dark accent panel: deep teal `#183B3D`
- Light divider: `#D8D6D0`
- Rare accent green: muted green `#8FAE9A`
- Rare accent gold: muted gold `#C7A46A`
- Approximate ratio: 70% warm white, 20% photographic imagery, 8% black line/text, 2% accent.

Photography: documentary, premium, low-saturation, quiet, and real-world. Use cropped images of work desks, institutional interiors, conference scenes, paper notes, code-like interfaces, portraits, laptops, document stacks, glass offices, landscapes, or abstract process imagery. Images should be integrated as rectangular grid modules. Avoid stocky smiling business photos, colorful SaaS dashboards, glossy device mockups, cartoon people, neon cyberpunk, or generic AI fantasy imagery.

Border and container rules: use hard-edged rectangular modules, thin black or gray strokes, straight dividers, and flat report surfaces inside the page system. Keep strokes away from the exact canvas edge. Avoid rounded cards, pill buttons, thick outlines, drop shadows, glassmorphism, soft pastel panels, floating blobs, decorative gradients, and any black frame around the full image.

Footer/header metadata: small, precise, and aligned to the grid. Footers can include source, section number, page number, or project label. Do not include dates, times, timestamps, export time, generated time, or current date by default. Include time/date only when the source article explicitly requires it, the user explicitly asks for it, or the slide topic itself is date-sensitive. Keep metadata tiny and restrained; it should feel like a report artifact, not a branding banner.

Cover vs inner slides: the cover may be dramatic, with oversized title over a dark cropped documentary image and a warm-white lower metadata panel. Inner pages should be calmer, more information-first, and easier to scan. Use dark teal sparingly for emphasis panels, headers, or a single focal block.

Text density limits: normal inner slides should be low-density. Use concise visible text; do not paste long source paragraphs. Tables and report extracts are allowed only when the page type needs them, and even then use compact labels plus placeholder marks rather than fake unreadable paragraphs.

Image2 negative constraints: no black border around the outer canvas, no full-slide rectangular outline, no edge-to-edge black frame, no colorful SaaS dashboard style, no cartoon illustration, no neon cyberpunk look, no 3D blobs, no thick shadows, no rounded pastel cards, no generic startup pitch-deck gradients, no decorative orb backgrounds, no busy icon systems, no dense unreadable paragraphs, no mixed historical visual styles, no unrelated climate/finance imagery unless used as a clear abstract metaphor.

## Page Type Preferences

- Cover: giant multi-line statement + dark documentary image + warm-white metadata block, no numbered top header.
- Contents: thin-line grid, plus-sign chapter list, narrow photographic strip, no numbered top header.
- Comparison: two or three columns separated by thin black lines.
- Framework: modular grid with one deep teal system block.
- Workflow: horizontal line logic with small document-like nodes.
- Contrast: pale left side versus structured deep-teal emphasized right side.
- Checklist/table: compact editorial table with tiny labels and black dividers.
- Conclusion: large decisive statement + narrow action list + small documentary strip.
- Thank-you closing: minimal closing page with large `谢谢` or `THANK YOU`, contact/action line if needed, documentary strip or quiet institutional image, no numbered top header.

## Reuse Prompt Prefix

Apply the `impact-grid-editorial` Style Lock. Create an Image 2-only full-slide image with a high-end consulting editorial report style: strict black-line grid, warm-white institutional background, deep teal accents, documentary low-saturation photography, oversized condensed typography, hard rectangular modules, tiny report metadata, and restrained information density. Chinese-first visible text. Keep every slide consistent with the same grid, line weight, palette, footer behavior, and rectangular container system. Do not add any black border or full-page outline on the outer canvas edge.
