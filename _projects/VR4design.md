---
title: VR for Design
year: Spring 19
order: 100
stlwv2_models: yes
type: research
---


The *VR for Design* research project is to develop and test a new pipeline for designers to interact and iterate with their models. 
This research is done under [Professor Bjoern Hartmann](https://people.eecs.berkeley.edu/~bjoern/) and the [Jacobs Institute for Design](https://jacobsinstitute.berkeley.edu/). 

![vr gif](/website/assets/images/YoutubeVr_1.gif)

---


### Motivation and Concept

As rapid prototyping tools and spaces increase, designers build more complicated assemblies with many moving parts.
The only way to interact with these designs is to build a physical prototype.

![Design Workflow](/website/assets/images/Vr4designFlow.JPG)

This project attempts to provide an alternative pathway to interact with designs through virtual reality.
The goal is to create a virtual representation with all the proper physics, material properties, and moving parts you would expect from a physical prototype.


This method has a number of potential advantages:

- Accelerates design cycle by saving fabrication time

- Lowers the barrier of entry for design by saving cost

- Test out ergonomic issues and relative size that you can't visualize from a screen

- Have interactable design reviews with multiple parties

With every iteration cycle, these benefits get realized over and over.
Similar to how 3D printing has become an ubiquitous prototyping tool in many industries, hopefully this can be a new design/interaction tool in many fields.

---

### Implementation

In a team of two, we implemented a pipeline that analyze the joint information from Fusion 360 CAD environment, re-configures the model with Unity's joint, and incorporates the user's movement into meaningful interaction in VR. 

![workflow](/website/assets/images/vrWorkflow.png)

The CAD program chosen was [Fusion 360](https://www.autodesk.com/products/fusion-360/overview#banner) for its more ubiquity amongst students (free software) and beginner friendly environment.

![api](/website/assets/images/Vr4designAPI.JPG)

A lot of the engineering effort went into using the information available through the [Fusion API](https://help.autodesk.com/view/fusion360/ENU/?guid=GUID-7B5A90C8-E94C-48DA-B16B-430729B734DC) to create geometric data to re-configure the joints in Unity.
The program must be robust enough to handle all the edge cases when there was not enough information while minimizing user input to make the program as seemless as possible. 

Check out the video below of how the program was used to help iterate on a standing desk design:

<iframe width="560" height="315" src="https://www.youtube.com/embed/BJeVW7IxlvY" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
