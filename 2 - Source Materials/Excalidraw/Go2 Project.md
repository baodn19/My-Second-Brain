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

- Go2's XT30 Output Power interface (28.8V) -> XT30 male connector
-> Buck converter (19V) -> Barrel Plug Connector ^Q7WYARij

%%
## Drawing
```compressed-json
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
```
%%