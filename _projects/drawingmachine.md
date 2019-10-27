---
title: Optimizing Surfaces for Grasping
year: Summer16 - Spring17
order: 99
latex: yes
stlwv2_models: yes
type: research
---

![drawing_animated](/website/assets/images/drawing_animated.gif){: width="100%"}

For our midterm project in UC Berkeley's *Introduction to Prototyping & Fabrication* course, my partner and I designed, built, and programmed a 2D plotter with a polar coordinate system.

---

<div class="stlwv2-model" data-model-url="/assets/models/drawingmachine.stl"></div>

![pen_holder](/website/assets/images/penholder.jpg)

### Mechanical Design

We constructed our plotter out of 1/4" plywood, and used standard NEMA17 steppers for both linear and angular movement. An SMT-1325S magnetic solenoid is attached to the pen holder for the lifting motion.

---

![drawing_machine](/website/assets/images/plotter.jpg)

### Software

To run the plotter, we developed a custom [g-code](https://en.wikipedia.org/wiki/G-code) interpreter that accepts standard CNC commands read from either our microcontroller's flash memory or a USB serial connection. The latter allows toolpaths to be easily generated using off-the-shelf CAM applications and sent to the machine via our dashboard application.

All of the firmware was written in C++ using the Arduino platform, and our dashboard application was built as a Google Chrome Packaged App in Javascript.

<!-- most of this blurb is just an excuse to use latex -->

Most of the code itself was pretty straightforward, but we initially had some issues with the quality of lines being drawn by our machine.
This was largely a result of our naive position interpolation, which didn't compensate for the nonlinear relationship between our polar motor positions and our cartesian pen coordinates.

When given two coordinates to draw a straight line between, this would result in an arc instead. Our original solution of treating longer lines as series of smaller segments (one arc becomes a series of smaller, less visible arcs) worked alright, but this method of discrete linearization had issues when we tried to increase the resolution. We ultimately approached this problem with some simple calculus, by calculating polar velocity setpoints for our system as functions of our desired cartesian velocities:

$$
\begin{align*}
    r &= \text{leadscrew linear position} \\
    \theta &= \text{turntable angular position} \\
    x &= \text{effective cartesian x} \\
    y &= \text{effective cartesian y} \\\\
    x &= r \cos \theta \\
    y &= r \sin \theta \\\\
    \frac{dx}{dt} &= \frac{dr}{dt} \cos \theta - r\frac{d\theta}{dt}sin \theta\\
    \frac{dy}{dt} &= \frac{dr}{dt} \sin \theta + r\frac{d\theta}{dt}cos \theta\\\\
    \begin{bmatrix}\frac{dx}{dt} \\ \frac{dy}{dt}\end{bmatrix} &= \begin{bmatrix}\cos \theta & -r \sin \theta \\ \sin \theta & r \cos \theta\end{bmatrix}\begin{bmatrix}\frac{dr}{dt} \\ \frac{d\theta}{dt}\end{bmatrix} \\\\
    \begin{bmatrix}\frac{dr}{dt} \\ \frac{dy}{dt}\end{bmatrix} &= \begin{bmatrix}\cos \theta & -r \sin \theta \\ \sin \theta & r \cos \theta\end{bmatrix}^{-1}\begin{bmatrix}\frac{dx}{dt} \\ \frac{dy}{dt}\end{bmatrix} \\
                                                               &= \begin{bmatrix}\cos \theta & \sin \theta \\ -\frac{1}{r} \sin \theta & \frac{1}{r} \cos \theta\end{bmatrix}\begin{bmatrix}\frac{dx}{dt} \\ \frac{dy}{dt}\end{bmatrix} \\\\
    \frac{dr}{dt} &= \frac{dx}{dt} * \cos \theta + \frac{dy}{dt} * \sin \theta \\
    \frac{d\theta}{dt} &= -\frac{dx}{dt} * \frac{1}{r} \sin \theta + \frac{dy}{dt} * \frac{1}{r} \cos \theta \\
\end{align*}
$$

---

### Electronics

All of the electronics work was done on perfboard, and included:
- an Arduino Nano microcontroller
- two DRV8825 stepper drivers (one for x, one for theta)
- an IRLB8721 logic-level N-fet (for actuating a solenoid that lifts the pen up and down)
- connectors broken out for external switches & LEDs

---

### Links

- [Demo video](https://www.youtube.com/watch?v=BZjUXDSYovs)
- [Earlier prototype video](https://www.youtube.com/watch?v=NW6hx6rUEO0)
- [Firmware repository](https://github.com/brentyi/drawing_machine_firmware)
- [Dashboard application repository](https://github.com/brentyi/drawing_machine_dashboard)
- [Mechanical design repository](https://github.com/nanditapiyer/drawing_machine_hardware)
