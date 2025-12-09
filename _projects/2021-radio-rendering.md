---
layout: project
title: Torque wrench CAD Rendering
description: Advanced CAD Project
technologies: [Autodesk Fusion and ANSYS]
image: /assets/images/Torque wrench.png
---
This project aims to design a beam that would meet the constraints demanded. It had to withstand a torque of 600 in-lbf, have a Yield/Brittle FoS constraint of ≥ 4, a crack growth FoS constraint of ≥ 2,
a Fatigue FoS constraint of ≥ 1.5, and an output voltage ≥ 1 mV/V.

![Shaded rendering of earlier version]({{ "/assets/images/Driver.png" | relative_url }}){: .inline-image-r style="width: 200px"}
![Shaded rendering of earlier version]({{ "/assets/images/Sketch.png" | relative_url }}){: .inline-image-r style="width: 200px"}
![Shaded rendering of earlier version]({{ "/assets/images/Mesurements.png" | relative_url }}){: .inline-image-r style="width: 200px"}

For our design, we selected Ti-6Al-4V because its high yield strength allows the wrench to avoid permanent deformation and failure under peak torque. However, its elastic modulus is relatively low, which enables it to be slightly flexible and allows for higher-sensitivity strain-gauge measurement. The material also offers strong fatigue resistance, supporting multiple loading cycles, and high fracture toughness, which slows crack growth from small flaws. 

![Shaded rendering of earlier version]({{ "/assets/images/Beam condition.png" | relative_url }}){: .inline-image-r style="width: 200px"}

For the FEM model, we first applied the displacement condition (Yellow) on the drive, telling the software that it does not move. We set the displacement to (0, 0, 0). Then we applied the force at the edge of the beam (red face) with a force of 37.5 lbf in the y direction, which allowed the software to determine the bending of the beam.

![Shaded rendering of earlier version]({{ "/assets/images/Material.png" | relative_url }}){: .inline-image-r style="width: 200px"}

Next, we defined to the software what kind of material we were using by giving it the Young’s modulus and the Poisson's ratio. Giving the software the necessary components to calculate the displacement, stress, and strain of the beam.
