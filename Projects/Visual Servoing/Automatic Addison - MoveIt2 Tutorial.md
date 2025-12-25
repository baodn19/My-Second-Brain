# Overview
- *Controller:*
	- *Joint Trajectory Controller:* arm movement
	- *Forward Velocity Controller:* speed control
	- *Gripper Controller:* end-effector actions (e.g. open and close gripper)
	- *Diff Drive Controller:* mobile base navigation
- *Feedback data (position, velocity, force, status):* **Joint State Broadcaster** and **Force Torque State Broadcaster**

# SRDF
- *Purpose:* add semantic information (1)
	- Naming groups of joints or links (e.g., “arm”, “gripper”) 
	- Defining default robot poses (e.g., “home”, “closed”, etc.)
	- Which parts of the robot should be checked for colliding with each other during movement.

# MoveIt2
- *Config folder:* allow for overriding defined in URDF file (1)
	- *URDF:* limit for individual joints
	- *cartesian_limits:* control speed & motion of gripper

# Motion Planner
## Pilz Industrial
- *Use case:* consistent, controlled movements; structured & predictable environment (1)
- *Mechanisms:* use simple, direct point-to-point paths (1)
	- Preprocesses the robot’s motion planning request: meets certain safety and feasibility criteria (starting position is safe)
## OMPL (Open Motion Planning Library)
- *Use case:* dynamic environments with unexpected obstacles (1)
- *Mechanisms:* sampling-based motion planning framework; provides various probabilistic algorithms like RRT, PRM, etc (1)
## STOMP (Stochastic Trajectory Optimization for Motion Planning)
- *Mechanisms:* uses random adjustments to improve paths