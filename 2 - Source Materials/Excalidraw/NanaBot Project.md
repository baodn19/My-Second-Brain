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

| Problems                        | Solution | Take-away |
| ------------------------------- | -------- | --------- |
| The chatbot often cut my speech |          |           |
|                                 |          |           |
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

%%
## Drawing
```compressed-json
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=
```
%%