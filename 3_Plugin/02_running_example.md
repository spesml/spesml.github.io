---
layout: default
title: SpesML Running Example
nav_order: 2
parent: SpesML Plugin
permalink: /plugin/running_example.html/
---
# The Window Lifter System As Running Example

To illustrate SpesML concepts and the tool implementation in the SpesML project, we have chosen the window lifter system (WLS) as a running example.
The system has the task of handling the opening and closing of the side windows in a car, with which usually everyone had already contact in real life and thus should be able to easily understand the basis aspects. 
In addition, the system is simple enough to be used as introduction example, but still has several possibilities to extend it to show all important concepts and features of SpesML. 
The general functionality of this example is based on the description of a fictitious WLS by Houdek and Peach [^1], which we filtered and adapted to have a perfectly fitting running example.

We have only selected the system specifications that are most useful for the demonstration purpose, which means that the following system description is not complete regarding an actual window lifter system.
Furthermore, it is not relevant whether our example system is perfectly realistic, because it should only demonstrate how specific SpesML concepts and the SpesML plugin can and should be used.

The following sections will introduce our running example of a window lifter system by first describing the elements it consists of, then explaining the functionality of the system, and finally presenting the resulting requirements that we used to develop the example model. 



## Hardware Setup

Our system consists of a standard car with four side doors, where each door has a window that can be opened and closed.
The vertical movement of these four windows is achieved by four electric motors, one for each window/door.
The movement of the windows can be controlled via switches that are integrated into the armrests of the doors.
The two rear doors and the front passenger door have exactly one window lifter switch each. The driver door has four window lifter switches to enable a global control possibility, one for each window, and further three switches for the child-proof lock, one for each other passenger window.

A brightness sensor exists in the car that provides the current brightness of the environment.
Every door has an own control unit, e.g., an ECU, that is connected to the respective window lifter motor to control the motor and receive the motor's feedback. In addition, a central control unit exists that is connected to all of the four door control units and is responsible for all the tasks that can be decided and performed centrally for all the doors and their windows. 
The central control unit is connected to the brightness sensor and all other input devices via Ethernet, except for the other four control units, because all control units are connected among each other via a bus system, e.g. a CAN bus. The four door control units are connected with their respective window motor via USB.

There are small sensors that detect whether a window has reached one of its end positions. When something is blocking the window movement in general, it is detected by a higher resistance of the respective window lifter motor. To reduce the complexity of the example model, we have decided to model this motor feedback simply as status feedback with four modes: if the window is in its top position, in its bottom position, somewhere in between, or blocked. 



## Functionality

The functionality can be best explained by first introducing the basic behavior of the windows and their switches. Afterwards, we describe safety features that make the basic behavior more secure before we finally show the comfort features that should support the driver and the passengers.

### Basic Functionality
Every door has a switch for its own window. If this switch is pushed downwards, the connected window will move down ("opening"), and if the switch is pulled upwards, the window will move up ("closing").
If the switch is not pushed or pulled anymore, it returns to its neutral position. The described window movements that are aligned with the positioning of the switch will continue as long as the switch is active, i.e., pushed or pulled. The window movement will stop when the switch is released or the window is in its corresponding end position or a safety feature overrides the movement. 

The driver can control these window movements not only for the driver window but for all windows, which is why the driver door panel has three additional window switches.

### Safety Functionality
As pinch protection, the window motor will immediately stop when an obstacle is detected for the current window movement and then open the window completely. A similar feature could be implemented for crash situations, but since the functionality and the implementation would be so similar to the pinch protection, we have ignored it in this example system for the sake of complexity reduction.

Passengers should not be allowed to control the windows in a way that disturbs the driver, which is why the global movement commands by the driver switches can always override any action from other switches.

The driver can disable the window control from other passengers by activating a child-proof lock in the driver's door panel. The child-proof lock can be activated for each other passenger window separately. If child-proof lock was activated for a window, all switch inputs by this passenger are disabled until the child-proof lock button is pressed again.

The window motors need a certain voltage to ensure a safe and complete opening or closing process. Therefore, the window motors, and thereby the window movement, is automatically disabled if the battery voltage is below a certain threshold, e.g., 10V.

### Comfort Functionality
As a comfort feature, it is not needed to hold the switch permanently in an active position to trigger a corresponding window movement. As soon as the switch is pushed or pulled for at least 0.5 seconds, the window will continue with the current movement until it reaches its end position or any other obstacle, even if the switch is released. If the switch is pushed or pulled again during this time after the first release, the automatic mode is stopped.

As another comfort feature, all windows are automatically closed as soon as the car enters a tunnel and if nothing else prevents or overrides it. This is detected by a rapid brightness change via the brightness sensor. 

Finally, if the car is closed and locked, all windows are automatically closed as well, if possible.



## Requirements

For the modeling process we needed to have specific requirements that can be used in the requirement view and can be traced to model elements of the other views.
The following table shows the selection that we have chosen based on the previous system description of our window lifter system. 

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


[^1]: Reference report by Houdek and Paech: ["Das Türsteuergerät. Eine Beispielspezifikation"](https://wwwbroy.in.tum.de/lehre/vorlesungen/ase/ss05/iese-002_02.pdf)