---
created: 2026-02-15
category:
  - "[[Literature Reviews - Agricultural Object Detection]]"
modified: February 16th 2026, 9:24:08 am
tags:
  - strawberry
  - object-detection
---
# Research question
- *Optimize model* to run on Jetson AGX Orin 64gb
	- Why this device?
	- What benefit does it provide to precision agriculture?
		- Cost efficient?
		- More compact?
- *Class increase:* can we increase more class while keeping it lightweight?
	- How many stages would be meaningful to the farmer?
	- Localize the where stages of strawberry => What value would this bring?
		- Research shows that **water stress** or specific **potassium levels** applied at the "Turning" stage can actually increase the final sweetness and size of the fruit. A robot that maps these stages tells the farmer exactly which rows need a change in fertigation _today_ to maximize the quality of _next week’s_ harvest.

# Search Strategy
- *Include:* 
	- **Architecture specific:** `YOLOv11n`, `StarNet backbone`, `SlimNeck`, `GSConv`, `Knowledge Distillation`
	- **Hardware specific:** `Jetson Orin Nano`, `FP16 quantization`, `TensorRT deployment`
	- **Agricultural specific:** `Occlusion-aware detection`, `Maturity classification`, `Illumination robustness`
- *Exclude:*
	- `A100`, `H100`, `RTX 4090` (These are "too powerful" data center GPUs).    
	- `Simulation-only` (You want "field" or "in-situ" results).

# First Pass
![[Strawberry Detection on Edge Devices.base]]
# Second Pass
![[Strawberry Detection on Edge Devices.base]]
# Third Pass
![[Strawberry Detection on Edge Devices.base]]
# State-of-the-art
# Research Gap
- [[Three-stage classification of ripeness simplifies strawberries' maturation]]