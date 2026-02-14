---
modified: February 4th 2026, 10:06:44 am
---
Machine learning models don’t usually say "This is a cat." Instead, they say "I am 85% sure this is a cat."

The **Threshold** is the cutoff you choose to turn that probability into a "Yes" or "No."

- **High Threshold (e.g., 0.9):** The model only says "Yes" when it is extremely certain. This leads to **High Precision** (few mistakes) but **Low Recall** (it misses many objects it wasn't sure about).
    
- **Low Threshold (e.g., 0.1):** The model says "Yes" to almost everything. This leads to **High Recall** (it finds almost every object) but **Low Precision** (it makes a lot of false-positive mistakes).