# A2 – Truss Stress Analysis

## Objective
- Design a lightweight planar truss using A500 steel or an alternative material.
- Create free body diagrams (FBDs) for joints and critical pins.
- Calculate the required cross-sectional area of truss elements with a safety factor.
- Determine pin sizes based on shear forces with a safety factor.
- Solve equations symbolically and numerically for both truss and pin design.
- Estimate the total weight of the truss and pins.
- Create a CAD model with accurate dimensions and connections.
- Compare CAD weight predictions with hand calculations.
- Document key engineering lessons learned from the process.

## Analyze
In this assignment, I was given the task of designing, modeling, and analyzing a truss made under the constraints given below:

<img width="317" height="215" alt="image" src="https://github.com/user-attachments/assets/147d608e-aeeb-4bd9-946d-023f22f86d3c" />

_Note: a = 0.4m, b = 0.3m. The cross sectional area of each element is to be identical.
The pins are to be identical to each other and each element is to have the same cross-sectional geometry._

I was free to choose what material the truss was made of, so I chose Grade C A500 steel. I chose this material because it is very strong relative to its weight, and because Grade C is the most common form of A500 Steel.
I also was given the freedom to choose a magnitude for the point force $P$ so long as it ranged between 25kN-30kN. I chose 30kN as the magnitude of $P$.

After deciding my conditions, I identified some specific attributes of the scenario given. Point $B$ contains a roller support and Point $A$ contains a pin support. This is a classic support combination, and its presence immediately let me know that the truss I will be creating will be in static equilibrium. The pin support at point A resists all 2D translational movement and it is also the only point where the truss would be able to rotate without the truss failing, were it not for the roller support at point $B$. The existence of this roller support and the fact that it is bordered by a rigid wall on two sides means that any translation caused by moment at A is being fully restricted, thus, the following truss is capable of static equilibrium.


## Decide
_Which geometry did you select, and why? This is your first open design choice in the course — defend it._

I selected a trapezoidal geometry because most trusses I come across feature shapes that can be made purely from triangles. 

<img width="396" height="359" alt="image" src="https://github.com/user-attachments/assets/be16126b-6a2f-4496-b509-8c7811206c5e" />

In order to move forward with any other calculations of this truss, I first needed to determine the lengths of each member. I identified them as below:

$L_{AB} = 3a = 1.2\ m$ 

$L_{CD} = a = 0.4\ m$ 

$L_{BC} = L_{AD} = \sqrt{a^2 + b^2} = 0.5\ m$ 

After specifying the lengths of each member, I then moved to solve the external forces symbolically.

<img width="435" height="401" alt="image" src="https://github.com/user-attachments/assets/e6e4389e-f337-45ba-acc0-57073c4655f4" />

In doing this, it took the sum of all external forces win the x and y direction, created  equalities out of them, and created definitions for each reaction force that involve our known applied force, $P$. I also took the sum of moments about $A$ in order to create a definition for $B_y$.

After solving symbolically I was then ready  to give numerical answers.

$A_x = 0\ kN$

$A_y = \frac{P}{3} = 10\ kN$

$B_y = -\frac{P}{3} = (-10\ kN)$ 

$P = 30\ kN$

I then moved to solve each joint in order to understand whether each member was under tension or compression and by what magnitude.

<img width="427" height="262" alt="image" src="https://github.com/user-attachments/assets/af7c65e8-7c16-4366-ade5-e90434ecbbc4" />

In solving joint $A$, I first identified my unknowns, forces $AD$ and $AB$, and my knowns, forces $A_x$ and $A_y$. 
I then solved for each using two equations of static equilibrium, one in the $x$-direction and one in the $y$-direction.
I repeated this process for each joint, shown below:

<img width="446" height="373" alt="image" src="https://github.com/user-attachments/assets/48ca02cd-971e-4e56-b1ea-4c78e4b562d0" />

<img width="372" height="344" alt="image" src="https://github.com/user-attachments/assets/8b5d4d78-0bae-4102-8ec8-fa818766cf80" />

After determining the forces within every member, I moved on to designing the cross-section of my members. 
In order to do so, I first had to list my knowns and unknowns:

**Knowns:**
- Internal Forces, Distances, External Forces, Factor of Safety (3.5, given in assignment instructions)

