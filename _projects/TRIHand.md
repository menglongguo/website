---
title: Robotic Hand for Human-like Tasks
year: Spring 21  - Present
order: 99
stlwv2_models: yes
type: research2
---

This was my main research project through my Master¡¯s under Professor Kim ([BRL Group](https://biomimetics.mit.edu/)) at MIT. 
Most projects are continuations of a previous student¡¯s work, this was a completely new project in an area new to our lab: manipulation. 
The project was to build a robotic hand for the home environment in collaboration with Toyota Research Institute and 4 other labs at MIT (). 
As the only member in our lab working on the project, I had a lot of freedom to explore but the design space of hand design is very complex. 
Compare to my previous hand project, we wanted far more functionality by adding more DOF while maintaining robustness even with the added complexity.

//Instead of video have a gif
<iframe width="560" height="315" src="https://www.youtube.com/embed/RCQNIgySaYw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<details><summary>Hello</summary>

Note the <b> double enter </b> or else Markdown won't work!
 <img src="/website/assets/images/1HandsPbrighter.jpg" alt="test" width="500" height="600">

</details>

<!--
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

//pictures of grippers

Here are the design variables that maps this incredibly complex space:

- Topology:
A cheaper hand lowers the barrier of entry for research. The final Bill of Material cost was $330.

- Geometry: 
Research sees a lot of collisions between end effector and environment. The HALT testing shows it could withstand 50,000 low speed impact collisions and 4,000 high speed collisions (video below).

- Actuation:
The gripper should be consistent through its life cycle. The *Blue* gripper was functional after 40,000 cycles of repeated grasping with no loss of performance.

- Joints:
The lighter the gripper the greater the payload can be. The final weight is 660 grams.

- Transmission:
To be able to handle objects around 2kg, a high grip force is required. *Blue's* nominal grip force is 100N with a peak at 150N.

- Sensorization:
Accurate feedforward force control is needed for handling of delicate objects.

A model of the gripper with inner mechanism shown:
<div class="stlwv2-model" data-model-url="/website/assets/models/BlueHandCompressed.STL"></div>
<!-- find and make stl -->


In hopes of growing the field of research in robotic grippers, we open-sourced the designs [here](https://berkeleyopengrippers.github.io/).
The research work was published in the 2019 IEEE's Conference on Automation Science and Engineering and a copy is shown below:
<iframe src="https://drive.google.com/file/d/1LC0DirgkaY__70R6G0JBzAUYHXj9ZpEU/preview"></iframe>

Footage of durability testing of the robot shown below:
<iframe width="560" height="315" src="https://www.youtube.com/embed/3JgtpOue68Y" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### Alternatives Designs using a Strain Gauge


In the process of designing the *Blue* Gripper, other designs were made along the way.
These designs played with the tradeoffs between force-control vs durability and force-control vs weight using different actuation modalities.

The "strain gauge design" uses a strain gauge attached to a non-backdrivable dc motor.
Although much lighter (a small motor), it was not backdrivabile (making it less safe) and not as durable (forces at finger tips directly transfer to motor).

The cross section of design is shown below with a interactable 3D Cad model.
![Hand1](/website/assets/images/04Hand1.jpg)
<div class="stlwv2-model" data-model-url="/website/assets/models/StrainHand.STL"></div>
<!-- find and make stl -->

---
### Alternatives Designs using a Ball screw


The "Ball screw design" uses a ball screw instead of the lead screw with a similar form factor as *Blue*.
A ball screw gives more backdrivability with a more transparent transmission compare to a lead screw.
However, the total weight was around 1100 grams compare to 660 grams of *Blue*, lowering the final payload of the arm.

The cross section is shown below with a interactable 3D Cad model.
![Hand2](/website/assets/images/04Hand2.jpg)
<div class="stlwv2-model" data-model-url="/website/assets/models/BallScrewHandGood.STL"></div>
<!-- find and make stl -->

---
### 3D Printer management

In addition to design, I was also in charge of the 8 Markforge printers and 3 Monoprice Select Minis in the lab.
After extensive rounds of protoyping, we decided to manufacture 8 whole arms in 2.5 weeks which meant printing 550 parts (90 days of continuous printing).
This required a lot of organization and logistics to save time and money (each roll of the Markforge Nylon filament was $180). 
I also was the one removing prints, swapping filament, and cleaning beds, so I wanted to minimize my work as well.

Below are snippets of the large multi-page excel document used to organize this. 
This below is the high level planning to split parts onto printers for each of the A and B cycle (each cycle took 23 hrs to give me an hour each day to remove parts and start the next cycle).
![Printerorg1](/website/assets/images/04PrinterOrg1.png)

This below is the day to day logs in the beginning to make sure the prints were coming out correctly (we had some underextrusion problems due to wet filament) and the filament usage rate was as predicted.
![Printerorg2](/website/assets/images/04PrinterOrg2.png)


---

### Links

- [Robot Learning Lab's website](http://rll.berkeley.edu/)
- [Professor Pieter Abbeel's website](https://people.eecs.berkeley.edu/~pabbeel/)
- [Berkeley Open Arms](https://www.berkeleyopenarms.org/)
- [Paper Arxiv link](https://arxiv.org/abs/1904.03815)
- [Berkeley Open Grippers](https://berkeleyopengrippers.github.io/)
