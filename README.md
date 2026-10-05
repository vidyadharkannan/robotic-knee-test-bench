# Collaborative Robot-Based Test Bench for Knee Motion Simulation and ICR Estimation

**Master's Thesis — LS2N, École Centrale de Nantes**  
**February 2026 – August 2026**

This project was carried out as part of my Master's thesis at LS2N (Laboratoire des Sciences du Numérique de Nantes).

## Why This Project?

<p align="justify">
Meniscus repair techniques need to be mechanically evaluated before clinical use. At CHU Poitiers, repaired cadaveric knees are subjected to repeated gait-like flexion–extension cycles to evaluate the stability of the repair. A collaborative robot is used to provide controlled and repeatable cyclic motion during these experiments.
</p>

<p align="justify">
However, reproducing physiological knee motion with a robot is not straightforward. The human knee does not behave like a simple hinge with a fixed centre of rotation. During flexion and extension, the femur undergoes a combination of rolling and sliding relative to the tibia, causing the Instantaneous Centre of Rotation (ICR) to migrate throughout the motion.
</p>

## Problem Statement

<p align="justify">
In the existing robotic test setup, the knee motion is approximated using a fixed centre of rotation. An impedance-based compliant controller compensates for the difference between this fixed centre and the actual motion of the knee.
</p>

<p align="justify">
Although this compliance allows the robot to accommodate the motion, it also slows the flexion–extension cycle and increases the execution time of the experimental protocol.
</p>

<p align="justify">
The objective of my Master's thesis was therefore to estimate the migrating knee ICR and incorporate it into a velocity-based robot control strategy. The aim was to enable the robot to follow the changing centre of rotation during flexion–extension, reducing reliance on compliance and potentially shortening the execution time of the experimental protocol.
</p>

## Proposed Approach

<p align="justify">
The objective of this work was to develop a collaborative robot-based knee test bench capable of following the migrating knee ICR during flexion–extension.
</p>

The work was structured around four main questions:

1. **ICR Estimation** — Can the knee ICR trajectory be estimated from measured knee kinematic data?

2. **Cross Four-Bar Design** — Can the geometric parameters of a cross four-bar mechanism be optimised to reproduce the estimated ICR trajectory?

3. **Robot Control** — Can the Franka Research 3 (FR3) reproduce flexion–extension while following the moving ICR trajectory?

4. **Interaction Adaptation** — Can interaction-wrench information from repeated cycles be used to adapt the desired ICR trajectory?

## 1. ICR Estimation

### Reconstructing the Knee ICR

<p align="justify">
The first step was to determine how the centre of rotation of the knee changes during flexion–extension. I used tibiofemoral kinematic data from the University of Denver Living Kinematics of the Knee dataset (https://digitalcommons.du.edu/living_kinematics_knee/1/), measured using high-speed stereo radiography. The flexion–extension (FE) angle, together with the anterior–posterior (AP) and superior–inferior (SI) translations, was used to reconstruct the motion of the tibia in the sagittal plane.
</p>

<p align="justify">
To estimate the Instantaneous Centre of Rotation, I used the Reuleaux geometric method. Two reference points were considered rigidly attached to the tibia, and their positions were reconstructed at consecutive configurations. The perpendicular bisectors of their displacements intersect at the instantaneous centre of rotation.
</p>

<p align="justify">
Repeating this calculation throughout the motion produced a reference trajectory showing how the knee ICR migrates during flexion–extension.
</p>

