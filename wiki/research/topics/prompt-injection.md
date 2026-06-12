---
title: "Prompt Injection"
type: topic
domain: research
tags: [sicurezza, LLM, agenti, attacchi, prompt-injection, integrazioni]
sources: 1
created: 2026-06-11
updated: 2026-06-11
---

## Summary

Tecnica di attacco in cui contenuto non trusted inserito nel contesto di un LLM modifica il comportamento del modello, potenzialmente estraendo dati privati o eseguendo azioni non autorizzate. Uno dei principali rischi di sicurezza nelle integrazioni LLM in produzione.

## Key Points

- **Il Lethal Trifecta** (Simon Willison): l'attacco diventa critico solo quando coesistono tre elementi:
  1. Accesso a dati privati
  2. Esposizione a contenuto non trusted (file caricati, web, email, database)
  3. Canale di esfiltrazione (network request in uscita)
- La validazione dell'input non è sufficiente — il contenuto iniettato può essere nascosto in dati legittimi (cache, allegati, risultati SQL)
- **Mitigazioni pratiche:**
  - Eliminare uno dei tre elementi del trifecta (approccio più robusto)
  - **Lockdown Mode** (OpenAI, 2026): taglia tutti i network request in uscita
  - **Sandboxing dell'esecuzione** (micropython-wasm): isola il runtime Python in WebAssembly
  - **Human-in-the-loop** per operazioni irreversibili o con accesso a dati sensibili
- Prompt injection ≠ jailbreak: non punta a bypassare le linee guida del modello, ma a redirigere le sue azioni verso obiettivi dell'attaccante

## Open Questions

- Come si applica il Lethal Trifecta nelle integrazioni HubSpot/ERP con accesso a dati cliente?
- Esistono pattern di sandboxing equivalenti per ambienti n8n?
- Come si può detectare (non solo prevenire) un'iniezione riuscita nei log?

## Connections

- [[simon-willison]] — ha formalizzato il Lethal Trifecta come framework pratico
- [[simon-willison-clip-2026-06]] — post "OpenAI Lockdown Mode" (5 giu) e "Running Python code in a sandbox" (6 giu)
- [[ai-automazione]] — rischio nelle integrazioni LLM in produzione
- [[system-integration]] — contesto operativo: integrazioni HubSpot/ERP esposte a dati di terzi

## Sources

- `raw/research/Simon Willison's Weblog.md` — posts: "OpenAI Lockdown Mode" (5 giu 2026), "Running Python code in a sandbox with MicroPython and WASM" (6 giu 2026)
