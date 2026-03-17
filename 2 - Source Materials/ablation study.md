---
created: March 17th 2026
categories:
  - "[[Concepts]]"
modified: March 17th 2026, 4:06:01 pm
tags:
  - research
---
- *Definition (machine learning):* an experiment where each components of a [[machine learning]] model are removed or modified to measure their impact on overall performance.
	- Borrowed from [[neuroscience]] & [[medicine]]: biological tissues are removed to observe the functional effect on the broader system.

# Purpose
- **Isolate Contributions:** proves a proposed module improves the network, separating its effect from external factors like [[hyper-parameter]] tuning or longer training times.
- **Identify Redundancy:** reveals if certain parameters contribute negligibly to the output $\implies$ they can be pruned to reduce computational cost without sacrificing accuracy.
- **Justify Complexity:** justify the performance gain warrants the added computational or architectural complexity by comparing the baseline model against the final proposed architecture.
- **Improve Interpretability:** quantify the reliance of the network on specific feature map units for decision-making.