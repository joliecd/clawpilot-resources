# Contributing to Clawpilot Resources

Thanks for contributing! Here's how to add to each part of the repo.

---

## Adding a Use Case

1. Copy the `use-cases/_template/` folder and rename it (use lowercase, hyphens: `summarize-meeting`)
2. Fill in `README.md` — describe the problem, when to use it, and any tips
3. Add at least one prompt to `prompts/` — name it descriptively (e.g., `basic.md`, `with-context.md`)
4. Optionally add a sample output to `examples/`
5. Update `skill.md` with your name as owner and set status to `draft`
6. Open a PR — keep the title clear: `Add use case: summarize-meeting`

### Skill Status Lifecycle

As a use case matures, update the `status` field in `skill.md`:

| Status | Meaning |
|---|---|
| `draft` | New, not yet tested by the team |
| `validated` | Team has used it and it works well |
| `ready-for-skill` | Ready for agentic skill creation |
| `skill-created` | A Clawpilot skill has been generated from this |

---

## Adding a Prompt to an Existing Use Case

1. Add a new `.md` file to the use case's `prompts/` folder
2. Follow the prompt template format (see `use-cases/_template/prompts/example.md`)
3. Open a PR

---

## Adding a Wish List Item

Got a use case you *wish* existed but don't have a solution for yet?

1. Copy `wish-list/_template.md` and rename it (e.g., `auto-draft-followup-email.md`)
2. Describe the problem clearly — what would you want Clawpilot to do?
3. Describe what a good solution would look like
4. Open a PR

When someone builds a solution, they'll convert the wish list item into a full use case and link back.

---

## Adding a Tip or Trick

1. Add a `.md` file to `tips-and-tricks/`
2. Keep it short and actionable
3. Open a PR

---

## PR Guidelines

- Keep PRs focused — one use case or change per PR
- Use clear titles: `Add use case: X`, `Improve prompt: Y`, `Add wish list: Z`
- No need for perfect polish on first submission — iteration is welcome
