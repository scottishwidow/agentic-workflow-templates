# Learning notes — note structure

Obsidian notes on learning material: courses, certifications, talks, webinars, articles, and labs. This file works the same in any folder. Nothing in it is filled in per topic. Instead, you work out each collection's conventions from the folder itself, using the rules below. Everything written in `<angle brackets>` is a slot you fill per note; never leave one in a note.

When asked to "refine", "apply the structure", or "structure" a note or folder, rewrite each note to match the template and rules below. Before you start, work out the collection's conventions, read its style references, and skim its other notes for overlapping topics.

## Working out the collection's conventions

A **collection** is the folder this file sits in. If this file sits above several topic folders, each immediate subfolder is its own collection.

Existing notes win. When the notes already structured in a collection consistently use a convention (a tag, a field name, a callout title, a file-name pattern), keep using it, even where it differs from the defaults here. Use the defaults only where the collection has no convention yet.

| Setting | How to work it out |
|---|---|
| **Subject** | The collection's folder name and the notes in it. |
| **Layout** | `sequential` if note files or subfolders carry numbers (`01 - `, `1. `, `1 - `), otherwise `flat`. Sequential notes follow course order. Flat notes are independent, and none is a hub for the others. |
| **File naming** | The pattern most existing files use. With no files yet: `NN - Title.md` for sequential, `<Title>.md` for flat. |
| **Base tag** | The tag every structured note already carries. Otherwise a short kebab-case form of the subject: `cissp`, `pqc`, `htb-cjca`. |
| **Module tag and field** | Only in sequential collections with numbered subfolders. Take the word the folders use (`Domain`, `Module`, `Section`; default `module`) and add the tag `<word>-N` and the field `<word>: "<Word> N — <Official Name>"`. Use official names where the subject has them. |
| **Note type** | Per note, from what it records: `course-notes`, `talk-notes` (talks, webinars, workshops), `reading-notes` (articles, books, papers), `lab-notes` (hands-on exercises), or `cheat-sheet`. |
| **Tip callout title** | Per note type: `Exam angle` or `Memory hook` for course notes toward an exam, `Takeaway` for talks, reading, and cheat sheets, `Command to remember` for labs. |
| **Authoritative sources** | The bodies that publish the subject's standards and references (e.g. csrc.nist.gov, rfc-editor.org, iso.org, the vendor's own documentation). Prefer primary sources over blogs and summaries. |
| **Index note** | An existing note tagged `moc`, or named `Notes.md`, `Index.md`, or `<Collection> Index.md`. Otherwise there is none. |
| **Style references** | The one or two existing notes that already follow these rules most closely. If none does, the template below is the only reference. |

## File layout

- Name new files following the collection's pattern. In sequential collections, zero-pad numbers (`01`, `02`, …) unless the collection already uses unpadded numbers.
- Don't rename existing files; wikilinks elsewhere depend on them. If a name breaks the pattern, tell the user rather than fixing it.
- Wikilinks resolve by file name across the whole vault. Before adding a note, check that its name is unique in the vault.

## Note template

```markdown
---
tags:
  - <base-tag>
  - <module-tag>         # sequential collections with numbered subfolders only
  - <note-type>
  - <topic-tag>          # 1–4 kebab-case topic tags
<module-field>: "<Word> N — <Official Name>"   # same condition as the module tag
source: "<url>"          # omit if none
author: "<Name — Role, Org>"   # speaker, author, or instructor; omit if unknown
event: "<Event, course, or publication, year>"   # omit if none
related: "[[<Closely related note>]]"   # omit if none
---

# <Title, without any number prefix>

> One or two sentences on what the note covers and why it matters.
>
> Source: [<Author — Title (Event)>](url) · Related: [[<Other Note>|Other Note]] · [[<Another>#Section|Section]]

## <Section>

### <Subsection>
```

- Omit any frontmatter field you don't know, and drop the `Source:` or `Related:` part of the summary if it would be empty.
- Never invent URLs, dates, names, or document numbers. Leave them out and tell the user what's missing.

## Formatting rules

- Use `##` and `###` headings for sections. Never use bold lines as fake headings, and don't use `---` dividers in the body.
- Turn term/definition lists, comparisons, levels, tiers, phases, timelines, and lists of standards, algorithms, or tools into **tables** with bold first-column keys.
- Use bullet lists for loose points and numbered lists for ordered processes. Indent nested lists with 4 spaces.
- Show a short sequence inline in bold with arrows: `**Discover → Assess → Prioritize → Migrate**`. Use Mermaid (`flowchart LR`, `timeline`, `sequenceDiagram`) for longer pipelines, timelines, and message exchanges.
- Put commands, code, config, and payloads in fenced code blocks with a language tag (`bash`, `powershell`, `python`, `text`). Put a one-line explanation before each block, not inside it as a comment.
- Link standards and references to their authoritative source in the form `[<ID> — <Full Title>](url)`. Mark drafts *(draft)* and withdrawn documents *(withdrawn)*. Check that a link resolves before adding it.
- Collapse long, low-value lists (contributors, vendor lists, raw output) into a folded callout: `> [!note]- Title (N)`.
- Use callouts sparingly, 1–3 per note:
    - `> [!tip] <tip callout title>` for the practical point to act on or remember
    - `> [!note]` for clarifications and contrasts (X vs. Y)
    - `> [!warning]` for blockers, hard deadlines, and mistakes that cause failure or liability
    - `> [!abstract]` for a core principle or formula
    - `> [!question]` for open questions the source raised or left unanswered
- Cross-link related notes inline where topics overlap, in either direction and across collections, in the form `[[<File name>#<Heading>|<Display text>]]`. Check that the target heading exists before linking to it.
- Write in plain, concise US English with serial commas. Fix typos.

## Content rules

- Keep all of the user's content. Restructure and rephrase it, but don't drop facts, opinions, or examples.
- Keep opinions separate from facts. Put a speaker's or author's views and the user's own thoughts in a clearly labeled section ("Discussion", "My thoughts") apart from material from the official source.
- Correct clear factual errors, such as a wrong document number, status, date, or misquoted definition, and tell the user what you changed. When a phrase is ambiguous, pick the most likely reading and tell the user.
- Keep facts consistent across notes. If two notes conflict, flag it rather than silently picking one.
- Keep additions small: a callout, a cross-link, a reference link. Don't add new sections of material.
- Don't edit other notes unasked, except the index note. If the note you're working on would improve another (a missing fact, a useful back-link), suggest the change.

## Index

If the collection has an index note, update it whenever you add or structure a note, keeping its existing layout. If it has none, don't create one unless the user asks; then create `<Collection> Index.md` in this format:

```markdown
---
tags:
  - <base-tag>
  - moc
---

# <Collection> — Index

> One sentence on what the collection covers and how it's organized.

## <Module>        <!-- sequential only; a flat index has no sections -->

- **[[<File name>|<Title>]]** — key topics, comma-separated.
```

- A sequential index has one `##` heading per module, in course order. List modules without notes at the end, marked *(not started)*.
- A flat index is a single bullet list sorted by title. It lists notes; it doesn't rank them or nest them under one another.

## Final report

After restructuring, tell the user briefly:

- the conventions you worked out, the first time you work in a collection during a session
- factual corrections made and ambiguous readings chosen
- missing details (URLs, names, dates)
- conflicts with other notes, and suggested edits to other notes

