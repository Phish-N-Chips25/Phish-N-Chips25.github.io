---
title: "Challenge 3 · Week 1: Topic Selection"
description: "Challenge 3 kicks off as our team reviews five cybersecurity proposals from the professors and selects our focus for the semester ahead."
category: "Challenge 3"
pubDate: 2026-03-01
heroImage: "../../images/blog/challenge-3-week-1.svg"
---

## A New Challenge Begins

Challenge 3 launched on **23 February 2026**, marking the start of the final stretch of the academic year. Unlike the previous challenges, this one spans two interlinked curricular units — **AAUT2IA** (Advanced AI Topics 2) and **LNIAGIA** (Natural Language and AI) — and culminates in a joint scientific article, a live implementation, and a Demo Day pitch.

## Key Deadlines to Keep in Mind

From day one, the professors made the calendar clear:

| Deliverable | Deadline |
|---|---|
| Preliminary article version (title, authors, abstract, keywords, introduction, state of the art, planned work, references) | 29 March 2026 |
| Final article | 19 April 2026 |
| Solution implementation | 19 April 2026 |
| Demonstrations | 20 April 2026 |
| Pitch delivery | 20 April 2026 |
| Demo Day with pitches | 21 April 2026 |

With roughly eight weeks from kick-off to Demo Day, every week counts.

## Five Proposals, One Choice

The professors presented **five research proposals** for the Cybersecurity vertical, each designed to leverage the ISEP robotics lab infrastructure:

1. **Sistema de Deteção de Ciberataques a Robots Autónomos** — Real-time detection of cyberattacks targeting autonomous robots (industrial arms, mobile platforms, drones), focusing on anomalous physical behaviour recognition using computer vision and LSTM/Transformer models.

2. **Sistema de Deteção de Intrusões em Sistemas Autónomos** — An Intrusion Detection System (IDS) for autonomous systems that monitors network traffic, system logs, and operational behaviour to identify both known and zero-day threats using ML and NLP.

3. **Simulador de Ataques e Testes de Penetração em Robots** — A simulation environment for executing controlled attacks on robotic systems and evaluating their resilience, producing automated pen-test reports.

4. **Assistente Inteligente de Segurança para Operadores** — An intelligent assistant supporting security operators in managing autonomous and robotic systems, reducing cognitive load via real-time LLM-based recommendations and RAG.

5. **Sistema de Auditoria Automatizada de Segurança** — An automated security auditing system analysing configurations, logs, and behaviour to ensure compliance with security standards.

## Our Decision: Topic 2

After reviewing all five proposals and discussing feasibility, team interest, and alignment with our existing knowledge from Challenge 2, we chose **Proposal 2 — Sistema de Deteção de Intrusões em Sistemas Autónomos**.

### Why Topic 2?

- It builds naturally on our Challenge 2 work on phishing detection and anomaly classification.
- The multi-layer approach (network, software, physical behaviour) offers a rich research space for the required article.
- The ISEP robotics lab (Cruzr, Booster/Unitree humanoids, industrial cobot) gives us concrete hardware targets to validate the IDS against realistic scenarios.
- The cross-disciplinary angle — combining ML, NLP/LLMs for log analysis, and multi-agent coordination — maps well to both **AAUT2IA** and **LNIAGIA** requirements.

### Scope Outline

The core system will:

- Monitor **network traffic**, **system logs**, and **operational behaviour** of autonomous systems.
- Apply **machine learning** techniques to identify suspicious patterns.
- Detect both **known attacks** and **zero-day events**.
- Use **LLMs and NLP** for log parsing, report generation, and operator-facing explanations (via RAG).
- Leverage **multi-agent architecture** where specialised agents handle different monitoring layers and correlate events for higher detection accuracy.

## First Steps

With the topic locked in, the team immediately began:

- Defining an initial reading list covering IDS taxonomies, anomaly detection in CPS/IoT, and robotic security research.
- Splitting responsibilities for the state-of-the-art survey.
- Setting up a shared workspace for collaborative article writing.

---

*Challenge 3 is underway. Next week we'll be welcoming a new team member and formalising our research plan.*
