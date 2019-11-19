---
title: Optimizing Surfaces for Grasping
year: Summer 16 - Spring 17
order: 99
latex: yes
stlwv2_models: yes
type: research
---

This research explores data-driven optimization of gripper jaw surfaces using rapid prototyping to manufacture many surfaces and an automated reset system to test the grippers.
The work was done under Professor [Ken Goldberg's](https://goldberg.berkeley.edu/) Automation Lab ([Autolab](http://autolab.berkeley.edu/)) in my 2nd year of undergrad. 
This work was the first time I led a research effort, we develop systems to test this idea and ultimately yielded the lab's primary gripper.

The research was published in the IEEE's International Conference on Robotics and Automation ([ICRA 2017](http://www.icra2017.org/)) and a copy is shown below: 
<iframe src="https://drive.google.com/file/d/1fUTLI-Pb5excH_t0La6Q3xOpYoIvCiUJ/preview"></iframe>

---
### Motivation and Concept

Parallel-jaw grippers are ubiquitous in industry but most commercially available grippers have rigid, planar surfaces.
A variety of designs have been proposed like human-inspired skin, gecko surfaces, and rubber coverings. 

Given the recent advances in 3D printing, we explore the method of guiding the design process empirically by evaluating on a physical system for a large number of prototype fingertip designs.
We first generate many gripper surfaces then prototype each using 3D printed molds and silicone.
After testing, we used the grasp success to further parametrize the features of the most promising design for further evaluation.

---
### The System

To physically realize each gripper, we first 3D print the gripper base and the textured mold and then pour silicone around the base to form textured surface.
Each finger would require 30 minutes of print time but many molds and base can be printed together and overnight.
Below is a picture of the process and model of molds & bases:

![molding process](/website/assets/images/moldingProcess.jpg)

<div class="stlwv2-model" data-model-url="/website/assets/models/Gripper.STL"></div>

To evaluate the gripper, we chose 7 total grasps across 3 objects.
The dataset was selected to test resistance to torques and ability to adapt to concavities of geometric features.

![testing grasp](/website/assets/images/testGrasps.jpg)

The automated reset mechanism was designed to raise and lower the test object after each grasp attempt to reset the object to a known stable pose.
The Zymark robot had 4 degrees of freedom plus gripper control and rotating turntable for 5 controllable degrees of freedom.
The vision system used a PrimeSense depth sensor to register the pose of the object.

Below is the full setup:
![setup gripper](/website/assets/images/setupGripper.jpg)


Considerable time was saved using rapid prototyping of unique molds and using a reset mechanism to autonomously test the grippers. 
The reset mechanism evaluated 32 unique grippers with 1377 total grasps taking over 30 hours to run. 
However, the operator only spent 1.5 hours to change out the gripper between tests.
![so many molds](/website/assets/images/manyMolds.jpg)


### Initial design concepts

The initial gripper surfaces were selected to test many parameters like curvature, angular resolution of webbing, radial resolution of concentrip pattern, and depth, shape and width of gridded indentations.
After testing each of the 16 grippers with 21 grasps on the 7 chosen grasps, the results were plotted and design 12 was chosen for futher expansion.

![first round exploration](/website/assets/images/firstRound.jpg)

### First parametrized expansion

In the second round, a 3x3x3 grid search was used to test 3 different void widths, depths, and material stiffness.
The result was plotted and the best performing design was further parameterized. 

![second round exploration](/website/assets/images/secondRound.jpg)

### Second parametrized expansion

In this round, we further explored void depth and material softness. 
Further softening the material and reducing depth decreased the success with all design having a lower probability of sucess.
This was due to a mechanical issue where the robot malfunctioned so we used the noisier backup robot.

![third round exploration](/website/assets/images/thirdRound.jpg)

### Final Testing
The highest-performing gripper was evaluated over 8 3D printed objects using the ABB Yumi industrial robot. 
We compared the final silicone gripper with the factory-provided gripper tips, factory-gipper with tape, gecko-inspired surfaces over 80 trials each (10 per object). 

![Yumi with objects](/website/assets/images/Yumi.jpg)

The final results are shown here with the silicone gripper performing at 94% success of trials. 

![final Numbers](/website/assets/images/finalNumbers.jpg)


