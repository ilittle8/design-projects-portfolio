# Motor Selection, Bracket Design, and Coupler Selection - Isaiah Little

## Motor Bracket CAD Files below:
### Solidworks Part File:
https://github.com/ilittle8/design-projects-portfolio/blob/main/docs/assignments/a11/A11%20Motor%20Bracket.SLDPRT

### STEP File:
https://github.com/ilittle8/design-projects-portfolio/blob/main/docs/assignments/a11/A11%20Motor%20Bracket.STEP


## 1. Project Overview

The objective of this project is to design a motorized leadscrew system for a tensile tester. The system uses two leadscrews to produce controlled linear motion of the crosshead.

The design uses one stepper gearmotor per leadscrew. Each motor independently drives one screw, allowing the system to provide the required motion while distributing the torque demand between two motors.

The primary design considerations documented here are the leadscrew geometry, required rotational speed, operating torque, and motor torque-speed performance.

## 2. Leadscrew Geometry

The selected leadscrew is a single-start Acme screw with a nominal diameter of $1/4$ inch and $20$ threads per inch.

For a single-start screw, the lead is equal to the thread pitch:

$$
L = \frac{1}{20}\text{ in/rev}
$$

Converting the lead to millimeters:

$$
L = \frac{25.4}{20}
$$

$$
\boxed{L = 1.27\text{ mm/rev}}
$$

Therefore, one complete revolution of the leadscrew produces $1.27$ mm of linear travel.

## 3. Leadscrew Operating Torque

The calculated operating torque required to drive one leadscrew is:

$$
\boxed{T_{\text{operating}} = 0.635\text{ N}\cdot\text{m}}
$$

Because the design uses two independent motors, each motor is responsible for supplying the operating torque of one leadscrew.

The total operating torque across both screws is:

$$
T_{\text{total}} = 2T_{\text{operating}}
$$

$$
T_{\text{total}} = 2(0.635)
$$

$$
\boxed{T_{\text{total}} = 1.27\text{ N}\cdot\text{m}}
$$

A design factor of safety of $4$ is used to establish the required motor torque.

For each motor:

$$
T_{\text{design}} = 4T_{\text{operating}}
$$

$$
T_{\text{design}} = 4(0.635)
$$

$$
\boxed{T_{\text{design}} = 2.54\text{ N}\cdot\text{m}}
$$

Thus, each motor must provide at least $2.54\text{ N}\cdot\text{m}$ under the relevant operating conditions.

## 4. Motor Selection

The selected motor candidate is the McMaster-Carr NEMA 23 stepper gearmotor, part number 4801N14.

### McMaster Carr Link:
https://www.mcmaster.com/4801N14/

The design uses one motor per leadscrew. Consequently, the motor must independently satisfy the torque and rotational-speed requirements of a single screw.

### 4.1 Required Motor Speed

The assignment specifies a crosshead linear velocity range of $1$ to $50\text{ mm/min}$.

The relationship between linear velocity and screw rotational speed is:

$$
n = \frac{v}{L}
$$

where:

- $n$ is the rotational speed in RPM.
- $v$ is the crosshead linear velocity in mm/min.
- $L$ is the leadscrew lead in mm/rev.

At the minimum crosshead velocity:

$$
n_{\min} = \frac{1}{1.27}
$$

$$
\boxed{n_{\min} = 0.79\text{ RPM}}
$$

At the maximum crosshead velocity:

$$
n_{\max} = \frac{50}{1.27}
$$

$$
\boxed{n_{\max} = 39.37\text{ RPM}}
$$

Therefore, each motor must operate over an approximate speed range of:

$$
\boxed{0.79\text{–}39.37\text{ RPM}}
$$

### 4.2 Torque-Speed Curve Evaluation

The motor's torque-speed curve was evaluated using the manufacturer's published performance data. The referenced curve specifies operation at $24\text{ V DC}$ and $2.2\text{ A}$ using half-stepping.

At approximately $40\text{ RPM}$, the curve indicates an available torque of roughly $700\text{ oz}\cdot\text{in}$.

Converting this value to SI units:

$$
1\text{ oz}\cdot\text{in} = 0.0070616\text{ N}\cdot\text{m}
$$

$$
T_{\text{available}} = 700(0.0070616)
$$

$$
\boxed{T_{\text{available}} \approx 4.94\text{ N}\cdot\text{m}}
$$

The available torque is compared with the required design torque for one motor:

$$
4.94\text{ N}\cdot\text{m} > 2.54\text{ N}\cdot\text{m}
$$

