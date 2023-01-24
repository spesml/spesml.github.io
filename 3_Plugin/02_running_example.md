---
layout: default
title: SpesML Running Example
nav_order: 2
parent: SpesML Plugin
permalink: /plugin/running_example.html/
---
# The Window Lifter System As Running Example

To support concept explanations and the tooling guide for the SpesML project, we have chosen the window lifter system (WLS) as a running example.
The system has the task of handling the opening and closing of the side windows in a car, with which usually everyone had already contact in real life and thus should be able to easily understand the basis aspects. 
In addition, the system is simple enough to be used as introduction example, but still has several possibilities to extend it to show all important concepts and features of SpesML. 
The general functionality of this example is based on ["Das Türsteuergerät. Eine Beispielspezifikation" by Houdek and Paech](https://wwwbroy.in.tum.de/lehre/vorlesungen/ase/ss05/iese-002_02.pdf), which we filtered and adapted to have a perfectly fitting running example.

The following sections will introduce our running example of a window lifter system by first describing which elements it consists of, then explaining the functionality of the system, and finally presenting the requirements that we used to develop the example model. 



## Context and Technical Elements of the Window Lifter System

Our basic example system consists of a standard car with four side doors, where each door has a window that can be opened and closed.
The vertical movement of these four windows is achieved with four motors, one for each window/door.
A passenger can control the window movement via switches that are integrated into the armrests of the doors.
The two rear doors and the front passenger door have exactly one window lifter switch each. The driver door has four window lifter switches to enable a global control possibility (one for each controllable window) and further three switches for the child-proof lock (one for each other passenger window).

A central brightness sensor exists in the car that provides the current brightness of the environment.
Every door has an own ECU that is connected to the respective window lifter motor to control the motor and receive the motor's feedback. In addition, a central ECU exists that is connected to all of the four door ECUs and is responsible for all the tasks that can be decided and performed centrally for all the doors and their windows. 
Regarding connection type, the central ECU is connected to the central brightness sensor and all other input providing devices via Ethernet, except for the other four ECUs, because all ECUs are connected among each other via a CAN bus. The four door ECUs are connected with their respective window motor via USB.

Whether a window has reached one of its end positions, is detected via small feelers at these positions. Whether something blocks the window's further movement in general, is detected via a higher resistance of the respective window lifter motor. To reduce the complexity of the example model, we have decided to model this motor feedback simply as status feedback with four modes: if the window is in its top position, in its bottom position, somewhere in between, or blocked. 



## Functionality of the Window Lifter System

The functionality can be best explained by first introducing the basic behavior of the windows and their switches. Afterwards, we describe the safety features that make the basic behavior more secure before we finally show the comfort features that should support the driver and the passengers.

### Basic Functionality
Every door has a switch for its own window. If this switch is pushed downwards, the own window will move down ("opening"), and if it is pulled upwards, the window will move up ("closing").
If the switch is not pushed or pulled anymore, it returns in its neutral position. The previously described window movements that are aligned with the positioning of the switch will continue as long as the switch is active, i.e., pushed or pulled, and the window is not in its corresponding end position. This means on the other side that the movement will automatically stop in two basic cases. First, the window will stop if the switch is not pushed or pulled anymore, but this can be overridden by a comfort feature, which will be explained later. Second, the window will stop if it is completely opened during a pushed switch or completely closed during a pulled switch, even if the switch is still pushed or pulled. These two basic cases are extended with more stop triggers by some safety features, which will be explained soon.

The exact same behavior is performed for every incoming window lifter control stimulus, which does not always need to be the direct stimuli from its own button but can be a global window movement command or a command from the global driver switches. This results in the situation that the driver can control with three switches in the driver door the other three windows besides the own driver window with the fourth switch.

### Safety Functionality
As jam protection, the window motor will not only stop when the window's end positions are reached, but also at any time when an obstacle is detected in the way of the current window movement. In addition, the respective window will immediately reverse its movement and open completely in the latter case of a detected obstacle to enable a possible release of such an obstacle. 

Passengers should not be allowed to control the windows in a way that disturbs the driver, which is why the global movement commands by the driver switches will always override any other switch stimuli.

In case the driver wants to prevent any manipulation of the windows by the other passengers, a child-proof lock can be activated via switches in the driver's door panel. The child-proof lock can be activated for each other passenger window separately. If child-proof lock was activated for a window, all switch inputs by this passenger are ignored until the child-proof lock button is pressed again to deactivate this mode.

The window motors need a certain voltage to ensure a safe and complete opening or closing process. Therefore, the window motors, and thereby the window movement, will not start if the battery voltage is below 10V.

### Comfort Functionality
As first comfort feature, it is not needed to hold the switch permanently in an active position for a corresponding window movement. As soon as the switch is pushed or pulled for at least 0.5 seconds, the window will continue with the current movement until it reaches its end position or any other obstacle, even if the switch is released. If the switch is pushed or pulled again during this time after the first release, the automatic mode is stopped.

The second comfort feature is that all windows are automatically closed as soon as the car enters a tunnel and if nothing else prevents or overrides it. This is detected by a rapid brightness change via the brightness sensor. 

Finally, if the car is closed and locked, all windows are automatically closed as well, if possible. This is not only a comfort but also a kind of safety feature.



## Requirements of the Window Lifter System

For the modeling process we needed to have specific requirements that can be used in the requirement view and can be traced to elements of the other views.
The following table shows our selection, which is based on the previous given description of our window lifter system. 
We have only selected the ones that are most useful for the demonstration purpose, which means that the requirement list is not complete.
Furthermore, it is not relevant whether these requirements are perfectly realistic, because they should only demonstrate how requirements can and should be used in SpesML.

| ID | Requirement |
|---|---|
| WL-1 | The system shall allow the driver and the passengers to (fully or partially) open and close the side windows of the car. |
| WL-2 | The system shall allow the driver to open and close the front and rear, left and side windows. |
| WL-3 | The system shall allow the passengers to only open and close their own window. |
| WL-4 | The system shall have a child protection feature that disallows operating the passenger windows for the passengers. |
| WL-5 | The system shall automatically close all windows when a tunnel is entered. |
| WL-6 | The system shall detect when window movement is blocked. In this case, the closing of the window shall be stopped and the window shall be lowered completely. |
| WL-7 | The system shall continuously move a window up or down as long as the corresponding button on the operating panel is pushed. |
| WL-8 | The system shall fully open or close a window when the corresponding button on the operating panel is pushed continuously for at least 0.5 seconds. |
| WL-9 | The system shall not drive the window motors to raise a window when the window is already fully closed. |
| WL-10 | The system shall not drive the window motors to lower a window when the window is already fully opened. |
| WL-11 | The system shall not operate the window motors when the battery voltage of the vehicle is below 10V. |
