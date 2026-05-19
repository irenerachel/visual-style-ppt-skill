---
description: Slash-entry shim for the visual-style-ppt skill. Creates Image 2 slide images and image-only PPTX decks.
---

# Visual Style PPT Command

Use this when invoking `/visual-style-ppt`.

## Canonical Surface

Apply the `visual-style-ppt` skill.

## Arguments

`$ARGUMENTS`

## Delegation

Use `$visual-style-ppt` to turn the provided document, outline, notes, or visual reference into Image 2-generated slide images and, when requested, an image-only PPTX deck.

Follow the skill's core constraints:

- Use Image 2 for final slide images.
- Do not use HTML, CSS screenshots, SVG mockups, canvas renders, or local browser rendering for final or intermediate image output.
- Keep PPTX as an image container unless the user explicitly asks for editable PPT content.
- Use Chinese-first slide text unless the user asks for another language.
