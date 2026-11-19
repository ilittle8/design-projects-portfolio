# Motor Selection, Bracket Design, and Coupler Selection - Isaiah Little

## Motor Bracket CAD Files below:

### Solidworks Part File:

https://github.com/ilittle8/design-projects-portfolio/blob/main/docs/assignments/a11/A11%20Motor%20Bracket%20(Remake).SLDPRT

### STEP File:

https://github.com/ilittle8/design-projects-portfolio/blob/main/docs/assignments/a11/A11%20Motor%20Bracket%20(Remake).STEP

### Motor Mount SolidWorks Drawing File:

https://github.com/ilittle8/design-projects-portfolio/blob/main/docs/assignments/a11/A11%20Motor%20Bracket%20(Remake).SLDDRW

<img width="1500" height="1151" alt="image" src="https://github.com/user-attachments/assets/0d66c746-da42-420e-a386-1db363f278bd" />



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

### McMaster Carr Link (CAD FILES CAN BE FOUND IN LINK):
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

## 6. Task 2 — Motor Mount Design REVISION

### Knowns

| Parameter | Value |
|---|---:|
| Mount configuration | Custom motor bracket mounted between the motor and tester frame |
| Bracket width | 2.90 in |
| Bracket length | 2.90 in |
| Bracket overall height | 1.71875 in |
| Central coupling bore diameter | 1.078125 in |
| Inner motor-side holes | Four tapped blind holes |
| Inner tapped-hole depth | 0.859375 in |
| Outer frame-side holes | Four tapped through-holes |
| Plate/bracket material | AISI 1018 cold-drawn steel (previously selected; verify for revised part) |
| Assumed material yield strength | 53,700 psi |
| Motor-side mounting pattern | 1.95 in × 1.95 in (verify against current CAD) |
| Motor bracket hole diameter | 0.217 in (existing motor-bracket interface dimension) |
| Frame-side mounting pattern | 2.40 in × 2.40 in |
| Frame-side thread | 10-32 tapped through-holes |
| Number of inner motor-side mounting locations | 4 |
| Number of outer frame-side mounting locations | 4 |

### Unknowns

| Parameter | Information Needed |
|---|---|
| Motor-side fasteners | Final fastener diameter, thread size, and length for the four inner tapped holes |
| Inner blind-hole engagement | Verify that 0.859375 in of tapped depth provides sufficient thread engagement |
| Frame-side fasteners | Final 10-32 fastener length, grade, and engagement |
| Coupling clearance | Verify the actual coupling outside diameter and whether additional clearance is needed around the 1.078125 in bore |
| Coupling installation | Verify that both hubs and the spider can be installed and rotate without contacting the bracket |
| Frame material | Exact material and properties of the tester frame |
| Alignment | Verify that the motor output shaft, coupling, and leadscrew are properly aligned |
| Structural validation | Verify the revised bracket, tapped holes, fasteners, and complete torque load path using the final CAD geometry |

### 6.1 Revised Motor Bracket Design

I redesigned the motor bracket to accommodate the McMaster-Carr L050 spider coupling. The revised geometry provides a central opening for the coupling and separate mounting locations for attaching the motor and the bracket to the tensile tester frame.

The updated bracket has an overall height of **1.71875 in**. I selected this dimension to match the full assembled height of the L050 spider coupling.

I also added a central through-hole with a diameter of **1.078125 in**. This opening is sized to match the outside diameter of the coupling so that the coupling can occupy the center of the bracket without interfering with its rotation. The actual coupling dimensions should be checked against the supplier drawing, and the bore clearance should be verified before manufacturing.

The revised bracket uses two separate sets of tapped holes:

- **Inner motor-mounting holes:** I added four tapped blind holes to secure the motor to the bracket. Each hole has a tapped depth equal to one-half of the bracket's overall height.

$$
d_{\text{inner}}=\frac{1.71875}{2}
$$

$$
\boxed{d_{\text{inner}}=0.859375\text{ in}}
$$

- **Outer frame-mounting holes:** I added four tapped holes that extend completely through the bracket. These holes secure the bracket to the tensile tester frame.

The inner holes are used exclusively to attach the motor, while the outer holes are used to attach the bracket to the frame. Separating these mounting locations allows the motor and coupling to be positioned within the bracket while maintaining a separate frame attachment.

The existing material selection is AISI 1018 cold-drawn steel, with an assumed yield strength of:

$$
S_y=53,700\text{ psi}
$$

The material selection and assumed yield strength must be verified for the revised bracket before completing the final structural analysis.


### 6.2 Revised Bracket Geometry and Mounting Arrangement

The final bracket geometry incorporates the following dimensions:

