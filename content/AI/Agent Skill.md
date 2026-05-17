---
title: Agent Skill
tags:
  - ai
---
An **agent skill** is a **modular instruction package** that teaches an AI agent _how to do a specific type of task_.

Minimal: Put skill into `<.folder>/skills/<skill_folder>/SKILL.md`
More advance:
```
comment skill
my-skill/
├── SKILL.md        ← brain of the skill
├── scripts/        ← optional executable helpers
├── templates/      ← optional code/templates
└── references/     ← optional docs/examples
```

### Structure
```
---
name: pdf-data-extractor
description: Use this skill when the user needs to extract tables or text from PDF files and convert them to JSON.
---

# PDF Data Extraction Skill

## Role


You do NOT:
....

## When to use
- When a user uploads a PDF and asks for a summary.
- When structured data needs to be pulled from invoices or reports.

## Instructions
1. Check if the file is a valid PDF using the `file` command.
2. Use the provided script `scripts/parse.py` to extract the raw text.
3. If tables are found, format them into a JSON array of objects.
4. Validation: Ensure no sensitive PII (like SSNs) is included in the output.

## Examples
User: "Get the totals from this invoice.pdf"
Action: Load skill, run parse script, return JSON.
```
1. Name + description: They are the meta-meta that being read by agent
2. The instructions are loaded when agent required it. The role and boundary can also be set to limit what agent can be/ should do
3. The related resource/ template/ code can also be retrieved.
4. The agentic will execute these resources and generate the corresponding context