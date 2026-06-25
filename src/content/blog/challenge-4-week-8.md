---
title: "Challenge 4 - Week 8: Integrating Face ID, MAS, PPO and Booster T1"
description: "The final week connected perception, decision-making, PPO navigation, A* planning and the Booster T1 Webots stack into one delivery pipeline."
category: "Challenge 4"
pubDate: 2026-06-25
---

## Week 8 Overview

Week 8 was the integration week. The project moved from separate working parts into a single cyber-physical pipeline for the Challenge 4 delivery.

By this point, the goal was clear: SentinelMAS should detect or receive security events, decide which zone matters most, plan a safe patrol route and send the simulated Booster T1 toward the target in Webots.

## PPO and A* Navigation

The first major integration connected reinforcement learning with SIMAGIA through the navigation bridge.

The navigation layer is now described as PPO + A*. PPO provides the learned movement behavior, while A* and map validation help keep the patrol route safe. This avoids treating the learned policy as an unchecked black box.

The navigation work included:

- `nav_bridge` integration with SIMAGIA.
- A* planning support.
- Map validation against walls and unsafe paths.
- Safe waypoint generation.
- Live demo and model evaluation scripts.
- Synchronization with the Webots office world.

This made the week 7 lesson concrete: reaching a target is useful, but safe patrol behavior needs explicit validation.

## Face Recognition Enters the Pipeline

The next integration step connected face recognition to SentinelMAS.

The InsightFace prototype in `alt1.py` was linked through `face_bridge.py`, allowing the system to distinguish known people from intruders. More importantly, those detections stopped being isolated perception results. They became security events that the multi-agent system could reason about.

The flow became:

1. The camera detects a face.
2. InsightFace compares it against known identities.
3. An unknown person is classified as a possible intruder.
4. `face_bridge.py` sends the event into SentinelMAS.
5. ThreatFusion and the other agents turn it into a patrol priority.

In practice, this means an intruder detection can become a dispatch decision: intruder to threat, threat to auction, auction to robot mission.

## SIMAGIA to Booster T1 Bridge

The Booster T1 integration was also consolidated this week. SIMAGIA writes missions in JSONL, and the robot-side stack reads those missions to execute patrol behavior in Webots.

The Booster stack now includes the supporting pieces needed for a repeatable demonstration:

- Docker and Webots scripts.
- ROS 2 launch structure.
- Windows and WSL helper scripts.
- Simulated odometry.
- Simulated lidar.
- Patrol node.
- Mission bridge.
- Tests for the robot-side integration.

This created a clean boundary between decision-making and robot execution. SIMAGIA decides what should happen, and the robot stack focuses on carrying out the mission.

## PPO Driving the Booster

The strongest milestone was the second part of the integration: the PPO policy can now drive the Booster T1 through `ppo_patrol_node.py`.

The final pipeline can be summarized as:

| Layer | Responsibility |
|---|---|
| SIMAGIA / SentinelMAS | Decide patrol priorities from threats and agent coordination. |
| PPO + A* | Plan and navigate through safe waypoints. |
| ROS 2 | Send movement commands to the robot stack. |
| Booster T1 in Webots | Execute and render the patrol in simulation. |

This is the point where the project becomes a complete cyber-physical demonstration instead of a collection of separate prototypes.

## Delivery State

The delivery state is strong for the project narrative. The full Python pipeline works, the Booster renders and integrates in Webots, and the system has a clear path from perception to decision to navigation. The final documentation was consolidated in the project README, the full-stack run guide and the handoff notes.

The main remaining limitation is not in the SentinelMAS logic itself. Real physical locomotion still depends on proprietary vendor configuration and calibration under `/opt/booster`. Until that part is available, the reliable demonstration target remains the integrated Webots simulation.

## Challenge 4 Summary

During June, Challenge 4 evolved from a reinforcement learning navigation baseline into an integrated autonomous security system.

First, we taught the robot to navigate. Then we gave the system agents that could decide where the robot should go. After that, we validated the navigation baseline and found its limits. Finally, we connected perception, threat fusion, auctions, PPO navigation, ROS 2 and Booster T1 simulation into one delivery pipeline.

---

*The final result is a working cyber-physical pipeline: perception informs agents, agents dispatch the robot, navigation plans the route, and the Booster T1 acts inside Webots.*
