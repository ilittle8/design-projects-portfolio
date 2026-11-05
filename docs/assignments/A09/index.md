# A9 – Pulleys
# Belt Drive Design – MEGR 2156 Assignment 8

**CAD File:** [A09Assembly.SLDASM](https://github.com/ilittle8/design-projects-portfolio/blob/main/docs/assignments/A09/A09Assembly.SLDASM)

## 1. Project Overview

For this project, I designed a belt-drive assembly connecting two parallel shafts. My design involved selecting and sizing the belt, calculating the required shaft diameter, analyzing the journal bearings, and developing a supporting frame.

I modeled the assembly in SolidWorks to visualize how the pulleys, shafts, and support structure fit together. I used engineering calculations throughout the design process to determine the dimensions and material selections for the individual components.

## 2. Design Specifications

The following table summarizes the specifications and component selections I used for my design.

| Parameter | Selected Value |
|---|---:|
| Pulley diameter | 3 in |
| Center distance | 5 in |
| Rotational speed | 1,500 rpm |
| Initial static belt tension | 5 lbf per span |
| Total initial belt tension | 10 lbf |
| Pulley material | Aluminum |
| Belt material | Polyurethane rubber |
| Belt yield strength | 471 psi |
| Assumed friction coefficient | 0.5 |
| Required factor of safety | 3 |
| Shaft material | 1060 hardened steel |
| Shaft diameter | 0.120 in |
| Bearing material | Maple |
| Bearing length | 0.500 in |
| Bearings per shaft | 2 |

---

## 3. Part 1 – Belt Design

### 3.1 Known Values

I began my belt design by identifying the required pulley dimensions, center distance, rotational speed, and initial belt tension.

- Pulley diameter: $D=3\text{ in}$
- Center distance: $C=5\text{ in}$
- Rotational speed: $N=1500\text{ rpm}$
- Initial static tension: $5\text{ lbf}$ per belt span
- Belt yield strength: $\sigma_y=471\text{ psi}$
- Factor of safety: $SF=3$
- Assumed coefficient of friction: $\mu=0.5$
- Angle of contact: $\theta=180^\circ=\pi\text{ rad}$

### 3.2 Belt Tension Ratio

<img width="902" height="265" alt="image" src="https://github.com/user-attachments/assets/816b88cb-a27a-48c8-874c-322486e613cb" />

I used the capstan equation to estimate the relationship between the tight-side and loose-side belt tensions:

$$
\frac{T_1}{T_2}=e^{\mu\theta}
$$

I substituted my assumed friction coefficient and contact angle:

$$
\frac{T_1}{T_2}=e^{(0.5)(\pi)}
$$

$$
\frac{T_1}{T_2}\approx4.81
$$

This gave me the following relationship:

$$
T_2=\frac{T_1}{4.81}
$$

Since I used an initial static tension of 5 lbf per span, I calculated the total initial tension as:

$$
T_1+T_2=10\text{ lbf}
$$

I substituted the tension relationship into this equation:

$$
T_1+\frac{T_1}{4.81}=10
$$

Solving for each tension gave me:

$$
T_1\approx8.28\text{ lbf}
$$

$$
T_2\approx1.72\text{ lbf}
$$

These values are based on my assumed friction coefficient and the assumption that the total tension remains 10 lbf during operation.

### 3.3 Transmitted Torque

After calculating the belt tensions, I determined the torque transmitted through the pulley using the difference between the tight-side and loose-side tensions:

$$
\tau=(T_1-T_2)r
$$

Since my pulley diameter is 3 inches, I calculated its radius as:

$$
r=\frac{3}{2}=1.5\text{ in}
$$

Substituting my calculated tensions:

$$
\tau=(8.28-1.72)(1.5)
$$

$$
\boxed{\tau\approx9.84\text{ lbf}\cdot\text{in}}
$$

I used this calculated torque as the basis for my shaft design.

### 3.4 Minimum Belt Cross-Sectional Diameter

<img width="747" height="283" alt="image" src="https://github.com/user-attachments/assets/f4193a58-83f5-46ba-848a-b1bca312039c" />

I calculated the minimum belt cross-sectional area by limiting the belt stress to the allowable stress.

First, I determined the allowable stress using the belt yield strength and required factor of safety:

$$
\sigma_{\text{allow}}=\frac{\sigma_y}{SF}
$$

I then related the allowable stress to the tight-side belt tension:

$$
\frac{\sigma_y}{SF}=\frac{T_1}{A}
$$

Rearranging for the required cross-sectional area:

$$
A=\frac{T_1(SF)}{\sigma_y}
$$

Since I was working with a circular belt cross-section, I used:

$$
A=\frac{\pi d^2}{4}
$$

Combining these equations allowed me to solve for the minimum belt diameter:

$$
d=\sqrt{\frac{4T_1(SF)}{\pi\sigma_y}}
$$

Substituting my values:

$$
d=\sqrt{\frac{4(8.28)(3)}{\pi(471)}}
$$

$$
\boxed{d_{\min}\approx0.259\text{ in}}
$$

This gave me a calculated minimum belt diameter of approximately 0.259 inches based on the tensile-stress model I used.

### 3.5 Belt Length

I calculated the approximate belt length using the equation for an open belt connecting two equal-diameter pulleys:

$$
L=2C+\pi D
$$

Substituting my center distance and pulley diameter:

$$
L=2(5)+\pi(3)
$$

$$
\boxed{L\approx19.43\text{ in}}
$$

This gave me an approximate pitch-line length of 19.43 inches. The actual belt length depends on the selected belt dimensions and pulley groove geometry.

### 3.6 Selected Belt

Based on my belt selection, I identified the McMaster-Carr belt as:

**McMaster-Carr belt designation: `304K608`**

I used my calculated minimum belt diameter and approximate belt length as reference values when evaluating my belt selection.

---

## 4. Part 2 – Shaft Design

### 4.1 Known Values

After determining the transmitted torque, I moved on to sizing the shafts. I selected 1060 hardened steel as my shaft material and used the calculated torque from my belt analysis.

- Shaft material: 1060 hardened steel
- Applied torque: approximately $9.84\text{ lbf}\cdot\text{in}$
- Factor of safety: 3
- Shear yield strength used in my calculation: approximately $86.6\text{ ksi}$

### 4.2 Torsional Shear Stress

<img width="600" height="166" alt="image" src="https://github.com/user-attachments/assets/957a3b51-e39e-4b03-9922-efd975c0a735" />

I used the torsional shear stress equation for a solid circular shaft:

$$
\tau_{\max}=\frac{Tc}{J}
$$

For a solid circular shaft, the outer radius is:

$$
c=\frac{d}{2}
$$

The polar moment of inertia is:

$$
J=\frac{\pi d^4}{32}
$$

Substituting these relationships into the torsional shear stress equation gave me:

$$
\tau_{\max}=\frac{16T}{\pi d^3}
$$

I incorporated my required factor of safety into the equation:

$$
\frac{\tau_y}{SF}=\frac{16T}{\pi d^3}
$$

I then rearranged the equation to solve for the minimum shaft diameter:

$$
d=\sqrt[3]{\frac{16T(SF)}{\pi\tau_y}}
$$

Substituting my values:

$$
d=\sqrt[3]{\frac{16(9.837)(3)}
{\pi(86.6\times10^3)}}
$$

$$
\boxed{d_{\text{shaft}}\approx0.120\text{ in}}
$$

Based on this calculation, I selected a shaft diameter of approximately 0.120 inches.

My calculation considers torsional loading. Additional bending loads, stress concentrations, and shaft deflection would also need to be considered if they are significant in the final design.

---

## 5. Part 3 – Journal Bearing Design

<img width="1002" height="297" alt="image" src="https://github.com/user-attachments/assets/5bbbee3a-9706-4e44-8c2b-79c8811ec73f" />

### 5.1 Known Values

For my journal bearing design, I selected maple and used a bearing length of 0.500 inches. I also designed the arrangement with two bearings supporting each shaft.

The values I used for my calculations were:

- Shaft diameter: $d=0.120\text{ in}$
- Bearing length: $L=0.500\text{ in}$
- Rotational speed: $N=1500\text{ rpm}$
- Total radial belt force used: $10\text{ lbf}$
- Number of bearings sharing the load: 2
- Assumed load per bearing: $5\text{ lbf}$
- Selected bearing material: Maple

### 5.2 Bearing Surface Velocity

I calculated the linear surface velocity of the shaft using:

$$
V=\frac{\pi dN}{12}
$$

I included the conversion factor of 12 to convert inches per minute into feet per minute.

Substituting my shaft diameter and rotational speed:

$$
V=\frac{\pi(0.120)(1500)}{12}
$$

$$
\boxed{V\approx47.12\text{ ft/min}}
$$

### 5.3 Projected Bearing Pressure

I calculated the projected bearing pressure using:

$$
P=\frac{F}{dL}
$$

I assumed that the two bearings supporting each shaft would share the total 10 lbf radial load equally. This gave me an estimated load of 5 lbf per bearing.

Substituting:

$$
P=\frac{5}{(0.120)(0.500)}
$$

$$
\boxed{P\approx83.33\text{ psi}}
$$

This result depends on my assumption that the bearing reactions are equal.

### 5.4 Pressure-Velocity (PV) Value

I calculated the pressure-velocity value to evaluate the bearing's operating conditions:

$$
PV=P V
$$

Substituting my calculated bearing pressure and surface velocity:

$$
PV=(83.33)(47.12)
$$

$$
\boxed{PV\approx3927\text{ psi}\cdot\text{ft/min}}
$$

I selected maple as my bearing material. To verify this selection, I need to compare my calculated pressure and PV values against the allowable values provided in the assigned Machinery's Handbook reference, Table 4, page 2440.

I will use both limits to determine whether maple is suitable for my design.

---

## 6. Part 4 – Frame and SolidWorks Assembly

<img width="2560" height="1380" alt="Screenshot 2026-11-04 204546" src="https://github.com/user-attachments/assets/61ac3f2e-937a-4b5e-96fc-43bcbb7b5c67" />

I created a SolidWorks assembly to represent the overall layout of my belt-drive system. My model includes the two pulleys, shafts, and connecting structural members.

### Assembly Features

My current assembly includes:

- Two 3-inch pulleys.
- Two parallel shafts.
- A 5-inch center distance between pulley axes.
- Shaft extensions through the pulley centers.
- Connecting structural members supporting the assembly.

### Frame Design Considerations

When developing my frame, I considered how it would support the shafts and bearings while maintaining the alignment of the two pulleys.

The main design considerations I identified were:

1. Maintaining the 5-inch center distance between pulley axes.
2. Keeping both shafts parallel.
3. Providing adequate support for the journal bearings.
4. Preventing excessive frame deflection under belt loading.
5. Providing sufficient clearance for the pulleys and belt.

My SolidWorks assembly provides a visual representation of how the individual components fit together. The frame's strength and stiffness would still need to be evaluated separately.

---

## 7. Lessons Learned

I spent approximately **6 hours** completing this project.

Throughout the design process, I learned how the different components of a belt-drive system depend on one another.

- I learned how belt tension determines the torque that can be transmitted through the pulleys.
- I used the difference between tight-side and loose-side tension to calculate transmitted torque.
- I learned how important belt cross-sectional area is when evaluating tensile stress and selecting a belt.
- I saw how strongly shaft diameter affects torsional stress because stress varies inversely with the cube of the diameter.
- I learned how journal-bearing pressure depends on the applied load and projected contact area.
- I learned that selecting a bearing requires checking both pressure and pressure-velocity limits.
- I also gained a better understanding of how frame stiffness and shaft alignment affect the overall reliability of a mechanical assembly.
- Finally, I learned that engineering calculations depend on assumptions, making it important to verify material properties, friction coefficients, and load distributions before finalizing a design.

Overall, this project helped me connect the theoretical equations I learned in class to the practical process of designing and assembling a mechanical power-transmission system.
