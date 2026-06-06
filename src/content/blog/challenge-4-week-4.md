---
title: "Challenge 4 - Week 4: Preparing the State-of-the-Art Delivery"
description: "The current focus is the state-of-the-art report, due next Sunday, while the technical proposal is being refined around cyber-physical event correlation."
category: "Challenge 4"
pubDate: 2026-06-02
---

## Week 4 Overview

The state-of-the-art document must be delivered next Sunday, so this week is focused on writing, reviewing and connecting the technical proposal to the literature.

At this stage, the project is no longer only a set of interesting components. The challenge is to explain why the integration matters and how the proposed architecture advances the current state of cyber-physical security monitoring.

## Research Positioning

Modern security threats do not always respect the boundary between digital and physical systems. An attacker who compromises a workstation may also attempt to access restricted facilities, and traditional tools often struggle to correlate those events in real time.

Most organizations still operate cybersecurity monitoring and physical access control as independent systems. Security Operations Centers analyze logs and alerts, while physical security teams manage cameras and access control systems.

Our work explores a different approach: an autonomous surveillance robot capable of combining cyber threat intelligence and physical security monitoring in one decision-making framework.

## Technology Stack

The proposed solution combines several technologies:

- Python.
- ROS 2.
- Nav2.
- SPADE.
- FIPA-ACL.
- YOLOv8.
- ArcFace.
- InsightFace.
- Ollama.
- Phi-3.
- Llama 3.2.
- SQLite.
- Webots Simulator.

This stack supports both simulation and future deployment on a physical robotic platform.

## Why This Matters

The most significant contribution of this work is not a new detection algorithm. The contribution is the integration framework.

By combining cybersecurity monitoring, physical security monitoring, autonomous robotics, multi-agent reasoning and Large Language Models, the platform demonstrates how future security systems can move beyond isolated alerts.

The target result is an autonomous decision-support system capable of understanding complex situations across multiple domains and escalating them to human operators with clear explanations.

## Current Writing Tasks

For the state-of-the-art delivery, we are working on:

- Describing the gap between cyber-only and physical-only monitoring systems.
- Comparing open-set face recognition approaches for security applications.
- Reviewing autonomous patrol robots and simulation environments.
- Explaining why a BDI multi-agent system is suitable for coordination.
- Defining evaluation dimensions such as response latency, detection effectiveness and false-positive interaction between domains.

## Looking Ahead

After the state-of-the-art delivery, the work will move toward implementation and validation of the proof of concept.

Future evaluation will consider:

- Response latency.
- Detection effectiveness.
- False-positive interactions between domains.
- Patrol optimization strategies.
- Real-world deployment scenarios.
- Anti-spoofing improvements for face recognition.

The long-term vision is a fully autonomous security platform capable of acting as an intelligent patrol agent, continuously correlating cyber and physical events and supporting security teams with faster, more informed decisions.

---

*This week is about making the research argument strong enough before the implementation work accelerates.*
