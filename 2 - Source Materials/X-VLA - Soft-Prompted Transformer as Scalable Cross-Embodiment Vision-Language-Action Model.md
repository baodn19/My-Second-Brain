---
categories:
  - "[[Research Literatures]]"
created: April 27th 2026
modified: April 27th 2026, 11:08:44 pm
reference note:
pass:
  - first
tags:
year:
---
# 1st Pass: Extract information into headings: research question, problems solved, contributions, methodologies, and limitations
## Research question
- How to facilitate the training of Vision-Language-Action ([[VLA]]) models across diverse robotic platforms using heterogeneous, cross-embodiment datasets.
## Problems
- Robot data fragmentation across platforms, sensors, embodiments, and collection protocols hinders the training of generalist VLA models.
- Deploying VLAs on new robots typically requires extensive and costly per-embodiment adaptation.
- Inconsistent human demonstrations (e.g., in cloth folding) cause unstable policy learning.
## Contributions
- Development of X-VLA, a soft-prompted, flow-matching VLA framework that handles varying hardware configurations using a single unified architecture.
- Demonstration of a 0.9 billion parameter model (X-VLA-0.9B) that reaches state-of-the-art performance across 6 simulation environments and 3 real-world robots.
- Creation of Soft-Fold, an open-source, high-quality cloth-folding dataset.

## Limitations
- The technical novelty is limited, as the core soft prompt mechanism is an adaptation from natural language processing.
- The model relies on validation error as a proxy for evaluating pre-training performance.

# 2nd pass
## Methodology
- Utilisation of separate sets of learnable embeddings (soft prompts) for each data source to capture embodiment and domain-specific variations.
- Disentanglement of high-dimensional observations (multi-view images, language) from low-dimensional states (proprioception, actions) within the encoding pipeline.
- A two-phase training process: pre-training an embodiment-agnostic policy on 290,000 episodes, followed by fine-tuning only 1% of parameters (the soft prompts and action-related projections) for new embodiments.
- Implementation of a flow-matching objective for action chunk generation.
- A two-stage demonstration collection strategy for cloth folding to reduce data inconsistency.
## Datasets

## Results

## Flaws

## Open Questions