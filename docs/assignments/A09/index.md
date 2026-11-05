# A9 – Pulleys
# Belt Drive Design – MEGR 2156 Assignment 8

## 1. Project Overview

This project involves designing a belt-drive assembly connecting two parallel shafts. The design includes pulley selection, belt sizing, shaft sizing, journal-bearing analysis, and a supporting frame.

The assembly was modeled in SolidWorks to visualize the relationship between the pulleys, shafts, and support structure.

## 2. Design Specifications

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

- Pulley diameter: $D=3\text{ in}$
- Center distance: $C=5\text{ in}$
- Rotational speed: $N=1500\text{ rpm}$
- Initial static tension: $5\text{ lbf}$ per belt span
- Belt yield strength: $\sigma_y=471\text{ psi}$
- Factor of safety: $SF=3$
- Assumed coefficient of friction: $\mu=0.5$
- Angle of contact: $\theta=180^\circ=\pi\text{ rad}$

### 3.2 Belt Tension Ratio

The relationship between the tight-side and loose-side belt tensions is estimated using the capstan equation:

$$
\frac{T_1}{T_2}=e^{\mu\theta}
$$

Substituting the assumed friction coefficient and contact angle:

$$
\frac{T_1}{T_2}=e^{(0.5)(\pi)}
$$

$$
\frac{T_1}{T_2}\approx4.81
$$

Therefore:

$$
T_2=\frac{T_1}{4.81}
$$

The initial total belt tension is:

$$
T_1+T_2=10\text{ lbf}
$$

Substituting:

$$
T_1+\frac{T_1}{4.81}=10
$$

Solving:

$$
T_1\approx8.28\text{ lbf}
$$

$$
T_2\approx1.72\text{ lbf}
$$

These values use the assumed friction coefficient and the assumption that the total tension remains 10 lbf during operation.

### 3.3 Transmitted Torque

The torque transmitted through the pulley is calculated using the difference between the belt tensions:

$$
\tau=(T_1-T_2)r
$$

The pulley radius is:

$$
r=\frac{3}{2}=1.5\text{ in}
$$

Substituting:

$$
\tau=(8.28-1.72)(1.5)
$$

$$
\boxed{\tau\approx9.84\text{ lbf}\cdot\text{in}}
$$

### 3.4 Minimum Belt Cross-Sectional Diameter

The minimum belt cross-sectional area is determined by limiting the belt stress to the allowable stress:

$$
\sigma_{\text{allow}}=\frac{\sigma_y}{SF}
$$

Using the tight-side tension:

$$
\frac{\sigma_y}{SF}=\frac{T_1}{A}
$$

Rearranging:

$$
A=\frac{T_1(SF)}{\sigma_y}
$$

For a circular belt cross-section:

$$
A=\frac{\pi d^2}{4}
$$

Combining the equations:

$$
d=\sqrt{\frac{4T_1(SF)}{\pi\sigma_y}}
$$

Substituting:

$$
d=\sqrt{\frac{4(8.28)(3)}{\pi(471)}}
$$

$$
\boxed{d_{\min}\approx0.259\text{ in}}
$$

This is the calculated minimum diameter based on the assumed tensile-stress model.

### 3.5 Belt Length

For two equal-diameter pulleys, the approximate open-belt length is:

$$
L=2C+\pi D
$$

Substituting:

$$
L=2(5)+\pi(3)
$$

$$
\boxed{L\approx19.43\text{ in}}
$$

This is an approximate pitch-line length. The actual belt length should be checked against the selected belt's dimensions and the pulley groove geometry.

### 3.6 Selected Belt

The handwritten design notes identify the selected belt as:

**McMaster-Carr belt designation: `30 4K608`**

The selected belt should be checked against the calculated minimum cross-sectional diameter and the required belt length before finalizing the design.

---

## 4. Part 2 – Shaft Design

### 4.1 Known Values

- Shaft material: 1060 hardened steel
- Applied torque: approximately $9.84\text{ lbf}\cdot\text{in}$
- Factor of safety: 3
- Shear yield strength used in the calculation: approximately $86.6\text{ ksi}$

### 4.2 Torsional Shear Stress

For a solid circular shaft, the maximum torsional shear stress is:

$$
\tau_{\max}=\frac{Tc}{J}
$$

