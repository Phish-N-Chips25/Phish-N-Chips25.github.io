---
title: "Challenge 4 - Week 1: Defining the Cyber-Physical Security Problem"
description: "The new trimester begins with a clearer research direction: integrate cybersecurity monitoring, physical security and autonomous robotics into one coordinated platform."
category: "Challenge 4"
pubDate: 2026-05-17
---

## Week 1 Overview

Challenge 4 started after the second weekend of May. We used the first week to reset the project narrative and define the technical problem we want to address this trimester.

The central question is simple: **how can an autonomous robot support security teams when cyber alerts and physical events may be related?**

Traditional security operations usually separate these domains. A Security Operations Center studies endpoint logs, alerts and attack techniques, while physical security teams monitor cameras, restricted areas and access control. Our work explores a unified approach where both sources of information can influence the same response strategy.

## Research Direction

The proposed system connects three major areas:

| Area | Role in the project |
|---|---|
| Cybersecurity monitoring | Analyze endpoint telemetry and identify suspicious activity. |
| Physical security | Verify identities, detect unknown people and observe restricted spaces. |
| Autonomous robotics | Move through the environment, patrol relevant areas and react to alerts. |

This week we focused on turning the idea into a research problem with clear boundaries. The goal is not only to build isolated modules, but to define an architecture that allows them to cooperate.

## Initial Architecture

The first version of the architecture combines two validated AI-based components from previous work:

- **Dual Sentinel**, focused on Windows endpoint telemetry analysis using LLM-based reasoning and MITRE ATT&CK mapping.
- **Open-set face recognition**, based on ArcFace embeddings and cosine similarity matching, capable of identifying authorized users while rejecting unknown people.

These modules will be connected to a mobile robot capable of navigation, object detection and local decision support.

## Key Decisions

Several project decisions were clarified during the week:

- Use **ROS 2** and **Nav2** for autonomous navigation.
- Use **Webots** as the simulation environment before considering physical deployment.
- Keep cybersecurity analysis local whenever possible, using **Ollama** and small language models.
- Structure the decision layer as a **multi-agent system** instead of a single monolithic controller.

## Next Steps

The immediate priority is to organize the literature review and begin the state-of-the-art document. The next post will focus on the technical baseline, related work and how we are positioning the project academically.

---

*Challenge 4 begins with one guiding idea: security systems should reason across both digital and physical evidence.*
