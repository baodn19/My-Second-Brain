---
categories:
  - "[[Research Literatures]]"
created: March 26th 2026
modified: March 26th 2026, 11:20:15 pm
reference note:
  - "[[linEfficientGPUbasedImplementation2025]]"
pass:
  - first
tags:
  - ssl
year: 2025
---
# 1st Pass: Extract information into headings: research question, problems solved, contributions, and limitations
## Research question
- How can a noise-robust [[Sound Source Localization (SSL)]] algorithm be efficiently deployed on a GPU to achieve real-time processing for large-scale microphone arrays?
- Specifically, how can [[Generalized Singular Value Decomposition-based Multiple Signal Classification (GSVD-MUSIC)]] be implemented on GPUs to improve robot audition in embedded systems operating in low [[Signal-to-Noise Ratio (SNR)]] environments?

## Problems
- [[Central Processing Unit (CPU)]]-based implementations lack the computational power to handle the intensive matrix operations required for SSL in real-time when array sizes increase.
- CPU processing bottlenecks do not leave adequate time for subsequent machine learning or deep learning tasks.
- Existing [[Standard Eigenvalue Decomposition (SEVD)-MUSIC]] algorithms fail to maintain accuracy in low-SNR environments.
- There was a lack of a GPU-based implementation for the superior, noise-robust GSVD-MUSIC algorithm.
- [[Field-Programmable Gate Array (FPGA)]] alternatives possess significantly lower bandwidth capabilities than GPUs, resulting in latency when processing large-scale audio data.
## Contributions
- Developed a GPU-accelerated implementation of the GSVD-MUSIC algorithm for the [[HARK]] open-source robot audition platform.
- Applied parallel computing strategies using NVIDIA GPUs and CUDA to replace original CPU-based matrix operations.
- Achieved processing speedups of 5648.7x for GSVD calculations and 10.7x for the complete SSL module on a **Jetson AGX Orin** embedded device using a **60-channel microphone array**.
- Achieved processing speedups of 4245.1x for GSVD calculations and 17.3x for the complete SSL module on an NVIDIA A100 server.
- Verified calculation reliability by demonstrating a [[Root Mean Squared Error (RMSE)]] on the order of $10^{-6}$ and 100.00% detection consistency compared to CPU baselines.
## Limitations
- The current system processes audio frames at fixed intervals instead of utilizing stream processing.
- Processing audio data at fixed intervals introduces unavoidable delays, which hinders optimal operation in dynamic environments.

# 2nd pass
## Methodology

## Datasets

## Results

## Flaws

## Open Questions