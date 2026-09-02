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


## Decide
_Which geometry did you select, and why? This is your first open design choice in the course — defend it._

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
