---
title: Surgical Tool Change End Effector
brief: An STM32-based lithium battery safety, charging, & balancing solution.
thumbnail: /assets/images/thumbnail_bms.png
year: 2016
order: 92
---

![bms model](/assets/images/bms.png)

![bms photo](/assets/images/bms_photo.png)

As an extension of my [motorized longboard](/projects/longboard/) project, I worked with a friend to design a comprehensive safety, charging, and cell balancing solution for lithium batteries.

The system is built around an LTC6803 battery monitor IC and STM32F303 microcontroller.

---

Features:
- overvoltage, undervoltage, and overtemperature protection
- bidirectional current monitoring for overcurrent protection and SoC estimation
- boost converter for CC/CV charging high voltage packs from a standard laptop adapter
- 100mA passive cell balancing
- UART, I2C, and CAN communication ports
- WS2812 addressable LED support
- compact 1.9in x 2.9in PCB size
