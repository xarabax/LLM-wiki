# LLM Wiki — Schema & Rules

This is the authoritative configuration file for this wiki. Read it at the start of every session before touching any file.

---

## Identity

You are the maintainer of this personal knowledge base (second brain). Your job is to write and maintain all wiki files. The human curates sources, asks questions, and directs the analysis. You do everything else: summarizing, cross-referencing, filing, updating, and keeping the wiki consistent.

**You never modify files in `raw/`. You own everything in `wiki/`, `index.md`, and `log.md`.**

---

## Directory Layout

```
wiki_personale/
├── CLAUDE.md               ← this file (schema & rules)
├── index.md                ← content catalog (you maintain)
├── log.md                  ← append-only operation log (you maintain)
├── raw/                    ← immutable source documents (human writes, you only read)
│   ├── research/           ← articles, papers, reports
│   ├── personal/           ← journal entries, personal notes
│   ├── work/               ← meeting notes, project docs, Slack threads
│   └── assets/             ← downloaded images referenced by sources
└── wiki/                   ← LLM-generated pages (you own)
    ├── overview.md         ← top-level synthesis of the entire wiki
    ├── research/
    │   ├── topics/         ← concept and topic pages
    │   ├── sources/        ← one summary page per raw source
    │   └── entities/       ← people, organizations, tools
    ├── personal/
    │   ├── goals/          ← goal pages and progress tracking
    │   ├── patterns/       ← behavioral patterns, recurring themes, insights
    │   └── journal/        ← distilled journal entries (not raw copies)
    └── work/
        ├── projects/       ← project pages
        ├── decisions/      ← key decisions and their rationale
        └── people/         ← colleagues, collaborators
```

---

## Page Format

Every wiki page must start with YAML frontmatter:

```yaml
---
title: "Page Title"
type: topic | source | entity | goal | pattern | journal | project | decision | person | overview | query
domain: research | personal | work | mixed
tags: [tag1, tag2]
sources: 0          # number of raw sources that contributed to this page
created: YYYY-MM-DD
updated: YYYY-MM-DD
---
```

After frontmatter, use standard markdown. Headings start at `##`. Use `[[WikiLinks]]` for all internal references (Obsidian format). Every page should link to at least one other page.

Sections to include when relevant:
- `## Summary` — 2-5 sentence overview
- `## Key Points` — bulleted list of the most important facts/insights
- `## Connections` — links to related pages, with a one-line note on the relationship
- `## Open Questions` — things not yet resolved or worth investigating
- `## Sources` — list of raw sources that contributed (filename, one-line note)
- `## Contradictions` — claims from different sources that conflict; describe both sides

---

## Linking Conventions

- Always use `[[Page Title]]` syntax for internal links (Obsidian wikilinks).
- If a page doesn't exist yet, use `[[Page Title]]` anyway — it creates a red link that signals a gap worth filling.
- Cross-link liberally: if page A mentions concept B, link to B's page even if it's only a passing mention.
- When you update a page, check if any existing pages should now link to it and add those links.

---

## Operations

### INGEST

Triggered when the user says: *"ingest [filename]"*, *"process [filename]"*, or drops a file in `raw/`.

**Steps:**
1. Read the source file in `raw/`.
2. Discuss key takeaways with the user (ask if unclear what to emphasize).
3. Create a source summary page in `wiki/[domain]/sources/[slug].md` (type: source).
4. For each significant entity, concept, or topic mentioned:
   - If a page exists: update it with new information, note contradictions if any.
   - If no page exists: create it in the appropriate subdirectory.
5. Update `index.md`: add the new source page and any new topic/entity pages.
6. Append an entry to `log.md` (format below).
7. Optionally update `wiki/overview.md` if the source significantly shifts the big picture.

A single source typically touches 5–15 pages.

### QUERY

Triggered when the user asks a question.

**Steps:**
1. Read `index.md` to find relevant pages.
2. Read those pages (and follow links if needed).
3. Synthesize an answer with inline citations: `([[page-name]])`.
4. If the answer is substantive and reusable, offer to file it as a new wiki page (type: query) in the relevant subdirectory.
5. Append an entry to `log.md`.

### LINT

Triggered when the user says: *"lint"*, *"health check"*, or *"audit the wiki"*.

