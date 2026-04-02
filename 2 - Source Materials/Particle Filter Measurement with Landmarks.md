---
created: 2026-03-31
modified: April 2nd 2026, 3:52:57 pm
---
When evaluating a particle filter in an environment with known landmarks, the measurement model relies on computing Euclidean distances rather than direct obstacle detection (like "walls").

1. **Observe Distances:** The robot gathers distance measurements to each landmark in the space (e.g., $z_{L_1}, z_{L_2}, z_{L_3}, z_{L_4}$).
2. **Compute Expected Distances:** For every individual cell or particle state, compute the geometric distance from the center of that cell to each landmark.
3. **Normal Probabilities:** Compare the robot's actual sensor measurement ($z$) to the expected distance of the cell using normal distributions. Calculate the normal probability ($N_z$) for the cell in relation to each specific landmark [19].
4. **Weighted Probabilities:** To find the overall likelihood of the robot being in that specific cell, compute the weighted probabilities for $z$ with respect to all landmarks [19, 20]. This is done by multiplying the normal probabilities of each landmark together [19, 20].
    - *Formula:* $W_{z} = N_{z, L_1} \times N_{z, L_2} \times N_{z, L_3} \times N_{z, L_4}$ [19, 20].
