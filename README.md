# 3-DoF-Robot-Arm-Kinematics

# Task 3: Calculate Inverse and Forward Kinematics for a Robot with 3 Degrees of Freedom 

## Description
This task involves calculating the Forward Kinematics (FK) and Inverse Kinematics (IK) for a robotic arm with 3 Degrees of Freedom (DoF). The goal is to determine the position and orientation of the robot's end-effector based on the joint angles (FK) and to find the required joint angles to achieve a desired end-effector position (IK).

## Forward Kinematics (FK)

Forward Kinematics involves determining the position and orientation of the robot's end-effector (usually a gripper or tool) based on the joint angles.

### Steps for FK:

1. **Define the Transformation Matrices for each Joint:**
Each joint's transformation matrix depends on its respective joint angle (θ_i) and link length (L_i).

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

Inverse Kinematics involves determining the joint angles (𝜃_1, 𝜃_2, 𝜃_3) that achieve a desired end-effector position.

### Steps for IK:

1. **Specify the Desired End-Effector Position:**
Choose the desired position (𝑥_𝑑, 𝑦_d, 𝑧_𝑑) in the workspace where you want the end-effector to move.

2. **Calculate 𝜃_1:**
<p align="center">
  <img src="https://github.com/GDHadeel/3-DoF-Robot-Arm-Kinematics/assets/126657301/b6e31758-a511-4c3d-8be5-a13313ac7167" alt="Robotic Arm Image 1" width="700" height="100">
</p>

3. **Calculate 𝑟 and 𝐷:**
First, calculate 𝑟:
<p align="center">
  <img src="https://github.com/GDHadeel/3-DoF-Robot-Arm-Kinematics/assets/126657301/b0d1fca8-0d00-4248-a705-b1d018c00e48" alt="Robotic Arm Image 1" width="700" height="100">
</p>
 Then, calculate 𝐷:
<p align="center">
  <img src="https://github.com/GDHadeel/3-DoF-Robot-Arm-Kinematics/assets/126657301/16031153-b1db-4c2d-a3af-d7f7c87ee621" alt="Robotic Arm Image 1" width="700" height="100">
</p>

4. **Calculate θ_2:**
<p align="center">
  <img src="https://github.com/GDHadeel/3-DoF-Robot-Arm-Kinematics/assets/126657301/a9076ed9-d04d-4683-9b68-88cdcca45ed2" alt="Robotic Arm Image 1" width="700" height="100">
</p>

5. **Calculate θ_3:**
<p align="center">
  <img src="https://github.com/GDHadeel/3-DoF-Robot-Arm-Kinematics/assets/126657301/d36ff166-459d-4269-88da-08f18abbfc86" alt="Robotic Arm Image 1" width="700" height="100">
</p>

### Example Calculation:
* Assume 𝐿_1 = 2, L2 = 2, 𝐿_3 = 1
* Desired end-effector position (x_d, y_d, z_d) = (3,3,0).



1. **Calculate θ_1:**
<p align="center">
  <img src="https://github.com/GDHadeel/3-DoF-Robot-Arm-Kinematics/assets/126657301/36221a36-f623-4549-ac98-508ffd1045a1" alt="Robotic Arm Image 1" width="700" height="100">
</p>

2. **Calculate 𝑟:**
<p align="center">
  <img src="https://github.com/GDHadeel/3-DoF-Robot-Arm-Kinematics/assets/126657301/c0ec7972-ba03-4d58-a7c7-c86180e2a9ca" alt="Robotic Arm Image 1" width="700" height="100">
</p>

3. **Calculate 𝐷:**
<p align="center">
  <img src="https://github.com/GDHadeel/3-DoF-Robot-Arm-Kinematics/assets/126657301/f4ec5f07-ce5f-4eca-9913-e25221eba795" alt="Robotic Arm Image 1" width="700" height="100">
</p>

4. **Calculate θ_2:**
<p align="center">
  <img src="https://github.com/GDHadeel/3-DoF-Robot-Arm-Kinematics/assets/126657301/9134da76-ee69-45a9-a5a1-6449d54de761" alt="Robotic Arm Image 1" width="700" height="100">
</p>

5. **Calculate θ_3:**
<p align="center">
  <img src="https://github.com/GDHadeel/3-DoF-Robot-Arm-Kinematics/assets/126657301/18bff842-96e7-4b54-a44f-c9a917338444" alt="Robotic Arm Image 1" width="700" height="100">
</p>

  ```
θ_3 ≈ arctan2 (−2,4.24) − 30.96 − 45 ≈ −18.43 degrees
  ```

These calculated angles 𝜃_1 ≈ 45, θ_2 ≈ 30.96, and 𝜃_3 ≈ −18.43 would position the end-effector at the desired coordinates.

## Acknowledgments
https://www.youtube.com/watch?v=1-FJhmey7vk
