---
title: Robotic Hand for Human-like Tasks
year: Spring 21  - Present
order: 11
stlwv2_models: yes
type: research
---

This was my main research project through my Master's under Professor Kim ([BRL Group](https://biomimetics.mit.edu/)) at MIT. 
Most projects are continuations of a previous student's work, this was a completely new project in an area new to our lab: manipulation. 

The project was to build a robotic hand for the home environment in collaboration with Toyota Research Institute and 4 other labs at MIT ([Perceptual Science](http://persci.mit.edu/), [MCube](https://mcube.mit.edu/), [CDFG](https://cdfg.mit.edu/wojciech),   [Improbabl AI](https://people.csail.mit.edu/pulkitag/), ).
As the only member in our lab working on the project, I had a lot of freedom to explore but the design space of hand design is very complex. 
Compare to my previous hand project, we wanted far more functionality by adding more DOF while maintaining robustness even with the added complexity.

(Instead of video have a gif)

<iframe width="560" height="315" src="https://www.youtube.com/embed/RCQNIgySaYw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<!--
<details><summary>Hello</summary>

Note the <b> double enter </b> or else Markdown won't work!
 <img src="/website/assets/images/1HandsPbrighter.jpg" alt="test" width="500" height="600">

</details>


A model of the arm:
<div class="stlwv2-model" data-model-url="/website/assets/models/longboard_remote.stl"></div>
 find and make stl -->

---
### Problem Statement

To understand the complexity of the challenge, it's good to evaluate the past present and future of robotic manipulation. 
In the past, most robotic applications in industry (assembly line arms, CNC machines) are position-controlled and minimized contacts  but manipulation is built on force control and embraces contacts with objects/environment. 
The current goal of roboticists is to get robots into the home.
This requires robots safely doing human tasks at human speeds while navigating an environment built for humans as opposed to the clutter-free and predictable factory floor built for robots.
The future of manipulation is to be able to build something that can emulate the functionality of our own hand.
This dream is to emulate an extraordinary intricate machine with 27 joints and 34 muscles able to twirl pencil and hit 100 mph home runs.

To illustrate the complexity of this design space, below is a snapshot of many robotic hands in the field.

pictures of grippers

Here are the design axis and variables that maps this incredibly complex space:

- Topology:
The number of fingers, degree-of-freedom (DOF) of each finger, and opposability fo the fingers affect the functionality of the hand in its grasp orientation.
The more DOF, the more complex it becomes with more moving parts, more difficult wiring routes, and more limited control bandwidth. 

- Geometry: 
The shape and material of the finger pad changes its ability to interact with the environment, the thinner the fingers the more able it is to reach into clutter and tight spaces.
The shape of the palm affect the size and types of the object it can grasp. 

- Actuation:
The type of motor used (stepper, bldc, dc with big gearbox) will change the torque-speed curve as well as the rotor inertia (useful in proprioception in collisions).
The size and shape affects where it can be mounted (in the palm, at the finger joint, or outside the hand).

- Joints:
The type of joint (revolute, rolling, prismatic) all changes the robustness and complexity of the finger. 
Deciding if joints are coupled will also change the kinematics and workspace. 

- Transmission:
Belt and pulley, direct, tendon-driven, and geared transmission all have their benefit and drawback in terms of elasticity, friction, efficiency and complexity.

- Sensorization:
What kind of sensor (contact, capcitative, force, proximity) will determine the type of information you can gather and utilize from the environment.

<!--
The complexity of the space is compounded by the inter-dependency of these core design axes. 
For example, by choosing a revolute joint makes a tendon driven transmission more difficult without adding a pulley to maintain the constant length of retraction.
Without tendon-driven transmission, that means that the actuators can't be placed outside the hand (tendons and redirect pulleys allows the actuation to be placed far from the joint)
This constricts the size of the motor's themselves if you have to put all the actuation in the hand.
 -->

---
### Design Methodology

The way I approached this space was to first fix the topology and geometry and let that dictate the other variables.
The goal was to maximize the functionality with the simplest topology.
To decide what types of grasping function the hand should be able to achieve, I went into the human grasp taxonomy literature to use human hand's as a baseline.

<details><summary>[Click for Details]</summary>

(go into details with the grasp taxonomy stuff)
 <img src="/website/assets/images/1HandsPbrighter.jpg" alt="test" width="500" height="600">

</details>
(Both dollar charts)

The topology chosen was 7 DOF with 3 fingers including a thumb that allows for finger opposition.
![Topology](/website/assets/images/31HandTopology.gif)

7 Dof with 6 motors (one finger underactuated) would be difficult to have all actuation in the hand, so using tendon transmission allows for remote actuation.
Remote actuation also allows for any form factor, a small dynamixel was chosen to minimize weight and size. 
Although a tendon transmission is doable for a revolute joint, a pulley is needed for constant length retraction.
The bigger problem is joint couping, the rolling joint makes it possible to route wires so that more distal joint aren't coupled to more proximal joints. 


The rolling joint and the wire coupling problem is shown below.

![RolingJointAnimation](/website/assets/images/32HandRolling.gif)

<img src="/website/assets/images/32HandRolling.gif" alt="RolingJointAnimation" width="450"/>

![RollingJointConservation](/website/assets/images/33conservation.jpg)

(workspace)


---
### First Prototype

This first version was meant to be (explain the context as a quick build)

The decision of 3 fingers with each a specialty and the springs to restore to save wire routing.

(Image of the thing and description)

Finish? the cad and put it in

(Video of it being controlled- combined)

[click to show more of the electronics]



---
### Second Prototype

(The big changes)

(wire routing picture)

(cad of it)



