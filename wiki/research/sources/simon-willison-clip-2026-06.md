---
title: "Simon Willison's Weblog — Clip giugno 2026"
type: source
domain: research
tags: [LLM, agenti, datasette, python, prompt-injection, claude-fable, sandboxing]
sources: 1
created: 2026-06-11
updated: 2026-06-11
---

## Summary

Clip della homepage di simonwillison.net, scaricata il 10 giugno 2026. Copre circa due settimane di post (fine maggio–10 giugno 2026). I pezzi più sostanziali riguardano: valutazione pratica di Claude Fable 5, evoluzione di Datasette Agent verso human-in-the-loop, sandboxing Python con WebAssembly, e sicurezza delle integrazioni LLM con Lockdown Mode.

## Key Points

- **Claude Fable 5** (9 giu, ~2400 parole): beast — lento, costoso ($74 in una sessione intensiva), già usato per scrivere release complete e aggiungere feature a Datasette Agent in autonomia con Claude Code
- **datasette-agent 0.2a0** (10 giu): i tool possono ora fare domande durante la propria esecuzione + approvazione umana per stored query — human-in-the-loop nativo negli agenti
- **datasette-agent-edit** (7 giu): pattern `view`/`str_replace`/`insert` per editing testuale agentico — blueprint riutilizzabile derivato dai tool Claude
- **micropython-wasm** (6 giu, ~2000 parole): Python in sandbox WebAssembly — esecuzione sicura di codice non trusted senza rischio corruzione sistema
- **OpenAI Lockdown Mode** (5 giu): taglia network request in uscita → soluzione pratica al "lethal trifecta" di prompt injection

## Connections

- [[simon-willison]] — autore
- [[fonte-simon-willison]] — pagina di monitoraggio della fonte
- [[prompt-injection]] — tema ricorrente; post OpenAI Lockdown Mode e micropython-wasm
- [[ai-automazione]] — pattern agentici applicabili al lavoro di Marco
- [[system-integration]] — contesto operativo: rischio prompt injection nelle integrazioni HubSpot/ERP

## Sources

- `raw/research/Simon Willison's Weblog.md` — clip homepage simonwillison.net del 2026-06-10
