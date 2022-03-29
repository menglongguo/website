---
title: Fingertip Sensor for Haptic Manipulation
year: Spring 21  - Present
order: 105
stlwv2_models: yes
type: research2
---
<img src="/website/assets/images/40Cover.JPG" alt="process" width="650"/>

Alongside my main research project (the Robotic Hand), I continued the current project on a fingertip sensor.
The motivation of the project was to develop a sensor to be mounted at the end of a robotic hand/end-effector that can sense the direction of external forces and the location of the contact.
This work was a continuation of [Michael Chuah's](https://www.linkedin.com/in/michaelchuah/) PhD research and [Lindsey Epstein's](https://www.linkedin.com/in/lindsay-epstein-60337a111/) Master's thesis.
While I worked mostly on the manufacturing, training software, and integration, [Andrew Salatous](https://www.linkedin.com/in/andrewsaloutos/) and [Adi Mehrota](https://www.linkedin.com/in/aditya-mehrotra/) worked on building the testing platform and the sensor electronics.

As this project required reverse engineering and improving an existing system, it focused more on data analysis, documentation, system-design, manufacturing, and troubleshooting.

---
### Problem Statement

The goal is to create a sensor with many design requirements, eventually, the paradigm of pressure sensor embedded in an elastomer was settled on:

- Normal and Shear sensing:
<br>
In addition to the sensing location, the magnitude of forces are vital to determine the nature of contact with the environment.
Force Sensitive Resistors (FSR) sense forces as it changes the resistivity of the conductive polymer, but due to delamination from shear forces it was ruled out.
Tactile sensing arrays are usually in a flat form does well in location sensing but not as well for multi-axis force measuring.

- Robust to high impacts: 
<br>
Since the focus of our lab is high force impacts especially as a hand explores the environment, robustness is quite important.
Although force-torque sensors are very accurate, don't survive impacts well due to their high stiffness.

- Lightweight and insensitive to noise:
<br>
As the application is at the end of the fingers, the lightweight and compact nature are crucial.
Being insensitive to noise is important as the sensor will be moving around quickly.
This is another reason why force-torque sensor, which are generally heavier, would introduce a large amount of inertial noise at high accelerations.

- High-frequency Response:
<br>
High-frequency response is needed as contact and collisions happen at very short time scales. 
The sensors in the end were able to operate at 200hz with possibility of going to 500hz.
This was also the reason to rule out optic-based sensing that relies on a camera to map deformations, which would be too slow for our application.

How this technology works is shown below, where the stress distribution of the embedded sensors can be mapped to the forces and location of contact.
<img src="/website/assets/images/42PressureDist.JPG" alt="stress field" width="650"/>


---
### Upgrade to the Manufacturing Process

After reverse-engineering how the system worked, I decided to rebuild the system from the ground up as the codebase was too messy and the testing platform was too complex to operate.
Almost the whole process was changed: the delta arm replacing the CNC mill testing platform, Matlab and python replacing LabView and C++. 
As a result, it gave a lot of opportunities to improve the process along with a lot of new issues to troubleshoot if the methodology deviated too much.
(Many images in the old sensor process were taken from Lindsey's thesis).

<img src="/website/assets/images/41ProcessFull.jpg" alt="process" width="650"/>

---
### Plans for future sensor

The half-sphere design is quite useful in many applications (see below) but it can be augmented for more sensing area.
This new design has around 2.5 times more sensing area than the current design.
This allows for more surface area to sense contact and manipulate objects.
An initial prototype was made from plastic for the test, the future ones will be made with an aluminum base for better tolerancing and mass-manufacturability.

<img src="/website/assets/images/43Sphere1.JPG" alt="process" width="650"/>
<img src="/website/assets/images/43Sphere2.jpg" alt="process" width="650"/>
<img src="/website/assets/images/43Sphere3.jpg" alt="process" width="650"/>
<img src="/website/assets/images/43Sphere4.jpg" alt="process" width="650"/>

---
### Applications

This sensor's high-frequency bandwidth and sensing capabilities allow it for many possible applications in manipulation.
In the first video, the finger is acting as a virtual magnet as it attempts to maintain a force of 3 newtons in the direction of contact.
The effect is a very fast contact following demo that can lead to fast in-hand object manipulation with coordination with another finger and sensor.

<iframe width="560" height="315" src="https://www.youtube.com/embed/j2KS7hLpRJE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

This demo is work done by [Elijah Stanger-Jones](https://www.linkedin.com/in/elijah-stanger-jones-216b10126/) and Andrew SaLatous, which uses the sensor to do rapid re-grasping.
The experiment is set up so the robot reaches forward to grasp without seeing the object using vision.
When it contacts the cylindrical shape, the program calculates the direction of the contact and automatically positions the hand to antipodal points.
The demo requires high-frequency sensing to avoid collisions that would perturb or damage the environment, the video below is slowed down to 1/8 the actual speed.

<iframe width="560" height="315" src="https://www.youtube.com/embed/zCNUWmhFmEU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### Troubleshooting

A big portion of the process was the troubleshooting aspect as most of the existing system hasn't been continued since the last student had graduated.
To manage the new and old bugs that appeared was good documentation and data analysis.
Below are some of the more challenging problems to troubleshoot.

<br>
During the beginning of the testing, I discovered that the sensor values are depreciating over time and usage.
In this picture below, the top shows the graph of fingertip forces, and the bottom is a graph of pressure from the 8 sensors on 1 fingertip sensor.
You can see the clear correlation of forces to pressure values.
<img src="/website/assets/images/44newTimeData.JPG" alt="process" width="650"/>

A month later, after running the trial, the pressure sensor no longer correlate well to the pressure values.
<img src="/website/assets/images/44oldTimeData.JPG" alt="process" width="650"/>

Since this is just a small snapshot of the whole training process, I graph the distribution of values in each of the 8 pressure sensors on 1 fingertip sensor.
This was the one from a month earlier:
<img src="/website/assets/images/44newDist.jpg" alt="process" width="650"/>

Compare that to the one a month later:
<img src="/website/assets/images/44oldDist.jpg" alt="process" width="650"/>

From the distribution, we can see the one from a month earlier was much smoother, giving great resolution in the data, compared to the one from a month later.
After investigation, the issue was that this resulted from us removing a protective covering (shown below) from the sensor in order for the elastomer to make better contact with the sensing element.
<img src="/website/assets/images/45BMP388.JPG" alt="process" width="400"/>

After inspection through a microscope of a dissected sensor, you can see that the wires to the piezo-electric element were damaged over repeated usage.
<img src="/website/assets/images/44CloseupWires.jpg" alt="process" width="650"/>
This was fixed by replacing the pressure sensor with a model that has a bigger hole so that the elastomer could achieve good contact without taking the protective covering off.
<br>
<img src="/website/assets/images/45BMP384.jpg" alt="process" width="400"/>

---
Another issue I found was that the material of the gripper slowly changes over time.
Realizing that this was most likely the degradation of the polyurethane material, I purchased a new batch and did some testing.
Although you can feel that the older material was more compliant and took longer to bounce back (more hysteresis), it's best to quantify this.

<br>
I left a weight on the gripper for ~20 seconds and then took it off to plot the change in the sensor value.
In the graph, we can see that the newer material took .4 seconds for the values to drop back compared to the .85 seconds for the older material.
The older material took even longer to fully restore to the non-load value (3.5 seconds vs 0.8 seconds).
As the gripper will be used to exert sustained forces and make rapid contacts, this hysteresis was a huge problem.
Luckily, the fix is simply to watch the shelf-life of the material and benchmark the hysteresis.

<img src="/website/assets/images/46Hyst.jpg" alt="process" width="650"/>

Although the new material fixed the hysteresis problem, I have found that the newer fingertip sensor had many dead values.
Of the 8 pressure sensors on each fingertip, some would not respond to pressures even though they are fully functioning.
After thorough testing and a dissection of the new sensors, I found that the new material was not seeping into the pressure sensor and making contact.
Funnily enough, the old material was much less hydrophobic and was able to squeeze into the hole in the pressure sensor, avoiding this problem.

I peeled off the polyurethane to examine the contact between the pressure sensor and the rubber.
In the image below, you can see that the newer material (on left) does not form a mushroom cap like the older material, meaning it does not fully seep into the pressure sensor.
The way that this was fixed was to de-gas (the process of vacuuming out the air that helps draw the material into cavities) for much longer (20 min vs 5 min) to ensure the new material flows better.

<img src="/website/assets/images/47hydrophobiciity.JPG" alt="process" width="650"/>




