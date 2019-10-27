---
title: Blue Robot- Low Cost 7 DOF Arm and Gripper
year: Spring17- Spring19
order: 105
stlwv2_models: no
---
<iframe src="https://drive.google.com/file/d/1LC0DirgkaY__70R6G0JBzAUYHXj9ZpEU/preview"></iframe>

![micromouse in maze](/website/assets/images/micromouse_maze.jpg)

Between 2016 and 2019, I helped design and teach a 2-unit robotics [DeCal](https://decal.berkeley.edu/courses/4635) course at UC Berkeley.
The course guides students with little to no technical background through the process of building and programming a "Micromouse" robot car, which attempts to autonomously solve a maze.
To do this, we cover the basics of:
- Arduino programming, C++
- Motor control
- Sensor reading: quadrature encoders, ToF distance sensors
- Interrupts, ADCs, I2C
- Robot localization & odometry
- Feedback control (PID)
- Search algorithms

---

### Robot Design

In addition to developing much of our labs and course material, I also designed a standard robot hardware kit.
These cost around $30 each, but are provided to students at no cost to assemble and program.

![micromouse robot](/website/assets/images/micromouse_robot.jpg)

Each kit contains:
- Custom lasercut wood chassis
- Custom main control PCB
- Arduino Nano microcontroller
- DRV8312 brushed DC motor driver
- MPU6050 6-DOF IMU
- nRF24l01+ 2.4Ghz wireless transciever
- 2x Brushed DC motors w/ 420 PPR magnetic quadrature encoders
- 3x VL53L0X ToF distance sensors
- Rechargeable 9V lithium battery

Main control PCB design:

<iframe src="https://drive.google.com/file/d/1XZtYgKT8Xb47ICcy3YtWv1HZHIAcDwEf/preview"></iframe>

---

### Links

- [Micromouse on UC Berkeley IEEE Website](https://ieee.berkeley.edu/micromouse)
- [Spring 2018 Class Photos](https://photos.app.goo.gl/H12PfdtpopbzCXpv5)
- [Fall 2018 Class Photos](https://photos.app.goo.gl/9azAu6kgRJ9qmyVQA)
- [Spring 2019 Class Photos](https://photos.app.goo.gl/3cusFcwXWEnJS4Y16)
