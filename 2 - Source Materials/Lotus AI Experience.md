---
categories:
  - "[[Experience]]"
modified: June 10th 2026, 1:58:13 pm
---
# Theory
- *Repository:* https://github.com/mbrishi/food_as_medicine
## Communication between Xiaozhi AI and Lotus AI
- *Pipeline:*
```
XiaoZhi mic  
    ↓  (speech → text, on-device or cloud STT)  
ESP32-S3 firmware / companion app  
    ↓  HTTP POST to LotusAI  
POST /api/recommend/jobs  
{ "ingredients": [...], "condition": "diabetes", "meal": "dinner" }  
    ↓  
Poll GET /api/recommend/jobs/{id} until status = "completed"  
    ↓  
Flatten JSON → natural language sentences  
    ↓  HTTP to XiaoZhi TTS endpoint  (or feed back into LLM)  
XiaoZhi speaks the recipe
```

# Experience

# Questions

