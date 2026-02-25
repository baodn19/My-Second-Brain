---
category:
  - "[[Quotes]]"
modified: February 17th 2026, 3:01:57 pm
created: "{{date:YYYY-MM-DD}}"
---
<%*
// 1. Define variables FIRST
let author = await tp.system.prompt("Enter Author Name");
let source = await tp.system.prompt("Enter Source (e.g., Genius Makers)");
let quoteText = await tp.system.prompt("Paste the Quote here");

// 2. Clear the output to avoid extra whitespace
tR = "";
-%>
---
modified: <% tp.date.now("MMMM Do YYYY, h:mm:ss a") %>
created: <% tp.date.now("YYYY-MM-DD") %>
author: "<%* tR += author %>"
source: "<%* tR += source %>"
tags: 
topics:
---

# Quote: 

> [!quote] <% author %>
> "<% quoteText %>"

---

# Context
