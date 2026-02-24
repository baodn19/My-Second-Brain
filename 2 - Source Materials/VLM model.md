---
created: 2026-02-24
categories:
  - "[[Meetings]]"
modified: February 24th 2026, 9:59:14 am
type:
  - "[[Lab Meeting]]"
org:
  - "[[ERA Lab]]"
loc:
  - Virtual
people:
  - "[[Xiaomin Lin]]"
topics: []
contact:
---
## Idea overview
- Implement RLM instead of VLM
	- Main limitation: split to chunk in primitive ways, only use
	- Advantage of VLM: decrease resolution and better representation
- Recursive idea: look at image -> extract image -> look at questions -> identify interested data
- declare_ROI create bounding box -> Verify_ROI: cross check with the VLM, if good then it zoom in
- Synthesize: produce results
- 6-7 recursive call
- When achieve high confidence reading, stop suggesting
- Leaf just need observation
- 200 questions
- Recursive allows bridge reason across different VLM

## Benchmark questions
- Too much info for background map
- Create another version without semantic
- Avoid questions that requires too much detail: estimate length, size, things that number
- 1-1 SCOUT is just a unit, the line is a graphic of the screen that the 1-1 SCOUT do
	- Alternative: What area are 1-1 SCOUT is supposed to screen? -> Screen above stage YELLOW, east & west direction
- Relational questions are good:
	- i.e: Is there any lake between 2 landmarks?
- If it's hard for a human, than it's going to be hard for VLM
- It's fine to have question with military context 
	- Most of VLM has no reasoning -> Better to avoid military context for now
## Questions
- What if ROI is wrong?
A: Verify solve this problem, limitation of RVLM, depend on how good the VLM is
- How does RVLM compare to MCP? How is it using the image information instead of html info? And is it better?
A: If html text and image is input than it might be better. Represent high-resolution of the scenario. Nobody has high-resolution to use dynamic ROI for