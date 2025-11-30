# Interesting info
## URDF
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