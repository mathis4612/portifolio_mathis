---
Bike pump dissection
---

In this project, I was put in a group to go and dissect an object and then anayse it with the help of the concepts and learning outcome that we have seen in our fluid mechanic class. Our object was a bike pump.

Our bike pump is specifically a dual-action pump, meaning that the pump generates output airflow on both the downstroke and the upstroke. The dual-action design, together with one-way valves allow the pump to maintain continuous volumetric airflow. 

The main chamber behaves as a piston cylinder container with a moving boundary. Inside the main chamber, we found two inner cylinders, each with its own one-way valves. On the upstroke, the control volume increases within the inner cylinder, creating a pressure lower than ambient and inducing inflow. However, due to the increased amount of air in the pump as a whole, the pressure in the outer cylinder increases, and the air is then pushed out through the outlet valve in the outer cylinder. During the downstroke, the actions reverse. Thus, by controlling the pressure inside the pump chamber, we are able to take advantage of the dual-action behavior.

This pump is an example of a positive displacement pump, as each inner cylinder encloses a fixed control volume of air and displaces that volume through the system. 

To start our analysis, we removed the base plate cover by hand and then used a screwdriver to take out the seal, which exposed the pump’s inlet and outlet check valves. After that, we unscrewed the top cap, which let us see the handle mechanism. This mechanism uses a piston and an upper cap to pull air into the main cylinder during the upstroke. Taking off the cap also revealed two inner cylinders inside the main body, each connected to the inlet and outlet valves. We also removed the hose from the outlet port by hand.

When the handle moves, it drives the piston up and down, creating low and high pressure inside the cylinder. This pressure change draws air in during the suction stroke and pushes it out during the compression stroke. The air flows through the inner passages, passes through the inlet and outlet valves, and leaves through the outlet port into the hose. The seal and gasket help prevent leaks, allowing the pump to maintain pressure and work efficiently.

These measurements will help us perform more detailed calculations later about the pump’s efficiency, flow rate, and operating speed.

The pump has connected tubes that function as short pipes with check valves. Flow through these passages is driven by pressure differences rather than by external freestream effects, and the air remains confined within solid walls throughout the process. As a result, the pump is fundamentally a container–pipe system governed by unsteady internal flow and the conservation of mass and momentum, rather than an airfoil-type flow device.

The equation used is Bernoulli's equations which is <img src="https://your-image-url.png" width="300" alt="Alt Text">

--> p/rho describes the pressure energy per unit mass created by the piston motion

--> v^2/2 describes the kinetic energy per unit mass of air accelerates as it moves through the narrow tubes

--> g*z describes the gravitational potential energy per unit mass for the high difference along the tubes

--> hL describes the Head loss due to the friction in the tube
