---
title: "Strategia Second Brain"
type: overview
domain: mixed
tags: [meta, metodologia, second-brain, architettura]
sources: 0
created: 2026-06-11
updated: 2026-06-11
---

# Strategia Second Brain

La filosofia e l'architettura di questo wiki personale. Questa pagina di riferimento spiega perché il sistema è fatto così e come va mantenuto nel tempo.

---

## Principio di fondo

Un solo posto, file leggibili, conoscenza che si accumula. Niente database vettoriale, niente strumenti sparsi: un vault Obsidian che è anche repo Git, dove un agente AI fa da bibliotecario seguendo le regole del `CLAUDE.md`. Si basa sul pattern **LLM Wiki** (ispirato a Karpathy). Vale come second brain personale e, allo stesso tempo, come demo viva di ciò che offro ai clienti.

---

## Architettura

- `raw/` → inbox: clip, trascrizioni, materiale grezzo (scritto dall'utente, a costo zero).
- `wiki/` → conoscenza compilata in pagine-concetto (scritto dall'agente, seguendo le regole di formattazione).
- `index.md` + `[[wiki-link]]` → la mappa che rende tutto navigabile senza database.

Il "retrieval" non è statistico: l'agente apre `index.md`, segue i wiki-link e legge le pagine. Trasparente e tracciabile per costruzione.

### Le tre aree, tre logiche diverse

| Area | Ancora di partenza | Logica di ingest |
|---|---|---|
| **personal** | [[modelli-mentali]] (Farnam Street) | smonta in pagine-concetto + "Come lo applico" |
| **work** | [[usability-heuristics]] (NN/g) | smonta in concetti applicati a UI/prototipi |
| **research** | [[fonte-simon-willison]] | monitora e segnala; scrive solo con approvazione |

*Distinzione chiave:* `personal` e `work` si smontano in concetti una volta e si arricchiscono nel tempo; `research` si monitora ciclicamente e non si accumula (le novità invecchiano).

---

## Principi operativi

- **Compilazione, non accumulo:** ogni fonte va integrata nelle pagine, non parcheggiata. I clip grezzi che restano in `raw/` non sono conoscenza.
- **Unità = concetto, non articolo:** un articolo si smonta in più pagine; due fonti sullo stesso concetto convergono in una singola pagina.
- **"Come lo applico":** la sezione che trasforma il sapere generico in conoscenza mia — l'agente propone, l'utente raffina.
- **Human-in-the-loop:** gli aggiornamenti sostanziali li approva l'utente; l'agente propone, non sovrascrive in silenzio.
- **Tracciabilità:** ogni pagina cita le fonti originarie.
- **Compounding:** il sistema vale di più ogni mese che lo uso.

---

## Flusso operativo

1. Clip via Obsidian Web Clipper → `raw/[area]/` (con nota sul perché).
2. Comando di ingest all'agente (procedure salvate nel `CLAUDE.md`: ingest, journal, monitor-research).
3. Review del changelog + raffinamento delle sezioni "Come lo applico".
4. File processato spostato in `raw/_processed/`.

---

## Obiettivi strategici

1. **Memoria condivisa multi-LLM:** collegare il wiki a più modelli (Claude, Gemini, altri) come memoria centralizzata unica — si aggiorna in un posto solo, ogni LLM attinge alla stessa conoscenza. Via maestra: MCP server sul vault (una fonte, N interfacce); via immediata: vault nel contesto dell'IDE + upload selettivo (Claude Projects, NotebookLM).
2. **Lezioni per i corsi:** generare materiale didattico (ITS, Galdus) dalle pagine-concetto — il wiki come base unica da cui derivare slide, dispense ed esercizi, coerenti e aggiornati a ogni edizione del corso.
3. **Agente di content generation:** collegare il wiki a un agente che genera in automatico contenuti multicanale (testo, video, audio, immagini) attingendo a `[[tone-of-voice]]` (da creare) e alle sezioni "Come lo applico". Il wiki è il cervello, l'agente il braccio editoriale.
4. **Esperimento → cliente:** tutto il sistema è il banco di prova di ciò che applicherò al prossimo cliente — ogni procedura validata qui diventa metodo consegnabile (e il making-of diventa case study).

---

## Evoluzioni operative

- **Decision journal** come procedura del wiki (prossimo, costo zero).
- **Weekly review** automatizzata (processa raw, monitora, propone contenuti).
- **MCP server** sul vault quando le pagine superano ~50 — abilita l'obiettivo 1.
- **Ponte wiki → contenuti:** le sezioni "Come lo applico" come semi di post — primo passo verso l'obiettivo 3.

---

## Strumenti esterni: criterio di ammissione

Per ogni nuovo strumento, una domanda sola: **scrive nel wiki o lo legge soltanto?**
- **Solo legge** (es. NotebookLM per audio/Q&A) → ammesso come interfaccia, purché sincronizzato e alimentato solo da pagine già compilate.
- **Scrive fuori dal wiki** → frammentazione, da evitare. La fonte di verità resta sempre il vault.

---

## Cosa NON aggiungere (per ora)

- **RAG/vettoriale** sopra il wiki: over-engineering sotto le ~200-300 pagine.
- **Altri tool di knowledge management:** ogni tool in più frammenta.
- **Automazione di research** senza approvazione: riempie il wiki di rumore.

---

## Connections

- [[modelli-mentali]] — Toolkit cognitivo del second brain (area personal)
- [[usability-heuristics]] — Euristiche di usabilità di Jakob Nielsen (area work)
- [[fonte-simon-willison]] — Fonte di monitoraggio settimanale (area research)
- [[overview]] — Sintesi top-level dell'intero wiki
