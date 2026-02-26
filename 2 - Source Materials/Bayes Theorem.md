---
categories:
  - "[[Concepts]]"
created: February 26th 2026
modified: February 26th 2026, 4:12:01 pm
tags:
  - mathematics
---
- *Definition:* obtain the [[probability]] of A given B by inverting the conditions from P(A|B) to P(B|A), using the following formula:
	- P(A|B): is the **posterior**, the probability of observing event A (the model configuration) given that event B (the observations) is true.
	- P(B|A) is the **likelihood** of observing event B given that A is true. 
	- P(A) is the **prior** probability, independent of p(B).
	- P(B) is the **marginal** probability, independent of p(A).
$$
P(A|B)=P(B|A) \frac{P(A)}{P(B)}
$$
- *Properties:* P(A|B) is proportional to the numerator and not the denominator P(B), thus avoiding the case where P(B) = 0