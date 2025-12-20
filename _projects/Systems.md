---
System project. 
---
This project aimed to analyse a chosen system and what capabilities it has, as well as its limitations.


**Topic of Interest:** Honeywell Room Fan
**Abstract:** I decided to study the Honeywell room fan. The system is an open loop with 4 settings for speed: Off, 1 speed, 2 speed, and 3 speed. The system requires user input (which is why it is an open loop). For each speed setting, I will study the settling time, steady state angular velocity, and overshoot (if present), and, based on these parameters, assess whether the design is optimal or if there’s room for improvement. I will be modeling and characterizing this system using some of the concepts I’ve learned in the systems dynamics class, such as ODEs, TFs, Block Diagrams, Parameter Estimation, Steady State analysis, and Step Response.

---
**The system Overview**
---
<img src="your-image-url.jpg" alt="Alt Text" width="500">

The TurboForce fan system is a fan produced by the company Honeywell. This fan possesses a unique feature in that it is relatively silent when turned on for any of the speed options that the fan presents. The fan has a 90-degree rotation and (LxWxH): 8.94 x 6.3 x 10.9 in. It weighs about 2.9 lbs according to the Honeywell website [1].

<img src="your-image-url.jpg" alt="Alt Text" width="500">

When the knob is turned, the fan controller mechanically switches between different electrical configurations that correspond to the different speeds wanted. Each configuration has a different impedance so selecting a higher speed applies a higher effective voltage to the motor windings. Higher effective voltage produces a larger current in the coils, which generates a stronger magnetic field and increases the motor’s torque and therefore rotational speed.

<img src="your-image-url.jpg" alt="Alt Text" width="500">

Here, we can see the main components of the motor. For our dissection, we separated the two major parts: the stator and the rotor. The stator is the stationary part of the motor and provides a fixed magnetic field. The rotor, which is connected to the fan blades, consists of a metal core with conductive wire coils wrapped around it. When current flows through the rotor coils, it interacts with the magnetic field from the stator, generating torque that causes the rotor and the attached fan blades to rotate.

---
**ODE Modeling and Transfer Functions**
---

I decided to model this system using a first-order, open-loop ODE with respect to the angular rotation, w, in rads/s. I decided to use two states, w and i (current, units of Amps), to address both the mechanical and electrical aspects of this system. I assumed that the other relevant variables are rotational inertia ( I, units of kg/m^2), viscous damping (b, units of Nms/Rads), user-controlled motor torque (Tu, units of Nm), disturbance torque (Td, units of Nm), inductance(L, units of H), resistance (R, units of Ohm), and torque gain (Ka, units of Nm/V). Since there are four speed settings (including “off”) with increasing voltages based on the desired fan speed, I decided to utilize a step function variable that represents the user voltage u(t) that can take four different values 0, U1, U2, U3, with U1 representing the input voltage at the lowest speed setting and U3 representing the input voltage at the highest speed setting. By analyzing the following variables and their relation to the system, the following ODEs and relations were produced.

<img src="your-image-url.jpg" alt="Alt Text" width="500">

The fan works as an open loop system since the user provides an input to set the speed, and the system does not use feedback to adjust the input.

<img src="your-image-url.jpg" alt="Alt Text" width="500">

In this model, the disturbance torque Td ​represents external disturbance torques such as friction changes and airflow interactions; however, for a typical room fan in a controlled environment, I assume that these disturbances are negligible (Td0), so they will be omitted from the model going forward, and T will be equal to Tu, which equals Kai(t).

Rearranging, we can find the time constant  for the electrical and mechanical equations:
