---
title: Mechatronics Class- Automated 3D Print Remover
year: Spring 18
order: 107
stlwv2_models: yes
type: class
---

This is my mechatronic senior design project. 
I wanted to automate the removal of 3D printed parts to print overnight and with many printers. 
The system uses one robotic gripper that services 4 independent 3D printers moving along a verticle gantry. 

![Cover closeup](/website/assets/images/21automatedCoverPic.jpg)
Closeup of the robotic gripper flexing the bed to pop off the part

---

### Design Constraints

The design constraints included:

- Time: 
There were 3 weeks to finish this project before the presentation day, so the margin for error was very small.

- Ingenuity:
I wanted to solve a problem that not many has attempted before. The closest thing out there was a [UR10 robot](https://www.youtube.com/watch?v=qo_rtzEI_7Y) clearing beds, which is expensive and not scalable.

- Creativity: 
I wanted to also solve the problem in a novel way from a mechanism perspective. That is why I chose thedouble differential paradigm to couple certain motions together.

- Material:
A $500 budget was agreed upon in the begining (most of that was spent on the aluminum frame).

- Scalability:
The potential of the design allows for more printers stacked vertically. It could be possible to add the horizontal dimension by redesigning the gantry.

<iframe width="560" height="315" src="https://www.youtube.com/embed/X024T64uNLE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe> 
The system in action!

---
### Double Differential Gripper

I was in charge of the mechanical design and assembly, including the complicated double differential gripper. 
I coupled the servo motors in a way that both will be involved in the enclosing and flexing motions.
The diagram of the coupling and model of the gripper are shown below:

![Differential Diagram](/website/assets/images/21automatedDifferential.jpg)

<div class="stlwv2-model" data-model-url="/website/assets/models/automatedDiff.STL"></div>

---
### Full System

My other group members (Philipp Wu[https://www.linkedin.com/in/wuphilipp/] and Allan Zhao[https://www.csail.mit.edu/person/allan-zhao-0]) worked on system integration, electronic design, and printer interface.
The diagram of the full system and model of the system are shown below:


![Full System Diagram](/website/assets/images/21automatedSystem.jpg)

<div class="stlwv2-model" data-model-url="/website/assets/models/automatedFull.STL"></div>

This is our system running autonomously and servicing 4 printers running continuously (sped up).
<iframe width="560" height="315" src="https://www.youtube.com/embed/rJwPoovYx2k" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
---

### Final thoughts	

There were some difficult cases that we encountered like very small objects that wouldnt un-adhere so we used the gripper to dislodge.
Other things we wish we had more time to do included adding sensors and using computer vision to detect failed prints. 
Overall, this project was a crazy experience and great sucess!

<iframe width="560" height="315" src="https://www.youtube.com/embed/oojNtPXFrFY" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

![No part Closeup](/website/assets/images/21automatedCloseup.jpg)



---