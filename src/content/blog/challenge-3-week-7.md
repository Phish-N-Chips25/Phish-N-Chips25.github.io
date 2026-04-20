---
title: "Challenge 3 · Week 7: Final Article and Integrated Front-End Delivered"
description: "Article finalised and the Flask SOC dashboard wires face recognition, anomaly detection and MITRE ATT&CK attribution into a single experience — both delivered on the 19 April deadline."
category: "Challenge 3"
pubDate: 2026-04-19
---

## Week 7 Overview

Week 7 (13 – 19 April) was the **delivery week**. Two artefacts had to be in by **19 April 2026**:

1. The **final scientific article** (graded version, after preview feedback).
2. The **working solution** — an integrated front-end exercising all three pillars end-to-end.

Both are in.

## The Final Article

The preliminary submission already covered title, authors, abstract, keywords, introduction, related work (9 subsections), system architecture and references. Week 7 closed the remaining gaps:

- **Experimental Setup** — datasets (LMD-2023, OTRF Atomic Red Team, Splunk Attack Range, SILRAD), preprocessing (Word2Vec 352-dim windows of 45 events), training protocol (100 % unsupervised on 2.3 M benign events), and the metrics for each layer (AP, AUC, FAR/FRR/EER, RAG recall, explanation grounding).
- **Results** — the headline numbers consolidated:
  - TransformerAE sequences: **AP 0.814** (OTRF) / **AP 0.836** (Splunk).
  - Single-event AE: **AUC 0.989 – 0.992** cross-dataset.
  - ATT&CK KB: **3,463** indexed entries, **60 %** recall on OTRF.
  - Face recognition: cosine-similarity threshold **0.70** with FAR/FRR/EER reported on the 5 enrolled users.
- **Discussion** — explicit comparison between the **main RAG + Qwen 2.5 32B** track and the **DualSentinel SLM→LLM** alternative, and why the opaque IsolationForest + GRU pipeline was dropped in favour of an auditable heuristic scorer.
- **Conclusions and Future Work** — privacy-by-design via local Ollama, scalability via DualSentinel, gaps acknowledged (anti-spoofing, broader T-code coverage).
- **References** — extended to cover the additional models cited (Phi-3 Medium, Llama 3.2, Qwen 2.5 32B) and the ATT&CK / Sigma sources powering the KB.

## The Integrated Front-End

`frontend/app.py` is now a coherent Flask application that ties the three pillars together:

```
Camera → InsightFace → Authentication → SOC Dashboard
                                            │
                              ┌─────────────┴──────────────┐
                              ▼                            ▼
                    Threat queue                 Model status
                    (OTRF / Splunk)              (AE + TransformerAE
                              │                  + ATT&CK KB + Ollama)
                              ▼
                    Pick a suspicious chain
                              │
                   ┌──────────┴───────────┐
                   ▼                      ▼
            Sequence scores         Per-event scores
            (TransformerAE)         (Single-event AE)
                   │
                   ▼
            ATT&CK attribution
            (RAG + Qwen 2.5 32B)
                   │
                   ▼
            Technique ID + confidence + explanation
```

What the dashboard actually does in the demo:

1. The webcam authenticates the analyst via **InsightFace buffalo_sc** with cosine similarity ≥ 0.70 sustained over the observation window.
2. The SOC view shows the **threat queue** (chains pre-scored by the TransformerAE) and the live **status of every model** (single-event AE, sequence AE, ATT&CK KB, Ollama).
3. Clicking a chain reveals the **sequence reconstruction error** and the **per-event scores** so the analyst sees exactly *which* Sysmon events drive the alert.
4. A click on “Attribute” fires the **hybrid RAG** retrieval and asks **Qwen 2.5 32B** (locally, via Ollama) to return the matching MITRE ATT&CK technique with a chain-of-thought explanation grounded on the retrieved evidence.

The Streamlit standalone demo for DualSentinel remains available as a secondary entry point, useful when GPU resources are constrained.

## Stack as Delivered

- **Face recognition** — InsightFace (ArcFace + RetinaFace), ONNX Runtime, facenet-pytorch, OpenCV; CNN + ResNet-50 fine-tuned for the 5 enrolled users.
- **Anomaly detection** — PyTorch (TransformerAE + single-event AE), Word2Vec via gensim, Optuna (NAS + HPO), MLflow tracking; DualSentinel heuristic scorer for the auditable alternative.
- **ATT&CK attribution** — ChromaDB, sentence-transformers (`all-mpnet-base-v2`), rank-bm25, Ollama (Qwen 2.5 32B / Phi-3 Medium / Llama 3.2 / phi4), Sigma rules, MITRE STIX.
- **Interface** — Flask + HTML/CSS/JS for the SOC dashboard, Streamlit for the DualSentinel demo.
- **Infrastructure** — Conda environment on Python 3.11 with CUDA 12.6, FastAPI + uvicorn for service endpoints.

## What Goes In Tomorrow

| Item | Status |
|---|---|
| Final article (PDF) | ✓ delivered |
| Integrated solution (Flask + models + KB) | ✓ delivered |
| Demonstration walkthrough rehearsed | ✓ |
| Pitch deck draft | ✓ — final pass during week 8 |

The article is in. The system runs end-to-end. Demo Day starts in the morning.

---

*Article and code shipped. Demo and pitch up next.*
