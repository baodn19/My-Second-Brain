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
## C++ project
### Set target pose
- *MoveGroupInterface:* a remote control to send commands to the arm (2)
``` cpp
using moveit::planning_interface::MoveGroupInterface;
auto arm_group_interface = MoveGroupInterface(node, "arm");
```
- *Set target pose:* tell arm where to go (2)
``` cpp
auto const arm_target_pose = [&node]{
	geometry_msgs::msg::PoseStamped msg;
	msg.header.frame_id = "base_link";
	msg.header.stamp = node->now();
	msg.pose.position.x = 0.061;
	msg.pose.position.y = -0.176;
	msg.pose.position.z = 0.168;
	msg.pose.orientation.x = 1.0;
	msg.pose.orientation.y = 0.0;
	msg.pose.orientation.z = 0.0;
	msg.pose.orientation.w = 0.0;
	return msg;
}();
arm_group_interface.setPoseTarget(arm_target_pose);
```
- *Plan motion:* calculate the steps to reach target pose (2)
``` cpp
auto const [success, plan] = [&arm_group_interface] {
	moveit::planning_interface::MoveGroupInterface::Plan msg;
	auto const ok = static_cast<bool>(arm_group_interface.plan(msg));
	return std::make_pair(ok, msg);
}();
```
- *Execute plan:* (2)
``` cpp
if (success) {
	arm_group_interface.execute(plan);
} else {
	RCLCPP_ERROR(logger, "Planning failed!");
}
```

### Plan around objects
- *Virtual joints:* describe movement of the whole robot in relation to the worlds environment ;  update planning scene with base movement (2)
	- Describe in **SRDF** file
	- **Odom:** robots position in the world based on its movement
	- **Planar joint:** allow robot to move on the plane
# Motion Planner
## Pilz Industrial
- *Use case:* consistent, controlled movements; structured & predictable environment (1)
- *Mechanisms:* use simple, direct point-to-point paths (1)
	- Preprocesses the robot’s motion planning request: meets certain safety and feasibility criteria (starting position is safe)
## OMPL (Open Motion Planning Library)
- *Use case:* dynamic environments with unexpected obstacles (1)
- *Mechanisms:* sampling-based motion planning framework; provides various probabilistic algorithms like RRT, PRM, etc (1)
## STOMP (Stochastic Trajectory Optimization for Motion Planning)
- *Mechanisms:* uses random adjustments to improve paths (1)