| Feature | Dimension |
|---|---:|
| Overall bracket height | 1.71875 in |
| Central through-hole diameter | 1.078125 in |
| Inner tapped-hole depth | 0.859375 in |
| Frame-side mounting pattern | 2.40 in × 2.40 in |
| Frame-side thread | 10-32 |
| Number of inner tapped holes | 4 |
| Number of outer tapped through-holes | 4 |

The center opening accommodates the L050 coupling, while the inner and outer tapped holes provide the two separate mounting interfaces.

The four outer frame-side holes are arranged in a square pattern with a center-to-center spacing of 2.40 in in both directions. This pattern replaces my previous 2.65 in spacing and 1/4 in fastener selection. I selected the 2.40 in pattern to keep the mounting holes within the 2.90 in bracket length and width.

The four inner tapped blind holes secure the motor to the bracket. Their tapped depth is 0.859375 in, which is half of the bracket's overall height.

<img width="710" height="506" alt="image" src="https://github.com/user-attachments/assets/c1b1e081-ebb6-478b-9bd1-45f9dc671cf7" />


### 6.3 Structural Analysis and Verification

The previous bearing-stress calculation used the older 2.65 in frame-side mounting pattern and a 0.250 in fastener diameter. Those assumptions no longer represent the revised bracket geometry.

Therefore, the previous calculated minimum thickness of 0.000224 in should not be treated as a verified result for the updated design.

The revised bracket requires a new structural analysis that accounts for its actual geometry, including:

- The 1.71875 in overall height.
- The 1.078125 in central coupling opening.
- The four inner tapped blind holes.
- The four outer tapped through-holes.
- The final fastener dimensions and thread engagement.
- The actual material properties.

The inner blind holes must provide sufficient thread engagement to secure the motor without breaking through the bracket. The outer through-tapped holes must provide adequate engagement with the selected frame fasteners.

The central opening also removes material from the bracket, so its effect on the bracket's strength and stiffness must be considered. The bracket should be checked for bearing, shear, bending, and deflection as appropriate to the actual loading and attachment arrangement.

The revised CAD geometry will be used for the updated calculations rather than relying on the previous mounting-plate analysis.

## Task 3 — Coupler Selection and Torsional Analysis

### 1. Coupler Selection

<img width="2388" height="1668" alt="38711" src="https://github.com/user-attachments/assets/9428dbdf-8c5b-45ad-a9b2-01ab5acd3a0f" />

#### Known and Unknown Variables

**Known variables**

| Variable | Description | Value |
|---|---|---:|
| $T_{op}$ | Operating torque per motor | 0.635 N·m |
| $N$ | Design factor of safety | 4 |
| $T_d$ | Design torque per coupling | 2.54 N·m |
| $T_d$ | Design torque per coupling, converted | 22.48 in·lbf |
| Hub trade size | Coupling size | L050 |
| Motor-side nominal bore | Hub 6408K11 | 16 mm |
| Leadscrew-side nominal bore | Hub 6408K92 | 1/4 in (6.35 mm) |
| Spider material | Spider 6408K91 | Hytrel |
| Hub material | Hubs 6408K11 and 6408K92 | Iron |
| Spider maximum torque | McMaster catalog value | 50 in·lbf |
| Maximum catalog speed | L050 spider | 18,000 RPM |

**Unknown variables and required verification**

- Confirm that the keyed 16 mm motor-side hub can securely retain the motor's D-shaped output shaft.
- Confirm the motor shaft engagement length and set-screw location.
- Confirm that the 1/4 in hub bore and set screw securely fit the actual leadscrew end.
- Verify the complete coupling dimensions and hub cross-sections using the supplier drawings.
- Verify that the coupling's catalog torque and speed limits are suitable for the actual operating duty and service conditions.
- Confirm that the motor and leadscrew are aligned within the coupling's published misalignment limits.

I changed the coupling selection from a one-piece NBK jaw coupling to a **McMaster-Carr L050 spider coupling**. A spider coupling consists of two metal hubs with a flexible center element (the spider) between them. The spider transmits torque while allowing a limited amount of angular and parallel misalignment.

The selected L050 assembly uses the following three components:

