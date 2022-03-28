---
title: Robotic Hand for Human-like Tasks
year: Spring 21  - Present
order: 106
stlwv2_models: yes
type: research
---

This was my main research project through my Master's under Professor Sangbae Kim ([BRL Group](https://biomimetics.mit.edu/)) at MIT. 
Although most research projects are continuations of a previous student's work, this was a completely new project in an area new to our lab: manipulation. 

The project was to build a robotic hand for the home environment in collaboration with [Toyota Research Institute](https://www.tri.global/) and 4 other labs at MIT ([Perceptual Science](http://persci.mit.edu/), [MCube](https://mcube.mit.edu/), [CDFG](https://cdfg.mit.edu/wojciech),   [Improbabl AI](https://people.csail.mit.edu/pulkitag/)).
As the only member in our lab working on the project, I had a lot of freedom to explore but the design space of hand design is very complex. 
Compare to my previous hand project, we wanted far more functionality by adding more DOF while maintaining robustness even with the added complexity.

<img src="/website/assets/images/3HandFull_2.jpg" alt="CoverShot1" width="650"/>
<img src="/website/assets/images/3HandFull.jpg" alt="CoverShot2" width="650"/>

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

<img src="/website/assets/images/3Designspace.jpg" alt="hands" width="650"/>

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

<details><summary><b><[Click for Taxonomy Details]</b></summary>

A lot of research has been done to categorize the grasps we do as humans.
Looking at this chart, there are 30+ grasps and a major distinction relies on the thumb's opposability.
<br>
<img src="/website/assets/images/39GraspChart1.png" alt="Chart 1" width="450" >
<br>"The GRASP Taxonomy of Human Grasp Types"(T. Feix, J. Romero, H. Schmiedmayer, A. Dollar, D. Kragic)
<br>
<br>The minimum number of point contact to maintain the stability of a grasped object in 3d space is 3, so 3 fingers were chosen to reduce complexity.
This also means that certain grasps cannot be achieved.
It is infeasible to achieve all 30+, so we looked primarily at the top 10 most used grasps.
The fewest degree of freedom was chosen to achieve as much of these grasps as possible.
<br>
<img src="/website/assets/images/310GraspChart2.gif" alt="Chart 2" width="450" >
<br>"Grasp frequency and usage in daily household and machine shop tasks"(I. Bullock, J. Zheng, S. LaRosa, C. Guertler, A. Dollar)
<br>
</details>


The topology chosen was 7 DOF with 3 fingers including a thumb that allows for finger opposition, this allows for a wide enough array of grasp shapes.
![Topology](/website/assets/images/31HandTopology.gif)

7 Dof with 6 motors (one finger underactuated) would be difficult to have all actuation in the hand, so using tendon transmission allows for remote actuation.
Remote actuation also allows for any form factor, a small dynamixel was chosen to minimize weight and size. 
Although a tendon transmission is doable for a revolute joint, a pulley is needed for constant length retraction.
The bigger problem is joint couping, the rolling joint makes it possible to route wires so that distal joints (far from the palm) aren't coupled to proximal (close to palm) joints.


The rolling joint and how it solves the wire coupling problem is shown below.

<img src="/website/assets/images/32HandRolling.gif" alt="RolingJointAnimation" width="400"/>

![RollingJointConservation](/website/assets/images/33conservation.jpg)


---
### First Prototype

This first version was a good testing ground for a couple of ideas that will be improved upon in future version.
All 6 motors were built into the palm, it was as compact as it could get, so adding another actuator would require expanding off the hand.
Each finger has a different number of actuator for better specialization.
A spring was used as the antagonistic tendon to restore the hand to the resting position. 

<img src="/website/assets/images/34hand1.jpg" alt="hand1"/>

A cad of the hand model:

<div class="stlwv2-model" data-model-url="/website/assets/models/TRIHand1_1.STL"></div>

The free motion control using a control glove through arduino and logging through matlab. 

<img src="/website/assets/images/37Hand1Free.gif" alt="hand1" width="500"/>

The grasping capabilities of the hand.
<img src="/website/assets/images/38Hand1Grasp.gif" alt="hand1grasp" width="500"/>


<details><summary><b><[Click for Electronics Details]</b></summary>

A control glove was designed to map the user's joint command to the hand.
The user would move the hand and the potentiometers attached to the arduino will map the joint space of the human hand to that of the robot.
The arduino also reports the joint position and current (both commanded and actual) to the computer to be live-plotted in matlab for troubleshooting and data-collection.

<img src="/website/assets/images/35ControlGlove.jpg" alt="control glove" width="500" >

<img src="/website/assets/images/36ElectronicSetup.jpg" alt="electronic glove" width="500" >

</details>


---
### Second Prototype

In the second prototype, many changes were implemented from the lessons learned from the first.
Physically, it is more reactive and robust with less friction (although that came at the cost of more pulleys and complexity)
The bandwidth and speed of the hand increased quite a lot as the electronics was upgraded from an arduino to a STM microcontroller.
In addition, the fingertips are easily exchangeable to fit the new sensors I have designed (see page for more details).

<img src="/website/assets/images/311Upgrades.jpg" alt="upgrades" width="600" >

<div class="stlwv2-model" data-model-url="/website/assets/models/TRIHand2.STL"></div>

The tendon routing was quite intricate to design, especially for the thumb that have 3 dof with an abduction joint not in plane as the distal and proximal phalange.
The pictures below show the 2 pair of wires in the thumb.
The red and green wires are the pair for the distal phalange that has to travel through the abduction joint and proximal phalange.
The light red and light green wires are the pair for the proximal phalange that only has to travel through the abduction joint.

<img src="/website/assets/images/3HandCable1.JPG" alt="cable" width="600" >
<img src="/website/assets/images/3HandCable2.JPG" alt="cable" width="300" >
<img src="/website/assets/images/3HandCable3.JPG" alt="cable" width="600" >
<img src="/website/assets/images/3HandCable4.JPG" alt="cable" width="600" >

Below are the videos for the experiments.
The hand and arm was control using a human operator via teleoperation, the limited dexterity of the hand was more of a function of the user's (which was me) inability to coordinate that many DOF well without any haptic feedback.

<iframe width="560" height="315" src="https://www.youtube.com/embed/WFKvJfAqSUY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/_ziXoVCXk-w" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

In addition to tele-operation, the hand's low friction and motor backdrivability has inspired some possible exploration in proprioception.
In the test videos below, the hand is sensing the external forces through the current readings at the motor (hard to see in the first video but the left middle graph on the Matlab interface has jolts corresponding to the touches).
Using this, a very rough reflex can be created to automatically close when detecting contact (a possible area for more research exploration in the future).

<iframe width="560" height="315" src="https://www.youtube.com/embed/2QKSCnbaOX4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/89BJrVGDbUY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>