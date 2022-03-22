---
title: TRI- A Low-Cost 7 DOF Arm and Gripper
year: Spring 17 - Spring 19
order: 99
stlwv2_models: yes
type: research2
---

*TRIHAND* is a low-cost, human-size, and compliant 7 degree of freedom arm with a 2kg payload.
It was developed in the [Robot Learning Lab](http://rll.berkeley.edu/) under [Professor Pieter Abbeel](https://people.eecs.berkeley.edu/~pabbeel/) as a low-cost platform to democratize robotic research.
I worked on this project from my 3rd to final year of my undergraduate degree at Berkeley.
What began in 2017 as a concept, is now a platform available for researchers (more information is available [here](https://www.berkeleyopenarms.org/)).

<iframe width="560" height="315" src="https://www.youtube.com/embed/RCQNIgySaYw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

The work was published in the IEEE's International Conference on Robotics and Automation ([ICRA 2019](https://www.icra2019.org/)), the Arxiv link is [here](https://arxiv.org/abs/1904.03815) and a copy is shown below: 

<iframe src="https://drive.google.com/file/d/1BF0iX-mr0g-xxwFFcOnAoNCMtre2P8h1/preview"></iframe>

<!--
A model of the arm:
<div class="stlwv2-model" data-model-url="/website/assets/models/longboard_remote.stl"></div>
 find and make stl -->

---
### Hand Design

I was in charge of the end effector on the team.
Seeing that there wasn't a gripper that fulfills all of *blue's* requirements for this type of research application, I set out to design and manufacture one.

The design constraints included:


- Low-cost- 
A cheaper hand lowers the barrier of entry for research. The final Bill of Material cost was $330.

- Durable: 
Research sees a lot of collisions between end effector and environment. The HALT testing shows it could withstand 50,000 low speed impact collisions and 4,000 high speed collisions (video below).

- Repeatable:
The gripper should be consistent through its life cycle. The *Blue* gripper was functional after 40,000 cycles of repeated grasping with no loss of performance.

- Lightweight:
The lighter the gripper the greater the payload can be. The final weight is 660 grams.

- High Grip Force:
To be able to handle objects around 2kg, a high grip force is required. *Blue's* nominal grip force is 100N with a peak at 150N.

- Force control:
Accurate feedforward force control is needed for handling of delicate objects.

- Human-Safe:
Safehandling encourage operation around humans. The gripper was designed with curved surfaces and no pinchpoints for ease of handling.


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
