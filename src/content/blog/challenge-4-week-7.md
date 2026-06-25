---
title: "Challenge 4 - Week 7: Training and Validating PPO Navigation"
description: "This week focused on the first complete PPO policy for the office layout, its baseline results and the limitations found during validation."
category: "Challenge 4"
pubDate: 2026-06-21
---

## Week 7 Overview

Week 7 was quieter in terms of visible integration work, but it was important for maturing the navigation layer.

The main outcome was the first fully trained PPO policy for the office environment. This model became the baseline v1 for the SentinelMAS patrol scenario.

## Baseline v1

The policy was trained for the `sentinelmas_office.wbt` layout and reached a strong first result: in validation tests with random initial positions, the agent reached all 8 office zones.

That result matters because the rest of the system depends on navigation being dependable. SentinelMAS can make the correct dispatch decision, but the robot still needs to physically reach the target area.

The final baseline included:

- A PPO policy trained for the office patrol layout.
- 2 million timesteps in the final training run.
- 100% zone arrival in baseline validation.
- Randomized initial positions during testing.
- Trajectory checks for patrol behavior.

## What Worked

The model proved that PPO could learn the basic patrol task. It could receive a target zone, move through the office layout and reach the requested destination with enough consistency to support the next integration stage.

This also validated the early decision to keep the navigation layer separate from the multi-agent logic. SentinelMAS does not need to know every low-level movement detail; it needs a navigation component that can accept a target and execute the mission.

## What Did Not Work Yet

The baseline also exposed limitations.

The first policy used a 10-D observation that included absolute position information. That made it effective for the current layout, but too dependent on the exact geometry of the office. If the map changes significantly, the same policy may not generalize well.

The trajectories could also become somewhat oscillatory. Reaching the target is not the only requirement for a patrol robot; the path should also be safe, smooth and aware of walls or obstacles.

## Design Consequences

These limitations shaped the next technical step. Instead of treating the first model as final, the navigation system needed a more layout-aware structure.

The conclusion was that PPO should be combined with explicit map validation and planning support. A learned policy can drive movement, but it should not be allowed to blindly choose unsafe waypoints or cut through walls. This analysis motivated a later redesign toward a more layout-agnostic policy.

## Next Steps

Week 8 will connect this navigation baseline to the rest of the stack. The goal is to move from a trained model to a full pipeline where SentinelMAS decides, navigation plans, and the simulated robot executes.

---

*This week showed that the robot could learn to reach the office zones, and also made clear why safe navigation needs more than a successful reward curve.*
