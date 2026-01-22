# Motion's variable
- *Inerital frame:* position (x, y), orientation ($\theta$)
$$p = p_1 = \xi_1 = \begin{bmatrix}
x \\
y \\
\theta \\

\end{bmatrix} = \begin{bmatrix}
x & y & \theta
\end{bmatrix}^T$$
- *Distance between wheels (d):* if d is small, the robot angular velocity is great
$$\omega = \frac{v_r - v_l}{d}$$
- You care more about velocity because you control it