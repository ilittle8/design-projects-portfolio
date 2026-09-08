# A3 – Parametric FEA

## Objective
The purpose of this assignment was to design a bar with a circular cross section under the constraints of specified values for the material, maximum deflection, and load. I specifically was looking to determine the bar's minimum geometry using parametric design (i.e. Solidworks) for a loading of direct tension. I also needed to verify the geometry using finite element analysis.

## Analyze
#### Parametric Design
For my assignment, I was supposed to design a bar with a direct applied load of $300lb_f < F < 500lb_f$. The maximum axial deflection for this load was set to 0.009 inches and the bar was to be made from Aluminium that could be anywhere in the range of $(8.5 - 11.5) \times 10^6\ psi$. I chose the values of $500\ lbs$ of force and $10 \times 10^6\ psi$ as young's modulus.

I then was tasked with deciding the values for the cross sectional area of the bar. I chose a 2 inch diameter for the bar. Using this value, I then found the value for the area to be about 3.14 ($\pi$) inches squared.

<img width="599" height="214" alt="image" src="https://github.com/user-attachments/assets/62903924-2bb7-4654-8f3b-945bd594e292" />


After deciding on the cross sectional area of the bar, I was then able to use the direct tension elongation equation to determine the length of the bar. I found its length to be about $565\ in$.

<img width="556" height="200" alt="image" src="https://github.com/user-attachments/assets/7dedc00f-c136-450f-9891-217416fe816a" />


<img width="599" height="263" alt="Screenshot 2026-09-08 164240" src="https://github.com/user-attachments/assets/3ed8e4cc-c571-45c9-9d31-5ad9bac98ff0" />


I then moved to model my bar parametrically in CAD. I started by sketching a circle, and ensuring its diameter was 2 inches.

<img width="1280" height="764" alt="Screenshot 2026-09-07 185609" src="https://github.com/user-attachments/assets/d26acf96-5b3d-4342-b334-4d495b20d523" />


I then extruded that circle to exactly $180 \times \pi$ or $\approx 565\ in$.

<img width="1280" height="764" alt="Screenshot 2026-09-07 185701" src="https://github.com/user-attachments/assets/6cabd7dd-9c2c-4ee2-b413-1bcf8a813c12" />


I set the material of my model to be 3003-H12, Rod (SS) Aluminum in Solidworks. I chose this material because its Elastic Modulus was very similar to my predetermined Elastic Modulus.

<img width="612" height="483" alt="Screenshot 2026-09-07 190340" src="https://github.com/user-attachments/assets/b34b1839-e186-40b3-abaa-0ee6ebca113f" />


#### FEA
With my bar modeled, I then moved to complete FEA. The type of loading assigned to me is in the image below.

<img width="391" height="104" alt="image" src="https://github.com/user-attachments/assets/ae8825e9-caae-4421-8f99-4257c837c965" />


In Solidworks Simulation, I replicated that loading and set of fixtures, shown in the image below.

<img width="1280" height="764" alt="Screenshot 2026-09-07 192420" src="https://github.com/user-attachments/assets/b5969643-2036-4076-a4c9-29d874d9ea55" />

After confirming that the load applied would equal $500\ lbs$ and would be applied uniformly to one flat surface of my bar, I ran the simulation. Here is the Deformation Plot and the Stress plot (yes, my bar bent... I will address that soon):

<img width="1280" height="764" alt="Screenshot 2026-09-07 193142" src="https://github.com/user-attachments/assets/d8a5cda7-d7da-47df-abd1-2b1ffd5b5b8c" />

<img width="1280" height="764" alt="Screenshot 2026-09-07 193015" src="https://github.com/user-attachments/assets/d8421406-f3c3-413b-acd4-a46f9e682a14" />

I then checked to see if the stress in the simulation was above or below the yield stress specified by my assignment ($40\ ksi$). To do this I used the _list results_ option in Solidworks to view the Von Mises stress across the bar. Here is the list it gave me:

<img width="344" height="272" alt="Screenshot 2026-09-07 193342" src="https://github.com/user-attachments/assets/c0c40636-69db-4c04-8498-13bae2b441e4" />

With this information, I was then able to calculate the Factor of Safety to be 233, which is more than safe.

#### Design Reflection
I then went to compare my hand calculated deflection (0.009 in) to my simulated deflection (0.0002 in). The percent difference ($Percent\ Difference = \frac{Calculated - Simulated}{Calculated} \times 100$) was found to be 97 percent. The discrepancy here is quite significant. I believe the source in the discrepancy here is that gravity is a factor within Solidworks, but in my calculations I had assumed that there was no gravity acting on the bar. This may have been what caused the bar to bend. Additionally, there may have been an issue with how force was applied within the simulation. The vectors for force maintained the exact position they were given before the simulation was run, but when the bar dipped downwards, those vectors may have no longer applied to the surface after bending had occurred.

<img width="536" height="237" alt="image" src="https://github.com/user-attachments/assets/ded039e4-b49a-468f-bdbe-63822d2cb3c6" />


As of of current, I'm going to trust my hand calculations more than the simulation. I don't believe my simulation accurately captured the conditions in which I intended for my bar to experience.

 The next step in the assignment was to imagine a substantial pin hole in the left side of my bar, look up the stress concentration factor for that hole, and estimate peak stress as that hole using results from FEA.  After calculating peak stress, I calculated factor of safety agai and found it to be significantly lower than if the bar did not have a pin hole, but the factor of safety was still high ($F.S. =\ 78$).

 <img width="588" height="265" alt="image" src="https://github.com/user-attachments/assets/fbf91cbf-281f-41d1-b641-160a589226d8" />


#### Modify Design Parameters
 I then decided to see what would happen if I changed the load, diameter, and orientation of my bar... all while keeping the material and fixture of the bar the same. I chose to set the load to be $300\ lb_f$ and the diameter to be 3 inches, and I set the axis of the bar to be in the Y-direction. Before calculating, I guessed that my bar's length would decrease.

 

 I found that I was wrong. The length, governed by $L = \frac{\delta E\ A}{F}$, resulted in $675\pi\ in$ or $\approx 2120\ in$.

 I then made the bar, oriented its axis in the Y-direction, set one side to fixed and the other to be under $300\ lbs$ of tension, and ran the simulation. Once again, I came across bending in the bar. This time, I'm not sure what is causing the bending. For this run, the deflection was about  about 0.0002 inches.

 Here is the deflection map:

 <img width="1280" height="764" alt="Screenshot 2026-09-08 162115" src="https://github.com/user-attachments/assets/a9ed4727-5b87-4c4c-8387-79a03d3a5bc8" />


 Here is the Von mises Stress map:

 <img width="1280" height="764" alt="Screenshot 2026-09-08 162121" src="https://github.com/user-attachments/assets/7096c61a-a60e-4f06-a344-c1d160568309" />


 The maximums stress within the model was 46 psi, and I calculated the safety factor to be about 870,000... which is exorbitantly high. Something is definitely off about my simulation.

 <img width="344" height="272" alt="Screenshot 2026-09-07 193342" src="https://github.com/user-attachments/assets/a1ddfdd4-416b-4725-9c37-777a9f691042" />

 <img width="542" height="338" alt="image" src="https://github.com/user-attachments/assets/c31ca50c-31eb-432c-b2a9-d83d51fcb1bc" />



 With this, I finished my assignment.

## Communicate
#### Lessons Learned
From this assignment, I learned how important it is to understand the details of your project and make sure that your results take those details into account. I missed a key point in not fixing my bar against gravity, or reorienting it so that gravity would not cause a bending moment. I spent about 8 hours total on this assignment.
