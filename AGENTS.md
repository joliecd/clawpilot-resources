# AGENTS.md — Instructions for AI Assistants

This file tells AI assistants (GitHub Copilot, Clawpilot, CoWork, or any LLM agent) how to read, navigate, and contribute to this repository.

---

## What This Repo Is

A team knowledge base for Clawpilot. It contains:
- **Use cases** — proven tasks Clawpilot can help with, each with ready-to-use prompts and examples
- **Wish list** — desired use cases that don't have a solution yet, open for anyone to tackle
- **Tips & tricks** — standalone guidance not tied to a specific use case

The repo also serves as a **pipeline for future Clawpilot skill creation** — well-validated use cases will be converted into first-class skills agentically.

---

## Directory Structure

```
/
├── README.md                        Repo overview and vision
├── CONTRIBUTING.md                  Human contribution guide
├── AGENTS.md                        This file — AI assistant instructions
├── use-cases/
│   ├── README.md                    Index of all use cases
│   ├── _template/                   Template — copy to create a new use case
│   │   ├── README.md
│   │   ├── prompts/
│   │   │   └── example.md
│   │   ├── examples/
│   │   │   └── sample-output.md
│   │   └── skill.md
│   └── [use-case-name]/             One folder per use case (kebab-case)
│       ├── README.md                What it does, when to use, tips
│       ├── prompts/
│       │   └── [prompt-name].md     One file per prompt variant
│       ├── examples/
│       │   └── [example-name].md    Sample inputs and outputs
│       └── skill.md                 Skill pipeline metadata
├── wish-list/
│   ├── README.md                    Index and instructions
│   ├── _template.md                 Template for new wish list items
│   └── [wish-name].md               One file per desired use case
└── tips-and-tricks/
    ├── README.md                    Index
    └── [tip-name].md                One file per tip
```

---

## How to Find Things

- **Looking for a use case?** → Browse `use-cases/`. Each folder is named for the task (e.g., `summarize-meeting`, `draft-status-update`). Read the `README.md` first, then pick a prompt from `prompts/`.
- **Looking for a prompt?** → Navigate to the relevant use case folder, then `prompts/`. Each `.md` file is a self-contained prompt with instructions.
- **Looking for examples?** → `examples/` inside any use case folder.
- **Looking for something that doesn't exist yet?** → Check `wish-list/` to see if it's been requested.
- **Looking for general tips?** → `tips-and-tricks/`.

---

## File Schemas

### `use-cases/[name]/README.md`
```markdown
# Use Case: [Name]
> One-line description

## Problem
## When to Use This
## How to Use
## Available Prompts    (table linking to prompts/ files)
## Tips & Gotchas
```

### `use-cases/[name]/prompts/[name].md`
```markdown
# Prompt: [Name]
**Best for:** [scenario]

## Prompt
[the actual prompt text, with [BRACKETED] placeholders]

## Notes
```

### `use-cases/[name]/examples/[name].md`
```markdown
# Example Output
**Prompt used:** [link]
**Context:** [description]

## Input
## Output
## Notes
```

### `use-cases/[name]/skill.md` (frontmatter)
```yaml
---
status: draft         # draft | validated | ready-for-skill | skill-created
skill-name:           # short identifier for the skill
owner:                # who owns this use case
tags: []              # topic tags
created:              # YYYY-MM-DD
last-updated:         # YYYY-MM-DD
notes:                # free text
---
```

### `wish-list/[name].md` (frontmatter)
```yaml
---
status: open          # open | in-progress | solved
requested-by:
date:                 # YYYY-MM-DD
tags: []
---
```

---

## Skill Status Lifecycle

```
draft → validated → ready-for-skill → skill-created
```

| Status | Meaning |
|---|---|
| `draft` | Newly added, not yet tested by the team |
| `validated` | Tested by multiple people, works reliably |
| `ready-for-skill` | Ready for agentic skill generation |
| `skill-created` | A Clawpilot skill has been generated from this use case |

---

## How to Contribute (AI Instructions)

### Add a new use case
1. Copy the entire `use-cases/_template/` folder to `use-cases/[new-name]/` (kebab-case)
2. Fill in `README.md` with problem, when to use, how to use, tips
3. Add at least one prompt to `prompts/` following the prompt schema
4. Set `skill.md` frontmatter: `status: draft`, `owner: [person]`, `created: [date]`
5. Update `use-cases/README.md` to list the new use case

### Add a prompt to an existing use case
1. Create a new `.md` file in `use-cases/[name]/prompts/`
2. Follow the prompt schema above
3. Update the `Available Prompts` table in the use case `README.md`

### Add a wish list item
1. Copy `wish-list/_template.md` to `wish-list/[descriptive-name].md`
2. Fill in problem, desired outcome, and context
3. Update the table in `wish-list/README.md`

### Convert a wish list item to a use case
1. Create the use case folder following the steps above
2. Update the wish list item's `status` to `solved` and link to the new use case
3. Update `wish-list/README.md`

---

## Naming Conventions

- Folder and file names: `kebab-case` (e.g., `summarize-meeting`, `basic-prompt.md`)
- Use descriptive names — prefer `draft-executive-summary.md` over `prompt2.md`
- Dates in frontmatter: `YYYY-MM-DD`

---

## What to Avoid

- Do not duplicate prompts across use cases — link to a shared prompt if needed
- Do not create top-level folders outside the defined structure without updating this file
- Do not mark a use case `validated` or `ready-for-skill` without evidence of team testing
