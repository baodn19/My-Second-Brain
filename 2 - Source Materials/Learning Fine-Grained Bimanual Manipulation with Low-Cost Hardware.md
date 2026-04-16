---
categories:
  - "[[Research Literatures]]"
created: April 11th 2026
modified: April 16th 2026, 2:51:34 pm
reference note:
  - "[[zhaoLearningFineGrainedBimanual2023]]"
pass:
  - first
tags:
year:
---
# 1st Pass: Extract information into headings: research question, problems solved, contributions, methodologies, and limitations
## Research question
- The primary research question is whether learning can enable low-cost and imprecise hardware to perform fine manipulation tasks.
## Problems
- Robotic fine manipulation requires precision, contact force coordination, and closed-loop visual feedback.
- Existing systems typically rely on high-end robots and sensors that are expensive and difficult to set up.
- Imitation learning in high-precision domains is degraded by compounding errors over time.
- Human demonstrations often exhibit non-stationary behaviors, complicating the imitation process.
- Single-step policies fail to handle temporally correlated confounders, such as pauses during demonstrations.
## Contributions
- The researchers developed ALOHA, a low-cost teleoperation system for learning fine bimanual manipulation.
- The ALOHA system costs less than $20,000 by utilizing off-the-shelf robots and 3D-printed components.
- The paper introduces Action Chunking with Transformers (ACT), a novel imitation learning algorithm that generates models over action sequences.
- ACT enabled the robot to learn six real-world tasks with 80% to 90% success rates using approximately 10 minutes of demonstration data.
- The hardware designs and software were open-sourced alongside detailed assembly tutorials.

## Limitations
- The ALOHA hardware cannot execute tasks requiring multiple fingers on a single hand, such as opening a child-proof pill bottle.
- The low-cost motors cannot generate the torque needed for high-force applications like lifting heavy objects or opening tightly sealed caps.
- The grippers cannot perform actions requiring fingernails, such as lifting the edge of packing tape or opening aluminum soda cans.
- The ACT policy failed to unwrap candies because the wrapper seam was too difficult for the perception system to locate.
- The ACT policy struggled to open a small ziploc bag lying flat on a table due to unpredictable bag deformation and visual perception challenges.

# 2nd pass
## Methodology
- **Hardware (ALOHA):** The system uses direct joint-space mapping to synchronize smaller leader robots with larger follower robots.
- **Hardware (ALOHA):** The robot utilizes custom 3D-printed see-through fingers wrapped in gripping tape to improve visibility and grasp.
- **Hardware (ALOHA):** A rubber band load-balancing mechanism counteracts gravity on the leader arms to reduce operator fatigue.
- **Hardware (ALOHA):** The visual setup processes 480x640 pixel RGB images at 50Hz using four cameras located at the top, front, and on both wrists.
- **Software (ACT):** The algorithm applies action chunking to predict target joint positions for the next $k$ timesteps rather than a single step, reducing the effective task horizon.
- **Software (ACT):** A temporal ensemble queries the policy at every timestep and calculates an exponentially weighted average of overlapping action predictions to generate smooth movements.
- **Software (ACT):** The policy is trained as a Conditional Variational Autoencoder (CVAE) utilizing transformer architectures to model the multi-modal variability in human demonstrations.

## Datasets

## Results

## Flaws

## Open Questions