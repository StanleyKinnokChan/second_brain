---
title: CLAUDE
tags:
---

# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Context

This is the `content/` directory of a [Quartz](https://quartz.jzhao.xyz) static site — Stanley Chan's personal digital garden / knowledge base. The Quartz project root is one level up at `../` (i.e., `C:\Users\Stanley\SynologyDrive\Tech\quartz`).

## Commands (run from the Quartz project root `../`)

```bash
# Local dev server
npx quartz build --serve

# Sync content to GitHub Pages
npx quartz sync

# Manual push
git add . && git commit -m "updated" && git push
```

## Note Format

All notes use Obsidian Flavored Markdown with YAML frontmatter:

```markdown
---
title: Note Title
tags:
  - some-tag
---

Content here...
```

- `title` and `tags` are the standard frontmatter fields
- Notes with `draft: true` in frontmatter are excluded from the published site
- Folders named `private`, `templates`, or `.obsidian` are ignored by Quartz

## Content Structure

Notes are organized by technology/topic under `⚙️ Stack/`, plus:
- `AI/`, `Data Engineering/` — domain-specific notes
- `Markdown Usage/` — reference for supported syntax
- `Template/Page Template.md` — blank template for new notes
- `Resource/` — badges, useful websites
- `Personal/` — personal notes (not published if kept private)

## Obsidian Markdown Features Supported

- Callouts: `>[!info]`, `>[!tip]`, `>[!warning]`, `>[!success]`, `>[!example]`, `>[!quote]`, `>[!faq]`
- Foldable callouts: append `-` (collapsed) or `+` (open) after type, e.g. `>[!faq]-`
- Wikilinks: `[[Note Name]]` (resolved by shortest path match)
- LaTeX: rendered via KaTeX
- Syntax highlighting via Shikiji (github-light/github-dark themes)
- Checkboxes, strikethrough (`~~text~~`), footnotes (`[^1]`)
- Obsidian comments: `%%hidden text%%`
