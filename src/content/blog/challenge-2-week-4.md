---
title: "Challenge 2 · Week 4: Refining Models and Optimization"
description: "Deepening our work on the Genetic Algorithm and fine-tuning our Machine Learning models for better accuracy."
category: "Challenge 2"
pubDate: 2025-12-13
heroImage: "../../images/blog/challenge-2-week-4.svg"
---

## Optimization and Tuning

This week was dedicated to the "grind"—refining the systems we started last week.

### Genetic Algorithm Improvements

We focused on the convergence speed of our Genetic Algorithm. By tweaking the mutation rates and experimenting with different selection strategies (e.g., tournament vs. roulette wheel), we are starting to see the algorithm find "good enough" schedules much faster.

We also added more realistic constraints to the problem, such as:

- **Dependency handling:** Ensuring patches that depend on others are scheduled in the correct order.
- **Resource limits:** Respecting the maximum number of patches a team can apply in a given window.

### ML Model Tuning

On the prediction side, we continued our work with LightGBM, XGBoost, Random Forest, and KNN.

- **Feature Selection:** We removed noisy features that were confusing the models.
- **Hyperparameter Tuning:** We used grid search and random search to find the optimal settings for our gradient boosting models.
- **Ensembling:** We are considering combining the outputs of multiple models to improve overall stability.

## Preparing for the Paper

As we approach the submission deadline, we are also starting to structure our findings. The results from these optimization runs will be crucial for the "Validation" section of our scientific paper.

## Next Steps

- Finalize the experimental results.
- Begin drafting the scientific paper.
- Prepare the final code submission.
