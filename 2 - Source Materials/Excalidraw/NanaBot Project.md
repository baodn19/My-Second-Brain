---
excalidraw-plugin: parsed
tags:
  - excalidraw
  - "#Project"
categories:
  - "[[Projects]]"
status:
  - ongoing
year: 2026
---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'

# Summary (250 words)
Nanabot is a social robot that helps elder people who lives alone with chronic diseases to eat healthy and take medicines timely. 

# Trials & Errors
## Technical

| Bugs Behavior                                                                                                                                                                         | Underlying problem                                                                  | Solution                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| On the 3.2" SPI Module ILI9341 LCD 320x240 screen, touching the upper left and lower right corners respectively return (15, 15) and (220, 286). The extreme values are never reached. |                                                                                     |                                                                                                                   |
| The ESP-IDF console is spammed with unnecessary log.                                                                                                                                  | Every info is being published by `ESP_LOGI` and the log is set to `Info` verbosity. | Switch unwanted logs to `ESP_LOGD`. This will hide the logs for `Info` verbosity, but show for `Debug` verbosity. |
|                                                                                                                                                                                       |                                                                                     |                                                                                                                   |

## Coding Convention
- When to use callback functions in general, and when for sync and async?

| Convention                                                                    | Purpose                                                                                                                      |
| ----------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Use type alias on repeating declaration.                                      | Improve abstraction, shorten declaration, and hide pointer syntax from API caller.                                           |
| Use function-pointer member for similar implementation on different instance. | Avoid driver-specific `if/else` dispatch.<br>Each driver assign its implementation while keeping the static function private |

## Non-technical

| Problems                                                                                                                                                             | Solution                                           | Take-away                                                                                                                             |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| I learned nothing from my projects when LLM does the planning, coding, and debugging and my only job is prompting. I don't have the understanding of the system code | Outline [[Coding Workflow]] with human-in-the-loop | Human does the thinking and planning<br>LLM does the coding and play devil's advocate to your<br>LLM MUST NOT do the thinking for you |

# Related Experience
- [[XiaoZhi AI Experience]]
- [[Lotus AI Experience]]
- [[ESP32-S3 Experience]]
# Excalidraw Data

## Text Elements
Vertical Scroll on 3.2inch SPI Module ILI9341
- Library: LVGL
- Component:
 + Allow overflow
 + Enable scroll flags

- Takeaways:
 + Avoid hard-coding variables
 + Only use inline for small function to minimize executable file size and speed up execution
 + Create a struct for functions with too many parameters
 + For long-lived elements, use heap (eg: UI elements persist after function return) - vice versa for stack ^KL2PE3bb

3.2" Touchscreen
Display driver: ILI9341
Touch driver: XPT2046 ^ySnLZ5kM

240 px ^PsnF3fpX

320
px ^a9nmBkOb

[[XPT2046 Touch Mechanism]] ^pG6ct8EH

Tap ^K5odjsaG

Front ^WoUSkIvc

Back ^PeQlg65P

SPI ^U9jyY9vU

TouchPollCallback
(compact_wifi_board_lcd_touch.cc) ^epvbCNtp

XPT2046 ^mlnHxAG2

PENIRQ is active-low ^L48wuGlN

Valid lotusAI pointer AND touch handler? ^xdShRqCw

X ^LUcFYdIS

A touch is detected? ^NfCKZZSf

x ^6hd9rodx

Get display object's pointer ^2LgwOZvo

## Embedded Files
bf0bb957c3d4bf23f03fd9c7b03d6784acec0ab5: https://www.lcdwiki.com/images/thumb/c/c4/MSP3218-021.jpg/500px-MSP3218-021.jpg

53a4559bd6e18b970d87c62cba1484c2959618bf: http://wiki.fluidnc.com/hardware/esp32-s3_devkitc-1_pinlayout_v1.1.jpg

%%
## Drawing
```compressed-json
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=
```
%%