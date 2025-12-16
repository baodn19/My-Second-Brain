# URDF
- Create a `<robot>_description` package is industry standard
- 5 steps process to add link together:
	1. Create a link
	2. Create a joint
	3. Fix joint origin (Edit origin in joint)
	4. Set joint type and axis 
	5. Fix visual origin (Edit origin in link)
- *xacro:*
	- *Main file:* {robot}.urdf.xacro
	- *Header:* {component}.xacro
- *Launch file:* debug and build urdf in package

# MoveIt
- *Simplify the geometry:* more complex shape means more computation for collision
	- Cylinder can be simplified as box
	- Complex mesh (visual tag) -> Approximation with stl file with less details (collision tag)
	- Precision isn't a problem because we don't want the links to be too close together; provide extra margin of error
- *Cartesian Path:* allow the end effector to travel linearly; if the planning fails -> Add more DOF
- *Launch file to bringup:*
	1. robot_state_publisher
	2. controller manager
	3. desired controllers
	4. moveit
	5. rviz2 (save rviz config if necessary)