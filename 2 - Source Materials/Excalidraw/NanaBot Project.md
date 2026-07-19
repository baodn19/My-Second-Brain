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

XPT2046 ^YwVtdG37

SPI ^U9jyY9vU

## Embedded Files
ac3f4b7092921fec3cedab64e9113bca2928a81b: https://www.svgrepo.com/show/456196/chip-computer.svg

9f0a00ba3912528ae9c9695380522e11653e928a: https://www.mouser.com/images/espressifsystems/lrg/ESP32-S3-DEVKITC-1-N8_SPL.jpg

%%
## Drawing
```compressed-json
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

p+FLBAA=
```
%%