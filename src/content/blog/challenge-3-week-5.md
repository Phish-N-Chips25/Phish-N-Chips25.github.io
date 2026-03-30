---
title: "Challenge 3 · Week 5: Article Preview Submitted"
description: "The preliminary article version is in — title, authors, abstract, keywords, introduction, state of the art, system architecture, and references delivered by the 29 March deadline."
category: "Challenge 3"
pubDate: 2026-03-29
heroImage: "../../images/blog/challenge-3-week-5-1.jpeg"
---

## Week 5 Overview

**29 March 2026** — deadline day for the preliminary article version (feedback-only, no grade). Week 5 was the final integration and review sprint before submission.

The Tuesday session on **24 March** was the last collaborative writing session before cutoff.

![Working session — 24 March](../../images/blog/challenge-3-week-5-1.jpeg)

![Pre-submission review](../../images/blog/challenge-3-week-5-2.jpeg)

## What Was Submitted

| Section | Status |
|---|---|
| Title | ✓ |
| Authors (6) | ✓ Arsénio Ferraz, Mário João, César Vieira, Gonçalo Jesus, Rui Soares, Rynalde Silva Serejo |
| Abstract | ✓ |
| Keywords | ✓ |
| Introduction | ✓ |
| Related Work (9 subsections) | ✓ |
| System Architecture | ✓ |
| References | ✓ |

## Abstract

The submitted abstract reads:

> *This paper presents a cyber-physical surveillance system designed to monitor both digital and physical security layers. The system is composed of two independent modules. The first addresses anomaly detection in Windows endpoint logs by comparing a classical machine learning pipeline, based on Isolation Forest and a GRU autoencoder, against Dual Sentinel, a fully LLM-native approach that uses a small language model for first-pass triage and a larger model as a judge to validate findings and produce natural-language explanations mapped to MITRE ATT&CK techniques. The second module addresses physical access control through a face recognition pipeline built on deep embeddings and cosine similarity matching, following an open-set verification paradigm. Both modules are evaluated on public datasets. The comparison between classical and LLM-native detection explores the trade-off between raw performance and interpretability, a gap that remains underexplored in literature.*

## Keywords

`anomaly detection` · `Windows endpoint logs` · `Sysmon` · `large language models` · `small language models` · `LLM-as-a-Judge` · `MITRE ATT&CK` · `Isolation Forest` · `GRU autoencoder` · `face recognition` · `open-set verification` · `cyber-physical security`

## Related Work Highlights

Nine subsections cover the full literature foundation:

| Subsection | Key takeaways |
|---|---|
| Windows Telemetry & Log Sources | Sysmon/ETW as primary signals; Kellect for lossless collection; LMD-2023 as benchmark |
| Classical ML for Anomaly Detection | Extra Trees + Sysmon features: AUC >0.99; LOF+PCA: F1 >0.98; Isolation Forest as baseline |
| Sequence-Based & Autoencoders | SILRAD (ADWIN drift detection); GRU autoencoder one-class training; F1 >0.99 on ransomware |
| Provenance Graphs | ProGrapher, ORTHRUS — strong results but reproducibility concerns; motivates simpler log approach |
| LLMs for Cybersecurity | Phi-3 Mini (local SLM), Llama 3.2 (local LLM), direct MITRE ATT&CK mapping; run via Ollama |
| LLM-as-a-Judge | G-Eval rubric scoring; MT-Bench reliability; known biases in judge models |
| Hallucination & Prompt Injection | Fabricated ATT&CK identifiers; OWASP prompt injection taxonomy; evidence-grounding as mitigation |
| Deep Face Recognition | MTCNN alignment; ArcFace loss; ResNet-50 backbone; InsightFace buffalo\_sc |
| Open-Set Recognition & Anti-Spoofing | Scheirer et al. formalisation; cosine similarity thresholding; liveness detection gap acknowledged |

## System Architecture Summary

**Module 1 — Log Anomaly Detection**

```
Sysmon/ETW logs
        │
        ▼
  Feature windowing
   /           \
Isolation   GRU Autoencoder        ← Classical pipeline
Forest

        │
        ▼
  ATT&CK Rule Tagger + Evidence Pack
        │
  Phi-3 Mini (SLM Analyst)         ← Dual Sentinel
        │  hypothesis
  Llama 3.2 (LLM Judge)
        │  verdict + MITRE ATT&CK mapping + unsupported_claims
        ▼
   Final detection output
```

**Module 2 — Face Recognition**

```
Webcam frame
      │
  InsightFace RetinaFace (detect + align)
      │
  buffalo_sc ArcFace (512-d embedding)
      │
  Cosine similarity vs enrolled centroids (threshold 0.75)
      │
  GRANT / DENY + colour-coded bounding box
```

## Feedback Expected

The professors review structure and content; no grade is assigned. We expect feedback on:
- Narrowing the Related Work to closest prior work.
- Strengthening the motivation gap in the Introduction.
- Adding detail to the Experimental Setup (metrics for LLM output quality: explanation quality, evidence grounding rate, hallucination rate).

## Remaining Deliverables

| Deliverable | Deadline |
|---|---|
| Final article | 19 April 2026 |
| Solution implementation | 19 April 2026 |
| Demonstrations | 20 April 2026 |
| Pitch delivery | 20 April 2026 |
| **Demo Day** | **21 April 2026** |

With the preview submitted, the team now shifts focus to **implementation**: setting up the Sysmon log pipeline, running the classical models on LMD-2023, beginning Ollama integration, and training the face recognition models.

---

*Preliminary article: submitted. Implementation sprint begins now.*
