---
title: Surgical Tool Change End Effector
year: Fall 15 - Spring 16
order: 92
type: research
stlwv2_models: yes
---
This research was on a novel surgical device for supervised autonomous surgeries.
The work was done under Professor [Ken Goldberg's](https://goldberg.berkeley.edu/) Automation Lab ([Autolab](http://autolab.berkeley.edu/)) during my first year at Berkeley. 

![tool change gif](/website/assets/images/01ToolChange500w.gif)

The part I designed was a tool change end effector that would facilitate automated switching between instruments of the DaVinci robot system.
This work was published in IEEE's International Conference on Automation Science and Engineering ([Case 2016](https://case2016.org/)).
<iframe src="https://drive.google.com/file/d/1-S85-cmj0PrY7fJXdeeDm79jxUIi20RZ/preview"></iframe>

---
### Motivation and Concept

Over 570,000 procedures in 2014 are done with Robotic Surgical Assistants where a surgeon tele-operates robotic appendages to perform sugical tasks.
These Robotic Minimally Invasive Surgical (RMIS) procedures like tumorectomy and prostatectomy are done with very high sucess rates.
The goal is to replace certain portions of the pure tele-operations with supervised autonomous operation in order to reduce tedium, fatigue, and time.
This paper introduces a novel interchangeable surgical end-effector system with a tool change device to save surgical time.

![tool devices](/website/assets/images/01ToolChangeGeneral.jpg)
Above is an image of all instruments designed for the Intuitive Surgical System and below shows the various mounting strategies.
![tool mounting](/website/assets/images/01ToolChangeInterface.jpg)

---
### Design

I worked primarily on the catch basin end effector attachment that facilitates instrument switching. 
The goal is to have this end effector attachment go into the cavity to introduce an instrument or remove an instrument to allow for greater access to a wider array of tools during autonomous surgery.

![tool mounting](/website/assets/images/01ToolChangeOverall.jpg)
The blue arm introduces a new device (orange) that the orange arm then picks up.
Below is the procedure of allignment, insertion, and release using the tool changer.
![tool devices](/website/assets/images/01ToolChangeProcedure.jpg)

In the process of iterating, many models were rapidly prototyped and tested.
Below is couple distinct models in the design process to show the evolution of the design as it developed from concept to product.
<div class="stlwv2-model" data-model-url="/website/assets/models/ToolChangeModel.STL"></div>

The final design incorporates a lot of features in a tight form factor that maximizes the ability of tool insertion and release.

![tool devices](/website/assets/images/01ToolChangeFeature.jpg)



