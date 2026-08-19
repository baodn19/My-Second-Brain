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
# Related Experience

## Drawing
```compressed-json
N4IgLgngDgpiBcIYA8DGBDANgSwCYCd0B3EAGhADcZ8BnbAewDsEAmcm+gV31TkQAswYKDXgB6MQHNsYfpwBGAOlT0AtmIBeNCtlQbs6RmPry6uA4wC0KDDgLFLUTJ2lH8MTDHQ0YNMWHRJMRZFFgBWRQAGMiRPVRhGMBoEAG0AXXJ0KCgAZQCwPlBJfDwc7A0+Rk5MTHIdGCIAIXRUAGtirkZcAGF6THp8BBAAYgAzcYmQAF8poA===
```
%%