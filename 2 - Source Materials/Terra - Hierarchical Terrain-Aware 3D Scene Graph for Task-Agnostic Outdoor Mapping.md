---
categories:
  - "[[Research Literatures]]"
created: March 4th 2026
modified: March 4th 2026, 1:53:33 pm
reference note:
  - "[[samuelsonTerraHierarchicalTerrainAware2025]]"
pass:
  - first
tags:
  - 3DSG
year: 2025
---
## 1st Pass: Extract information into headings: problems solved, contributions, and limitation
### Problems
- Classical geometric mapping methods retain essential structural environment information, but lack a semantic understanding and organization to allow high-level robotic reasoning
- LiDAR models are closed-set (restricted to a fixed set of semantic classes
- Constructing mesh maps over large areas is both computationally and memory intensive
- camera-derived depth has limited range (≤ 20 meters). These both restrict indoor 3DSG techniques from scaling to large outdoor settings
- Traditional VLMs struggle to robustly identify terrain because the online image captions they are trained on rarely describe terrain types and instead focus on foreground objects.
### Contributions
- Combine indoor 3DSG techniques with geometrically robust outdoor LiDAR SLAM methods, enabling metric-semantic mapping in large-scale outdoor environments, we term our method Terra
- A novel, memory-efficient, and task-agnostic approach for open-set metric-semantic mapping in large-scale outdoor environment
	- **Does the paper test on edge device?**
- A terrain layer in the outdoor 3DSG that supports terrain-aware tasks where VLMs alone struggle
- Hierarchical region layers to handle multiple levels of task abstraction
- In-depth evaluation on simulated and real world data comparing Terra with state-of-the-art (SOTA) indoor 3DSG methods
	- **Why not compare with SOTA outdoor method?**
- The researchers fine-tuned a YOLOv11-segment network to successfully mask and classify common terrain types, including sidewalk, grass, and asphalt.
### Limitations
- The current method completes its three mapping and querying phases in sequence.
- full real-time pipeline remains a goal for future work.
- The system's reliance on prompt-tuning and view-dependent recognition continues to be a limitation.

## 2nd pass
## Methodology

## Datasets

## Results

## Flaws

## Open Questions