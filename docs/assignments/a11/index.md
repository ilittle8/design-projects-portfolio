# MEGR Leadscrew Tensile Tester — Design Documentation

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
