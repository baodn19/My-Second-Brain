# Order of bit: Start at LSB (rightmost) to MSB (leftmost)

# Definition: used for manipulating binary data
- "a | b" - *OR operation*: combine byte a and b together
- "a << b" - *Left shift*: shift byte a over b bits to the left
- "a >> b" - *Right shift*: shift byte a over b bits to the right

# Arithmetic Implication:
## >> N is division by  $2^N$
- *Odd number* is truncated. Eg: 11 >> 1 = 5
- Example:
	- $10_{10}$ = $00001010_{2}$
	- $00001010_{2}$ >> 1 = $00000101_{2}$ = $5_{10}$
	- $10_{10}$ >> 1 = $5_{10}$ 
## << N is multiplication with $2^N$
## Advantages:
- Faster than division operations as they are CPU instructions. 