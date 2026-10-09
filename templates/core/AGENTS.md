# Agent Workflow Guidelines

This file defines how coding agents should operate in this repository.

<!-- Short project description -->

## What the project is

<!-- Short project description -->

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

## Security

Before adding, removing, or changing a dependency, read `SECURITY.md` and obey its supply-chain rules.

---

<!-- BEGIN: Terraform projects -->

## Terraform

**An agent must:**

- **Never allow** `.terraform/` or `.terraform.lock.hcl` inside submodules. These files are permitted only at the root module level.
- **Never apply Terraform.** Only CI or a human can apply Terraform.

<!-- END: Terraform projects -->
