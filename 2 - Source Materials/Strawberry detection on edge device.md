---
created: 2026-02-15
category:
  - "[[Literature Reviews - Agricultural Object Detection]]"
modified: February 15th 2026, 1:41:16 pm
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