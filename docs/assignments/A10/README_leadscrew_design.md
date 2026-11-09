# Lead Screw System Design --- Part 1

## Project scope

This document records my design process for the lead-screw portion of
the tensile tester assignment. I am documenting the decisions,
assumptions, calculations, and design changes I made rather than
presenting only the final answer.

The tensile tester uses **two identical lead screws** to move the
crosshead and apply a maximum tensile force of **2 kN** to the specimen.

> **Scope note:** This documentation covers the lead-screw calculations
> and component selection only. Nut/flange and crosshead design will be
> documented separately.

------------------------------------------------------------------------

## 1. Design requirements and initial knowns

  Parameter                           Symbol                        Value
  --------------------------------- -------- ----------------------------
  Maximum specimen tensile force       (F_T)                      2,000 N
  Number of identical lead screws      (n_s)                            2
  Factor of safety                     \(N\)                            4
  Required crosshead speed             \(v\)                 1--50 mm/min
  Minimum lead-screw length              ---                        18 in
  Initial material choice                ---   AISI 1020 cold-drawn steel

I selected **AISI 1020 cold-drawn steel** as the material for my initial
strength calculations. I used an assumed yield strength of
(S_y=350`\text{ MPa}`{=tex}). This value should be checked against a
material datasheet or the assignment's approved material-property source
before treating it as a verified property of the purchased screw.

I assumed the tensile load would be shared equally by the two identical
screws:

\[
F_s=`\frac{F_T}{n_s}`{=tex}=`\frac{2000}{2}`{=tex}=1000`\text{ N per screw}`{=tex}
\]

This equal-load-sharing assumption depends on the two screws being
aligned and driven synchronously.

------------------------------------------------------------------------

## 2. Minimum screw diameter from axial stress

I first estimated the minimum required screw diameter using the axial
normal-stress relationship:

\[ `\sigma`{=tex}=`\frac{F}{A}`{=tex}
`\qquad `{=tex}`\text{where}`{=tex} `\qquad`{=tex}
A=`\frac{\pi d^2}{4}`{=tex} \]

For a factor of safety of 4, the allowable stress used in my calculation
was:

\[ `\sigma`{=tex}\_{`\text{allow}`{=tex}}=`\frac{S_y}{N}`{=tex}
=`\frac{350}{4}`{=tex} =87.5`\text{ MPa}`{=tex} \]

Solving the axial-stress equation for diameter:

\[
d\_{`\min`{=tex}}=`\sqrt{\frac{4F_s}{\pi\sigma_{\text{allow}}}}`{=tex}
\]

Substituting the load carried by one screw:

\[ d\_{`\min`{=tex}}= `\sqrt{\frac{4(1000)}
{\pi(87.5\times10^6)}}`{=tex} \]

\[ `\boxed{d_{\min}=0.003815\text{ m}=3.815\text{ mm}}`{=tex} \]

This is a theoretical minimum diameter based on axial stress. For a
threaded screw, the **minor/root diameter** is the relevant nominal
diameter for this check, and manufacturing tolerances and other possible
failure modes still need to be considered.

------------------------------------------------------------------------

## 3. Lead selection and rotational speed

My initial goal was to use a relatively small lead so that the crosshead
displacement per revolution would be small. I wanted finer positioning
while applying tension to the specimen.

I initially considered a lead of 1 mm/rev. When I found an available
screw with a lead of 0.05 in/rev, I accepted changing the design lead to
match the actual component:

\[ L=0.05(25.4)=1.27`\text{ mm/rev}`{=tex} \]

The relationship between crosshead linear speed and screw rotational
speed is:

\[ v=nL `\qquad `{=tex}`\Longrightarrow `{=tex}`\qquad`{=tex}
n=`\frac{v}{L}`{=tex} \]

At the minimum crosshead speed:

\[ n\_{`\min`{=tex}}=`\frac{1\text{ mm/min}}{1.27\text{ mm/rev}}`{=tex}
=0.787`\text{ rev/min}`{=tex} \]

At the maximum crosshead speed:

\[ n\_{`\max`{=tex}}=`\frac{50\text{ mm/min}}{1.27\text{ mm/rev}}`{=tex}
=39.37`\text{ rev/min}`{=tex} \]

Therefore, the screw speed range is:

\[ `\boxed{n=0.787\text{ to }39.37\text{ RPM}}`{=tex} \]

Both screws must rotate synchronously at the same speed to keep the
crosshead level.

A smaller lead improves displacement resolution per revolution, but it
does not by itself guarantee positioning accuracy. Backlash, thread
tolerances, bearing play, structural stiffness, motor control
resolution, and load-cell feedback also affect positioning and force
control.

