---
title: "Design Thinking"
type: topic
domain: research
tags: [design-thinking, framework, problem-solving, user-research]
sources: 1
created: 2026-06-10
updated: 2026-06-10
---

## Sintesi

Design Thinking is a hands-on, user-centric approach to problem-solving that drives innovation and provides competitive advantage. It is composed of a core **ideology** (asserting that starting with real user needs leads to better products) and a structured, non-linear **process** of 6 phases: Empathize, Define, Ideate, Prototype, Test, and Implement. It helps teams align, define the correct problems, and execute them effectively through "design doing."

---

## The 6-Phase Framework

The process is structured into three overall buckets: **Understand**, **Explore**, and **Materialize**.

```
       UNDERSTAND                EXPLORE                MATERIALIZE
  ┌──────────────────┐    ┌──────────────────┐    ┌────────────────────┐
  │ 1. Empathize     │───>│ 3. Ideate        │───>│ 5. Test            │
  │ 2. Define        │    │ 4. Prototype     │    │ 6. Implement       │
  └──────────────────┘    └──────────────────┘    └────────────────────┘
```

### 1. Understand

#### Empathize
*Develop deep knowledge about what your users do, say, think, and feel.*
- **Activity:** Talk to real users, observe them directly, map motivations and frustrations.
- **Goal:** Build empathy to look at the problem from the user's perspective rather than engineering assumptions.

#### Define
*Analyze user research to identify where the core problems and unmet needs exist.*
- **Activity:** Synthesize observations, locate patterns, and write user need statements.
- **Goal:** Pinpoint opportunities for innovation by focusing on the right problem (avoiding the risk of solving the wrong problem beautifully).

### 2. Explore

#### Ideate
*Brainstorm a wide range of creative, unconstrained ideas.*
- **Activity:** Team brainstorming sessions, sketching concepts, mixing and building upon others' ideas.
- **Goal:** Prioritize quantity over quality to unearth innovative solutions. Suspended judgment is crucial.

#### Prototype
*Build low-fidelity, tactile representations of ideas.*
- **Activity:** Draw wireframes, construct mockups, or write quick-and-dirty script drafts.
- **Goal:** Understand what works and what does not. Evaluate impact vs. feasibility.

### 3. Materialize

#### Test
*Return to users for feedback on the prototypes.*
- **Activity:** Put prototypes in front of real customers, observe interactions, and measure if the solution addresses their needs.
- **Goal:** Validate assumptions and refine the product direction based on real-world behavior.

#### Implement
*Execute the vision and deliver the solution to the end-users.*
- **Activity:** Transition from planning to engineering, deploying the actual product or automated workflow.
- **Goal:** Realize innovation. As Don Norman notes: *"We need more design doing. Design thinking only leads to true innovation if the vision is executed."*

---

## Core Advantages

1. **User-Centered Validation:** Relies on empirical user data rather than internal opinions, avoiding imaginary requirements.
2. **Collective Expertise & Buy-in:** Builds cross-functional alignment and a shared vocabulary within the team.
3. **Systematic Innovation:** Encourages exploration of multiple paths before committing resources.
4. **Scalability:** Applicable to micro-level features (e.g., search indexing) or macro-level societal challenges.

---

## Iterative and Cyclical Nature

Design Thinking is not a linear, step-by-step checklist. It serves as **scaffolding** that should be tweaked.
- **Feedback Loops:** Testing a prototype frequently uncovers new user behaviors, requiring teams to loop back to *Empathize* or *Define*.
- **Repetition:** Phases (especially *Define*) should be repeated if there is a lack of alignment or buy-in on the problem statement.

---

## Application in AI & Automation

For an AI Solution Architect (like [[marco-cassani]]):
- **Avoid the "Tool-First" Trap:** AI projects often fail because developers focus on the technology (GPT models, databases) rather than the user's workflow. Design Thinking forces the team to *Define* the problem first (e.g., "Why is drafting bandi slow?") before picking the model.
- **Prototyping in n8n/Python:** Rapidly prototyping workflows with mock data allows clients to see inputs/outputs (*Test* phase) before executing heavy API integrations.

---

## Connections

- [[sarah-gibbons]] — Author of the NN/g framework overview.
- [[marco-cassani]] — Incorporates these stages during discovery workshops with SMB clients.
- [[ai-automazione]] — Design Thinking ensures automation builds the right workflows.

---

## Sources

- [[design-thinking-101]] — Sarah Gibbons' article: *Design Thinking 101* (NN/g).
