# Clawpilot Resources

A community-maintained library of Clawpilot use cases, prompts, tips, and tricks — built by the team, for the team.

---

## 🎯 Vision

This repo is the team's living knowledge base for getting the most out of Clawpilot. It serves three purposes today, with a bigger ambition ahead:

1. **Share what works** — Capture proven use cases and prompts so the whole team benefits
2. **Surface what's missing** — Document desired use cases that don't have solutions yet, so others can pick them up and build
3. **Pipeline to skills** — Validated use cases here are candidates to become first-class Clawpilot skills, created agentically from the content in this repo

---

## 📁 How This Repo Is Organized

```
use-cases/          Proven use cases with prompts and examples
wish-list/          Desired use cases with no solution yet — open for contributors
tips-and-tricks/    Standalone tips not tied to a specific use case
```

### Use Cases
Each use case lives in its own folder and contains:
- `README.md` — what it does, when to use it, tips
- `prompts/` — one or more prompt files, ready to copy and use
- `examples/` — sample outputs so you know what to expect
- `skill.md` — metadata for future skill generation

### Wish List
Use cases the team *wants* but that don't have a solution yet. If you figure one out, convert it into a full use case. See [`wish-list/README.md`](wish-list/README.md).

### Tips & Tricks
Short, standalone tips that don't belong to a single use case — formatting tricks, prompt patterns, things that surprised you.

---

## 🚀 How to Contribute

There are four ways to contribute:

| Contribution | What to do |
|---|---|
| Add a new use case | Copy `use-cases/_template/`, fill it in, open a PR |
| Improve an existing use case | Edit the prompts or README, open a PR |
| Add a wish list item | Copy `wish-list/_template.md`, describe the problem, open a PR |
| Add a tip or trick | Add a `.md` file to `tips-and-tricks/`, open a PR |

See [CONTRIBUTING.md](CONTRIBUTING.md) for full guidance.

---

## 🔮 Future: Agentic Skill Creation

The long-term vision is for this repo to serve as a **skill factory**. When a use case is well-documented, tested, and marked `ready-for-skill` in its `skill.md`, an agent will:

1. Read the use case README, prompts, and examples
2. Generate the Clawpilot skill scaffolding
3. Open a PR in the skills repo for human review

This means: **write good markdown today → get a skill tomorrow.**

The `skill.md` frontmatter in each use case is designed with this pipeline in mind, even if it's lightweight for now.

---

## 🤖 Working with AI Assistants

This repo is designed to be navigable by AI assistants (GitHub Copilot, Clawpilot, CoWork, etc.). See [AGENTS.md](AGENTS.md) for instructions on how an LLM should read and work with this repo.

---

## 📬 Questions?

Open an issue or reach out to the team.
