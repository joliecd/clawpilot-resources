# GitHub Copilot Instructions

This repository is a team knowledge base for Clawpilot. It contains use cases, prompts, tips, and a wish list of desired capabilities.

## Repo Purpose

Help the team get more out of Clawpilot by sharing proven prompts and use cases. Well-validated use cases are candidates for future Clawpilot skill creation.

## Key Conventions

- Use cases live in `use-cases/[kebab-case-name]/` — each has a `README.md`, `prompts/`, `examples/`, and `skill.md`
- Prompts use `[BRACKETED]` placeholders for user-specific values
- `skill.md` frontmatter tracks status: `draft → validated → ready-for-skill → skill-created`
- Wish list items in `wish-list/` describe desired use cases without solutions yet
- All folder and file names are `kebab-case`

## When Helping with This Repo

- To find a use case: look in `use-cases/` folders, read the `README.md`
- To find a prompt: look in `use-cases/[name]/prompts/`
- To add a use case: copy `use-cases/_template/` and follow `AGENTS.md`
- To understand the full structure and schemas: read `AGENTS.md` — it is the authoritative guide for AI assistants working in this repo
- When suggesting new content, follow the file schemas defined in `AGENTS.md`
- Prefer editing existing use cases over creating duplicates

## Skill Pipeline Awareness

Use cases with `status: ready-for-skill` in `skill.md` are intended for agentic Clawpilot skill generation. When working with these, preserve the frontmatter structure exactly — it will be consumed programmatically in the future.
