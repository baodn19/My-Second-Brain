# Source
- [StatQuest: Principal Component Analysis (PCA), Step-by-Step](https://www.youtube.com/watch?v=FgakZw6K1QQ)

# Overview
- *Purpose:* 
	- take > 3 dimension of data and make a 2-D PCA plot 
	- Decide which variable is most valuable for clustering the data
	- Show accuracy of the 2-D plot 
- *Eigenvector:* which direction is data most and least spread out
- *Eigenvalue:* the variance along directions

# Mechanism
## 2 variables (Singular Value Decomposition)
1. *Find average coordinate* of the variables and translate the whole plot so the average point is on the origin
2. *Find line of best fit (Principle Component 1 - PC1):* by finding the greatest distance from the origin to the data's projection on the line = Sum of squared distances = SS(distance); PC1 is a **linear combination** of variables
3. *Find eigenvector of PC1:* scale down so that the hypotenuse of the linear combination is 1; the proportion of each variable is **Loading Scores**
4. *Find PC2:* perpendicular to PC1
5. *Rotate plot* so PC1 is horizontal & reconstruct data points from projections on both PCs
6. *Find percentage of variation for each PC* with $\sum{PC} = PC1 + PC2$ 
- *Eigenvalues:* measure of variation
$$
\frac{SS(distances)}{n-1} = Eigenvalue
$$
$$
\sqrt{SS(distances)} = Singular Value
$$
- *# of PC:* the smaller between the # of variables or the # samples

## Convert to 2-D plot
- *Scree Plot:* a column plot that display the percentage of variation for each PC
	- >2 variables: Find the 2 highest PCs and convert data based on them
- *Steps:* 
	1. Eliminate unwanted PCs
	2. Following from **step 5** above