**Unknowns:**
- Yield Stress of Material, Cross-Sectional Area, Density of Material

After a quick google search I was able to find that the yield stress ($\sigma_y$) of Grade C A500 steel is about 317 MPa ([Source Here](https://alllandsteel.com/products/astm-a500-grade-c/)).

Before moving on to design the cross-section, I needed to add a specification. Since our factor of safety is 3.5, I used $\sigma_a = \frac{\sigma_y}{Factor\ of\ Safety}$ with $\sigma_a$ being actual stress. This equation divides the yield stress by the factor of safety in order to determine what stress the members will actually be designed to be withstand.

Using this equation, I determined that the actual stress would be $\sigma_a = \frac{317\ MPa}{3.5} \approx 90.57\ MPa$.

Stress is defined as $\sigma = \frac{Force}{Area}$, so we can determine that $A_{member} = \frac{F}{\sigma_a}$. However, we want to design the members to be able to withstand the greatest force within the system. We can identify this as the magnitude of $BC$, which is about $16.66\ kN$. Therefore $A_{member} = \frac{BC}{\sigma_a} = \frac{16.66\ kN}{90.57\ MPa} \approx 1.84 \times 10^-4\ m^2 = 184\ mm^2$

<img width="442" height="279" alt="image" src="https://github.com/user-attachments/assets/7ff8854c-ee5e-4d4a-ba41-aa56fce5ff60" />

With this, I have successfully identified that the cross-sectional area of the members should equal $184\ mm^2$

Next, I determined the weight of the truss. My plan to do this was to find the total volume , then multiply by the density of the material. In order to find the volume of each member, I multiplied the length of the member by the cross-sectional area. Then I found the density of Grade C A500 Steel to be $7850 \frac{kg}{m^3}$. After finding the density, I multiplied the volume of each member by the density of the material, to get the weight of each member, then I added all of them together and found that the truss weighs $\approx 2.1955\ kg$

<img width="425" height="437" alt="image" src="https://github.com/user-attachments/assets/33bceb8a-a749-4ea9-a69b-0c4fd7e3a3b5" />

After finding the cross-sectional area of the members, I had to specify the cross-sectional area of the pins. These pins, as specified by the assignment, are made of hardened tool steel with a yield shear strength of $170\ ksi$, a density of $0.278 \frac{lb}{in^3}$, and are to be designed with a factor of safety of 4.  In order to design these pins, I had to identify my knowns and unknowns once more:

**Knowns:**
- Internal Forces, Distances, External Forces, Factor of Safety (given as 4 in the assignment), Yield Shear Strength ($\tau$)

**Unknowns:**
- Cross-Sectional Area, Resultant Reaction Force

The first thing I needed to do was figure out my actual shear load ($\tau_a$). I found it to be $42.5\ ksi$. From there I was able to calculate the area of the pin by dividing the greatest reaction force by $\tau_a$. I then found that in its current state, my equation had a mismatch in units. I then performed unit conversion to get the shear stress from ksi to MPa, and found that the value was approximately 293 MPa. From there, I was finally able to calculate and found that the minimum cross-sectional area of my pins should be $1.0238 \times 10^-4\ m^2$.

<img width="358" height="230" alt="image" src="https://github.com/user-attachments/assets/0249bd2d-1e3a-4ca1-8271-e2e02d857bf4" />

Next, I needed to find the weight of my pins. This means I would once again be multiplying volume by density. I knew that the cross-section of my pins would be circular, as that is standard, however, determining the length of the pins required further work. In order to simply the problem, I determined that my members should have a square cross section, and then I was able to solve further with ease. By taking the square root of the cross-sectional area of my members, I was able to determine a side length, and I set the length of the pin to be equal to that side length. Multiplying the cross-sectional area of the pin by the side length netted me a volume per-pin of $1.388 \times 10^-6\ m^3$. If we recall from earlier, the density of each pin was given in $\frac{lb}{in^3}$, however, this gives yet another unit mismatch when put into an equation with our numeric value for volume. To compensate for this, I converted the density of each pin into Standard Index units and found that their density was $7695\ \frac{kg}{m^3}$. With this, I was finally able to calculate the weight of the pins and found that they were approximately 0.010684 kg each, and since there were 4 of them, all the pins together weighed 0.04273 kg.

<img width="345" height="288" alt="image" src="https://github.com/user-attachments/assets/2252b006-a258-4eed-8f54-feca4618e920" />

After that, it was time to make a CAD model. I started by creating a sketch that matched the dimensions.

<img width="648" height="379" alt="Screenshot 2026-09-02 205206" src="https://github.com/user-attachments/assets/e7f64f17-52d8-4309-a5e0-1ddec79bc81e" />

Then i extruded the sketch by the side length I determined (0.01356 m).

<img width="647" height="385" alt="Screenshot 2026-09-02 210209" src="https://github.com/user-attachments/assets/0139cada-ea00-4f34-847e-3a9e79a30bef" />

I then created 4 holes with the same cross-sectional area I determined for the pins.

<img width="649" height="388" alt="Screenshot 2026-09-02 210949" src="https://github.com/user-attachments/assets/e6a6f490-9f07-4ac3-8ed9-585344671d99" />

Then I began work on creating the pin. I created a circle sketch with a radius of about 0.0057m to get the correct area.

<img width="785" height="401" alt="Screenshot 2026-09-02 211100" src="https://github.com/user-attachments/assets/0aa5507b-2403-48ac-afe9-678309ff529f" />

Then I extruded it to the side length 0.01356 m so it would sit flush in the truss.

<img width="792" height="382" alt="Screenshot 2026-09-02 211239" src="https://github.com/user-attachments/assets/44178213-d513-4e17-855c-a0d43f62ef9c" />

I then assembled the pins into the truss.

<img width="785" height="383" alt="Screenshot 2026-09-02 211440" src="https://github.com/user-attachments/assets/34d99c10-6148-47d0-8cec-92afd6211117" />

First I had to set the pins as coincident along the curved surface.

<img width="650" height="389" alt="Screenshot 2026-09-02 211513" src="https://github.com/user-attachments/assets/fad34362-8053-45bd-801c-07b6e12fd37c" />

Then I set the flat side of the pin coincident with the flat side of the truss for the flush fit.

<img width="649" height="383" alt="Screenshot 2026-09-02 211719" src="https://github.com/user-attachments/assets/79b62b33-e4b0-448d-9ef7-236d2d6b3250" />

My truss's geometry is now complete!

<img width="607" height="479" alt="Screenshot 2026-09-02 213057" src="https://github.com/user-attachments/assets/7e307032-1393-4b4a-a383-f90e61c59323" />

I then had to set the material properties for the truss.


<img width="604" height="473" alt="Screenshot 2026-09-02 213409" src="https://github.com/user-attachments/assets/2ba80bc8-894b-4066-911a-b6321bd48907" />

I also set the material properties for the pins

<img width="356" height="499" alt="Screenshot 2026-09-02 213617" src="https://github.com/user-attachments/assets/09a7f42e-33fe-46be-9f22-b1369b0bc714" />

Then I let solidworks determine the mass properties and it determine my truss was 3.5kg.



## Communicate

After finishing the design of the truss, i then evaluated the most likely ways it could fail and ways that those failures can be circumvented. In order to do so, I used Google Gemini to review the most common forms of failure within a truss and identify which parts of my truss are most susceptible to each type.

**Discussion with Google Gemini:**

Prompt: what is the likelihood of different failure modes within a truss?

Response: Truss failures usually result from a chain reaction starting at a single critical point rather than simultaneous global collapse. The likelihood of different failure modes depends heavily on member orientation (compression vs. tension), material properties, joint details, and environmental conditions.

| Failure Mode | Likelihood | Primary Stress / Driver | Typical Mechanism |
| --- | --- | --- | --- |
| **Member Buckling** | **Very High** | Compression | Slender compression members sudden sideways deflection before reaching yield strength (Euler buckling or local flange buckling). |
| **Joint / Connection Failure** | **High** | Shear / Tension | Bolt shear, weld cracking, gusset plate tear-out, or punching shear at connections—often exacerbated by poor fabrication. |
| **Fatigue & Cyclic Cracking** | **Moderate to High** | Cyclic Tension | Micro-cracks propagating over time at weld toes or bolt holes due to repetitive dynamic loads (e.g., bridges, cranes). |
| **Tensile Yielding / Rupture** | **Moderate** | Axial Tension | Ductile yielding or sudden fracture across the net sectional area of a tension diagonal or bottom chord. |
| **Support / Foundation Failure** | **Low to Moderate** | Bearing / Settlement | Roller bearing seizure causing unexpected thermal bending moments, or pier settlement inducing unplanned forces. |
| **Out-of-Plane Buckling** | **Low** | Global Instability | Inadequate lateral bracing allowing the top chord or entire truss to buckle sideways out of its vertical plane. |

(10pt) Part 1 – Truss Members
Each truss member is under either tension or compression and may fail due to the applied loading. For each member:

Identify the expected failure mode (yielding, fracture, or buckling).
State whether the material is ductile or brittle.
Support your choice using stress comparisons and simple reasoning.
Propose a design modification that could reduce the likelihood of this failure.

Members AB, BC, and CD are under compression. These members are made of a ductile material (Grade C A500 Steel). The expected failure mode for these compression members is buckling.This is supported by comparing the critical buckling stress ($\sigma_{\text{cr}}$) to the material yield strength ($\sigma_y$). Because these members are relatively long and slender, their critical Euler buckling stress is lower than the material's yield strength ($\sigma_{\text{cr}} < \sigma_y$). As a result, the member will experience geometric instability and buckle laterally before the stress ever reaches the yield strength required to cause plastic yielding.We can reduce the likelihood of buckling by increasing the member's cross-sectional area or area moment of inertia ($I$), which raises the critical buckling stress ($\sigma_{\text{cr}}$) relative to the applied load.


Member AD is the only member which is under tension. It's also made of a ductile material (Grade C A500 Steel). Due to the fact that it is under tension, I believe that the most likely mode of failure for it is tensile yielding. This is supported by comparing the applied normal stress ($\sigma = \frac{F}{A}$) to the material's yield strength ($\sigma_y$). Because the member is loaded in tension, geometric instability (buckling) cannot occur ($\sigma_{\text{cr}}$ is not a factor). Instead, failure occurs if the internal normal stress meets or exceeds the material's yield strength ($\sigma \ge \sigma_y$), it will cause plastic deformation. We can reduce the likelihood of this failure by increasing the cross section of the member. By increasing the cross section we can reduce normal stress, keeping the material farther away from reaching yield strength while under the same load.

(10pt) Part 2 – Pin Connections

Identify the expected failure mode of the pin.
Support your answer with data from credible, known sources.
Propose a design modification to reduce the likelihood of this failure

The primary failure mode for the connecting pins is shear failure (the pin snaps across its cross-section due to sideways forces). Under heavy or repeated loads, bearing failure (crushing or denting of the pin's outer surface where it contacts the joint) can also happen.

According to standard engineering texts like Shigley’s Mechanical Engineering Design, structural metals fail in shear at much lower stress levels than in tension. Based on the Von Mises yield criterion, the shear yield strength ($\tau_y$) of a ductile metal is only about 57.7% of its tensile yield strength ($\sigma_y$):$$\tau_y \approx 0.577 \, \sigma_y$$Because shear strength is significantly lower than tensile strength, pins under heavy loads are prone to shear failure whenever the applied shear stress exceeds the pin's allowable shear strength:$$\tau = \frac{F_{\text{shear}}}{A_{\text{pin}}} \ge \tau_y$$

We can prevent this issue by using a double-shear joint (like a clevis fork). Double shear splits the shear force in half across two sides of the pin ($\tau = \frac{F}{2 A_{\text{pin}}}$), doubling the joint's load capacity without needing a bigger pin.


### Lessons Learned
- From this exercise I learned the ins and outs of designing parts and structures as well as how to communicate my process effectively. I also learned how to use the LaTex language!
- This assignment took me about 9 hours to complete

**Key Risk Drivers:**

* **Compression members are the most vulnerable:** Buckling occurs instability-first, giving far less warning than ductile tensile yielding.
* **Connections are the weak link:** Real-world failures disproportionately originate at gusset plates or welded joints due to stress concentrations and fabrication flaws.

## Find CAD Files below
- https://github.com/ilittle8/design-projects-portfolio/blob/main/docs/assignments/A02/Truss.SLDPRT
- https://github.com/ilittle8/design-projects-portfolio/blob/main/docs/assignments/A02/Pin.SLDPRT
- https://github.com/ilittle8/design-projects-portfolio/blob/main/docs/assignments/A02/Full%20Truss%20Assembly.SLDASM

