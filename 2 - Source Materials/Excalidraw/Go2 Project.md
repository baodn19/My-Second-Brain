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

Architecture ^VwwKXP68

Connections to Orin Nano ^9a7cNGAH

- D435i Depth Camera: USB 3.2 Type-A ports
- LiDAR: Go2 (LiDAR + robot state) ^Lyo92Rtc

Power ^iayVbpnv

%%
## Drawing
```compressed-json
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
```
%%