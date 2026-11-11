# Agent Workflow Guidelines

This file defines how coding agents should operate in this repository.

## What the project is

This project contains reusable templates of Markdown files used in agentic workflow setups for various types of projects.

**Files in `templates/` are templates for other repos.** Their rules do not apply to this repo. Do not fill their placeholders.

### Template directories

| Directory             | Target                                                             | Content                                                                                                                                         |
| --------------------- | ------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| `templates/common/`   | Root of a target repo                                              | Sections for the `AGENTS.md` / `CLAUDE.md` of a repo, and supporting files. Copy the files, then keep only the sections that apply to the repo. |
| `templates/global/`   | User-level agent configuration directory, for example `~/.claude/` | Rules that apply to the whole system, in every project.                                                                                         |
| `templates/obsidian/` | Folder in an Obsidian vault                                        | Note-structure rules.                                                                                                                           |

### Editing templates

- Put a rule in `templates/global/` only when it applies at system level, outside any single repo.
- In `templates/common/AGENTS.md`, put a project-agnostic rule above the `---` divider. Put a rule for one project type in its own `##` section after the divider. Start that section with a `Template note:` that says which projects keep it.
- Never use HTML comments (`<!-- -->`) for template markers or instructions. Renderers hide them. Write each one as a visible blockquote that starts with `> **Template note:**`, and end it with "Delete this note." An agent removes every `Template note:` line after it fills the template.

## User Interaction & Documentation Standards

**An agent must:**

- **Be concise.** Write in ASD-STE100 Simplified Technical English.
- **Never use emojis** in Markdown documentation.
- **Write well-structured documentation** with appropriate headings.
- **Never document** anything unless asked specifically to do so.

## Code Comments

**An agent must:**

- **Write self-documenting code.** Name variables and functions so a comment that restates them is unnecessary.
- **Never reference** chats, PRs, or change logs inside code files.
- **Use comments only when required**, for example:
  - `TODO`/`FIXME` markers tracking outstanding work
  - A short note where behavior is genuinely non-obvious and cannot be made clear by the code itself

## AI Policy

This repo has an `AI_POLICY.md` in `.github/`. When helping a contributor open a PR or issue, point them to it. Key points: contributor owns every line, slop gets closed without discussion.

## Agent skills

### Issue tracker

Issues are tracked in GitHub Issues for `scottishwidow/agentic-workflow-templates`, using the `gh` CLI. See `docs/agents/issue-tracker.md`.

### Triage labels

The repo uses the five default triage labels: `needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`. See `docs/agents/triage-labels.md`.

### Domain docs

Single-context: one `GLOSSARY.md` and one `docs/adr/` at the repo root. See `docs/agents/domain.md`.
