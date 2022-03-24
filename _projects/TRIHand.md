---
title: Robotic Hand for Human-like Tasks
year: Spring 21  - Present
order: 11
stlwv2_models: yes
type: research
---

This was my main research project through my Master's under Professor Sangbae Kim ([BRL Group](https://biomimetics.mit.edu/)) at MIT. 
Although most research projects are continuations of a previous student's work, this was a completely new project in an area new to our lab: manipulation. 

The project was to build a robotic hand for the home environment in collaboration with [Toyota Research Institute] (https://www.tri.global/) and 4 other labs at MIT ([Perceptual Science](http://persci.mit.edu/), [MCube](https://mcube.mit.edu/), [CDFG](https://cdfg.mit.edu/wojciech),   [Improbabl AI](https://people.csail.mit.edu/pulkitag/), ).
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

The complexity of the challenge stems from the environment robotic hands are trying to be deployed in.
Currently, most robotic applications in industry (assembly line arms, CNC machines) are position-controlled and avoids contacts but manipulation is built on controlling forces and contacts with objects/environment. 
Robotic research, on the other hand, is trying to push robots into the home environment.
This requires robots safely doing human tasks at human speeds while navigating an unstructured environment. 
Compare that to the clutter-free, human-free, predictable factory settings that the current robots are operating in, there are a lot of challenges to account for the clutter, safety, and object collision.


To illustrate the complexity of this design space, below is a snapshot of many robotic hands in the field.

(pictures of grippers)

Here are the design axis and variables that maps this incredibly complex space:

- Topology:
The number of fingers, degree-of-freedom (DOF) of each finger, and opposability fo the fingers determines the grasp types a hand can perform.
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
To decide what types of grasping functions the hand should be able to achieve, I went into the human grasp taxonomy literature to use human hand's as a baseline.

<details><summary>[Click for Details]</summary>

A lot of research has been done to categorize the grasps we do as humans.
Looking at this chart, there are 30+ grasps and a major distinction relies on the thumb's opposability.
<br>
<img src="/website/assets/images/39GraspChart1.png" alt="Chart 1" width="450" >
<br>"The GRASP Taxonomy of Human Grasp Types"(T. Feix, J. Romero, H. Schmiedmayer, A. Dollar, D. Kragic)

<br>The minimum number of point contact to maintain the stability of a grasped object in 3d space is 3, so 3 fingers were chosen to reduce complexity.
This also means that certain grasps cannot be achieved.
It is infeasible to achieve all 30+, so we looked primarily at the top 10 most used grasps.
The fewest degree of freedom was chosen to achieve as much of these grasps as possible.

<img src="/website/assets/images/310GraspChart2.gif" alt="Chart 2" width="450" >
<br>"Grasp frequency and usage in daily household and machine shop tasks"(I. Bullock, J. Zheng, S. LaRosa, C. Guertler, A. Dollar)
\
</details>

The topology chosen was 7 DOF with 3 fingers including a thumb that allows for finger opposition.
![Topology](/website/assets/images/31HandTopology.gif)

7 Dof with 6 motors (one finger underactuated) would be difficult to have all actuation in the hand, so using tendon transmission allows for remote actuation.
Remote actuation also allows for any form factor, a small dynamixel was chosen to minimize weight and size. 
Although a tendon transmission is doable for a revolute joint, a pulley is needed for constant length retraction.
The bigger problem is joint couping, the rolling joint makes it possible to route wires so that more distal joint aren't coupled to more proximal joints. 


The rolling joint and how it solves the wire coupling problem is shown below.

<img src="/website/assets/images/32HandRolling.gif" alt="RolingJointAnimation" width="500"/>

![RollingJointConservation](/website/assets/images/33conservation.jpg)

(workspace)


---
### First Prototype

This first version was a good learning block and testing ground for a couple of ideas that will be improved upon in future version.
All 6 motors were built into the palm, it was as compact as it could get, so adding another actuator would require expanding off the hand.
Each finger has a different number of actuator for better specialization.

The decision of 3 fingers with each a specialty and the springs to restore to save wire routing.

<img src="/website/assets/images/34hand1.jpg" alt="hand1"/>


<div class="stlwv2-model" data-model-url="/website/assets/models/TRIHand1_1.STL"></div>

<img src="/website/assets/images/37Hand1Free.gif" alt="hand1" width="500"/>

<img src="/website/assets/images/38Hand1Grasp.gif" alt="hand1grasp" width="500"/>


<details><summary>[Click for Details]</summary>

 <img src="/website/assets/images/35ControlGlove.jpg" alt="control glove" width="500" >

 <img src="/website/assets/images/36ElectronicSetup.jpg" alt="electronic glove" width="500" >

</details>


---
### Second Prototype

(The big changes)

(wire routing picture)

(cad of it)



