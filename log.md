# Log

Append-only chronological record of all wiki operations.
Quick grep: `grep "^## \[" log.md | tail -10`

---

## [2026-06-11] ingest | Marco Cassani — Profilo LLM Consolidato
- Source: `raw/personal/marco-cassani-profilo.md` → spostato in `raw/_processed/`
- Pages created (8): wiki/personal/goals/goal-riferimento-ai-pmi.md, wiki/personal/goals/goal-automazione-verticale.md, wiki/personal/goals/goal-saas-b2b.md, wiki/personal/goals/goal-formazione-curricolo.md, wiki/personal/patterns/pattern-context-first.md, wiki/personal/patterns/pattern-mvp-incrementale.md, wiki/personal/patterns/pattern-buy-before-build.md, wiki/personal/patterns/pattern-roi-driven.md
- Pages updated: wiki/personal/marco-cassani.md (Preferenze Operative + interessi + stack + connections), index.md
- Fonte debole (merge 4 LLM) — estratti fatti confermati e pattern operativi; contenuti [DA VALIDARE] marcati esplicitamente
- Conflitti sospesi (non ingested): ergo-Sum.tv identità, ricerca lavoro [PX], B&B/associazione [PX], VibeLoom/Decision Mate [GM]

## [2026-06-11] create | Overview: Strategia Second Brain
- Source: None
- Pages created: wiki/strategia-second-brain.md
- Pages updated: index.md, wiki/overview.md
- Key takeaway: Documented the philosophy, architecture (raw -> ingest -> wiki), operative principles, and strategic evolution goals of this personal knowledge base.

## [2026-06-11] ingest | Simon Willison's Weblog — Clip giugno 2026
- Source: `raw/research/Simon Willison's Weblog.md` → spostato in `raw/_processed/`
- Pages created: wiki/research/sources/simon-willison-clip-2026-06.md, wiki/research/entities/simon-willison.md, wiki/research/topics/prompt-injection.md
- Pages updated: index.md, wiki/research/fonte-simon-willison.md
- Key takeaway: Pattern emergente — human-in-the-loop negli agenti (datasette-agent 0.2), sandboxing Python con WASM, e "lethal trifecta" come framework pratico per valutare il rischio prompt injection nelle integrazioni HubSpot/ERP

## [2026-06-11] monitor | Simon Willison's Weblog
- Source: live fetch simonwillison.net + raw/research/Simon Willison's Weblog.md
- Periodo: 4–11 giugno 2026
- Post rilevanti segnalati: 5 (datasette-agent 0.2, datasette-agent-edit, micropython-wasm, OpenAI Lockdown Mode, Claude Fable 5 impressions)
- Pages updated: wiki/research/fonte-simon-willison.md (tabella + sezione Segnale)

## [2026-06-10] lint | Wiki Health Check & Link Alignment
- Source: None
- Pages created: None
- Pages updated: index.md, wiki/personal/marco-cassani.md, wiki/work/projects/orchestrazione-processi.md, wiki/work/projects/drafting-tecnico.md, wiki/work/projects/system-integration.md
- Key takeaway: Audited wiki structure. Resolved orphan statuses by linking ergo-sum-website and fonte-simon-willison in the main user profile. Structured real-case project pages by adding mandatory '## Fonti' sections.

## [2026-06-10] create | Guide: Clean Code and Lighthouse Optimization
- Source: modern-web-guidance
- Pages created: wiki/research/topics/clean-code-lighthouse.md
- Pages updated: index.md, wiki/overview.md, wiki/personal/marco-cassani.md
- Key takeaway: Achieved Lighthouse 100/100 and Core Web Vitals optimization by defining structural rules for Critical Rendering Path, LCP caching, main thread task-yielding (50ms long tasks), and layout containment.

