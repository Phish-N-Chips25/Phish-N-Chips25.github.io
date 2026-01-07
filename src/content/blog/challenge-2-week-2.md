---
title: "Challenge 2 · Week 2: Pivoting to Patch Management"
description: "A strategic pivot in our project direction: focusing on Vulnerability Risk Prediction and Enterprise Patch Management."
category: "Challenge 2"
pubDate: 2025-11-29
heroImage: "../../images/blog/challenge-2-week-2.svg"
---

## A Strategic Pivot

This week marked a significant turning point for our team. After evaluating our initial direction, we decided to pivot our theme to a more impactful and data-rich area: **Integrating EPSS-Based Vulnerability Risk Prediction with Genetic-Algorithm Scheduling for Enterprise Patch Management**.

This shift allows us to tackle a critical problem in cybersecurity: the overwhelming volume of vulnerabilities (CVEs) that organizations face and the limited resources available to patch them.

## The New Focus: EPSS and Patch Management

Our new objective is to build a system that not only predicts the risk associated with specific vulnerabilities but also optimizes the schedule for applying patches.

### Key Concepts

- **EPSS (Exploit Prediction Scoring System):** We are leveraging EPSS scores to estimate the probability that a vulnerability will be exploited in the wild.
- **Genetic Algorithms:** We plan to use evolutionary algorithms to solve the scheduling problem—finding the optimal order to apply patches given constraints like server downtime, team availability, and risk reduction.

## Hunting for New Data

With the change in topic came the need for new datasets. We spent a significant portion of the week scouting for high-quality data sources:

1. **NVD (National Vulnerability Database):** For core CVE details.
2. **EPSS Data:** Historical and current scores to train our risk models.
3. **CISA KEV (Known Exploited Vulnerabilities):** To validate our risk predictions against ground truth.

We are now in the process of cleaning and merging these datasets to create a unified view of vulnerability risk.

## Next Steps

- Finalize the dataset schema.
- Begin the implementation of the Genetic Algorithm for the scheduling component.
- Start preliminary model training for risk prediction.
