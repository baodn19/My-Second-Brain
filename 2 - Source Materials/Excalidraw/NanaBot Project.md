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

| Convention                                                                                                                                                                                                                                   | Purpose                                                                                                                                                                                                      |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Use type alias on repeating declaration.                                                                                                                                                                                                     | Improve abstraction, shorten declaration, and hide pointer syntax from API caller.                                                                                                                           |
| Use function-pointer member for similar implementation on different instance.                                                                                                                                                                | Avoid driver-specific `if/else` dispatch.<br>Each driver assign its implementation while keeping the static function private                                                                                 |
| Use `inline` for a non-template free function defined in a header<br>(lotusai_utils.h: L47-94)                                                                                                                                               | If the header file is referenced by many files, `inline` allows 1 function to be defined in many translation untis while the linker treats them as 1, ultimately avoiding a multiple-definition error (ODR). |
| Define a function in a header for:<br>->Small helpers shared across files (optional)<br>-> Templates (required)<br>-> `constexpr` helpers to work at compile time (required)<br>-> No separate `.cc` (optional)<br>(lotusai_utils.h: L47-94) | The definition has to be visible to the compiler at the place it's used - either sharing, convenience, or language requirements.                                                                             |
| Use `const T&` (pass by reference) for large objects like string or vector<br>(lotusai_utils.h: L24, 40)                                                                                                                                     | Avoid copying and prevent the function from modifying the object                                                                                                                                             |
| Use `auto` only for long type. Even then, it's still encouraged to use type alias                                                                                                                                                            | Prevent overuse of `auto` which lead to ambiguous data type                                                                                                                                                  |
| Use `const char*` for any fixed character instead of `std::string`<br>(lcd_display.cc: L1164-1165)                                                                                                                                           | Comply with C++ convention and setting the string to read-only                                                                                                                                               |

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

Create empty string vector ^7MA3fLLo

Is the CSV empty? ^hXociKjW

x ^XWzFzjfw

Parse CSV with ',' into a string ^igw9DqOd

Trim front and back from white-space and tabs ^t5llK2EV

Is the parsed string empty? ^KLEpYs1h

x ^hLCA07J2

Add to string vector ^W1A8W2to

True ^jGP7MTDo

False ^Qe0jQG6l

True ^JW6iAplK

Until nothing left to parse ^yhGDoOYP

Return string vector ^MjL2HpG2

Finished parsing ^cVFaAglu

LotusAiSplitCsv ^a8u5XPZT

lotusai_utils.h ^rcSv1tZK

LotusAiBuildRecommendRequestBody ^s0jCb3Sq

LotusAiAddStringArray ^8ZYop2zs

Create empty JSON array ^MmX5wlBw

Iterate over each items in the 
string vector ^rcrXj6ZR

Turn item into JSON string 
and add to JSON array ^opFg6Uaa

Add JSON array to JSON body 
under corresponding property key ^InrpqLT0

Finished iterating ^aqq6OJBO

Property isn't completely iterated ^dGTWDiEw

Create an empty LotusAiRecommendBodyResult struct (output)
and JSON body ^5Nty8YW4

LotusAiRecommendBodyResult (struct) ^Ew35vTN8

- body: string
- error: string ^nNBLEuY0

Parse the "ingredients" string ^Xyj1310Q

Is "ingredients" empty? ^iZzGYQPx

Delete JSON body
 and add error to output ^8ScJlP1Q

Add "ingredients" to JSON body ^tdzntRsi

Parse optional parameters ^rsa27HvK

Is optional parameters empty? (per-field) ^DthuOl7E

Add optional parameters to JSON body ^RfStf5mQ

Print & copy JSON body to output ^rwI7bxUn

Delete JSON body ^wcZltHeS

True ^zs9MUIfs

False ^IlRXYX0L

return output ^SIyI8ZEA

False ^OFp1TcOL

True ^IADyhGwJ

Add "top_k" to JSON body ^UNdCc7GZ

ShowQrCode ^UhEhdGUu

SetLotusContent ^J3UZ0wGV

ClearLotusRecipeRows ^4qeM6JkY

Does recipe container exist? ^MJ6QiUD9

x ^GxzvhRNI

Delete each element in the recipe container
until there is no element left ^Dij52Fln

False ^3dOfyqDA

True ^shRwvzjf

RestoreLotusChrome ^AbThVkcq

Does bottom bar exist and subtitle enabled? ^RtgX1n23

Extract chat message label 
(nullptr if label doesn't exist) ^kYAmMuqO

Does chat message label exist and have content? ^iiykSLWv

Show bottom bar (subtitle, etc) ^6zG64yEx

True ^lW64BagJ

True ^B2igM5T7

## Embedded Files
bf0bb957c3d4bf23f03fd9c7b03d6784acec0ab5: https://www.lcdwiki.com/images/thumb/c/c4/MSP3218-021.jpg/500px-MSP3218-021.jpg

53a4559bd6e18b970d87c62cba1484c2959618bf: http://wiki.fluidnc.com/hardware/esp32-s3_devkitc-1_pinlayout_v1.1.jpg

%%
## Drawing
```compressed-json
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
```
%%