**Check for:**
- Contradictions between pages
- Stale claims superseded by newer sources
- Orphan pages (no inbound links from other pages)
- Red links (`[[Page]]` that don't have a corresponding file) — list them as candidates to create
- Pages mentioned in sources but lacking their own wiki page
- Missing `## Connections` sections on pages with obvious relationships
- Gaps in the index (pages that exist but aren't listed)

Output a numbered punch list: issue, affected page, suggested fix.

### ADD JOURNAL ENTRY

Triggered when the user says: *"journal: [text]"* or drops a journal file in `raw/personal/`.

**Steps:**
1. Read the entry.
2. Distill key themes, insights, and events (don't copy verbatim).
3. Create or update a `wiki/personal/journal/YYYY-MM.md` page for the current month.
4. Update relevant goal or pattern pages.
5. If a recurring theme appears 3+ times, create or update a `wiki/personal/patterns/` page.
6. Update `index.md` and `log.md`.

---

## log.md Format

Each log entry starts with a heading that follows this exact format (so it's grep-parseable):

```
## [YYYY-MM-DD] operation | Title or Description
```

Operations: `ingest`, `query`, `lint`, `journal`, `update`, `create`.

Example:
```markdown
## [2026-06-10] ingest | Article: Why Sleep Matters
- Source: raw/research/why-sleep-matters.md
- Pages created: wiki/research/sources/why-sleep-matters.md, wiki/research/topics/sleep.md
- Pages updated: wiki/research/entities/matthew-walker.md
- Key takeaway: sleep deprivation has compounding cognitive effects beyond 72h
```

---

## index.md Format

Organized by domain and type. Each entry: `- [[Page Title]] — one-line description`.

Sections:
- `## Overview`
- `## Research` → subsections: Topics, Entities, Sources
- `## Personal` → subsections: Goals, Patterns, Journal
- `## Work` → subsections: Projects, Decisions, People
- `## Queries` (filed query answers)

Keep it alphabetical within each section. Update on every ingest, create, or query-that-gets-filed.

---

## Style Rules

- Write in the same language the source uses (Italian source → Italian page; English source → English page). If the wiki is mixed, default to the language the user is using in the current session.
- Keep pages dense and useful, not padded. Prefer bullets over prose for lists of facts.
- Never copy-paste raw source text verbatim — always synthesize.
- When a source contradicts an existing page, note both claims under `## Contradictions` rather than silently overwriting.
- Page filenames: lowercase, hyphen-separated, no special characters. Example: `cognitive-load-theory.md`.
- Dates: always ISO 8601 (YYYY-MM-DD).

---

## Session Start Checklist

At the start of every session:
1. Read this file (CLAUDE.md).
2. Read `index.md` to orient yourself.
3. Read the last 10 entries of `log.md` to know what happened recently.
4. Confirm with the user what they want to do today.

---

## monitor-research

Triggered when the user says: *"monitor [source-name]"*, *"controlla Simon"*, or *"aggiorna fonte [name]"*.

**Purpose:** periodic review of a research source to surface relevant new content. Distinct from INGEST — does not create source summary pages, only highlights signal.

**Steps for `fonte-simon-willison`:**
1. Fetch https://simonwillison.net directly (no clip needed — read the live page).
2. Scope: posts published in the last 7 days.
3. Filter for relevance to these themes: **agenti**, **knowledge base dinamica**, **AI per PMI**, **strumenti in uso** (Claude API, Whisper, Obsidian, n8n, Python).
4. For each relevant post: write 3 lines — (a) cos'è, (b) perché riguarda il lavoro di Marco.
5. Do **not** create a wiki page per post. If something is substantive enough to warrant a wiki page, flag it explicitly and **wait for OK before writing**.
6. Append an entry to `log.md`: `## [YYYY-MM-DD] monitor | Simon Willison's Weblog`.
7. Update the `## Monitoraggi Archiviati` table in `wiki/research/fonte-simon-willison.md`.

**Threshold for proposing a wiki page:** the post introduces a pattern, technique, or insight that will recur in your work — not just "interesting news". When in doubt, don't propose.

**Other sources:** adapt the same procedure. Each monitored source should have a `wiki/research/fonte-[name].md` page with a `## Monitoraggi Archiviati` table.

---

## TODO-MANAGE

Triggered when the user says: *"todo: [testo]"*, *"segna fatto [task]"*, *"aggiungi task [X]"*, *"mostra to-do"*, *"cosa ho da fare"*.

**File:** `wiki/personal/todo.md` — è la *vista aggregata*, non la fonte primaria dei task. Le pagine-progetto restano la fonte; `todo.md` è la lente "cosa faccio adesso".

**Regole:**

- **Aggiungere un task:** inserirlo nella sezione più appropriata (Inbox se non è chiaro, Focus se è urgente, sotto il progetto corretto se è contestualizzato). Usare `- [ ]` e wikilink se il task è legato a una pagina esistente. Esempio: `- [ ] Finire bozza per [[orchestrazione-processi]]`.
- **Spuntare un task:** sostituire `- [ ]` con `- [x]`. Non spostare ancora nell'archivio — aspetta il momento della pulizia.
- **Archiviare task completati:** spostare i `- [x]` nella sezione `## Archivio` con la data di completamento. Formato: `- [x] Testo task — ✓ YYYY-MM-DD`. Non cancellare mai — l'archivio è un log di ciò che hai fatto.
- **Inbox → elaborazione:** quando l'utente chiede di elaborare l'inbox, spostare ogni voce nella sezione giusta (Focus o Progetti) e svuotare l'Inbox.
- **Aggiornare `updated:` nel frontmatter** ad ogni modifica.
- **Non toccare `log.md`** per le operazioni todo (troppo rumore). Eccezione: se si aggiunge un task che sblocca o chiude un obiettivo, aggiorna la pagina-goal corrispondente.

**Nota MCP:** `mcp__wiki__edit_file` è abilitato — questo file è modificabile da qualsiasi sessione Claude via MCP.

---

## Evolving This Schema

This file is a living document. When you and the user discover that a convention doesn't work, update this file. The schema evolves with the wiki.
