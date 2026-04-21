---
title: "Challenge 3 · Week 8: Demonstration and Pitch"
description: "20 April — live demonstration of the integrated cyber-physical surveillance system. 21 April — Demo Day pitch in front of the jury."
category: "Challenge 3"
pubDate: 2026-04-21
---

## Week 8 Overview

Two days. Two very different formats.

- **20 April 2026 — Demonstration day.** A full technical walkthrough of the working system in front of the professors.
- **21 April 2026 — Demo Day pitch.** A short, narrative-driven presentation to the wider audience.

The deliverables (article + code) had already been handed in on 19 April, so week 8 was about **showing** the work, not writing it.

## Day 1 — Demonstration (20 April)

The demonstration followed the system flow end-to-end, exactly as the dashboard is built:

### 1. Authentication

The webcam picks up the analyst. **InsightFace buffalo_sc** computes the embedding, compares it against the 5 enrolled centroids, and grants access only when cosine similarity stays **≥ 0.70** over the sustained-match window. No password, no smart card.

### 2. SOC Dashboard

After authentication, the **Flask SOC dashboard** loads showing:

- The **threat queue** — chains pre-scored by the TransformerAE on OTRF Atomic Red Team and Splunk Attack Range data.
- **Model status** — single-event AE, sequence AE, ATT&CK KB and Ollama, all live.

### 3. Sequence and Per-Event Inspection

Selecting a suspicious chain renders both views in the same screen:

- **Sequence reconstruction error** from the **Transformer Autoencoder** (`hidden=256`, `latent=128`, 2 layers, 8 heads, threshold 0.627528) — AP 0.814 on OTRF, AP 0.836 on Splunk.
- **Per-event scores** from the **single-event AE** (`[353→231→176→162→8]` ELU) — AUC 0.989 – 0.992 cross-dataset — pinpointing the exact Sysmon events driving the alert.

### 4. MITRE ATT&CK Attribution

A click on “Attribute” triggers the **hybrid RAG** (dense `all-mpnet-base-v2` via ChromaDB + BM25 sparse) over the **3,463-entry knowledge base** (MITRE STIX + OTRF metadata + Splunk YAML + Sigma rules), and asks **Qwen 2.5 32B locally via Ollama** for a chain-of-thought attribution. The dashboard returns:

- ATT&CK **technique ID**.
- **Confidence**.
- **Explanation** grounded on the retrieved evidence (60 % recall on OTRF Atomic Red Team).

### 5. The Auditable Alternative — DualSentinel

To close the demo, we showed the **DualSentinel** path running on the same data:

```text
Heuristic Scorer (ATT&CK rules + smart features + baseline + KB hybrid)
        → SLM Analyst (Phi-3 Medium)
        → LLM Judge (Llama 3.2)
```

Every term in the heuristic scorer is inspectable. The SLM produces a fast hypothesis; the LLM Judge validates or refutes it with explicit references to the events. Same dataset, smaller models, full auditability — the message being that the architecture **scales down** without losing its grounding.

## Day 2 — Demo Day Pitch (21 April)

The pitch built on six anchor points distilled from the project summary:

1. **The problem is real.** SOC analysts drown in alerts; alert fatigue is a leading cause of missed incidents.
2. **Security starts at the door.** InsightFace makes sure only the right people get in.
3. **The investigation was serious.** 10 notebooks, 4 datasets, multiple architectures benchmarked — autoencoders won on merit, not on first-idea bias.
4. **The model does not hallucinate without evidence.** Hybrid RAG + chain-of-thought forces the LLM to ground its conclusions in retrieved facts.
5. **Privacy by design.** Everything runs locally via Ollama. Sensitive Windows logs never leave the machine.
6. **Scalability.** DualSentinel demonstrates that the same concept works with smaller models (Phi-3 Medium + Llama 3.2) on top of an auditable heuristic scorer — viable even without top-tier GPUs, and every decision defensible to an analyst.

### Headline Numbers Used in the Pitch

| Component | Metric | Value |
|---|---|---|
| Face authentication | Cosine similarity threshold | 0.70 |
| TransformerAE (sequences) | AP — OTRF Atomic | **0.814** |
| TransformerAE (sequences) | AP — Splunk Attack Range | **0.836** |
| Single-event AE | AUC cross-dataset | **0.989 – 0.992** |
| ATT&CK KB | Indexed entries | **3,463** |
| RAG attribution | Recall — OTRF | **60 %** |
| Training corpus | Benign Sysmon events | **2.3 M** |
| Evaluation corpora | OTRF + Splunk | **~2.6 M events** |
| Ground-truth coverage | T-codes (OTRF + Splunk) | **230 techniques** |

### What Differentiates Us

| Traditional approach | Challenge 3 |
|---|---|
| Hand-written rules | Unsupervised learning — detects the unknown |
| Alerts without context | ATT&CK attribution with chain-of-thought + evidence |
| External APIs (data leaves) | 100 % local via Ollama — sensitive data stays put |
| Password or smart card | Face recognition with ArcFace |
| Binary alert | Per-event score + sequence score + technique + confidence |

## Wrap-Up

| Day | Activity | Outcome |
|---|---|---|
| 19 April | Final article + integrated solution | Delivered |
| 20 April | Live demonstration | Performed end-to-end |
| 21 April | Demo Day pitch | Delivered |

Three pillars. One integrated system. End of Challenge 3, end of the academic year.

---

*Demonstration: shown. Pitch: delivered. Challenge 3: closed.*