The estimated available torque at the maximum required operating speed exceeds the design torque requirement.

The ratio of estimated available torque to operating torque is:

$$
\frac{T_{\text{available}}}{T_{\text{operating}}} = \frac{4.94}{0.635} 
$$

$$
\boxed{\frac{T_{\text{available}}}{T_{\text{operating}}}\approx 7.78}
$$

This comparison indicates that the motor candidate has sufficient estimated torque capacity at approximately the maximum required screw speed, based on the manufacturer's torque-speed curve.

## 5. Motor Selection Summary

The selected design uses two NEMA 23 stepper gearmotors, with one motor driving each leadscrew.

<img width="1050" height="811" alt="image" src="https://github.com/user-attachments/assets/13ddc33e-5d81-4014-808f-88b20b8ae267" />


The calculated requirements for each motor are:

- Operating torque: $0.635\text{ N}\cdot\text{m}$
- Design torque, using a factor of safety of $4$: $2.54\text{ N}\cdot\text{m}$
- Required rotational speed: $0.79$ – $39.37\text{ RPM}$
- Estimated available torque near $40\text{ RPM}$: $4.94\text{ N}\cdot\text{m}$

<img width="1045" height="773" alt="image" src="https://github.com/user-attachments/assets/3d7df07f-5f37-4ea5-845e-2b41d151fd31" />


Based on the approximate torque-speed curve reading, the selected motor candidate exceeds the calculated design torque requirement at the maximum required operating speed.


## 6. Task 2 — Motor Mount Design

### Knowns

| Parameter | Value |
|---|---:|
| Mount configuration | Adapter plate mounted between the motor bracket and tester frame |
| Motor mounting bracket | Supplied with the selected motor |
| Plate width | 2.90 in |
| Plate length | 2.90 in |
| Selected plate thickness | 0.125 in (1/8 in) |
| Plate material | AISI 1018 cold-drawn steel |
| Assumed material yield strength | 53,700 psi |
| Motor-side mounting pattern | 1.95 in × 1.95 in |
| Motor bracket hole diameter | 0.217 in |
| Frame-side mounting pattern | 2.65 in × 2.65 in |
| Frame-side fastener diameter | 0.250 in |
| Number of motor-side mounting locations | 4 |
| Number of frame-side mounting locations | 4 |
| Operating torque per motor | 5.62 lb·in |
| Frame-side bolt-pattern radius | 1.874 in |
| Calculated frame-side force per fastener | 0.750 lbf |
| Allowable bearing stress | 13,425 psi |
| Calculated minimum plate thickness | 0.000224 in |
| Selected plate thickness compared with calculated minimum | 0.125 in |

### Unknowns

| Parameter | Information Needed |
|---|---|
| Motor-side fasteners | Final fastener diameter, thread size, and length |
| Motor-side tapped holes | Required thread engagement and available plate thickness for tapping |
| Frame-side fasteners | Final bolt length, grade, and thread engagement |
| Frame material | Exact material and properties of the tester frame |
| Plate attachment | Final details of how the plate is secured to the frame |
| Alignment | Final verification that the motor output shaft is aligned with the leadscrew |
| Structural validation | Further verification of the plate, fasteners, and complete torque load path |


### 6.1 Mounting Plate Design

I designed a horizontal steel adapter plate to connect the motor's existing mounting bracket to the top of the tensile tester frame. The adapter plate provides four mounting locations for the motor bracket and four additional mounting locations for attachment to the frame.
<img width="743" height="962" alt="image" src="https://github.com/user-attachments/assets/555e6371-8495-4a90-9fd5-a275b322631e" />

The selected plate dimensions are:

- Plate width: $2.90$ in
- Plate length: $2.90$ in
- Selected material: AISI 1018 cold-drawn steel
- Selected plate thickness: $0.125$ in ($1/8$ in)

The assumed yield strength of AISI 1018 cold-drawn steel is:

$$
S_y=53,700\text{ psi}
$$

### 6.2 Bearing Stress Analysis

I evaluated the bearing stress at the frame-side mounting holes to determine the minimum required plate thickness.

The allowable bearing stress is calculated using the required factor of safety of 4:

$$
\sigma_{b,\text{allow}}=\frac{S_y}{N}
$$

$$
\sigma_{b,\text{allow}}=\frac{53,700}{4}
$$

$$
\boxed{\sigma_{b,\text{allow}}=13,425\text{ psi}}
$$

The operating torque per motor is:

