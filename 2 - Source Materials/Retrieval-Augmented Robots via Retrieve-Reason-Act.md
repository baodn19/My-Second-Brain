---
categories:
  - "[[Research Literatures]]"
created: March 12th 2026
modified: March 12th 2026, 5:40:24 pm
reference note:
  - "[[temiralievRetrievalAugmentedRobotsRetrieveReasonAct2026]]"
pass:
  - first
tags:
  - rag
year: 2026
---
# 1st Pass: Extract information into headings: research question, problems solved, contributions, and limitation
## Research question
- How can a robot solve a strictly [[zero-shot]] manipulation task where no prior kinematic trajectory exists, but explicit visual procedural instructions are available?
## Problems
- **Zero-Shot Procedural Execution:** The framework bridges the gap between semantic understanding and physical execution for novel tasks that lack prior demonstrations or internal parametric memory.
- **Visual Grounding of Abstract Data:** The system solves the challenge of mapping abstract part identifiers (e.g., "part_0") to 3D physical components represented in 2D visual manual diagrams.
- **Limitations of Prior Retrieval Methods:** It overcomes the constraints of earlier robotic retrieval systems that relied solely on fetching past motor skills or text-based safety rules.
## Contributions
- **Retrieval-Augmented Robotics (RAR) Paradigm:** The authors defined the Retrieve-Reason-Act loop, enabling agents to actively retrieve and parse visual procedural manuals from unstructured corpora.
- **Visual Document RAG Validation:** The study demonstrated that grounding robotic planning in exact visual manuals improves task success rates (F1 score) by 20.4% compared to zero-shot reasoning.
- **3D-to-2D Parts Mapping:** The authors developed a preprocessing strategy that renders 3D object models into labeled 2D overview images, allowing the language model to connect symbolic identifiers to physical geometry.
- **Retrieval Strategy Analysis:** The research provided empirical evidence that retrieving exact procedural instructions is more effective for complex physical tasks than retrieving structurally different, albeit visually similar, past examples.
- **Closed-Loop Simulation Integration:** The complete RAR pipeline was successfully implemented and validated in real-time within NVIDIA Isaac Sim using a mobile robot.
## Limitations
- **Capacity Limits for Complexity:** System performance degrades significantly as the number of components increases, with a sharp drop in effectiveness observed when items exceed 5 parts.
- **Visual Procedural Understanding Deficits:** The underlying vision-language model struggles to track simultaneous spatial relationships across multiple manual pages and has difficulty disambiguating visually similar components. (*Assign ID to each part*)
- **Under-prediction Error Mode:** The system systematically under-predicts necessary connections (missing 62.9% of the ground truth connections) rather than hallucinating nonexistent ones.
- **Simulation Simplifications:** The robotic execution experiments relied on perfect simulation localization and simplified geometric representations (colored 0.1 m x 0.1 m x 0.1 m cubes) to bypass low-level manipulation complexities.

# 2nd pass
## Methodology

## Datasets

## Results

## Flaws

## Open Questions