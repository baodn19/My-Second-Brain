---
excalidraw-plugin: parsed
tags:
  - excalidraw
  - "#Project"
categories:
  - "[[Projects]]"
year: 2026
status:
  - ongoing
---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'

# Summary (250 words)
The Go2 Air is deployed to collect visual and lidar data inside the burned Marine Science Lab building that is post-processed into 3D maps and scenes. On May 2, a lightning strike started the fire and salt water was used to distinguished. The Go2 is tasked to map out the building and retrieve useful insights.

# Trials & Errors

| Bugs Behavior                                                                                                                                                                                                                                                            | Underlying problem                                                                                                   | Solution                                                       |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| Rviz2 cannot play the video from the `ros2 bag play` and displayed a warning `[rosbag2_player]: New subscription discovered on topic '/camera/image_raw', requesting incompatible QoS. No messages will be sent to it. Last incompatible policy: RELIABILITY_QOS_POLICY` | The ROS2 bag recorded the video in `Best Effort` QoS policy and Rviz2 is trying to play it in `Reliable` QoS policy. | Expand `Image` and set **Reliability Policy** to `Best Effort` |
|                                                                                                                                                                                                                                                                          |                                                                                                                      |                                                                |
# Related Experience

# Excalidraw Data

## Text Elements
Jailbreak Go2 Air ^sVNNAF9M

- Provide access to EDU tier services (Cyclone DDS) ^MVbo8d08

Jetson Orin Nano Constraint ^j5n5F2B1

- 8GB shared unified memory LPDDR5 (102 GB/s)
- 6-core Arm CPU => 6 true parallel thread before time-slicing
- Ampere GPU w/ 1024 CUDA cores + 32 Tensor cores  ^ln50oUCs

TensorRT ^cOccvoze

CUDA Kernel ^alvfKmQW

%%
## Drawing
```compressed-json
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
```
%%