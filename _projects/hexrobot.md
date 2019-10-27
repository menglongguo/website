---
title: VR for Design
year: Spring19
order: 100
stlwv2_models: yes
---

![hexrobot gif](/website/assets/images/sparky_animated.gif)

For our final project in UC Berkeley's *Introduction to Prototyping & Fabrication* course, my partner and I set out to design an extremely low cost (~$60) [RHex](https://en.wikipedia.org/wiki/Rhex)-style robot.

---

<div class="stlwv2-model" data-model-url="/assets/models/hexrobot_full.stl"></div>

### Mechanical Design

Mechanical design was done with an emphasis on simplicity: we only needed to fabricate 5 unique parts!

The chassis is constructed out of three pieces of 1/4" plywood, and the motorized leg modules are printed in ABS using a consumer-grade 3D printer. The current version of the legs are lined with 5mm polyurethane timing belt (teeth outwards), which acts as a cheap and wear-resistant tread.

---

### Electronics

![hexrobot electronics](/website/assets/images/rhex_electronics.jpg)

Each leg module contains a custom 14-bit absolute encoder board (linked below), which communicates to a central microcontroller over I2C.

A central control PCB was designed to co-locate:
- three TB6612 dual h-bridge driver ICs (for driving 6 individual leg motors)
- an ADXL345 3-axis accelerometer for orientation detection
- an MP1584 5V/3A buck converter (for powering peripherals)
- an N-fet-based electronic power switch
- I2C output connectors for our absolute encoders
- 10-bit filtered battery voltage measurement
- ATmega328P-based Arduino Nano microcontroller

---

### Firmware

All of the code for our robot was built around the Arduino platform in C++.

It's made of a few main components:
- an open-loop gait controller for generating synchronized leg trajectories in an alternating tripod gait
- six local joint controllers: these are simple PD loops w/ velocity feedforwards
- a BLE interface for remote monitoring and teleoperation
- a set of dynamically configurable settings which can be pushed to & pulled from the EEPROM (primarily for control loop tuning on the fly)

---

### Links

Videos:
- [Final project video](https://www.youtube.com/watch?v=aiBIEI0JHwY)
- [Earlier prototype video](https://www.youtube.com/watch?v=FYNiEJGiTPM)

Source code and design files:
- [Firmware](https://github.com/brentyi/sparky_firmware)
- [Mechanical design](https://github.com/nanditapiyer/sparky_mechanical)
- [Main control PCB design](https://github.com/brentyi/sparky_electronics)
- [Absolute encoder PCB design](https://github.com/brentyi/as5048b_breakout)
