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

As this project required reverse-engineering and improving an existing system, it focused more on data analysis, documentation, system-design, manufacturing, and troubleshooting.

---
### Problem Statement

The goal is to create a sensor with many design requirements, eventually the paradigm of pressure sensor embedded in an elastomer was settled on:

- Normal and Shear sensing:
<br>
In addition to the location of sensing, the forces are vital to determine the nature of the contact with the environment.
Force Sensistive Resistors (FSR) sense forces as it changes the resistivity of the conductive polymer, but due to delamination from shear forces it was rules out.
Tactile sensing arrays are usually in a flat form does well in location sensing but not as well for multi-axis force measuring.

- Robust to high impacts: 
<br>
Since the focus of our lab is in high force impacts especially as a hand explores the environment, robustness is quite important.
Although force torque sensors are very accurate, don't survive impacts well due to their high stiffness.

- Lightweight and insensitive to noise:
<br>
As the application is at the end of fingers, the lightweight and compact nature are crucial.
Being insensitive to noise is important as the sensor will be moving around quickly.
This is another reason why force-torque sensor, which are generally heavier, would introduce a large amount of inertial noise at high accelerations.

- High frequence Response:
<br>
The high frequency response is needed as contact and collisions happen at quite high frequencies. 
The sensors in the end were able to operate at 200hz. 
This was also the reason to rule out optic-based sensing that rely on a camera to map deformations, which would be too slow for our application.

How this technology work is shown below, where the stress distribution of the embedded sensors can be mapped to the forces and location of contact.
<img src="/website/assets/images/42PressureDist.JPG" alt="stress field" width="650"/>


---
### Upgrade to the Manufacturing Process

After reverse-engineering how the system worked, I decided to rebuild the system from the ground up as the codebase was too messy and the testing platform was too complex to operate.
Almost the whole process was changed: the delta arm replacing the CNC mill testing platform, Matlab and python replacing labview and C++. 
As a result, it gave a lot of opportunities to improve the process along with a lot of new issues to troubleshoot if the methodology deviated too much.
(Many images in the old sensor process taken from Lindsey's thesis).

<img src="/website/assets/images/41ProcessFull.jpg" alt="process" width="650"/>

---
### Plans for future sensor

The half-sphere design is quite useful in many applications (see below) but it can be augmented for more sensing area.
This new design has around 2.5 times more sensing area than the current design.
This allows for more surface to sense contact and manipulate objects.
An initial prototype was made from plastic for test, the future ones will be made with an aluminum base for better tolerancing and mass-manufacturability.

<img src="/website/assets/images/43Sphere1.JPG" alt="process" width="650"/>
<img src="/website/assets/images/43Sphere2.jpg" alt="process" width="650"/>
<img src="/website/assets/images/43Sphere3.jpg" alt="process" width="650"/>
<img src="/website/assets/images/43Sphere4.jpg" alt="process" width="650"/>

---
### Applications

This sesnsor's high frequency bandwidth and sensing capabilities allows it for many possible applications in manipulation.
In the first video, the finger is acting as a virtual magnet as it attempts to maintain a force of 3 newtons in the direction of contact.
The effect is a very fast contact following demo that can lead to fast in-hand object manipulation with coordination with another finger and sensor.

<iframe width="560" height="315" src="https://www.youtube.com/embed/j2KS7hLpRJE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

This demo is work done by [Elijah Stanger-Jones](https://www.linkedin.com/in/elijah-stanger-jones-216b10126/) and Andrew SaLatous, that uses the sensor to do rapid regrasping.
The experiment is set up so the robot reaches forward to grasp without seeing the object using vision.
When it contacts the cylindrical shape, the program calculates the direction of the contact and automatically position the hand to antipodal points.
The demo requires high frequency sensing to avoid collisions that would perturb or damage the environment, the video below is slowed down to 1/8 the actual speed.

<iframe width="560" height="315" src="https://www.youtube.com/embed/zCNUWmhFmEU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### Troubleshooting

A big portion of the process was the troubleshooting aspect as most of the existing system hasn't been continued as the last student had graduated.
To manage the new and old bugs that appeared was good documentation and data analysis.
Below are some of the more challenging problems to troubleshoot.


wire saga

new material saga





