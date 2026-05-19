---
created: 2026-03-26
tags:
  - research
modified: May 19th 2026, 5:08:45 pm
categories:
  - "[[Experience]]"
---

| Problem                                                                                          | Solution                                                                                           |
| ------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------- |
| The camera feed is running at 20 fps but the visual appears to be laggy.                         | Disconnect the monitor from Jetson for it consumes GPU resources.                                  |
| The script is optimized with TensorRT but still runs at 15 fps                                   | Set the clock frequency to max or change the power draw of jetson through `jtop`                   |
| Couldn't setup pytorch - CUDA for Jetson                                                         | Refer to Ultralytics guide                                                                         |
| Running 3 camera with fourcc format YUYV fails but removing one camera allows the other 2 to run | Lower the format to MJPG format since YUYV is unnecessarily large and lead to bandwidth saturation |
|                                                                                                  |                                                                                                    |
