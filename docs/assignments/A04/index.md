# A4 – Motor Mount

## Objective
The objective of this assignment is to design a motor mount for a [Brushed 24V DC Gear Motor](https://www.omc-stepperonline.com/brushed-24v-dc-gear-motor-3-6kg-cm-46rpm-w-99-5-1-planetary-gearbox-pa28-28245800-g100) that attaches to a rigid wall. This motor mount is specified to have two features designed with two purposes: yield strength and a set maximum deflection. This meant that I would be designing two motor mounts to fulfill each purpose respectively. I was given the choice of which material the mount would be made of, and I chose PLA because it is the cheapest and most common 3D printing filament. In this assignment, I was given a specified safety factor of 3 to design with, and I was instructed to ignore the weight of the motor itself. An example of this design is attached below:

<img width="123" height="99" alt="image" src="https://github.com/user-attachments/assets/7da73543-f57e-446b-b517-13a6d4a1c2a1" />

Figure 1: Shows the motor, the rigid wall, and the force received on the shaft of the motor, where P = 300 N




## Analyze
### Feature 1
To begin this project, I did research on different designs of motor mounts to get an idea of what motor mounts usually look like, as well as some common trends in their structure. I went to Google and searched for images of "Brushed Gear Motor Mounts" and found several results. A common theme across most of them is that they are L-shaped sheet metal with holes for a fastener to go through.

<img width="1275" height="671" alt="image" src="https://github.com/user-attachments/assets/067a3128-cd9f-4dba-90bc-73b6b0759e81" />

An immediate difference I noticed between the design constraints of my motor mount and the common motor mounts is that I would be making mine out of plastic, while theirs will be made out of metal. From noticing this discrepancy, I determined that the safety factor of 3 is quite necessary, as I would be using a standard motor within a weaker, non-standard assembly.

With this information in mind, I determined that my first step would be to draw a free body diagram of the feature of the mount that is attached to the motor. Given the loading described in Figure 1 (particularly with the $300\ N$ force on the end of the shaft of the motor, which is a certain distance from the feature), I determined that there would be normal and bending stress in this feature. Assuming the feature was perfectly rigid and attached to a fixed wall at the top, I began  calculating the forces within the feature as well as the reaction forces from the wall. By calculating these forces, I would then be able to determine what the cross-sectional geometry of the feature would be.

To model the forces experienced by the feature attached to the motor, I began by representing the motor shaft and the force on the shaft as a cantilever beam. By solving for the reaction forces in the "wall" of this model, I can understand the stress that the feature needs to withstand.

In order to solve this first free body diagram, I needed the shaft length. I found it from the motor's webpage. The shaft length was specified to be $18\ mm$

<img width="1168" height="543" alt="image" src="https://github.com/user-attachments/assets/ce713ee3-b6e3-45fc-b0c8-04cbefe5b86a" />

Using the shaft length, I was able to find the reaction forces within feature 1. They are specified as $R_y = 300N $ and $M_R =\ 5.4\ N \times m$. $M_R$ will be defined as the maximum bending moment experienced by feature 1.

With my reaction forces determined, I was then able to determine the cross-sectional geometry of the feature in the Z direction by using the bending stress equation ($\sigma = \frac{M_z \times c}{I_z}$


## Decide


## Communicate