------------------------------------------------------------------------

## 4. Thread type and nut material decisions

I chose an **Acme-style power-screw thread** because it is a common
thread form for power transmission applications.

For a standard Acme thread, the included thread angle is 29 degrees,
giving a half-angle of:

\[ `\alpha=14.5`{=tex}\^`\circ`{=tex} \]

I initially considered a steel nut, but changed the nut material to
**bronze** because a steel screw/bronze nut pairing is commonly used for
sliding power-screw contact and can reduce the likelihood of
steel-on-steel galling.

I also decided to assume **lubricated** screw/nut contact. My notes use:

\[ `\mu=0.15`{=tex} \]

This is an assumed coefficient for the preliminary calculation, not a
verified value for the exact bronze alloy, lubricant, surface finish,
and operating conditions. The final design should state the assumed
lubrication condition and cite an appropriate friction-data source.

------------------------------------------------------------------------

## 5. First candidate screw: Roton 3/16--20 Stub Acme

My first candidate was the Roton 3/16--20 Stub Acme steel lead screw,
part **62240**:

[Roton 3/16--20 Stub Acme Steel Lead
Screw](https://www.roton.com/product/stub-acme-lead-screw-3-16-20-rh-steel/)

The dimensions I recorded from the product information were:

  Parameter                               Value
  ---------------- ----------------------------
  Major diameter            0.188 in = 4.775 mm
  Minor diameter            0.151 in = 3.835 mm
  Lead               0.050 in/rev = 1.27 mm/rev

The nominal minor diameter exceeded my calculated minimum:

\[ 3.835`\text{ mm}`{=tex}\>3.815`\text{ mm}`{=tex} \]

However, the margin was only:

\[ 3.835-3.815=0.020`\text{ mm}`{=tex} \]

This was a very small nominal margin. More importantly, I found that the
bronze nut's published operating load rating was below the load required
per screw. The required load per screw was:

\[ F_s=1000`\text{ N}`{=tex}`\approx224.8`{=tex}`\text{ lbf}`{=tex} \]

The published operating rating I identified for the bronze nut was 75
lbf. Because the screw/nut assembly would move while applying tension, I
decided not to use this first candidate.

This was an important design change: checking only the screw's diameter
was not enough; I also needed to check the nut's operating load rating.

------------------------------------------------------------------------

## 6. Selected candidate: Roton 1/4--20 Acme steel screw

I then selected the larger Roton 1/4--20 Acme steel screw, part
**60758**:

[Roton 1/4--20 Acme Steel Screw --- Part
60758](https://www.roton.com/product/acme-steel-screw-right-60758/)

The manufacturer information I recorded for this candidate was:

  Parameter                                                  Value
  ---------------------------------- -----------------------------
  Thread                                              1/4--20 Acme
  Major diameter                               0.250 in = 6.350 mm
  Minor diameter                               0.175 in = 4.445 mm
  Lead                                 0.050 in/rev = 1.270 mm/rev
  Bronze-nut static load rating                          1,000 lbf
  Bronze-nut operating load rating                         300 lbf
  Forward-drive efficiency                                     32%
  Drive torque ratio                              0.025 in·lbf/lbf

The minor diameter check is:

\[ 4.445`\text{ mm}`{=tex}\>3.815`\text{ mm}`{=tex} \]

The nominal minor diameter exceeds the calculated minimum by:

\[ 4.445-3.815=0.630`\text{ mm}`{=tex} \]

The load per screw in pounds-force is:

\[ F_s=`\frac{1000}{4.44822}`{=tex}=224.8`\text{ lbf}`{=tex} \]

Using the operating rating recorded from Roton's engineering data:

\[ 224.8`\text{ lbf}`{=tex}\<300`\text{ lbf}`{=tex} \]

Therefore, the candidate's published bronze-nut operating load rating is
above the calculated load per nut. This comparison assumes that the
rating applies to the exact compatible bronze nut and the intended
lubrication/operating conditions. I still need to confirm the exact nut
part number and the manufacturer's rating conditions.

**Material verification still needed:** Roton describes the screw as
steel. I have selected AISI 1020 cold-drawn steel for my calculations,
but I have not yet verified that part 60758 is specifically manufactured
from AISI 1020 cold-drawn steel. I should not claim the purchased
screw's exact grade until the manufacturer confirms it.

------------------------------------------------------------------------

## 7. Preliminary torque calculation

The torque calculation is based on raising the tensile load with an Acme
screw. The load is assumed to be shared equally between the two screws:

\[ F_s=1000`\text{ N per screw}`{=tex} \]

For an Acme screw, the raising torque per screw can be expressed as:

\[ T_s=`\frac{F_s d_m}{2}`{=tex} `\left[
\frac{L+\pi\mu d_m\sec\alpha}
{\pi d_m-\mu L\sec\alpha}
\right]`{=tex}\]

where:

-   (F_s) = axial load carried by one screw
-   (d_m) = mean/pitch diameter of the thread
-   \(L\) = lead
-   (`\mu`{=tex}) = thread friction coefficient
-   (`\alpha`{=tex}) = Acme thread half-angle

The total torque for two identical screws is:

\[ T\_{`\text{total}`{=tex}}=2T_s \]

### Mean diameter and torque status

In my handwritten notes, I estimated a mean diameter of 4.305 mm for the
**first 3/16-inch candidate** by averaging its major and minor
diameters. That value does **not** apply to the selected 1/4-inch screw.

I have not yet established a manufacturer pitch/mean diameter or
completed a verified mean-diameter estimate for part 60758. Therefore, I
should not reuse the earlier 4.305 mm value for the final screw.

Roton's recorded drive torque ratio for the selected candidate was 0.025
in·lbf/lbf. Using that manufacturer ratio as a preliminary estimate:

\[ T_s=(224.8`\text{ lbf}`{=tex})(0.025`\text{ in·lbf/lbf}`{=tex})
=5.62`\text{ in·lbf}`{=tex} \]

For two screws:

\[ T\_{`\text{total}`{=tex}}=2(5.62)=11.24`\text{ in·lbf}`{=tex} \]

\[ `\boxed{T_{\text{total}}\approx1.27\text{ N}\cdot\text{m}}`{=tex} \]

This is a manufacturer-ratio-based preliminary estimate. I need to
confirm the conditions associated with Roton's torque ratio and whether
it represents the same lubrication, nut, and load conditions as my
design.

**Safety-factor note:** I applied the factor of safety of 4 in the
axial-stress diameter calculation. I have not multiplied the required
operating torque by 4 because the assignment asks for the torque needed
to provide the specified 2 kN specimen tension. A separate torque margin
would be appropriate only if required for motor/drive sizing or
explicitly required by the assignment.

------------------------------------------------------------------------

## 8. Current design record

  -----------------------------------------------------------------------
  Design item                         Current selection/status
  ----------------------------------- -----------------------------------
  Number of screws                    Two identical screws

  Screw material used for             AISI 1020 cold-drawn steel (exact
  calculations                        product grade unverified)

  Screw manufacturer/product          Roton part 60758

  Thread style                        Acme, 1/4--20

  Major diameter                      6.350 mm

  Minor diameter                      4.445 mm

  Lead                                1.270 mm/rev

  Nut material                        Bronze

  Contact condition                   Lubricated

  Preliminary friction coefficient    (`\mu=0.15`{=tex}), assumed

  Axial-stress minimum diameter       3.815 mm

  Calculated screw speed range        0.787--39.37 RPM

  Preliminary total operating torque  1.27 N·m, based on manufacturer's
                                      torque ratio
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## 9. Remaining checks before finalizing the lead-screw design

-   [ ] Confirm the exact compatible bronze nut part number for Roton
    screw 60758.
-   [ ] Confirm that the 300 lbf operating load rating applies to that
    nut and the intended operating conditions.
-   [ ] Confirm the screw's actual steel grade and condition with Roton
    if AISI 1020 cold-drawn steel is required.
-   [ ] Confirm the manufacturer's torque-ratio definition and test
    conditions.
-   [ ] Obtain the actual pitch/mean diameter or a manufacturer thread
    drawing for the selected screw.
-   [ ] Complete and include the detailed lead-screw/nut free-body
    diagram.
-   [ ] Verify the selected screw's available length is at least 18 in.
-   [ ] Check screw buckling, alignment, bearing support, and
    synchronization as appropriate to the complete design.

## 10. Design decisions and lessons learned

1.  I began by calculating a minimum screw diameter from axial stress
    and a factor of safety of 4.
2.  I selected Acme threads because they are common in power-screw
    applications.
3.  I changed the design lead to 1.27 mm/rev to match an available
    commercial screw.
4.  I chose a bronze nut and lubricated contact rather than dry
    steel-on-steel contact.
5.  My first screw candidate passed the nominal diameter check but did
    not meet the published bronze-nut operating load rating.
6.  I selected a larger 1/4--20 screw after checking both its minor
    diameter and the bronze-nut operating load rating.
7.  I learned that selecting a lead screw requires checking the screw
    and nut as a system---not just checking the screw diameter.

------------------------------------------------------------------------

*This document records the current design state and identifies items
that still require manufacturer verification. It will be updated as the
nut/flange and remaining lead-screw checks are completed.*
