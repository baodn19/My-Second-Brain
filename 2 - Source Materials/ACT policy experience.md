---
created: 2026-04-12
modified: April 12th 2026, 4:03:37 pm
---
# Theory

# Experience
## Task: picking up K-cups and placing in carton box
- *Some generalizability:* The ACT model is trained on 3 out of 6 flavors. Regardless, the robot can finish the task with all 6 flavors since K-cups have identical shapes with the top cover as the only difference. 
	- The robot has higher accuracy for flavors that are trained than those that aren't in the trained dataset.
- *Background dependent:* The ACT model when the robot is moved to a different workstation or the workstation is moved to a different background. The robot failed to approach the cup and got stuck in a sequence.

# Question
- Why does the policy when the environment have some changes?