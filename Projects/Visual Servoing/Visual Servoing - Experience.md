# URDF
- *Optical frame*: requires a frame rotated by -90 degrees because ROS is "X-forward" while computer vision is "Z-forward" (`rpy="${-pi/2} 0 ${-pi/2}`)
- *Camera plugin Gazebo*: add before the end of the urdf, still within the `robot` tag
	- Use new Gazebo sim `gz`
	- Attach `camera_link` to `tool0` frame on UR5e
	- Publish to `camera/image_raw` topic and use `ros_gz_bridge` to map the Gazebo topic `camera/image_raw` to the ROS topic `/camera/image_raw`

# ros2_control
- *Necessary controller in yaml:*
	- *joint_state_broadcaster:* publishes the state of joints to /joint_states
	- *joint_trajectory_controller:* accepts position commands

# Gazebo
## Launch file
- *Reading URDF XML:* wrapped URDF in `ParameterValue(..., value_type=str)` to prevent ROS from crashing when reading URDF XML as YAML
- *Read robot mesh files:* Used `SetEnvironmentVariable` to set `GZ_SIM_RESOURCE_PATH` to the `install/share` directory
- *Ensure sensor plugin to see camera feed:* Swapped the default `empty.sdf` for a custom `ur5e_world.sdf`
- *Spawn controllers:* Added nodes to spawn `joint_state_broadcaster` and `joint_trajectory_controller`
