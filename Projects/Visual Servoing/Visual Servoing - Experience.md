# URDF
- *Optical frame*: requires a frame rotated by -90 degrees because ROS is "X-forward" while computer vision is "Z-forward" (`rpy="${-pi/2} 0 ${-pi/2}`)
- *Camera plugin Gazebo*: add before the end of the urdf, still within the `robot` tag
	- Use new Gazebo sim `gz`

# Gazebo
## Launch file
