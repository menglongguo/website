---
title: Fingertip Sensor for Haptic Manipulation
year: Spring 21  - Present
order: 105
stlwv2_models: yes
type: research2
---

Alongside my main research project (the Robotic Hand), I continued a previous student's work on a fingertip sensor.
(background of the project)
(introduce the people (lindsey and Chuah) as well as andrew and adi that helped)
(lay out how most of this will be revamping the old method to the new one)
---
### Problem Statement

Issue with current sensors, comparison of the technology of what is available (maybe a chart).


---
### Upgrade to the Manufacturing Process



The way I approached this space was to first fix the topology and geometry and let that dictate the other variables.
The goal was to maximize the functionality with the simplest topology.
To decide what types of grasping functions the hand should be able to achieve, I went into the human grasp taxonomy literature to use human hand's as a baseline.

<details><summary>[Click for Taxonomy Details]</summary>

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


The topology chosen was 7 DOF with 3 fingers including a thumb that allows for finger opposition.
![Topology](/website/assets/images/31HandTopology.gif)

7 Dof with 6 motors (one finger underactuated) would be difficult to have all actuation in the hand, so using tendon transmission allows for remote actuation.
Remote actuation also allows for any form factor, a small dynamixel was chosen to minimize weight and size. 
Although a tendon transmission is doable for a revolute joint, a pulley is needed for constant length retraction.
The bigger problem is joint couping, the rolling joint makes it possible to route wires so that more distal (far from the palm) joint aren't coupled to more proximal (close to palm) joints. 


The rolling joint and how it solves the wire coupling problem is shown below.

<img src="/website/assets/images/32HandRolling.gif" alt="RolingJointAnimation" width="500"/>

![RollingJointConservation](/website/assets/images/33conservation.jpg)

(workspace)


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


<details><summary>[Click for Electronics Details]</summary>

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

The tendon routing was quite complicated to design, especially for the thumb that have 3 dof with an abduction joint not in plane as the distal and proximal phalange.
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

In addition to 

