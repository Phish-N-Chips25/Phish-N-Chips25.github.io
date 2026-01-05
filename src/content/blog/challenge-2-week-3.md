---
title: "Challenge 2 · Week 3: Genetic Algorithms and Model Training"
description: "Kicking off the implementation of the Genetic Algorithm for scheduling and training our first batch of ML models."
category: "Challenge 2"
pubDate: 2025-12-06
heroImage: "../../images/blog/challenge-2-week-3.svg"
---

## Building the Planner

This week, we moved from theory to code. The core of our solution involves a **Genetic Algorithm (GA)** designed to optimize the patch management schedule.

We started implementing the GA with the following components:
- **Chromosome Representation:** How we encode a potential patch schedule.
- **Fitness Function:** A metric that balances risk reduction against operational costs (e.g., downtime).
- **Selection, Crossover, and Mutation:** The evolutionary operators that will help us find better schedules over generations.

## Training the Risk Models

In parallel with the planning module, we began training Machine Learning models to predict vulnerability risk. We want to classify or score vulnerabilities based on their likelihood of exploitation.

We experimented with several algorithms to establish a baseline:

1.  **LightGBM:** Known for its speed and efficiency with large datasets.
2.  **XGBoost:** A powerful gradient boosting library that often performs well on structured data.
3.  **Random Forest:** A robust ensemble method that helps prevent overfitting.
4.  **KNN (K-Nearest Neighbors):** A simpler instance-based learning approach for comparison.

## Early Results

Initial training runs are promising, but we are seeing the need for careful feature engineering. The raw CVE data needs to be transformed into meaningful numerical features for the models to learn effectively.

## Next Week's Goals

- Continue refining the Genetic Algorithm parameters.
- Perform hyperparameter tuning on the best-performing ML models.
- Integrate the risk predictions into the fitness function of the GA.
