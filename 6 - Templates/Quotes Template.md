---
category:
  - "[[Quotes]]"
modified: February 17th 2026, 3:01:57 pm
created: "{{date:YYYY-MM-DD}}"
---
<%*
// 1. Define variables and prompt for input
let author = await tp.system.prompt("Enter Author Name");
let source = await tp.system.prompt("Enter Source");
let quoteText = await tp.system.prompt("Paste the Quote here");

// 2. Sanitize and Truncate for Filename
// Removes characters illegal in filenames: \ / : * ? " < > |
let cleanQuote = quoteText.replace(/[\\/:*?"<>|]/g, "").substring(0, 50).trim();
let fileName = `${cleanQuote} - ${author}`;

// 3. Rename the file
await tp.file.rename(fileName);

// 4. Clear output for clean rendering
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
