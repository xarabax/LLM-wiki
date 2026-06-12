---
title: "Pattern: Buy Before Build"
type: pattern
domain: personal
tags: [pattern, make-or-buy, SaaS, pragmatismo, architettura]
sources: 1
created: 2026-06-11
updated: 2026-06-11
---

## Summary

Prima di costruire da zero, verificare se esiste un SaaS, un'API o un template che copre l'80% del bisogno. Il custom si giustifica solo quando il gap residuo è misurabile e strategicamente rilevante.

## Key Points

- SaaS / API / template esistenti → custom solo se il gap è reale e misurabile
- L'integrazione di strumenti esistenti è spesso più veloce e manutenibile del codice custom
- Framework decisionale: build vs buy vs partner
- Corollario: no lock-in ideologico su un vendor — scegliere il miglior tool per il contesto

## Come si manifesta

- Filosofia dichiarata: "L'innovazione si fa ridisegnando le connessioni tra strumenti che già possiedono"
- Adozione di n8n per automazioni invece di scrivere tutto in Python custom
- Multi-model benchmark prima di scegliere un LLM per un progetto

## Connections

- [[marco-cassani]] — principio operativo
- [[ai-automazione]] — applicato alla scelta dei tool AI
- [[pattern-mvp-incrementale]] — complementare: l'MVP spesso è un tool esistente configurato
- [[pattern-roi-driven]] — il ROI del custom si confronta con il costo del SaaS esistente
