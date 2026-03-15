---
categories:
  - "[[Concepts]]"
created: March 14th 2026
modified: March 14th 2026, 10:48:01 pm
tags:
  - data-analysis
---
# Overview
- *Definition:* iterative algorithm to detect outliers in dataset
- *Mechanisms:* fit a line/ plane to small group of points and check how other points fit this model (inliers); repeats to find the model with most inliers
# Maximum Likelihood Estimation Sample Consensus
- *Original paper:* [MLESAC: A New Robust Estimator with Application to Estimating Image Geometry](https://www.sciencedirect.com/science/article/abs/pii/S1077314299908329)
- *Difference:* Instead of counts # points fit the model (yes/no), MLESAC calculates the statistical likelihood of the point fitting the model
	- Select plane that maximizes the total probability (likelihood) of the data
- *Inliers:* follow a Gaussian error distribution (bell curve)
	- The distribution accounts for sensor imperfections while the point still belong to the model
- *Outliers:* are spread randomly (uniform distribution)
	- "points of gross error" that have no relationship to the model whatsoever. They could be anywhere in the sensor's view.