$$
T=0.635\text{ N}\cdot\text{m}
$$

Converting to pound-inches:

$$
T=0.635(8.8507)
$$

$$
T=5.62\text{ lb}\cdot\text{in}
$$

The outer frame mounting pattern consists of four holes arranged in a square with a center-to-center spacing of 2.65 in.

The radius from the center of the bolt pattern to each mounting hole is:

$$
r_f=\sqrt{\left(\frac{2.65}{2}\right)^2+
\left(\frac{2.65}{2}\right)^2}
$$

$$
\boxed{r_f=1.874\text{ in}}
$$

Assuming equal torque distribution among the four mounting fasteners, the force per fastener is:

$$
F_f=\frac{T}{4r_f}
$$

$$
F_f=\frac{5.62}{4(1.874)}
$$

$$
\boxed{F_f=0.750\text{ lbf}}
$$

The bearing stress relationship is:

$$
\sigma_b=\frac{F}{td}
$$

Rearranging to solve for the minimum plate thickness:

$$
t_{\min}=\frac{F}{d\sigma_{b,\text{allow}}}
$$

Using a $0.250$ in frame-side fastener diameter:

$$
t_{\min}=\frac{0.750}{(0.250)(13,425)}
$$

$$
\boxed{t_{\min}=0.000224\text{ in}}
$$

### 6.3 Final Plate Thickness Selection

Based on the bearing-stress calculation, the minimum required plate thickness is approximately $0.000224$ in.

I selected a final plate thickness of:

$$
\boxed{t_{\text{selected}}=0.125\text{ in}}
$$

The selected thickness is substantially greater than the calculated minimum bearing thickness. I chose a standard $1/8$ in steel plate as a practical thickness for the motor adapter.

The calculated minimum is based specifically on the frame-side bearing-stress model and equal distribution of the motor's operating torque among the four frame mounting fasteners. The selected thickness is therefore a preliminary design selection rather than a complete verification of every possible plate failure mode.

### 6.4 CAD Drawing

### Frame-Side Mounting Holes

I designed the adapter plate with four tapped 10-32 holes to secure it to the frame. The holes are arranged in a square pattern with a center-to-center spacing of 2.40 in in both directions. This updated pattern replaces my previous 2.65 in spacing and 1/4 in fastener selection. I did this in order to make sure all the holes fit into my 2.9 inch bracket length and width.

<img width="950" height="792" alt="image" src="https://github.com/user-attachments/assets/4241f902-8a71-44e1-be51-c8cf3da11a57" />

## Task 3 — Coupler Selection and Torsional Analysis

### 1. Coupler Selection

I selected the **NBK MJC-30-WH-6.35-16 jaw-type flexible shaft coupling** to connect the motor output shaft to the leadscrew.

I chose this coupling because it accommodates the two different shaft diameters and provides a rated torque greater than the required design torque.

| Specification | Selected Coupler |
|---|---:|
| Manufacturer | NBK |
| Part number | MJC-30-WH-6.35-16 |
| Coupling type | Jaw-type flexible coupling |
| Outside diameter, $D_o$ | 30 mm |
| Motor-side bore, $D_{i,1}$ | 16 mm |
| Leadscrew-side bore, $D_{i,2}$ | 6.35 mm |
| Overall length | 35 mm |
| Hub material | A2017 aluminum |
| Spider material | Polyurethane |
| Rated torque | 7.5 N·m |
| Maximum torque | 15 N·m |

