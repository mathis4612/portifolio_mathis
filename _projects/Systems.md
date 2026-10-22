---
layout: default
title: Honeywell Room Fan System
image: /assets/images/Honeywell_fan.png
---

# Honeywell Room Fan System

This project aimed to analyze a chosen system and what capabilities it has, as well as its limitations.

**Topic of Interest:** Honeywell Room Fan  
**Abstract:** I decided to study the Honeywell room fan. The system is an open loop with four settings for speed: Off, 1 speed, 2 speed, and 3 speed. The system requires user input, which is why it is considered an open-loop control system rather than a closed-loop system.

---

**The System Overview**

<img src="{{ '/assets/images/Honeywell_fan.png' | relative_url }}" alt="Honeywell fan" width="300">

The TurboForce fan system is a fan produced by the company Honeywell. This fan possesses a unique feature in that it is relatively silent when turned on for any of the speed options that the fan provides. The fan is designed for comfort and circulation in a room and uses a simple speed-selection interface.

<img src="{{ '/assets/images/Fan_knob.png' | relative_url }}" alt="Fan knob" width="300">

When the knob is turned, the fan controller mechanically switches between different electrical configurations corresponding to different desired speed levels. Each configuration has a different impedance and therefore different power delivery to the motor.

<img src="{{ '/assets/images/Fan_motor.png' | relative_url }}" alt="Fan motor" width="500">

Here, we can see the main components of the motor. For our dissection, we separated the two major parts: the stator and the rotor. The stator is the stationary part of the motor and provides a fixed magnetic structure, while the rotor rotates in response to the electromagnetic interaction.

---

**ODE Modeling and Transfer Functions**

I decided to model this system using a first-order, open-loop ODE with respect to the angular rotation, w, in rad/s. I used two states, w and i (current, in amps), to address both mechanical dynamics and electrical behavior.

<img src="{{ '/assets/images/ODEs.png' | relative_url }}" alt="ODEs" width="500">

The fan works as an open-loop system since the user provides an input to set the speed, and the system does not use feedback to adjust the input.

<img src="{{ '/assets/images/Model.png' | relative_url }}" alt="Fan model" width="500">

In this model, the disturbance torque Td represents external disturbance torques such as friction changes and airflow interactions; however, for a typical room fan in a controlled environment, the primary concern is the relationship between applied voltage and resulting speed.

<img src="{{ '/assets/images/mechanical_equations.png' | relative_url }}" alt="Mechanical equations" width="350">

The mechanical time constant is the term in front of the rotational speed derivative, which is I/b; hence,

<img src="{{ '/assets/images/Time_constant.png' | relative_url }}" alt="Time constant" width="200">

Thinking about this physically, this time constant makes sense since higher inertia means more resistance to motion and slower acceleration, and higher damping means faster settling, so smaller values of time constant correspond to quicker response.

<img src="{{ '/assets/images/current_derivative.png' | relative_url }}" alt="Current derivative" width="200">

Thinking about this physically, this time constant makes sense since higher inductance resists changes in current, causing the current to rise more slowly when the input voltage changes, while higher resistance means faster current response.

To find i(t), we first need to find i(s). Converting it to the frequency domain gives us:

<img src="{{ '/assets/images/frequency_domain.png' | relative_url }}" alt="Frequency domain equation" width="350">

Solving for i(s),

<img src="{{ '/assets/images/solve_Is.png' | relative_url }}" alt="Solve for I(s)" width="250">

Now, we have an equation that can be used to find the equation for i(t) using the MAE 3260 Laplace table. This expression best matches a standard transform pair from the table.

<img src="{{ '/assets/images/transform_equation.png' | relative_url }}" alt="Transform equation" width="400">

In this form, we see that the equation is now in a standard transform form, where the gain term is Un/R. Hence, we can now solve for i(t), and we get:

<img src="{{ '/assets/images/wt_eq.png' | relative_url }}" alt="w(t) equation" width="500">

This equation describes the current over time, which ultimately leads to a second-order system. However, since electric dynamics happen extremely quickly, the system effectively behaves as a first-order mechanical system for our purposes.

<img src="{{ '/assets/images/first_order_equations.png' | relative_url }}" alt="First-order equations" width="150">

Now, we can repeat this process to find w(t):

<img src="{{ '/assets/images/repeat_process_wt.png' | relative_url }}" alt="Repeat process w(t)" width="500">

Plug in i(t) assuming i(t) = Un/R:

<img src="{{ '/assets/images/UnR.png' | relative_url }}" alt="Un over R" width="300">

Transform to the frequency domain with zero initial conditions:

<img src="{{ '/assets/images/frequency_domain_initial_zero.png' | relative_url }}" alt="Frequency domain with zero initial conditions" width="300">

Find w(s):

<img src="{{ '/assets/images/find_w(s).png' | relative_url }}" alt="Find w(s)" width="200">

This is also similar to a standard transform pair, so we convert to the time domain:

<img src="{{ '/assets/images/convert.png' | relative_url }}" alt="Conversion" width="250">

Convert to the time domain using the table:

<img src="{{ '/assets/images/time_domain_using_table.png' | relative_url }}" alt="Time domain using table" width="250">

And now we have an equation that describes the rotational speed in terms of the defined parameters. From this equation, we can see that the steady-state solution is (Ka * Un)/(b * R), which makes sense physically.

<img src="{{ '/assets/images/Graph.png' | relative_url }}" alt="System graph" width="500">

As expected, rotational speed increases rapidly at the beginning from zero to the steady-state value and then remains steady. Depending on the values of b and I, the system exhibits different settling behavior.

---

**Step Response and Parameter Estimation**

The Honeywell turbofan adjusts its speed by modulating the motor current rather than using PWM or direct voltage control. Therefore, the appropriate input for the step response is the commanded speed setting.

Unfortunately, we could not measure the rotating speed of the Honeywell fan nor read the input that the system is trying to achieve, since the speeds are only described as “1, 2, 3” and we were not able to instrument the fan directly.

For speed 1: ts = 3.0 seconds  
For speed 2: ts = 2.4 seconds  
For speed 3: ts = 1.7 seconds

---

**System Assessment + Improvements**

Overall, the Honeywell Room Fan is designed very effectively in terms of system design. Having the system open loop is the right decision, as the goal of the fan is simple and does not require continual correction. The system is robust, inexpensive, and easy to operate.

Some improvements that could be made would be to add a feature to make it a closed loop by adding feedback control. If the system could sense the temperature of the room, then it could modify its output in response to changing conditions. That would improve comfort and efficiency.

---

**References**

- [Honeywell Turboforce Air Circulator Fan](https://www.honeywellstore.com/store/products/honeywell-turboforce-air-circulator-fan-ht-900.htm)
- MAE 3260 Laplace table

<img src="{{ '/assets/images/laplace_table.png' | relative_url }}" alt="Laplace table" width="350">
