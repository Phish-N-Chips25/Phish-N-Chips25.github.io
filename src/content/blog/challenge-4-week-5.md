---
title: "Challenge 4 - Week 5: Building the SentinelMAS Foundation"
description: "The first week of implementation established the technical base for SentinelMAS: Python, Docker, PPO training files and the first autonomous patrol environment."
category: "Challenge 4"
pubDate: 2026-06-07
---

## Week 5 Overview

After the state-of-the-art delivery, Challenge 4 moved from writing into building. This first implementation week was mostly about foundations.

Before connecting perception, decision-making and robotics, we needed a reproducible base where an autonomous patrol agent could be trained and tested.

The project started from a simple technical objective: **train an agent capable of navigating an office-like environment**. That first target shaped the structure of the work for the rest of the month.

## Reinforcement Learning Baseline

The first major block was the reinforcement learning setup. We created the initial Python environment, Docker configuration, PPO training files and the first project modules of the cyber-physical security system.

At this stage, the system was not yet a complete SentinelMAS pipeline. It was closer to a controlled navigation experiment, but an important one: if the robot could not move reliably, the later security logic would have nowhere useful to act.

The work this week focused on:

- Creating the base project structure.
- Configuring a reproducible training environment.
- Adding the first reinforcement learning scripts.
- Defining PPO as the first navigation strategy.
- Preparing the system for autonomous patrol in simulation.

## Why PPO

PPO was selected as the first navigation approach because it offers a practical balance between training stability and implementation speed. The goal was not to prove that PPO is the only possible choice, but to build a policy that could learn patrol behavior in a repeatable simulated environment.

## Why Docker

Docker mattered from the beginning because the project combines Python, simulation, robotics tooling and, later, ROS 2 components. Keeping training, testing and execution reproducible avoids the classic problem of a system that only runs on one machine.

## Technical Direction

The most important result of this week was not a final model. It was the direction of the architecture.

The system would grow from a navigation baseline into a cyber-physical platform where a robot can receive mission priorities, move through an environment and eventually react to security events.

## Next Steps

With the first PPO environment in place, the next goal is to stop treating the robot as an isolated learner. The project needs a decision layer that can choose where the robot should go and why.

The next week will focus on reorganizing the repository, introducing the first Webots world and connecting navigation to a multi-agent security architecture.

---

*This week gave SentinelMAS its first moving part: a patrol agent that could start learning how to navigate.*
