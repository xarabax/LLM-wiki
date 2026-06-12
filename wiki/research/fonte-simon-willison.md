---
title: "Fonte: Simon Willison's Weblog"
type: source
domain: research
tags: [fonte, LLM, agenti, claude, tool-use, monitoraggio-settimanale]
sources: 0
created: 2026-06-10
updated: 2026-06-11
---

## Cos'è

Blog personale di [Simon Willison](https://simonwillison.net), co-creatore di Django, autore di Datasette. Pubblica quasi quotidianamente su LLM applicati, agenti, sicurezza AI, strumenti pratici. Mix di post lunghi, TIL (Today I Learned), link commentati e citazioni.

**URL:** https://simonwillison.net
**Feed:** https://simonwillison.net/atom/everything/
**Frequenza monitoraggio:** settimanale (ogni lunedì o su richiesta)

## Perché la monitoro

Segnale alto, bassa rumorosità. Simon testa le novità in prima persona — non commenta comunicati stampa ma pubblica risultati reali con codice e screenshot. Copre esattamente i temi rilevanti per il mio lavoro: agenti, LLM applicati, tool-use, sicurezza delle integrazioni, Claude API. È uno dei pochi blogger che passa da "ho letto l'annuncio" a "ho passato 5 ore a testarlo" nello stesso giorno.

## Temi Ricorrenti Rilevanti

- Agenti e tool-use (Datasette Agent, Claude text editor patterns)
- Sandboxing e sicurezza delle integrazioni AI
- Claude / Anthropic (utente e commentatore critico)
- Prompt injection e vettori di attacco
- Produttività con coding agents
- LLM pricing e cost management

## Monitoraggi Archiviati

| Data | Metodo | Post segnalati |
|---|---|---|
| 2026-06-10 | clip Clippings/ | 4 post (vedere log.md) |
| 2026-06-11 | live fetch + clip | 5 post rilevanti (vedere log.md) |

## Segnale — 2026-06-11

**1. datasette-agent 0.2a0** (10 giu) — Tool che fanno domande durante la propria esecuzione + stored query con approvazione umana. Human-in-the-loop nativo negli agenti, applicabile a workflow con n8n/Python dove servono checkpoint prima di operazioni irreversibili.

**2. datasette-agent-edit plugin** (7 giu) — Pattern `view`/`str_replace`/`insert` per editing testuale agentico, derivato dai tool Claude. Blueprint riutilizzabile per agenti che modificano documenti strutturati (bandi, template).

**3. Running Python code in a sandbox — micropython-wasm** (6 giu) — Python in sandbox WebAssembly: esecuzione sicura di codice non trusted senza rischio corruzione sistema. Requisito chiave per pipeline agentiche in produzione.

**4. OpenAI Lockdown Mode** (5 giu) — Taglia i network request in uscita → soluzione pratica al [[prompt-injection#lethal-trifecta|lethal trifecta]]. Approccio replicabile in qualsiasi integrazione LLM con accesso a dati privati.

**5. Initial impressions of Claude Fable 5** (9 giu) — Potente, lento, costoso ($74 in una sessione intensiva). Il costo è il vero vincolo per l'uso sistematico in contesti PMI; la capacità per task complessi agentica è alta.

## Connections

- [[ai-automazione]] — temi sovrapposti su agenti e integrazioni
- [[marco-cassani]] — fonte di riferimento per il lavoro di consulenza

## Note

Simon usa una scrittura molto densa: anche i post brevi ("link") contengono osservazioni originali che vale la pena leggere. Non clippare tutto — preferire il monitoraggio diretto via URL (vedere procedura `monitor-research` in CLAUDE.md).
