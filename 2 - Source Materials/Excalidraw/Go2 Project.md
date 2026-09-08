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

## Embedded Files
20e7caf528345ca9361a484ea38d2ec450cdb218: https://doc-cdn.unitree.com/static/2024/2/19/b24fbf6ab5ec4604bd0110464da2a848_7261x2328.png

%%
## Drawing
```compressed-json
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
```
%%