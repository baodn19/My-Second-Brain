---
categories: "[[Video]]"
source: https://www.youtube.com/watch?v=LRAqeM8EjOo
author:
  - "[[Benjamin Joseph Mildenhall]]"
published: 2020-08-04
created: 2026-01-31
description: "Best Paper Honorable Mention at ECCV 2020. This is the full 10 minute talk video accompanying the paper at the virtual ECCV conference.Project Page: http://www.matthewtancik.com/nerfPaper: https://arxiv.org/abs/2003.08934Code: https://github.com/bmild/nerfSupplemental video with additional comparisons: https://www.youtube.com/watch?v=JuH79E8rdKcNeRF: Representing Scenes as Neural Radiance Fields for View SynthesisBen Mildenhall*, Pratul P. Srinivasan*, Matthew Tancik*, Jonathan T. Barron, Ravi Ramamoorthi, Ren Ng*denotes equal contribution"
modified: 01/31/2026
---
# Key Takeaways
## The problem of novel view synthesis
- *Input:* images of scene along w/ camera pose
- *Output:* photorealistic new views of the same scene
- *Challenge:* large pixel shift between input images
- **Goal:** generate seamless novel views

## Approach: predict 3D [[discretized voxel]] RGB-alpha grid
- *Procedure:* process input image with 3D [[convolutional neural network (cnn)]] to predict a discrete volumetric representation like a voxel grid -> render new views by compositing a long rays
- *Characteristic:* differentiable and is easy to optimize
	- What does it mean by differentiable?
- *Drawback:* storing these large voxel grids can become unwieldy for large or high resolution scenes

## [[Neural networks]] as a shape representation
- *Represent shaped surface:* the level set of a fully connected [[neural network]] that's defined on 3d space

# What to explore next