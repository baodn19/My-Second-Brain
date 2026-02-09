---
categories:
  - "[[Research Literatures]]"
created: February 8th 2026
modified: February 8th 2026, 11:43:45 am
reference note:
  - "[[chenAccurateRecognitionLocalization2025]]"
tags:
  - object-detection
  - strawberry
pass:
  - first
---
## 1st Pass
### Problems
- [[labor shortage in strawberry harvesting]]
- *Existing method:* increase detection speed = reduce detection accuracy
### Contributions
- *[[StarNet]]:* reconstruct the backbone network of [[YOLOv10]]n to reduce the number of parameters and achieve fast detection.
- *[[Coordinate Attention (CA) module]]:* enhance the accurate recognition of the region of interest or the position of important objects in the [[convolutional neural network (cnn)]] $\implies$ improving the detection effect of strawberries under complex backgrounds
- *Integrate [[Inner-IoU]] into [[CIoU]] as loss function:* accelerates the regression process of low IoU samples through a larger auxiliary bounding box

## 2nd pass
## Methodology

## Datasets

## Results

## Flaws

## Open Questions