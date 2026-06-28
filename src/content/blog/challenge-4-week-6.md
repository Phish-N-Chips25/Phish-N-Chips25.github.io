---
title: "Challenge 4 - Week 6: From Navigation Agent to Multi-Agent System"
description: "This week connected PPO navigation to Webots and ROS 2, and introduced the first SentinelMAS agents for patrol dispatch and threat-driven decisions."
category: "Challenge 4"
pubDate: 2026-06-14
---

## Week 6 Overview

Week 6 was when the project stopped being only a reinforcement learning experiment and started becoming an integrated cyber-physical system.

The repository was reorganized into three large areas: the cyber-physical security system, SIMAGIA and the Booster T1 / Unitree G1 Webots stack. That separation made the project easier to reason about because each subsystem now had a clearer role.

## Webots and ROS 2 Structure

The first Webots office world entered the project during this week. It introduced the simulated workspace, patrol zones, Booster T1 assets and the first ROS 2-oriented structure for controlling the robot.

This mattered because the PPO policy needed a realistic place to operate. A patrol agent is only useful if it can be tested against zones, routes and physical constraints that resemble the final demonstration scenario.

The robotics work included:

- First office worlds in Webots.
- Zone definitions for patrol targets.
- Booster T1 assets for the simulated robot stack.
- ROS 2 structure for future robot integration.
- Early links between the navigation policy and the simulation layer.

## SentinelMAS Appears

The other major change was the introduction of SentinelMAS as the decision layer. Instead of sending the robot through fixed routes, the system began to model patrol as a coordination problem.

Several agents were added or sketched during this phase:

| Agent | Role |
|---|---|
| PatrolAgent | Executes patrol decisions and robot movement requests. |
| ZoneCoordinator | Manages zones and patrol priorities. |
| ThreatFusion | Combines physical and cyber events into threat context. |
| Reactive agents | Respond when new events appear during a mission. |

The core idea was that the robot should not simply follow a route. It should be dispatched according to the current security context.

## Auctions for Patrol Dispatch

This week also introduced the use of auctions, inspired by Contract Net style coordination. When the system needs to decide where the robot should go, agents can evaluate zones and priorities instead of relying on a hardcoded sequence.

That makes the robot more useful in a security scenario. If a new event appears while the mission is running, the patrol can change direction and move toward the area that currently matters most.

## PPO as a Navigation Layer

The PPO work continued, but its role changed. It was no longer only a standalone training experiment. It started becoming the navigation layer that SentinelMAS could call once a decision had already been made, and the first bridge toward the future Booster T1 integration.

That distinction became important for the rest of the challenge:

1. SentinelMAS decides the target.
2. PPO helps the robot navigate.
3. Webots and ROS 2 provide the simulated execution environment.

## Next Steps

The next step is to validate whether the PPO policy can reliably reach the office zones. Week 7 will focus less on adding new components and more on training, testing and understanding the limitations of the first navigation baseline.

---

*This week gave the project its coordination layer: the robot no longer just moves, it moves because the system has a reason to send it somewhere.*