## [2026-06-10] ingest | IBM Design for AI Framework
- Source: raw/work/IBM Design for AI.md, raw/work/IBM Design for AI 1.md, raw/work/IBM Design for AI 2.md, raw/work/IBM Design for AI 3.md, raw/work/IBM Design for AI 4.md
- Pages created: wiki/research/sources/ibm-design-for-ai.md, wiki/research/entities/ibm.md, wiki/research/topics/design-for-ai.md, wiki/research/topics/ai-ethics.md, wiki/research/topics/conversational-ai-design.md
- Pages updated: index.md, wiki/overview.md, wiki/personal/marco-cassani.md
- Key takeaway: Designing for AI requires building mutual trust and symbiotic human-machine relationships. IBM's framework details foundational relational development, 5 ethical areas, and conversation design strategies (MVK).

## [2026-06-10] ingest | Article: Design Thinking 101
- Source: raw/work/Design Thinking 101.md
- Pages created: wiki/research/sources/design-thinking-101.md, wiki/research/entities/sarah-gibbons.md, wiki/research/topics/design-thinking.md
- Pages updated: index.md, wiki/overview.md, wiki/personal/marco-cassani.md
- Key takeaway: Design thinking is a hands-on, user-centric ideology and process (Understand, Explore, Materialize) focused on iteratively solving the correct human problems.

## [2026-06-10] ingest | Jakob Nielsen's 10 Usability Heuristics
- Source: raw/work/10 Usability Heuristics for User Interface Design.md
- Pages created: wiki/research/sources/10-usability-heuristics.md, wiki/research/entities/jakob-nielsen.md, wiki/research/topics/usability-heuristics.md
- Pages updated: index.md, wiki/overview.md
- Key takeaway: The 10 Usability Heuristics provide a timeless interaction design framework focused on reducing user cognitive load and providing clear control, consistency, and error prevention.

## [2026-06-10] ingest | Mental Models — fs.blog (~100 Models Explained)
- Source: `raw/personal/Mental Models...md` → spostato in `raw/_processed/`
- Estratti: 5 modelli su ~100 (inversione, secondo ordine, circle of competence, probabilistico, rasoio di Occam)
- Pagine create (6):
  - `wiki/personal/modelli-mentali.md` — pagina-indice
  - `wiki/personal/modelli-mentali/inversione.md`
  - `wiki/personal/modelli-mentali/pensiero-di-secondo-ordine.md`
  - `wiki/personal/modelli-mentali/circle-of-competence.md`
  - `wiki/personal/modelli-mentali/pensiero-probabilistico.md`
  - `wiki/personal/modelli-mentali/rasoio-di-occam.md`
- Pagine aggiornate: `index.md`
- Key takeaway: modelli estratti come toolkit cognitivo applicato alla consulenza AI per PMI; sezioni "Come lo applico" da raffinare con esperienza reale

## [2026-06-10] ingest | Sito Personale — ergo-sum.tv
- Source: `Clippings/Connettere i punti tra AI, persone e processi.md`
- Pagine create (11):
  - `wiki/personal/marco-cassani.md` — profilo principale
  - `wiki/personal/sources/ergo-sum-website.md` — source summary
  - `wiki/work/projects/orchestrazione-processi.md` — caso 1
  - `wiki/work/projects/drafting-tecnico.md` — caso 2
  - `wiki/work/projects/system-integration.md` — caso 3
  - `wiki/research/topics/ai-automazione.md` — area tematica
  - `wiki/work/organizations/pigreco-consulting.md`
  - `wiki/work/organizations/its-tech-talent-factory.md`
  - `wiki/work/organizations/galdus-academy.md`
  - `wiki/work/organizations/abtc-milano.md`
  - `wiki/work/organizations/cifa-spa.md`
- Pagine aggiornate: `index.md`, `wiki/overview.md` (stats)
- Key takeaway: Marco è un consulente AI one-man con background design+product, filosofia process-first, 3 casi reali documentati

## [2026-06-10] create | Wiki initialized
- Structure created: raw/, wiki/, CLAUDE.md, index.md, log.md
- Domains configured: research, personal, work (mixed)
- Schema version: 1.0
