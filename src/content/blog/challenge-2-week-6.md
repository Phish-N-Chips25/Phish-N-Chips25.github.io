---
title: "Challenge 2 · Week 6: Post-Break Reviews & Refinements"
description: "Returning from the Christmas break to present our progress to Professors Diogo and Vitorino, and refining our models based on their feedback."
category: "Challenge 2"
pubDate: 2026-01-05
heroImage: "../../images/blog/challenge-2-week-6.svg"
---

## Back to Work

After the Christmas break, we returned with renewed energy to tackle the final stretch of Challenge 2. This week was crucial for validating our progress with the professors and identifying the final adjustments needed before the Demo Day.

## Planning Project Review (Prof. Diogo)

Our first major milestone of the week was presenting the **Planning** component to Professor Diogo. We showcased our **Genetic Algorithm (GA)** implementation for patch scheduling.

### Key Discussion Points

- **Constraint Handling:** We demonstrated how our GA respects team availability and patch dependencies.
- **Fitness Function:** We explained how we balance risk reduction (from our ML models) with operational costs.
- **Feedback:** The feedback was positive, with suggestions to further tune the mutation operators to avoid getting stuck in local optima.

## Dataset Training Review (Prof. Vitorino)

Later in the week, we presented the **Machine Learning** component to Professor Vitorino. We detailed our pipeline for predicting vulnerability risk using EPSS and CVE data.

### Key Discussion Points

- **Model Comparison:** We presented the performance metrics (Accuracy, F1-Score, ROC-AUC) of our LightGBM, XGBoost, Random Forest, and KNN models.
- **Feature Engineering:** We discussed the impact of the features we engineered from the raw NVD data.
- **Feedback:** Professor Vitorino emphasized the importance of explainability—understanding *why* a model classifies a vulnerability as high risk.

## Refinements and Improvements

The rest of the week was dedicated to implementing the feedback received:

- **GA Tuning:** We adjusted the selection pressure and crossover rates in our Genetic Algorithm.
- **Model Optimization:** We revisited our hyperparameter tuning scripts to squeeze out a bit more performance from our best models.
- **Integration:** We ensured that the interface between the risk prediction module and the scheduling module is robust and seamless.

## Looking Ahead

With the technical validation largely behind us, our focus shifts to the final deliverables. Next week is all about the paper and the pitch!