| Component | McMaster-Carr Part Number | Description | Material / Shaft Interface |
|---|---|---|---|
| Motor-side hub | [6408K11](https://www.mcmaster.com/6408K11-6413K119/) | L050 keyed hub, 16 mm bore | Iron; keyed bore |
| Leadscrew-side hub | [6408K92](https://www.mcmaster.com/6408K92-6408K111/) | L050 hub, 1/4 in bore | Iron; set-screw shaft mount |
| Flexible spider | [6408K91](https://www.mcmaster.com/6408K91/) | L050 spider | Hytrel |


The two hubs must have the same L050 coupling trade size as the spider. McMaster identifies the 6408K11 hub as a keyed 16 mm option and the 6408K92 hub as an iron set-screw hub available with a 1/4 in bore. The selected spider is the L050 Hytrel version.

**Important fit verification:** The motor output shaft is 16 mm in diameter and has a D-shaped profile. Although the selected motor-side hub has a 16 mm bore, McMaster lists it as a keyed hub. A keyed bore is not automatically a confirmed match for a D-shaped shaft. The shaft must be checked against the hub drawing, and the set-screw/retention arrangement must be verified before ordering or manufacturing. The 1/4 in leadscrew-side bore also needs to be checked against the actual leadscrew end.

### 2. Coupling Specifications

| Specification | Selected L050 Spider Coupling |
|---|---:|
| Manufacturer / supplier | McMaster-Carr |
| Coupling type | L050 spider (jaw) coupling |
| Motor-side hub | 6408K11 |
| Leadscrew-side hub | 6408K92 |
| Spider | 6408K91 |
| Hub material | Iron |
| Spider material | Hytrel |
| Motor-side nominal bore | 16 mm |
| Leadscrew-side nominal bore | 1/4 in (6.35 mm) |
| Maximum catalog torque for selected spider | 50 in·lbf |
| Maximum catalog speed | 18,000 RPM |
| Catalog parallel misalignment capability | 0.015 in |
| Catalog angular misalignment capability | 0.5° |

<img width="724" height="554" alt="image" src="https://github.com/user-attachments/assets/6fbdb7e9-d73b-4462-bc3c-3a25f51e00ca" />

<img width="749" height="493" alt="image" src="https://github.com/user-attachments/assets/bcfd0c28-ad29-430c-9fcf-85c321f0432d" />

<img width="710" height="547" alt="image" src="https://github.com/user-attachments/assets/22213e33-a531-4367-b74c-4bd55ed638af" />


McMaster describes Hytrel as a relatively stiff spider material that provides direct torque transfer and less vibration damping than softer spider materials. The spider coupling's flexible center accommodates limited misalignment; it does not eliminate the need to align the motor and leadscrew carefully.

### 3. Design Torque and Catalog Capacity Check

Each motor drives one leadscrew, so each coupling transmits the torque from one motor.

The operating torque per motor is:

$$
T_{op}=0.635\text{ N}\cdot\text{m}
$$

Using the design factor of safety of 4:

$$
T_d=4T_{op}
$$

$$
T_d=4(0.635)
$$

$$
\boxed{T_d=2.54\text{ N}\cdot\text{m}}
$$

Converting the design torque to pound-inches:

$$
T_d=2.54(8.8507)
$$

$$
\boxed{T_d\approx22.48\text{ in}\cdot\text{lbf}}
$$

The selected L050 Hytrel spider has a published maximum torque of 50 in·lbf. The ratio of the catalog maximum torque to the required design torque is:

$$
\text{Torque Ratio}=\frac{50}{22.48}
$$

$$
\boxed{\text{Torque Ratio}\approx2.22}
$$

The published maximum torque is greater than the calculated design torque. This is a preliminary catalog-capacity check; the manufacturer's maximum torque value should not be treated as a substitute for checking the complete coupling's service conditions, duty cycle, and shaft retention.

### 4. Torsional Loading and Analysis

Each coupling transmits the design torque from one motor to one leadscrew:

$$
\boxed{T_d=2.54\text{ N}\cdot\text{m}}
$$

The torque is transferred from the motor shaft into the motor-side iron hub, through the Hytrel spider, into the leadscrew-side iron hub, and finally into the leadscrew.

The coupling components do not have the same geometry as the previously considered NBK MJC-30-WH coupling. Therefore, the earlier calculations based on a 30 mm outside diameter, 16 mm and 6.35 mm hub bores, and A2017 aluminum hubs do **not** describe this L050 coupling and should not be used as its hub stress results.

A numerical torsional shear-stress calculation for the iron hubs requires the actual hub cross-sectional dimensions from the McMaster/manufacturer drawings. Those dimensions have not yet been verified. The spider's published maximum torque provides a separate catalog-level capacity check, but it does not replace a detailed stress analysis of the hubs or verification of the shaft-to-hub connections.



### 5. Coupler Selection Summary

The updated design uses two iron L050 hubs and one Hytrel spider. The motor-side hub has a nominal 16 mm bore, and the leadscrew-side hub has a nominal 1/4 in bore. The selected spider has a published maximum torque of 50 in·lbf, compared with the required design torque of approximately 22.48 in·lbf.

The catalog torque check is promising, but the coupling is not yet a confirmed drop-in fit because the motor-side hub is listed as keyed while the motor shaft is D-shaped. That shaft-retention detail must be resolved before the coupling is finalized.

McMaster-Carr component links:

- Motor-side hub: https://www.mcmaster.com/6408K11-6413K119/
- Leadscrew-side hub: https://www.mcmaster.com/6408K92-6408K111/
- Hytrel spider: https://www.mcmaster.com/6408K91/
- Spider coupling catalog: https://www.mcmaster.com/products/spider-couplings/

## Lessons Learned

Throughout this design process, I learned the importance of translating the requirements of a mechanical system into practical component selections and design decisions. Selecting a motor required more than checking its rated torque; I also had to consider the required operating speed and verify that sufficient torque was available across the entire operating range.

I also learned that designing mounting hardware requires careful attention to hole patterns, fastener dimensions, alignment, and load transfer. The motor already included a mounting bracket, so I designed an adapter plate to connect that bracket to the frame rather than unnecessarily redesigning the motor mount itself. I also recognized the importance of distinguishing between a clearance-hole diameter and the actual fastener diameter.

For the coupler, I learned that compatibility involves more than matching shaft diameters. I needed to consider the hub bores, shaft-retention method, spider material, torque capacity, and allowable misalignment. The updated design uses two iron L050 hubs with a Hytrel spider. I also learned that a catalog bore diameter alone does not prove compatibility with a D-shaped motor shaft; the hub's keyed geometry and retention method must be checked against the actual shaft.

Finally, I learned that engineering calculations must be tied to the actual geometry and assumptions of the design. A calculated minimum thickness is not automatically the same as a sensible manufacturing thickness. I chose a 1/8-inch adapter plate, recognizing that practical considerations such as rigidity, fabrication, and fastener engagement also matter when finalizing a design.

# FEA of Vertical Components of Frame, Floating Bearing Mount Design, CAD Assembly, Drawings - Jack Brandon

## FEA of Vertical Components of Frame

The first task I had was to run an FEA simulation on the frame by applying the transverse and axial loads to the motor mounts. In order to prepare the assembly for this evaluation, I first checked that all of the components were properly aligned and constrained in the design. Moving to the simulation, I did the same by using the "automatic contacts" function in Fusion which ensured that all of the components were constrained to each other via the L-brackets.

**Model Setup**

<img width="1305" height="683" alt="Screenshot 2026-11-18 182433" src="https://github.com/user-attachments/assets/0c59dd41-489e-4fea-90ba-4861e1c36793" />

Here, I applied the fixed constraints to the "feet" of the tester to ensure it was on a stable base.

<img width="992" height="446" alt="Screenshot 2026-11-18 200543" src="https://github.com/user-attachments/assets/7a7ef6f7-a5db-4a61-9440-26b06cec6aad" />

Next I a applied the 2.54 N-M torque/moment to the motor mounts.

<img width="1242" height="516" alt="Screenshot 2026-11-18 182810" src="https://github.com/user-attachments/assets/050fab5a-a315-4408-8881-9357c689b8ee" />

The compressive axial load of 1000 N per mount was then applied.

<img width="547" height="776" alt="Screenshot 2026-11-18 182905" src="https://github.com/user-attachments/assets/beeb3965-f14b-42ca-beb3-ebf7d620650c" />

All four of the independent loads applied to the two motor mounts.

**Meshing and Verification 1**

<img width="1025" height="511" alt="Screenshot 2026-11-18 205548" src="https://github.com/user-attachments/assets/ee9f9741-2d8b-4f87-aa45-e3d5dea9b274" />

The mesh size selected for the first pass was the maximum (10%).

<img width="1917" height="910" alt="Screenshot 2026-11-18 201819" src="https://github.com/user-attachments/assets/936db4fd-80de-4515-be99-6802784c7c22" />

<img width="1917" height="887" alt="Screenshot 2026-11-18 202031" src="https://github.com/user-attachments/assets/72cf205a-8959-459f-8c1c-4fc26dde7560" />

<img width="1917" height="888" alt="Screenshot 2026-11-18 202337" src="https://github.com/user-attachments/assets/c5d43682-f177-4102-9d22-40078bda051e" />

**Meshing and Verification 2**

<img width="1027" height="510" alt="Screenshot 2026-11-18 205457" src="https://github.com/user-attachments/assets/31cb88a4-8223-4652-abf8-b05f275c8489" />

The next pass was performed with a medium (~6%) mesh size.

<img width="1917" height="890" alt="Screenshot 2026-11-18 204726" src="https://github.com/user-attachments/assets/bb7acacc-745b-4840-b976-7b2078eb7f6a" />

<img width="1917" height="946" alt="Screenshot 2026-11-18 204756" src="https://github.com/user-attachments/assets/af5fdc88-8a58-4daf-b238-d305275eccd3" />

<img width="1917" height="917" alt="Screenshot 2026-11-18 204827" src="https://github.com/user-attachments/assets/893e549f-d1c5-4d8e-9cc7-b8a7bc44ff2f" />

**Meshing and Verification 3**

<img width="1030" height="512" alt="Screenshot 2026-11-18 220331" src="https://github.com/user-attachments/assets/d8f23c09-456d-4b7f-b905-b0f68ff62d9f" />

Finally, the last pass was performed with the finest mesh (1%).

<img width="1917" height="917" alt="Screenshot 2026-11-18 215853" src="https://github.com/user-attachments/assets/8da3843b-9ee1-43e3-9455-8bbf6382ddcb" />

<img width="1917" height="945" alt="Screenshot 2026-11-18 215930" src="https://github.com/user-attachments/assets/1ca854a8-a12d-4f1d-b9f2-28759349635d" />

<img width="1917" height="943" alt="Screenshot 2026-11-18 215942" src="https://github.com/user-attachments/assets/d565b849-7006-4a21-9fed-57ea83fa28bf" />

**Results**

| Iteration | Mesh Size | Max Von Mises Stress & Location | Max Vertical Deflection at Grip Line | Factor of Safety |
|---|---|---|---|---|
| 1 | Coarse | 12.5 MPa (top and bottom of columns and center of top horizontal beam) | 0.001 mm | 31.9 |
| 2 | Medium | 10.8 MPa (same locations) | 0.001 mm | 32.6 |
| 3 | Fine | 15.3 MPa (same locations) | 0.001 mm | 13.6 |

As can be seen from the table, the results never converged to a 2% difference for the von mises stress (14% difference between coarse and medium) and so the fine mesh was used.

**Optimization Pass**

<img width="566" height="682" alt="Screenshot 2026-11-18 224333" src="https://github.com/user-attachments/assets/82f771c0-840d-4f6e-b394-7cc1d8f953f4" />

Although the columns were already well above the required safety factor of 4, I wanted to see how much stronger they and the frame could be made. In order to do this I added plates to the front and back of the columns to increase their rigidity. These in effect increased the cross sectional area of the columns, therefore increasing their stiffness.

<img width="1917" height="945" alt="Screenshot 2026-11-18 230428" src="https://github.com/user-attachments/assets/fec7fa57-21b3-4d73-8c50-867a1e54c57a" />

<img width="1917" height="946" alt="Screenshot 2026-11-18 230454" src="https://github.com/user-attachments/assets/d518eead-932e-4ea9-9c55-252ca959cb95" />

<img width="1917" height="912" alt="Screenshot 2026-11-18 230511" src="https://github.com/user-attachments/assets/dec81d0d-51a7-468a-8378-6dbc7748baac" />

| Iteration | Mesh Size | Max Von Mises Stress & Location | Max Vertical Deflection at Grip Line | Factor of Safety |
|---|---|---|---|---|
| Optimization | Fine | 14.9 MPa (top and bottom of columns and center of top horizontal beam) | 0.001 mm | 13.9 |

As can be seen from the table above, the optimization performed as expected. The maximum stress decreased slightly from 15.3 to 14.9 MPa. The factor of safety increased from 13.6 to 13.9 and the maximum z displacement stayed the same. Overall, the optimization would likely not be worth it due to the increase in mass and cost for a marginal increase in strength.

## Floating Bearing Mount Design

The second task I had was to design the floating bearing mount. For this, I figured that at the very least a plate would be necessary a bearing system to be attached to the T-slot. I considered adding supplier bearings but since that was not detailed in the instructions for the assignment, I simply made the plate with the appropriate RC3 class fit for the lead screw and correct size/spacing for the bolts.

<img width="783" height="618" alt="Screenshot 2026-11-17 183607" src="https://github.com/user-attachments/assets/094c22cb-5b23-4dc9-8f89-0d67d34cbd01" />

The sketch for the bearing mount. The lead screw hole dimension is such that there is a 0.001" total clearance between the screw and hole, given the 1/4" nominal lead screw diameter. This falls within the standard specifications of an RC3 fit. Also, worth mentioning, is that the actual size of the lead screw can and likely will vary slightly, is a threaded surface, and needs to be able to rotate freely, so the hole was made larger to account for these factors. Typically, the dimensions would be between 0.2491 - 0.2495" and 0.25 - 0.2506" for the shaft and hole diameters respectively.

The holes for the 1/4-20 screws to be used to fasten the plate were sized 0.266" as per the recommendation for a clearance hole.

<img width="822" height="562" alt="Screenshot 2026-11-17 195318" src="https://github.com/user-attachments/assets/3c87c278-ba4c-492c-af16-17895049f382" />

Next, the sketch profile was extruded to 0.5". This height was chosen to provide strength to the bearing mount without causing potential unnecessary friction between the hole and lead screw in the case that the two touch while the tester is running.

<img width="668" height="480" alt="Screenshot 2026-11-18 093328" src="https://github.com/user-attachments/assets/960f19b4-74ea-4d1b-9ec6-0105b3ab1bd2" />

The completed bearing mount.

<img width="596" height="687" alt="Screenshot 2026-11-18 174211" src="https://github.com/user-attachments/assets/22d2c399-5a86-4192-b782-0c85d2260757" />

The bearing mounts installed on the top and bottom of the tensile tester assembly.

**CAD File Downloads**

Frame Only: https://a360.co/4A5ueqb

Full Assembly: https://a360.co/4sRWwSe

## Lessons Learned

This project revealed two crucial aspects of a team engineering effort. First, was the importance of communication. Due to the way that our team's tasks were divided, some of us had overlapping tasks. For example, Aidan and I were both doing our own FEA on two separate parts of the frame. Because of this, we each arrived at different bracket solutions in order to complete the assembly and prepare it for verification. I later realized that we had different brackets (Grainger vs McMaster Carr) being used to connect the top horizontal beam to the vertical columns. This caused a delay in getting the FEA verifications completed as one of our assemblies had to be changed to maintain consistent brackets. Second, another issue occurred when the tester assembly file was not shared early enough in the process. This created issues with the motor mount and coupling designs. Once the file was shared, the designs were updated accordingly. The lesson was that these problems could have been avoided if communication was taken more seriously by myself.

Second, this project highlighted the importance of critical thinking when running an FEA. In this instance, the supplied brackets came with mounting hardware (bolts and t-slot parts) which created many extra small components in the frame. When it came time to run the first FEA simulation, the mesh failed. It took some time to figure out why but after going through the error messages, it became clear that the assembly was not constrained and there were too many complex surfaces for the mesh. These two issues were solved by using the automatic contacts function to fix all the components together as an assembly as designed and by removing the unnecessary hardware from the L-brackets. Finally the mesh was able to be produced and the FEA could be run.

## Drawings

<img width="1115" height="722" alt="Screenshot 2026-11-18 114536" src="https://github.com/user-attachments/assets/63657c34-4b15-459c-8172-d8a49d167427" />

<img width="940" height="610" alt="Screenshot 2026-11-18 232600" src="https://github.com/user-attachments/assets/1e8ac8c8-b1a0-4a4c-a998-798a18da9e7a" />

<img width="1120" height="728" alt="Screenshot 2026-11-18 233740" src="https://github.com/user-attachments/assets/f6d7684f-a023-410c-878e-e484b8c71ca3" />

## T Slot Connectors - Aidan Cadle

In designing the frame, the top must be rigid enough to support the moment induced by the motors.
The material of the bracket candidate, the 90 degree flush L bracket, is listed on Mcmaster as 6063 T6 Aluminum, which has a yield strength of 214 MPA, or 214 N/mm^2.
The moment induced from each motor is known, with a stall torque of 2931 in-ozf, which converted into metric, is 20.7 N*m per motor.
The interior width of the frame is 12in, add the column width, and the total length of the beam is known, at 15.15 in. Solving for the distance between the leadscrew hole and the face of the bar, the distance is 3.575 in, or 90.8mm.
Since the beam is symmetric about the center, one side of the beam will be analyzed to simplify the analysis.
Summing moments around the leadscrew hole, and treating the resultant reaction force as a single-point force at the furthest edge of beam, a force acting on the bracket can be calculated. 

<img width="3929" height="4936" alt="A11 Work_page-0001" src="https://github.com/user-attachments/assets/770edb44-83c4-4f91-b499-37472d371e48" />

The bracket is treated as a beam that is fixed on one end, and loaded at the other. Since the first mounting point on the bracket is 20mm away from the edge of the bracket, this is treated as the effective beam length. 
The width of the bracket is doubled, as there is one bracket on each side of the column. 
Using the appropriate equation for stress and section modulus, as found in the Machinery's Handbook, the maximum bending stress is determined to be 4.87 MPa.
Since this is significantly lower than the yield strength of the material, 2 L brackets are more than adequate to support the top of the frame. 

The link for the bracket can be found [here](https://www.mcmaster.com/3136N924/)


## Frame FEA - Aidan Cadle

The top of the frame was analyzed to ensure adequate strength and minimal deflection given the 2kN axial load and moments induced by the 2 chosen electric motors.
The stall torque from the electric motors data sheet was used in order to design for the 'worst case' scenario.
In an attempt to accurately conduct the FEA, the column brackets were mated to a double 40 series beam, as that is how our frame is assembled.

<img width="1513" height="1007" alt="initial model" src="https://github.com/user-attachments/assets/35e8d7fb-5593-4589-a701-0d44ed5259f7" />

The column brackets were set as fixed geometry, and center holes were placed where the leadscrews would go. The loading was centered around these holes. 

<img width="1896" height="906" alt="initial load" src="https://github.com/user-attachments/assets/9516322e-2643-4331-a9b3-c35d871a64d9" />

Then, the FEA was attempted. However, unlike previous assignments, the end results were not clear. The first pass was conducted on the coarse setting within Solidworks.

### Initial Results
<img width="1896" height="895" alt="assembly fea test" src="https://github.com/user-attachments/assets/9dc6ef62-87aa-4227-89dc-e4892c214e15" />

Stress

<img width="1851" height="748" alt="assemb disp" src="https://github.com/user-attachments/assets/5274ca81-42d9-4df6-8551-52769f7926d4" />

Strain

<img width="1749" height="725" alt="assemb FOS" src="https://github.com/user-attachments/assets/0314cbf7-c434-475e-bd64-e593155fd56b" />

Factor of Safety

As can be seen in both the stress and factor of safety images, there is almost no color variation, and yet the plot ranges all the way to 21 GPa, well outside of the yield strength of aluminum.
Despite this, the deformation plot seemed to be accurate, showing gradual variation, and a peak displacement of only 0.0078 mm. 

In an attempt to fix this, a finer mesh was used. However, despite multiple attempts, Solidworks would not run the same simulation on a finer mesh

<img width="253" height="159" alt="fea failure" src="https://github.com/user-attachments/assets/522d5d37-0f36-4aba-970c-5d5309bbb27d" />

One of many error codes.

### Second Assembly Configuration

Since motor mount plates were designed and now available as Solidworks parts, those were added to the assembly in an attempt to resolve this issue.
The loads were applied through the motor mounts, as that is how the loads would be distributed on a physical frame.

<img width="1126" height="679" alt="load" src="https://github.com/user-attachments/assets/a32800f1-f8ca-478d-bfb5-f5152bfeac0f" />

Despite the computer's best efforts, often exceeding 77 degrees Celsius, this did not solve the problem. The stress and factor of safety again came out monochromatic, and the displacement plot appeared to be properly scaled. 

<img width="1399" height="1026" alt="run 2 stress" src="https://github.com/user-attachments/assets/c3a09a4f-b1e2-4c34-99e3-aa0f6f98469f" />

Stress

<img width="974" height="854" alt="disp 2" src="https://github.com/user-attachments/assets/b105fcad-b126-4873-b796-ec24b47e27e6" />

Displacement

<img width="923" height="787" alt="run 2 fos" src="https://github.com/user-attachments/assets/ef921a3f-ead0-45fc-8688-d00563f25cca" />

Factor of Safety

In addition to adding the motor mounts, the scale of the charts were adjusted in an attempt to view a rough idea of the maximum stress. The upper limit was set to that of the yield strength of aluminum, 275 MPa. Despite this, the charts remained monochromatic. 

A finer mesh was used, however the computer took over 10 minutes to complete it, and the results were not significantly different or more conclusive than the coarser mesh. 

### Final Assembly Config

In a final attempt to 'correctly' conduct the FEA, the column L brackets were removed, but the motor mounts remained. In this configuration, the ends of the beams were treated as fixed geometry, but the loads were still applied through the motor mounts. 

<img width="1494" height="639" alt="fea 3 fixtures" src="https://github.com/user-attachments/assets/970bdc74-9c3b-4730-b666-b2002dd5109e" />

The model was meshed on coarse, and the FEA simulation was run.

Worth noting, for every FEA conducted for this assignment, Solidworks always had a warning pop-up saying the mesh contained distorted elements. It did not matter the mesh density, although the number was generally higher the finer the mesh.

Despite the new constraints, the results did not change.

<img width="954" height="815" alt="stress 3" src="https://github.com/user-attachments/assets/7682a2e5-3b67-4408-9a6b-fef135e2951f" />

Stress

<img width="961" height="684" alt="disp 3" src="https://github.com/user-attachments/assets/a3b7a37a-64ce-4d45-a129-12345c29964e" />

Displacement

<img width="946" height="747" alt="fos 3" src="https://github.com/user-attachments/assets/6dc3dd94-c7df-400d-b377-eabed9693d21" />

Factor of Safety

The stress plots appear to be inconclusive, but the displacement plots tell another story. They show minimal deflection in every test, suggesting that the beam is indeed rigid enough to support the given loading. 

### Final FEA attempt

In a final attempt to gain usable data, FEA was conducted on the beam only. 
The ends were set as fixed geometry, and the force and torque were applied around vertical walls of the clearance holes for the lead screw. 

<img width="1690" height="748" alt="part load and fixture" src="https://github.com/user-attachments/assets/eea4604a-a9a6-4575-9abb-d870cb1e797c" />

The mesh was set to coarse, and the simulation was run.

Finally, the simulation resulted in usable results. 

<img width="1343" height="604" alt="stress" src="https://github.com/user-attachments/assets/4cbf3bea-dc82-489a-87c7-e621e50480d8" />

Stress. Peak 116 MPa

<img width="921" height="785" alt="disp 4 1" src="https://github.com/user-attachments/assets/5d3477e2-33c1-4c7e-b224-1d8f16f87094" />

Displacement. Peak 0.042 mm

<img width="860" height="744" alt="fos 4 1" src="https://github.com/user-attachments/assets/7bfd108c-3cc7-4b0e-88b1-1f793c86c582" />

Factor of Safety. Minimum 2.4

All plots now show a gradient, and appear to show correct stresses and factors of safety. Now, the mesh was refined in order to gather more data, and to look for possible convergence. 

According to Solidworks, for both the coarse and medium fine mesh, there were no distorted elements. This is significantly different than the previous attempts.

<img width="1408" height="772" alt="stress 4 2" src="https://github.com/user-attachments/assets/624aaf54-e8e6-459a-bc28-549fecbecbe2" />

Stress. Peak 120 MPa

<img width="885" height="749" alt="displacement 4 2" src="https://github.com/user-attachments/assets/f9c8475b-8f38-46aa-b097-b790300c0b3e" />

Displacement. Peak 0.042mm

<img width="845" height="690" alt="fos 4 2" src="https://github.com/user-attachments/assets/dd7f1997-425c-49da-af73-44d4b0366bf7" />

Factor of Safety. Minimum 2.3

These values converge within 4.2% of one another, so further refinements are not necessary. 

Although the factor of safety is not 4, the beam itself appears to be adequate to support the loading scenario for the frame. There is not significant deflection, there appears to be no torsion, and the stress is less than half of the yield strength. If Solidworks could properly analyze the assembly, further modifications to the final product may not be necessary. Additionally, the areas experiencing the highest stress are the surfaces of the clearance hole, which in a real application, would not see the direct axial force or moment induced by the motors. 

### Possible Refinements

For refinements, the frame may not need double wide framing, and that would drastically cut down on both weight and material cost. 

The beam was loaded and fixed in the same manner as the previous beam.

Initially, the part was meshed at a coarse setting. However, after many failed attempts, the mesh size was increased to medium, and the mesh quality was reduced to draft, at which point it successfully meshed.

The results were similar to the previous test, although stress distribution changed.

<img width="639" height="1013" alt="stress 5 1" src="https://github.com/user-attachments/assets/5e447413-988d-4f29-8070-90a996c966a0" />

Stress. Peak 96 MPa

<img width="622" height="708" alt="disp 5 1" src="https://github.com/user-attachments/assets/2f094ea5-48aa-439a-a673-2190e47da90e" />

Displacement. Peak 0.32 mm

<img width="632" height="667" alt="fos 5 1" src="https://github.com/user-attachments/assets/94df4ca8-b507-4d71-8b33-77763e345843" />

Factor of Safety. Minimum 2.88

Initially, these appear to be better results than the unrefined pass, and save almost 50% of the weight. However, to verify the results, the mesh must be refined, and the analysis re-ran. 

The mesh size was then increased to medium fine (~75% towards fine on the slider).

<img width="1554" height="923" alt="stress 5 2" src="https://github.com/user-attachments/assets/322f5f2d-7ad8-41a0-9960-7bc06a319fef" />

Stress. Peak 104 MPa

<img width="1441" height="831" alt="disp 5 2" src="https://github.com/user-attachments/assets/c5da71db-6295-4022-a340-56acc913c987" />

Displacement. Peak 0.32 mm

<img width="1578" height="810" alt="fos 5 2" src="https://github.com/user-attachments/assets/f8b5d464-494a-4b2f-bfd0-3d7c79303b5f" />

Factor of Safety, Minimum 2.66

These results converge within 10%, with a maximum difference of 8.3%. The results of the finer mesh are used for analysis.

Since the results converge, conclusions can be drawn regarding the proposed change. While stress remains high around the leadscrew clearance hole, the stress has increased near the ends of the beam, showing how the stress distribution has changed. The displacement and factor of safety plots do not show a significant change in the distribution. Overall, the single wide frame appears to be a better solution for this application, although it would require a redesign of the motor mount. 

## Lessons Learned - Aidan Cadle
I learned that using Solidworks for assembly analysis is not ideal, and that I need more information about assemblies in order to adequately use the function. Additionally, I was able to find 'bandaid' workarounds, showcasing the problem solving required of engineers at any given moment. This portion of the assignment took around 6 hours.




