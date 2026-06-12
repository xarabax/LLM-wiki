---
title: "Conversational AI Design"
type: topic
domain: research
tags: [conversation-design, chatbots, virtual-assistant, mvk]
sources: 1
created: 2026-06-10
updated: 2026-06-10
---

## Sintesi

Conversational AI Design focuses on structuring and planning natural language interactions between humans and bots. According to IBM's framework, a conversational agent (bot) must have a focused purpose that provides distinct value over traditional interfaces (like web forms or static documents). Successful conversational design requires defining a bot's **Minimum Viable Knowledge (MVK)**, mapping topic depth, constructing elegant **fail-and-repair** mechanisms, and styling a consistent **personality** aligned with the brand and domain.

---

## 1. Justifying a Bot

Bots are not a universal solution. Conversation has its highest value when there is a need for engaging, contextual interactions. Before building, design teams must justify a bot using these questions:
- What is the user’s primary goal?
- How in-depth is the assistance they require? Is the domain better off left to human experts?
- How is a conversational model superior to traditional alternatives (e.g., online documentation, search filters, form wizards)?

---

## 2. Minimum Viable Knowledge (MVK)

The goal of bot planning is to establish its MVK: the **minimum set of topics** your bot must discuss proficiently to fulfill its purpose.

```
                  MINIMUM VIABLE KNOWLEDGE (MVK)
          ┌──────────────────────────────────────────────┐
          │               Topic Breadth                  │
          │  (Prioritized list of essential subjects)    │
          │                      │                       │
          │                      ▼                       │
          │               Topic Depth                    │
          │  (Mapped dialog paths & error boundaries)    │
          └──────────────────────────────────────────────┘
```

- **Topic Breadth:** List and prioritize possible subjects. Fewer, more focused topics yield higher interaction quality.
- **Topic Depth:** Map individual turns between human and bot until a resolution or dead-end is reached.

---

## 3. Topic Depth & Fail-and-Repair

Every topic must account for both ideal user paths and **conversational breakdowns**. When the user strays outside bot capabilities, frustration occurs.
- **Fail-and-Repair:** The bot's ability to gracefully handle misunderstandings, repair the conversation, and guide the user back.
- **Handoffs:** Knowing when to smoothly transition the conversation to a human agent rather than trapping the user in a loop.

---

## 4. Bot Personality Mapping

A bot's personality is the vehicle for its voice. Once the MVK is defined, teams should draft conversational responses through a structured persona. Key personality dimensions to define include:
- **Tone & Formality:** How professional vs. friendly is it?
- **Social Style:** How thoughtful, moody, or excitable is it?
- **Hostility Management:** How does it react to negative or angry inputs?
- **Brand Alignment:** Does its character reflect the company's core values?

*Methodology Tip:* Mapping can utilize psychology profiling frameworks like the Caliper Profile or Myers-Briggs Type Indicator (MBTI).

---

## Application in AI & Automation

For developers like [[marco-cassani]]:
- **Workflow Inputs:** Designing automated Slack bots or customer support assistants requires establishing MVK. For example, a bot managing invoice queries should only handle invoice checks and hand off everything else to support staff.
- **n8n Chat Nodes:** When configuring chat interfaces in n8n or HubSpot, setting clear system instructions defines the "personality" and boundaries (MVK), preventing the LLM from hallucinating or answering out-of-scope queries.

---

## Connections

- [[ibm]] — Author of the conversational planning guidelines.
- [[design-for-ai]] — Foundational framework for human-AI relationships.
- [[marco-cassani]] — Designs intent-parsing and failure-handling logic in custom conversational integrations.

---

## Sources

- [[ibm-design-for-ai]] — IBM Design for AI documentation (Conversation & Planning).
