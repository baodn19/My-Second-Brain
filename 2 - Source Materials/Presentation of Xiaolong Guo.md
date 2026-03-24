---
created: 2026-03-24
categories:
  - "[[Meetings]]"
modified: March 24th 2026, 3:29:36 pm
type: []
org:
loc:
people:
  - "[[Xiaolong Guo]]"
topics: []
contact:
---
# Domain-specific LLM deployment
- *Fine-tune for hardware debug:* many cybersecurity accidents are caused by hardware bug (semiconductor errors)
	- Debug in design stage
- [[Llm4sechw - Leveraging domain-specific large language model for hardware debugging]]

# Edge LLMs
- *Benefit:*
	- Reliable, low latency
	- Enhanced privacy & security
	- Customization & control
- *Limitation:* Computing power constraints
	- *Solution:* distillation, pruning, **[[quantization]]**
- *Voltage instability:* 
	- Vulnerable to environmental stressors: battery aging, thermal drift, fluctuations in power delivery
- *Silent semantic drift
- [[Edge LLM under Voltage Instability]]
- Pi 5 16GB: power management interface
	- *Normal:* baseline 0mV
	- *Mild:* undervolt 25mV
	- *Moderate:* undervolt 50mV

# Interdisciplinary
- *Why:*
	- solve existing domain research questions
	- Security is a can of worms
- *Education:*
	- LLM empowered hands-on education
## Financial fraud
## Antimicrobial
- LLMs to predict peptide synthesis
- Web-lab to validate the structure
	- If structure invalid: waste of time and money
	- Potential data poisoning 
## Tagatose
- Use wasted product from yogurt to make tagatose
## Nuclear Reactor
- LLMs to operate nuclear reactor
- Hallucination of LLMs is dangerous
	- Build guard: integrate explainability

## Robotics
- Less venue to attack since power is more stable