Manufacturer reference: [NBK MJC-30-WH-6.35-16](https://www.nbk1560.com/en-US/products/coupling/couplicon/jaw_type/MJC-WH/MJC-30-WH/MJC-30-WH-6.35-16/)

The selected coupling has a rated torque of 7.5 N·m. The required design torque is 2.54 N·m, giving a rated-torque margin of:

$$
\text{Torque Margin}=\frac{7.5}{2.54}=2.95
$$

Therefore, the coupling's published rated torque is approximately 2.95 times the required design torque.

### 2. Known and Unknown Variables

**Known variables**

| Variable | Description | Value |
|---|---|---:|
| $T_{op}$ | Operating torque per motor | 0.635 N·m |
| $N$ | Design factor of safety | 4 |
| $T_d$ | Design torque per coupling | 2.54 N·m |
| $D_o$ | Coupling outside diameter | 30 mm |
| $D_{i,1}$ | Motor-side bore diameter | 16 mm |
| $D_{i,2}$ | Leadscrew-side bore diameter | 6.35 mm |
| $S_{rated}$ | Manufacturer rated torque | 7.5 N·m |

The design torque is:

$$
T_d=NT_{op}
$$

$$
T_d=4(0.635)=2.54\text{ N}\cdot\text{m}
$$

**Unknown variables and assumptions**

- The exact A2017 aluminum alloy temper and corresponding yield strength need to be confirmed.
- The actual internal geometry of the coupling hubs must be verified from the manufacturer's drawing.
- The torsional analysis initially treats each hub as a uniform hollow circular shaft.
- The coupling's published torque rating is used as a separate catalog-level capacity check.

### 3. Free-Body Diagram — Torsional Loading

Each motor drives one leadscrew through its own coupling. Therefore, each coupling transmits the torque from one motor rather than the combined torque of both motors.

The applied design torque is:

$$
T_d=2.54\text{ N}\cdot\text{m}
$$

The internal resisting torque in the coupling is equal in magnitude and opposite in direction to the applied torque.

<img width="876" height="653" alt="image" src="https://github.com/user-attachments/assets/dd41d27a-2cf3-4982-9163-7312ab5e4e06" />


The coupling is modeled as a hollow circular shaft under pure torsion.

### 4. Torsional Shear Stress Equations

The maximum torsional shear stress in a hollow circular shaft is:

$$
\tau_{max}=\frac{Tc}{J}
$$

For a hollow circular cross-section:

$$
J=\frac{\pi}{32}(D_o^4-D_i^4)
$$

Since the maximum radial distance is:

$$
c=\frac{D_o}{2}
$$

Substituting these relationships gives:

$$
\tau_{max}=
\frac{16TD_o}
{\pi(D_o^4-D_i^4)}
$$

The radial wall thickness is:

$$
t=\frac{D_o-D_i}{2}
$$

For a material-based design, the allowable shear stress would also need to be established from the verified material properties and selected safety factor.

### 5. Numerical Solution

I evaluated the two coupling bores separately because the motor shaft and leadscrew have different diameters.

All dimensions are converted to meters for the stress calculations.

**Motor-side hub**

Given:

$$
T=2.54\text{ N}\cdot\text{m}
$$

$$
D_o=0.030\text{ m}
$$

$$
D_{i,1}=0.016\text{ m}
$$

Calculate the polar moment of inertia:

$$
J_1=\frac{\pi}{32}
\left(0.030^4-0.016^4\right)
$$

$$
J_1=7.309\times10^{-8}\text{ m}^4
$$

Calculate the maximum shear stress:

$$
\tau_{max,1}=
\frac{2.54(0.030/2)}
{7.309\times10^{-8}}
$$

$$
\boxed{\tau_{max,1}=0.5213\text{ MPa}}
$$

Calculate the radial wall thickness:

$$
t_1=\frac{30-16}{2}
$$

$$
\boxed{t_1=7.00\text{ mm}}
$$

**Leadscrew-side hub**

Given:

$$
T=2.54\text{ N}\cdot\text{m}
$$

$$
D_o=0.030\text{ m}
$$

$$
D_{i,2}=0.00635\text{ m}
$$

Calculate the polar moment of inertia:

$$
J_2=\frac{\pi}{32}
\left(0.030^4-0.00635^4\right)
$$

$$
J_2=7.936\times10^{-8}\text{ m}^4
$$

Calculate the maximum shear stress:

$$
\tau_{max,2}=
\frac{2.54(0.030/2)}
{7.936\times10^{-8}}
$$

$$
\boxed{\tau_{max,2}=0.4801\text{ MPa}}
$$

Calculate the radial wall thickness:

$$
t_2=\frac{30-6.35}{2}
$$

$$
\boxed{t_2=11.825\text{ mm}}
$$

### 6. Results and Selection

| Parameter | Motor-Side Hub | Leadscrew-Side Hub |
|---|---:|---:|
| Outside diameter | 30 mm | 30 mm |
| Inside diameter | 16 mm | 6.35 mm |
| Radial wall thickness | 7.00 mm | 11.825 mm |
| Polar moment of inertia | $7.309\times10^{-8}$ m⁴ | $7.936\times10^{-8}$ m⁴ |
| Maximum shear stress | 0.5213 MPa | 0.4801 MPa |

The motor-side hub experiences the greater calculated torsional shear stress because its larger bore leaves less material to resist the applied torque.

The selected coupling has a manufacturer-rated torque of 7.5 N·m, compared with the required design torque of 2.54 N·m. Based on the catalog torque rating, the selected coupling has sufficient rated torque capacity for this selection.






