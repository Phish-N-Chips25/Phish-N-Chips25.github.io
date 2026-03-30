---
title: "Challenge 3 · Week 4: System Architecture and Article Draft"
description: "Designing Dual Sentinel and the face recognition pipeline in full detail, and assembling the article draft ahead of the 29 March preliminary submission."
category: "Challenge 3"
pubDate: 2026-03-22
heroImage: "../../images/blog/challenge-3-week-4-1.jpeg"
---

## Week 4 Overview

One week from the article preview deadline. Week 4 was a high-intensity sprint to translate the literature into a concrete architecture and get every article section into a reviewable state.

The Tuesday session on **17 March** brought the full team together for a concentrated design and writing block.

![Team session — 17 March](../../images/blog/challenge-3-week-4-1.jpeg)

![Architecture discussion](../../images/blog/challenge-3-week-4-2.jpeg)

![Reviewing drafts at the table](../../images/blog/challenge-3-week-4-3.jpeg)

## Module 1: Classical Anomaly Detection Pipeline

The classical side of the log anomaly detection module processes Sysmon events through a structured feature extraction pipeline feeding two independent models:

- **Isolation Forest** — unsupervised one-class detector. Trained exclusively on normal baseline logs; anomalies are identified by isolation depth. No labels required at training time.
- **GRU Autoencoder** — sequence model trained on normal event windows. Anomalies surface as high reconstruction error. Captures temporal patterns that stateless feature-based classifiers miss.

Both models receive the same fixed-window feature representation derived from aggregate statistics (event counts, unique processes, entropy values, network connection counts) computed over sliding Sysmon log windows.

## Module 1: Dual Sentinel — LLM-Native Pipeline

Dual Sentinel is the centrepiece of the project. It processes the same windowed Sysmon logs through a sequential **analyst–judge** configuration, running entirely on-premise via Ollama.

### Evidence Pack

Each log window is first represented as a structured **Evidence Pack** — the only input either model ever sees:

- Aggregate statistics (event counts, unique processes, entropy, network connections)
- **ATT&CK rule tagger** hits: twelve hand-coded conditions for indicators like PowerShell execution, lateral movement port activity, and process injection, each mapped to a specific technique identifier (e.g., T1059.001, T1021.002, T1055)
- A representative sample of raw event lines (up to 15, 30, or 50 lines depending on window density)

Command-line strings are truncated to 120 characters and code fences are sanitised to mitigate prompt injection. The pack contains **no interpretive content** — each model reasons only from observable facts.

### SLM Analyst (Phi-3 Mini)

Microsoft's Phi-3 Mini (~4B parameters) performs rapid first-pass triage:

- Identifies visible risk indicators in the Evidence Pack
- Suggests potential ATT&CK techniques
- Assigns a preliminary risk score on a **0–10 integer scale**
- Flags whether the window warrants deeper analysis by the Judge

A **deterministic pre-filter** runs before any model call: windows with zero threat signals (no suspicious processes, no shell activity, no tool indicators, no ATT&CK rule hits, fewer than five network connections) bypass the model entirely with a pre-score of zero. On the LMD-2023 normal baseline, this eliminated 35% of windows, significantly reducing inference cost.

### LLM Judge (Llama 3.2)

Meta's Llama 3.2 (~8B parameters) receives both the Evidence Pack **and** the Analyst's pre-diagnosis — explicitly framed as a **hypothesis to validate**, not an established fact:

- Must cite a specific event or statistic from the Evidence Pack for every ATT&CK technique it reports
- Applies a defined scoring rubric: 0–2 (benign), 3–4 (mildly suspicious), 5–6 (moderate, lateral movement indicators), 7–8 (highly suspicious, confirmed Mimikatz/PsExec), 9–10 (critical, multiple corroborated techniques)
- Reports any Analyst claims it could not substantiate in a dedicated `unsupported_claims` field

A cap of 50 windows is submitted to the Judge stage, selected by descending Analyst pre-score.

### Hallucination Mitigation

Five complementary mechanisms:

1. Evidence Pack contains only verifiable observations — no interpretive content to distort.
2. Both system prompts explicitly prohibit fabricating process names, IPs, or file paths not present in the pack.
3. JSON-only output enforced at the Ollama API level, with a three-step fallback parser (direct parse → markdown fence stripping → regex brace matching).
4. Analyst output is labelled as a hypothesis in the Judge's prompt.
5. The `unsupported_claims` field creates a traceable disagreement log between the two models.

## Module 2: Face Recognition Pipeline

### Closed-Set Training Pipeline

Fine-tunes a deep model on authorised individuals and classifies via softmax. Training data: **VGGFace2**, 15,236 images across 50 identities (70/15/15 split). MTCNN performs face detection and alignment to 192×192 pixels with IQR-based outlier removal.

Two architectures compared:

| Model | Architecture | Embedding size |
|---|---|---|
| FaceCNN | 4-block Conv→BatchNorm→ReLU→MaxPool | 512-d |
| ResNet50Face | ResNet-50 backbone + linear projection | 512-d (from 2,048-d) |

Training: 30 epochs, Adam (lr=10⁻³, weight decay=10⁻⁴), cosine annealing, mixed-precision. Both are then fine-tuned on organisation-specific photos (~20 augmentation variants per image) for 30 additional epochs.

### Open-Set Real-Time Pipeline

Uses InsightFace's pre-trained `buffalo_sc` ArcFace model via ONNXRuntime. Enrollment is directory-based: reference images loaded at startup, embeddings extracted per image plus horizontal flip, single L2-normalised centroid computed per identity.

At inference, each webcam frame's embedding is compared against all centroids via **cosine similarity**. Default threshold: **0.75** (adjustable at runtime). Decisions displayed via colour-coded bounding boxes overlaid on the video feed.

### Why Compare Both?

| Factor | Closed-set | Open-set |
|---|---|---|
| Retraining on new identity | Required | Not needed |
| Unknown rejection | No natural boundary | Threshold-based |
| Hardware | GPU preferred | CPU-only viable |
| Dynamic enrollment | Hard | Native |

## Article Status

| Section | Status |
|---|---|
| Title + authors | Done |
| Abstract | Draft ready |
| Keywords | Done |
| Introduction | In review |
| Related Work (9 subsections) | First draft complete |
| System Architecture | In progress |
| Experimental Setup | Skeleton only |
| References | ~80% complete |

## Next Steps

- Integrate all sections into a single document.
- Peer-review round across the full team.
- Submit preliminary article by **29 March**.

---

*Architecture frozen, article sections assembling. One week to the preview deadline.*
