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
  ```
   T = T_1 x T_2 x T_3
  ```

3. **Extract the End-Effector Position:**
The position of the end-effector in the workspace can be obtained from the translation part of the final transformation matrix 𝑇.
  ```
   [x,y,z] = [T_14, T_24, T_34]
  ```

## Inverse Kinematics (IK)

Inverse Kinematics involves determining the joint angles (
𝜃
1
,
𝜃
2
,
𝜃
3
θ 
1
​
 ,θ 
2
​
 ,θ 
3
​
 ) that achieve a desired end-effector position.

### Steps for FK:

1. **Define the Transformation Matrices for each Joint:**
Each joint's transformation matrix depends on its respective joint angle (\(\theta_i\)) and link length (\(L_i\)).





If you need further clarification or have specific questions about any part of the process, feel free to ask!
```



## Acknowledgments
