---
title: "Challenge 2 · Week 1: Reframing the Problem and Hunting for Data"
description: "Kicking off the planning & decision-making challenge by defining the ML problem, aligning objectives between PLNTDIA and AAUTIA, and scouting datasets."
category: "Challenge 2"
pubDate: 2025-11-22
heroImage: "../../images/blog/challenge-2-week-1.svg"
---
## Why Challenge 2 Feels Different

Challenge 1 was all about symbolic reasoning and knowledge acquisition. Challenge 2—shared between **PLNTDIA** (Planeamento e Tomada de Decisão) and **AAUTIA**—raises the stakes: we must **use machine learning for planning and decision support**. That means understanding not only *what* we want to predict, but also *how* those predictions influence real decisions.

### Shared Objectives

- **PLNTDIA focus**: internalize Automatic Problem Solving, Search/Optimization, Game Theory, Planning, and Decision Making.
- **AAUTIA focus**: deliver collaborative ML work—framing the problem, building the model, writing a paper, and preparing a Demo Day pitch.
- **Challenges4Teams core**: strengthen teamwork while solving a complex, realistic problem.

## Step 1 · Re-asking “What is Machine Learning?”

The professors challenged us to revisit the fundamentals:

1. **Discuss the definition**: we mapped the classic ML pipeline (data ➜ features ➜ model ➜ decision).
2. **Map applications**: for our cybersecurity theme, we compared URL classification, anomaly detection in network telemetry, and resource planning for incident response.
3. **Narrow the problem**: we converged on a planning scenario where ML scores links/emails, feeding a decision layer that recommends analyst actions (auto-block vs. manual review).

## Step 2 · Datasets Before Models

Before writing a single line of model code, the instructors emphasized that **data quality defines success**.

### Our Data Strategy

- **Combine sources**: we plan to merge phishing URL datasets (Kaggle) with benign corporate traffic samples (EU Open Data, Zenodo) to avoid bias.
- **Normalize formats**: every raw source—CSV, JSON, PCAP summaries—needs to become a **tabular view** with consistent features (e.g., domain age, lexical entropy, TLS signals).
- **Clean aggressively**: we drafted a checklist for handling missing values, removing duplicate URLs, and flagging outliers (e.g., extremely long query strings).

### Repositories in Focus

- [EU Open Data Portal](https://data.europa.eu/): regulatory reports and telecom stats.
- [Zenodo](https://zenodo.org/): research datasets on phishing and fraud.
- [IEEE DataPort](https://ieee-dataport.org/): curated cybersecurity telemetry dumps.
- [Kaggle](https://www.kaggle.com/): varied phishing URL corpora with community baselines.
- [Awesome Public Datasets](https://github.com/awesomedata/awesome-public-datasets): to discover niche security collections.

## Step 3 · Planning Milestones

| Track | Week 1 Outcome |
| --- | --- |
| **Problem definition** | Drafted the ML problem statement: predict risk scores for links to aid planning decisions. |
| **Data management** | Built a shared spreadsheet that logs every dataset, licensing terms, preprocessing needs, and potential biases. |
| **Team sync** | Scheduled alternating PLNTDIA/AAUTIA working sessions so both courses see the same artefacts. |
| **Research** | Gathered reference papers on combining ML predictions with optimization heuristics. |

## Early Insights

1. **Planning + ML requires interfaces**: the model output must plug into a decision policy—nothing lives in isolation.
2. **Data provenance matters**: mixing multiple sources adds coverage but also demands detailed documentation for reproducibility.
3. **Theory underpins practice**: game-theory scenarios from PLNTDIA may influence how we evaluate false positives vs. false negatives.
4. **Team rituals**: challenge reviews every Friday keep PLNTDIA and AAUTIA deliverables aligned.

## Next Week’s Focus

- Finalize the shortlist of datasets and start exploratory data analysis (EDA).
- Prototype a feature-extraction notebook that converts raw URLs/logs into tabular vectors.
- Draft the outline for the scientific paper (introduction + related work).
- Define success metrics that reflect decision support (e.g., cost-aware accuracy rather than pure precision).

---

*Challenge 2 officially began with intentional questions and disciplined data gathering. Week 2 will be about turning those raw assets into structured knowledge the model can learn from.*
