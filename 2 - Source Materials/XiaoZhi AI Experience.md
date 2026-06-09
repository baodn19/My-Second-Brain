---
categories:
  - "[[Experience]]"
modified: June 9th 2026, 10:54:40 am
---
# Theory
- *Source:* https://github.com/78/xiaozhi-esp32
- *Handy translated documentations:* https://github.com/will-cogley/Coglet/tree/main/Translated%20Docs%20for%20XiaoZhi%20AI

# Experience
## Deploying XiaoZhi AI on breadboard
1. Buy the required components ([BOM](https://github.com/will-cogley/Coglet/blob/main/Translated%20Docs%20for%20XiaoZhi%20AI/Purchase%20Instructions%20for%20Xiaozhi%20AI%20ESP32S3%20Development%20Board%20%2B%20Breadboard%20DIY%20Module%20-%20Feishu%20Docs.pdf)) and solder electronics
2. Follow section 2.1 of [Xiaozhi AI Chatbot Hardware List and Wiring Tutorial](https://github.com/will-cogley/Coglet/blob/main/Translated%20Docs%20for%20XiaoZhi%20AI/DIY%20Breadboard%20for%20Xiaozhi%20AI%20Chatbot%20Hardware%20List%20and%20Wiring%20Tutorial%20-%20Feishu%20Docs.pdf) or other sections depend on your layout
3. Download the latest firmware (`vx.x.x_bread-compact-wifi.zip`) and unzip
4. Ubuntu: Go to the `.bin` files and flash firmware with `esptool` which is downloaded through `pipx`  (use either 1152000 or 460800 baud rate)

# Questions

