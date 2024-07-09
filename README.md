# 3-DoF-Robot-Arm-Kinematics

# Task 3: Calculate Inverse and Forward Kinematics for a Robot with 3 Degrees of Freedom 

## Description
This task involves calculating the Forward Kinematics (FK) and Inverse Kinematics (IK) for a robotic arm with 3 Degrees of Freedom (DoF). The goal is to determine the position and orientation of the robot's end-effector based on the joint angles (FK) and to find the required joint angles to achieve a desired end-effector position (IK).

## Forward Kinematics (FK)

Forward Kinematics involves determining the position and orientation of the robot's end-effector (usually a gripper or tool) based on the joint angles.

### Steps for FK:

1. **Define the Transformation Matrices for each Joint:**
Each joint's transformation matrix depends on its respective joint angle (\(\theta_i\)) and link length (\(L_i\)).

*
   For Joint 1:
   ```math
   T_1 = \begin{bmatrix}
   \cos(\theta_1) & -\sin(\theta_1) & 0 & L1 \cos(\theta_1) \\
   \sin(\theta_1) & \cos(\theta_1) & 0 & L1 \sin(\theta_1) \\
   0 & 0 & 1 & 0 \\
   0 & 0 & 0 & 1 \\
   \end{bmatrix}
*
   For Joint 2:
   ```math
   T_2 = \begin{bmatrix}
   \cos(\theta_2) & -\sin(\theta_2) & 0 & L2 \cos(\theta_2) \\
   \sin(\theta_2) & \cos(\theta_2) & 0 & L2 \sin(\theta_2) \\
   0 & 0 & 1 & 0 \\
   0 & 0 & 0 & 1 \\
   \end{bmatrix}
*
   For Joint 3:
   ```math
   T_3 = \begin{bmatrix}
   \cos(\theta_3) & -\sin(\theta_3) & 0 & L3 \cos(\theta_3) \\
   \sin(\theta_3) & \cos(\theta_3) & 0 & L3 \sin(\theta_3) \\
   0 & 0 & 1 & 0 \\
   0 & 0 & 0 & 1 \\
   \end{bmatrix}

2. **Compute the Overall Transformation Matrix:**
Combine the transformation matrices of all joints to get the overall transformation from the base to the end-effector.
To write the multiplication of transformation matrices \(T = T_1 \times T_2 \times T_3\) in GitHub Markdown, you can use LaTeX notation within math blocks for better clarity. GitHub supports rendering LaTeX for mathematical expressions.
   \[
   T = T_1 \times T_2 \times T_3
   \]

3. **Extract the End-Effector Position:**

   The position of the end-effector in the workspace can be obtained from the translation part of the final transformation matrix \( T \).

   \[
   [x, y, z] = [T_{14}, T_{24}, T_{34}]
   \]

## Inverse Kinematics (IK)

Inverse Kinematics involves determining the joint angles (\(\theta_1, \theta_2, \theta_3\)) that achieve a desired end-effector position.

### Steps for IK:

1. **Specify the Desired End-Effector Position:**

   Choose the desired position \((x_d, y_d, z_d)\) in the workspace where you want the end-effector to move.

2. **Calculate \(\theta_1\):**

   \[
   \theta_1 = \arctan2(y_d, x_d)
   \]

3. **Calculate \(r\) and \(D\):**

   First, calculate \(r\):
   \[
   r = \sqrt{x_d^2 + y_d^2}
   \]

   Then, calculate \(D\):
   \[
   D = \frac{r^2 - L1^2 - L2^2}{2 \cdot L1 \cdot L2}
   \]

4. **Calculate \(\theta_2\):**

   \[
   \theta_2 = \arctan2(\sqrt{1 - D^2}, D)
   \]

5. **Calculate \(\theta_3\):**

   \[
   \theta_3 = \arctan2(z_d - L1, r) - \theta_2 - \theta_1
   \]

## Example Calculation

Let's go through a quick example:

- Assume \(L1 = 2\), \(L2 = 2\), \(L3 = 1\).
- Desired end-effector position \((x_d, y_d, z_d) = (3, 3, 0)\).

1. **Calculate \(\theta_1\):**

   \[
   \theta_1 = \arctan2(3, 3) = 45^\circ
   \]

2. **Calculate \(r\):**

   \[
   r = \sqrt{3^2 + 3^2} = \sqrt{18} \approx 4.24
   \]

3. **Calculate \(D\):**

   \[
   D = \frac{4.24^2 - 2^2 - 2^2}{2 \cdot 2 \cdot 2} = \frac{18 - 4 - 4}{8} = 1.25
   \]

4. **Calculate \(\theta_2\):**

   \[
   \theta_2 = \arctan2(\sqrt{1 - 1.25^2}, 1.25) \approx \arctan2(0.75, 1.25) \approx 30.96^\circ
   \]

5. **Calculate \(\theta_3\):**

   \[
   \theta_3 = \arctan2(0 - 2, 4.24) - 30.96^\circ - 45^\circ
   \]
   \[
   \theta_3 \approx \arctan2(-2, 4.24) - 30.96^\circ - 45^\circ \approx -18.43^\circ
   \]

These calculated angles \(\theta_1 \approx 45^\circ\), \(\theta_2 \approx 30.96^\circ\), and \(\theta_3 \approx -18.43^\circ\) would position the end-effector at the desired coordinates.

## References

- [Forward Kinematics](https://en.wikipedia.org/wiki/Forward_kinematics)
- [Inverse Kinematics](https://en.wikipedia.org/wiki/Inverse_kinematics)

If you need further clarification or have specific questions about any part of the process, feel free to ask!
```



## Acknowledgments
