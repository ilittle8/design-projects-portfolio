# A4 – Motor Mount

## Objective
The objective of this assignment is to design a motor mount for a [Brushed 24V DC Gear Motor](https://www.omc-stepperonline.com/brushed-24v-dc-gear-motor-3-6kg-cm-46rpm-w-99-5-1-planetary-gearbox-pa28-28245800-g100) that attaches to a rigid wall. This motor mount is specified to have two features designed with two purposes: yield strength and a set maximum deflection. This meant that I would be designing two motor mounts to fulfill each purpose respectively. I was given the choice of which material the mount would be made of, and I chose PLA because it is the cheapest and most common 3D printing filament. In this assignment, I was given a specified safety factor of 3 to design with, and I was instructed to ignore the weight of the motor itself. An example of this design is attached below:

<img width="123" height="99" alt="image" src="https://github.com/user-attachments/assets/7da73543-f57e-446b-b517-13a6d4a1c2a1" />

Figure 1: Shows the motor, the rigid wall, and the force received on the shaft of the motor, where P = 300 N

<img width="1625" height="505" alt="image" src="https://github.com/user-attachments/assets/3670b2c4-61d1-4a19-9504-d348bd6f8352" />


Figure 2: Dimensions of the gear motor in mm




## Analyze
### Feature 1
To begin this project, I did research on different designs of motor mounts to get an idea of what motor mounts usually look like, as well as some common trends in their structure. I went to Google and searched for images of "Brushed Gear Motor Mounts" and found several results. A common theme across most of them is that they are L-shaped sheet metal with holes for a fastener to go through.

<img width="1275" height="671" alt="image" src="https://github.com/user-attachments/assets/067a3128-cd9f-4dba-90bc-73b6b0759e81" />

An immediate difference I noticed between the design constraints of my motor mount and the common motor mounts is that I would be making mine out of plastic, while theirs will be made out of metal. From noticing this discrepancy, I determined that the safety factor of 3 is quite necessary, as I would be using a standard motor within a weaker, non-standard assembly.

With this information in mind, I determined that my first step would be to draw a free body diagram of the feature of the mount that is attached to the motor. Given the loading described in Figure 1 (particularly with the $300\ N$ force on the end of the shaft of the motor, which is a certain distance from the feature), I determined that there would be normal and bending stress in this feature. Assuming the feature was perfectly rigid and attached to a fixed wall at the top, I began  calculating the forces within the feature as well as the reaction forces from the wall. By calculating these forces, I would then be able to determine what the cross-sectional geometry of the feature would be.

To model the forces experienced by the feature attached to the motor, I began by representing the motor shaft and the force on the shaft as a cantilever beam. By solving for the reaction forces in the "wall" of this model, I can understand the stress that the feature needs to withstand.

In order to solve this first free body diagram, I needed the shaft length. I found it from the motor's webpage. The shaft length was specified to be $18\ mm$

<img width="1168" height="543" alt="image" src="https://github.com/user-attachments/assets/ce713ee3-b6e3-45fc-b0c8-04cbefe5b86a" />

#### Designing for Strength

Using the shaft length, I was able to find the reaction forces within feature 1. They are specified as $R_y = 300N$ and $M_R =\ 5.4\ N \times m$. $M_R$ will be defined as the maximum bending moment experienced by feature 1. I also looked up the yield stress ($\sigma_y$) of PLA plastic and found it to be $25\ MPa$. I then divided that yield stress by the safety factor ($S.F. = 3$) to get my allowable stress ($\sigma_{all}$ or $\sigma_{allow}$).

With my reaction forces and allowable stress determined, I was then able to determine the cross-sectional geometry of the feature in the Z direction by using the bending stress equation ($\sigma = \frac{M_z \times c}{I_z}$). I intentionally set the height and depth of my feature to be 2mm greater to the diameter of the motor ($8\ mm$) so that I could isolate one variable within the moment of inertia ($I_z$) equation to make solving possible.I chose 8mm so that when I was creating feature 2, I could keep a consistent depth and still have enough space for the fasteners. Using this, I determined that the length and base of the motor mount would be $8\ mm$, and the thickness would be $\approx 22\ mm$. I made this choice so that the motor would have an appropriate amount of surface area to connect with the motor mount.

#### Designing for Deflection

After designing the motor mount with strength as the primary constraint, I then began designing the motor mount again, but with maximum deflection as my primary constraint. For this assignment, my maximum deflection was set to be $0.30\ mm$ ($\delta = 0.30\ mm$). In order to solve for geometry with deflection from bending as my constraint, I needed to use the equation for deflection in a cantilever beam. An important note is that, from the perspective of the feature, there is an axial force and a bending moment being applied in the middle of it. Since axial forces do not generate moment, we can ignore them with regard to deflection. The equation for deflection at the free end of a cantilever with a moment loading is $\delta_{max} = -\frac{3ML^2}{8EI}$.

In the previous equation, there are a few unknowns: the base and height of the y-direction cross section (where deflection occurs), the length of the feature, and the elastic modulus. We already know the moment from previous work, and we already know the maximum deflection. To make solving easier, I determined that the length of the feature and the base of its y-direction cross section should be equal to 2mm plus the motor diameter ($8\ mm$), and I looked up the elastic modulus of PLA plastic and found it to be $2.0\ GPa$. After making these determinations, the final unknown was the height of the y-direction cross-section.

After solving, I found the thickness of the motor mount to be $6.24\ mm$. With this, the dimensions of this version of feature one were $8\ mm$ length, $8\ mm$ depth, and $6.87\ mm$ thickness.

### Feature 2
In planning my approach to design feature 2, I remembered something about the motor mounts I had searched up earlier... **they all had consistent depth**. I realized that if I maintained consistent thickness throughout my design, not only would calculating but manufacturing be easier. As such, I decided that the cross-sectional depth of feature two would be equal to that of feature 1 when designing for strength and deflection, respectively. I also decided to make feature two out of the same material as feature 1 (PLA plastic), as that would be the easiest to model and manufacture.

#### Desiging for Strength
Knowns: Depth, Elastic modulus, yield stress, allowed stress, bending moment
Unkowns: Thickness, Second Moment of Area
When desigining feature 2 for strength, I was able to use the bending stress equation once again, but with a key nuance: the term $I$ has changed. Rather than jusst being $\frac{bh^3}{12}$, the second moment of area, due to the existence of holes in the structure for 3.4 mm diameter screws, had become $\frac{h^3}{12}(b-2d)$. With this, I was able to rearrange the eqution to solve for the thickness of feature two and found it to be $56.9\ mm$.

#### Desigining for Deflection
When observing the maximum deflectiion question using the information gathered by previous steps, I found that the unkowns within this problem were length and depth of the feature. For length. Since I was assigned to solve for cross-sectional geometry, I decided that I would arbitrarily choose 8mm to be the length of the feature, as that is the length of feature 1. With this, my last unknown was thickness. I rearranged the maximum deflection equation to solve for thickness and then solved numerically. I found my thickness to be $\approx 12.93\  mm$
## Decide
#### CAD Modeling
When I finally got to modeling my motor mount in CAD, I realixed that the shape I had designed was very odd and nothing like the other motor mounts I had seen. With this in mind, I decided to edit the design. I set the length of feature 2 to be the thickness of feature 1 + 8mm. here is the result:
<img width="1280" height="764" alt="image" src="https://github.com/user-attachments/assets/8456f10b-62a2-4661-9896-b2fc93a67e75" />

Then I added 4 holes to the mount design

<img width="1280" height="764" alt="image" src="https://github.com/user-attachments/assets/244b97db-b35c-432e-bf3e-d273d0273336" />

I then added a hole with the diameter of the motor shaft (6mm) to the first feature
<img width="1280" height="764" alt="image" src="https://github.com/user-attachments/assets/31a8840a-fd3e-4761-a98c-fa1b7db53d31" />

Here is the CAD file for the part





## Communicate

