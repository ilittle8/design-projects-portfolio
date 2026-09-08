# A3 – Parametric FEA

## Objective
The purpose of this assignment was to design a bar with a circular cross section under the constraints of specified values for the material, maximum deflection, and load. I specifically was looking to determine the bar's minimum geometry using parametric design (i.e. Solidworks) for a loading of direct tension. I also needed to verify the geometry using finite element analysis.

## Analyze
#### Parametric Design
For my assignment, I was supposed to design a bar with a direct applied load of $300lb_f < F < 500lb_f$. The maximum axial deflection for this load was set to 0.009 inches and the bar was to be made from Aluminium that could be anywhere in the range of $(8.5 - 11.5) \times 10^6\ psi$. I chose the values of $500\ lbs$ of force and $10 \times 10^6\ psi$ as young's modulus.

I then was tasked with deciding the values for the cross sectional area of the bar. I chose a 2 inch diameter for the bar. Using this value, I then found the value for the area to be about 3.14 ($\pi$) inches squared.

After deciding on the cross sectional area of the bar, I was then able to use the direct tension elongation equation to determine the length of the bar. I found its length to be about $565\ in$.

I then moved to model my bar parametrically in CAD. I started by sketching a circle, and ensuring its diameter was 2 inches.

I then extruded that circle to exactly $180 \times \pi$ or $\approx 565\ in$.

I set the material of my model to be 3003-H12, Rod (SS) Aluminum in Solidworks. I chose this material because its Elastic Modulus was very similar to my predetermined Elastic Modulus.

#### FEA
With my bar modeled, I then moved to complete FEA. The type of loading assigned to me is in the image below.

In Solidworks Simulation, I replicated that loading and set of fixtures, shown in the image below.

After confirming that the load applied would equal $500\ lbs$ and would be applied uniformly to one flat surface of my bar, I ran the simulation. Here is the Deformation Plot and the Stress plot (yes, my bar bent... I will address that soon):

I then checked to see if the stress in the simulation was above or below the yield stress specified by my assignment ($40\ ksi$). To do this I used the _list results_ option in Solidworks to view the Von Mises stress across the bar. Here is the list it gave me:

With this information, I was then able to calculate the Factor of Safety to be 233, which is more than safe.

#### Design Reflection
I then went to compare my hand calculated deflection (0.009in) to my simulated deflection (insert here). The percent difference (insert governing equation) was found to be (insert here). The discrepancy here is quite significant. I believe the source in the discrepancy here is that gravity is a factor within Solidworks, but in my calculations I had assumed that there was no gravity acting on the bar. This may have been what caused the bar to bend. Additionally, there may have been an issue with how force was applied within the simulation. The vectors for force maintained the exact position they were given before the simulation was run, but when the bar dipped downwards, those vectors may have no longer applied to the surface after bending had occurred.

As of of current, I'm going to trust my hand calculations more than the simulation. I don't believe my simulation accurately captured the conditions in which I intended for my bar to experience.

 The next step in the assignment was to imagine a substantial pin hole in the left side of my bar, look up the stress concentration factor for that hole, and estimate peak stress as that hole using results from FEA.  After calculating peak stress, I calculated factor of safety agai and found it to be significantly lower than if the bar did not have a pin hole, but the factor of safety was still high ($F.S. =\ 78$).

#### Modify Design Parameters
 I then decided to see what would happen if I changed the load, diameter, and orientation of my bar... all while keeping the material and fixture of the bar the same. I chose to set the load to be $300\ lb_f$ and the diameter to be 3 inches, and I set the axis of the bar to be in the Z-direction. Before calculating, I guessed that my bar's length would decrease.

 I found that I was wrong. The length, governed by $L = \frac{\delta E\ A}{F}$, resulted in $675\pi\ in$ or $\approx 2120\ in$.

## Communicate
#### Lessons Learned
From this assignment, I learned how important it is to understand the details of your project and make sure that your results take those details into account. I missed a key point in not fixing my bar against gravity, or reorienting it so that gravity would not cause a bending moment. I spent about 4 hours total on this assignment.
