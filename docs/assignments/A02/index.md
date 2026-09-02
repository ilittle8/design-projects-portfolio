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


## Communicate


Discussion with Google Gemini:

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

Members AB, BC, and CD are under compression. These members are made of a ductile material (Grade C A500 Steel). The expected failure mode of these members is buckling. This is due to the fact that they are relatively slender in cross-section, which makes them more liekly to deflect sideways before reaching yield strength. We can reduce the likelihood of this failure by increasing the cross-sections of the members. By increasing the cross section we create more material to resist a potential bending moment that would cause beam deflection.

Member AD is the only member which is under tension. It is also made of a ductile material (Grade C A500 Steel). Due to the fact that it is under tension, I believe that the most likely mode of failure for it is tensile yielding. We can reduce the likelihood of this failure by increasing the cross section of the member. By increasing the cross section we can reduce normal stress, keeping the material farther away from reaching yield strength while under the same load.

(10pt) Part 2 – Pin Connections

Identify the expected failure mode of the pin.
Support your answer with data from credible, known sources.
Propose a design modification to reduce the likelihood of this failure

**Key Risk Drivers:**

* **Compression members are the most vulnerable:** Buckling occurs instability-first, giving far less warning than ductile tensile yielding.
* **Connections are the weak link:** Real-world failures disproportionately originate at gusset plates or welded joints due to stress concentrations and fabrication flaws.
