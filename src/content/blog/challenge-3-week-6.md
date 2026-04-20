---
title: "Challenge 3 · Week 6: Tuning the Three Pillars"
description: "Acting on preview feedback — refining the face recognition module, hardening the anomaly detection autoencoders, and tightening the MITRE ATT&CK attribution pipeline."
category: "Challenge 3"
pubDate: 2026-04-12
---

## Week 6 Overview

With the preliminary article submitted on **29 March**, week 6 (30 March – 12 April) was the **adjustment sprint**. Feedback from the professors plus our own internal review pushed us back into the code: each of the three pillars needed work before the final delivery on 19 April.

The plan for the week was clear:

1. Stabilise the **face recognition** module (Pillar 1) and finish the organisational fine-tuning.
2. Squeeze the last percentage points out of the **anomaly detection** stack (Pillar 2).
3. Cement the **ATT&CK attribution** pipeline (Pillar 3) and validate the alternative DualSentinel path.

## Pillar 1 — Face Recognition Adjustments

The InsightFace `buffalo_sc` baseline was already working end-to-end, but the team focused on **organisational fine-tuning** so that the system performs well specifically for the 5 enrolled users.

Work completed during the week:

- **Data augmentation** of ~20× per enrolment photo (rotation, lighting, slight occlusion) to compensate for the small per-user dataset.
- Fine-tuning of a **CNN baseline** and a **ResNet-50** backbone on top of the InsightFace embeddings.
- Evaluation with **FAR / FRR / EER** so we can defend the threshold choice numerically rather than by intuition.
- Final cosine-similarity threshold locked at **0.70** with sustained-match observation window — no single-frame false positives.
- Fine-tuned models exported for deployment in the Flask front-end.

The result is a recogniser that behaves consistently under the lighting conditions of our working room, which is exactly where the demo will run.

## Pillar 2 — Anomaly Detection Hardening

The detection stack runs on Windows Sysmon logs in two layers. Both received targeted improvements:

### Sequence layer — Transformer Autoencoder

- Re-confirmed the **Optuna NAS+HPO** architecture (`hidden=256`, `latent=128`, 2 layers, 8 heads) on the held-out folds.
- Re-calibrated the reconstruction-error threshold to **0.627528** after re-running on a refreshed benign corpus.
- Cross-dataset evaluation reproduced: **AP = 0.814** on OTRF Atomic Red Team, **AP = 0.836** on Splunk Attack Range.

### Single-event layer — Autoencoder

- Confirmed the `[353 → 231 → 176 → 162 → 8]` ELU autoencoder as the per-event scorer.
- Cross-dataset **AUC between 0.989 and 0.992** — genuine generalisation, not over-fitting to LMD-2023.

The two layers together give the analyst both *“this chain looks wrong”* and *“these specific events inside the chain are the wrongest”*, which was the missing piece in earlier iterations.

## Pillar 3 — MITRE ATT&CK Attribution

The attribution pipeline now stands on two parallel tracks:

### Main track — Hybrid RAG + Qwen 2.5 32B

- Knowledge base finalised at **3,463 entries** combining MITRE STIX, OTRF metadata, Splunk YAML and Sigma rules.
- Hybrid retrieval = **dense** (`all-mpnet-base-v2` via ChromaDB) **+ sparse** (BM25).
- Chain-of-thought prompt to **Qwen 2.5 32B** running locally via Ollama, returning structured JSON (technique ID, confidence, explanation).
- **RAG recall: 60 %** on OTRF Atomic Red Team — the headline number for the article.

### Alternative track — DualSentinel

The original IsolationForest + GRU classical pipeline was replaced with a **fully auditable heuristic scorer** (ATT&CK rules + 7 smart-feature flags + self-supervised baseline deviation + hybrid KB hits with RRF). Empirical tests on LMD-2023 and Splunk Attack Data showed that the opaque models added no measurable gain *and* prevented the LLM Judge from auditing the evidence — a regression we were not willing to ship.

The resulting chain is:

```
Heuristic Scorer (ATT&CK rules + smart features + baseline + KB hybrid)
        → SLM Analyst (Phi-3 Medium)
        → LLM Judge (Llama 3.2)
```

Four consolidated notebooks back this up: `defesa_lmd_full_report`, `threshold_calibration`, `kb_ablation`, and `eda`. Everything runs locally via Ollama — sensitive logs never leave the machine.

## What's Next

| Item | Target |
|---|---|
| Final article | 19 April 2026 |
| End-to-end Flask front-end wiring all three pillars | 19 April 2026 |
| Demonstrations | 20 April 2026 |
| Pitch | 21 April 2026 |

Week 7 is reserved for finishing the article and gluing everything together behind a single dashboard.

---

*Three pillars tuned. One week left to ship.*
