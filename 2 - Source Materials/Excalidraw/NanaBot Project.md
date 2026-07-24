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

# MVP Development


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

Get display object's pointer (ILI9341) ^2LgwOZvo

Valid display object? ^YFNmDzeC

x ^2IULoLBb

Lock display ^zLublUhS

Initiate the SPI transaction with the XPT2046 ^lPD1C9OX

Returned touched coordinates in (x, y, strength) ^rq2FPo7C

Returned valid coord AND >0 touch points? ^XpizeTtG

screen wasn't touched ^LQcciJAx

Was the screen touched? ^XnUBS1rr

screen wasn't touched ^gD8SAvo4

x ^XHOXVHdc

screen was touched ^L6qaBpoK

calculate corresponding row index 
based on the touch point ^zv6qjvDz

Index non-negative? ^VvjiymiJ

## Embedded Files
bf0bb957c3d4bf23f03fd9c7b03d6784acec0ab5: https://www.lcdwiki.com/images/thumb/c/c4/MSP3218-021.jpg/500px-MSP3218-021.jpg

53a4559bd6e18b970d87c62cba1484c2959618bf: http://wiki.fluidnc.com/hardware/esp32-s3_devkitc-1_pinlayout_v1.1.jpg

%%
## Drawing
```compressed-json
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

CzhJDjte4QHWyfgpYEAA
```
%%