Using:

$$
c=\frac{d}{2}
$$

and:

$$
J=\frac{\pi d^4}{32}
$$

The equation becomes:

$$
\tau_{\max}=\frac{16T}{\pi d^3}
$$

Applying the factor of safety:

$$
\frac{\tau_y}{SF}=\frac{16T}{\pi d^3}
$$

Rearranging for the minimum shaft diameter:

$$
d=\sqrt[3]{\frac{16T(SF)}{\pi\tau_y}}
$$

Substituting:

$$
d=\sqrt[3]{\frac{16(9.837)(3)}
{\pi(86.6\times10^3)}}
$$

$$
\boxed{d_{\text{shaft}}\approx0.120\text{ in}}
$$

The selected shaft diameter is therefore approximately 0.120 in based on the torsional loading calculation.

This calculation considers torsion. Additional bending loads, stress concentrations, and shaft deflection should be considered if required by the final design analysis.

---

## 5. Part 3 – Journal Bearing Design

### 5.1 Known Values

- Shaft diameter: $d=0.120\text{ in}$
- Bearing length: $L=0.500\text{ in}$
- Rotational speed: $N=1500\text{ rpm}$
- Total radial belt force used: $10\text{ lbf}$
- Number of bearings sharing the load: 2
- Assumed load per bearing: $5\text{ lbf}$
- Selected bearing material: Maple

### 5.2 Bearing Surface Velocity

The linear surface velocity is:

$$
V=\frac{\pi dN}{12}
$$

The factor of 12 converts inches per minute to feet per minute.

Substituting:

$$
V=\frac{\pi(0.120)(1500)}{12}
$$

$$
\boxed{V\approx47.12\text{ ft/min}}
$$

### 5.3 Projected Bearing Pressure

The projected bearing pressure is:

$$
P=\frac{F}{dL}
$$

Using the assumed 5 lbf load on each bearing:

$$
P=\frac{5}{(0.120)(0.500)}
$$

$$
\boxed{P\approx83.33\text{ psi}}
$$

The calculation assumes that the two bearings share the total radial load equally.

### 5.4 Pressure-Velocity (PV) Value

The pressure-velocity value is calculated using:

$$
PV=P V
$$

Substituting:

$$
PV=(83.33)(47.12)
$$

$$
\boxed{PV\approx3927\text{ psi}\cdot\text{ft/min}}
$$

The selected bearing material is Maple. Its allowable pressure and PV rating should be compared with these calculated values using the assigned Machinery's Handbook reference (Table 4, page 2440).

The bearing material should not be considered verified until both limits have been checked.

---

## 6. Part 4 – Frame and SolidWorks Assembly

The SolidWorks assembly represents the overall pulley-drive arrangement, including the two pulleys, shafts, and connecting support structure.

### Assembly Features

- Two 3-inch pulleys
- Two parallel shafts
- 5-inch pulley center distance
- Shaft extensions through the pulley centers
- Connecting structural members supporting the assembly

### Frame Design Considerations

The frame must support the shafts and bearings while maintaining pulley alignment. It should also resist the forces produced by belt tension without excessive deformation.

Important design considerations include:

1. Maintaining the 5-inch center distance between pulley axes.
2. Keeping both shafts parallel.
3. Providing adequate support for the journal bearings.
4. Preventing excessive frame deflection under belt loading.
5. Providing sufficient clearance for the pulleys and belt.

The SolidWorks assembly provides a visual representation of the design layout. Final frame strength and stiffness still need to be evaluated separately.

---

## 7. Lessons Learned

This design process demonstrated how the different components of a belt-drive system are connected.

- Belt tension determines the torque that can be transmitted through the pulleys.
- The difference between tight-side and loose-side tension determines transmitted torque.
- Belt cross-sectional area must be sufficient to keep tensile stress below the allowable stress.
- Shaft diameter has a significant effect on torsional stress because stress varies inversely with the cube of the diameter.
- Journal-bearing pressure depends on the applied radial load and the projected contact area.
- Bearing selection requires checking both pressure and pressure-velocity limits.
- Frame stiffness and shaft alignment are important for maintaining reliable belt operation.
- Engineering calculations depend on assumptions, so material properties, friction coefficients, and load distributions must be verified before finalizing a design.
