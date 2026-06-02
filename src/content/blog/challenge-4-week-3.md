---
title: "Challenge 4 - Week 3: Designing the Autonomous Surveillance Architecture"
description: "The architecture now connects cyber analysis, identity verification, robot perception, navigation and a BDI multi-agent decision layer."
category: "Challenge 4"
pubDate: 2026-05-31
---

## Week 3 Overview

Week 3 was about turning the state-of-the-art findings into a concrete system architecture.

The project is now framed as an autonomous surveillance robot that combines cyber threat intelligence and physical security monitoring within a single decision-making framework.

## Unified Security Platform

The platform integrates two previously validated AI-based security modules.

### Dual Sentinel - Cyber Threat Detection

Dual Sentinel analyzes Windows endpoint telemetry using Large Language Models and an LLM-as-a-Judge architecture.

Instead of producing only a score, it generates human-readable security assessments and maps suspicious activity to MITRE ATT&CK techniques. This gives analysts more context than a black-box alert.

### Open-Set Face Recognition

The physical security component uses ArcFace embeddings and cosine similarity matching to identify authorized individuals while detecting unknown persons.

Unlike a closed-set classifier, this approach supports dynamic enrolment and can reject identities that are not present in the authorized database.

## Bringing AI to the Physical World

The independent modules are being integrated into a robotic platform with the following capabilities:

- Autonomous navigation using ROS 2 and Nav2.
- Real-time object detection using YOLOv8.
- Face recognition and identity verification.
- Continuous environmental monitoring.
- Cybersecurity telemetry analysis running locally.

The intention is to create a platform that can observe both the digital and physical environments at the same time.

## Multi-Agent Intelligence

The decision layer is based on a Belief-Desire-Intention multi-agent system implemented with SPADE and FIPA-ACL.

The current design includes six specialized agents:

| Agent | Function |
|---|---|
| Perception Agent | Collects and distributes information from sensors and cybersecurity telemetry. |
| Cyber Sentinel Agent | Evaluates cyber threat intelligence and generates security alerts. |
| Physical Sentinel Agent | Manages identity verification and physical access control decisions. |
| Navigation Agent | Controls autonomous movement and patrol execution. |
| Coordinator Agent | Correlates information from all agents and defines response strategies. |
| Operator Agent | Provides human-readable summaries and escalation reports. |

## Demonstration Scenario

The main scenario is a coordinated incident:

1. The cybersecurity module detects suspicious activity on a server in a restricted area.
2. The robot identifies an unknown individual approaching the same area.
3. The Coordinator Agent correlates both events.
4. The robot elevates the security posture and changes patrol priority.
5. Operators receive a summary explaining the cyber event, the physical anomaly and the action taken.

This scenario helps demonstrate why the project should not treat cyber and physical incidents as separate problems.

## Next Steps

The next milestone is the delivery of the state-of-the-art document. We will focus on tightening the academic writing, linking each technology choice to the literature and clarifying evaluation criteria for the proof of concept.

---

*The architecture is now stable enough to support both the written report and the implementation plan.*
