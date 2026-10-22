---
layout: default
title: Torque Wrench CAD Rendering
image: /assets/images/Torque_wrench.png
---

# Torque Wrench CAD Rendering

<img src="{{ '/assets/images/Torque_wrench.png' | relative_url }}" alt="Torque wrench" width="650">

This project aims to design a beam that would meet the constraints demanded. It had to withstand a torque of 600 in-lbf, have a Yield/Brittle FoS constraint of ≥ 4, a crack growth FoS constraint of ≥ 1.5, and an output voltage ≥ 1 mV/V.

<img src="{{ '/assets/images/Driver.png' | relative_url }}" alt="Torque wrench driver" width="500">
<img src="{{ '/assets/images/Sketch.png' | relative_url }}" alt="Torque wrench sketch" width="500">

<img src="{{ '/assets/images/Mesurments.png' | relative_url }}" alt="Measurements" width="750">

For my design, I selected Ti-6Al-4V because its high yield strength allows the wrench to avoid permanent deformation and failure under peak torque. However, its elastic modulus is relatively low, so I had to carefully size the beam to balance stiffness and strength.

<img src="{{ '/assets/images/Beam_condition.png' | relative_url }}" alt="Beam condition" width="500">

For the FEM model, I first applied the displacement condition (yellow) on the drive, telling the software that it does not move. I set the displacement to (0, 0, 0). Then I applied the force at the handle location and used the material properties to calculate the resulting stress and displacement.

<img src="{{ '/assets/images/Material.png' | relative_url }}" alt="Material rendering" width="500">

Next, I defined to the software what kind of material I was using by giving it the Young’s modulus and the Poisson’s ratio. Giving the software the necessary components to calculate the displacement and stress allowed me to compare the simulation to hand calculations.

<img src="{{ '/assets/images/Normal_strain_contours.png' | relative_url }}" alt="Normal strain contours" width="500">
<img src="{{ '/assets/images/Contour_plot_of_maximum_principal_stress.png' | relative_url }}" alt="Maximum principal stress" width="500">

(Used max stress under clamped boundary line for the maximum principal stress since the indicated max is likely artificial.)

<img src="{{ '/assets/images/Static_Structural.png' | relative_url }}" alt="Static structural" width="500">

I can see at the base of the drive that the maximum and minimum normal stress occur. The largest magnitude stress is near the clamp-handle intersection, though the printed max/min values there are likely artificially inflated due to boundary effects.

<img src="{{ '/assets/images/Displacement.png' | relative_url }}" alt="Displacement result" width="500">

The load point deflection from the FEM is 0.40865 in, which is only slightly higher than the hand-calculated displacement of 0.3448 in.

<img src="{{ '/assets/images/Strain_gauge.png' | relative_url }}" alt="Strain gauge result" width="500">

The strain at the location of the strain gauge has a magnitude of 1136.6 microstrain, or 0.0011366 strain. The hand-calculated strain gauge strain was 1212 microstrain, which is very close to and acceptable for the prediction model.

All in all, I can see that my design of the beam meets almost all the criteria, and this is mainly due to the hand calculation having implicit assumptions to simplify the problem, while the FEM model includes more realistic boundary conditions and deformation behavior.
