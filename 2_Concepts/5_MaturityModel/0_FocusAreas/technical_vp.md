---
layout: default
title: Technical Viewpoint
nav_order: 4
parent: Capability description
grand_parent: SpesML Maturity Model
permalink: /concepts/maturity_model/focus_areas/technical_vp.html
---

# Technical Viewpoint
In this page we describe the Technical Viewpoint functional domain. There are five focus areas in this Viewpoint: the Technical Component Modeling (TCM), the Technical Architecture Modeling (TAM), the Technical Context Modeling (TTM), the Modeling of Software Execution Platform (HAM), and the Software Architecture Modeling (HAM). This functional domain lacks 'behavior modeling' capabilities, the behavior modeling happens in the Functional and Logical Viewpoints. Modeling guideline for this functional domain can e seen [here](https://spesml.github.io/plugin/technical_viewpoint.html#how-to-model).
	
## Technical Component Modeling (TCM)
This focus area describe capabilities related to the modeling of technical components.                                    

### TCM A: For technical components, their interface is modeled with associated input and output  signals.
Technical components must be modeled to the level of interface definition. The technical component can have sub-type which describes to the domain it belongs to (e.g., mechanical component, electrical component). *Plugin usage*: A component must look like the one on this picture. Signal lines connecting it to other components is not needed. This is a requirement of capability TAM A. This capability is similar to the SFM A and LCM A.

### TCM B: technical components and requirements they satisfy are related by a satisfy or require relation.
This capability traces requirements and technical components through the _satisfy_ relation.
 

## Technical Architecture Modeling (TAM)                                 
This focus area is concerned with the modeling of the relations between technical components, which form the technical architecture. Behavior modeling is not part of the Technical Viewpoint, thus, this focus area encompasses a smaller amount of capabilities compared to the other Viewpoints.

### TAM A: The technical components and their dependencies are modeled.
The technical components are connected with signal lines indicating their dependencies with other technical components.

### TAM B: Technical components are related to logical components that they implement by a realize relation. 
Some of the technical components implement logical components and this is made explicit through a _realize_ relation. More on tracing between logical components and functions can be found [here](https://spesml.github.io/concepts/modeling_framework/functional_viewpoint.html#tracing-between-functions-and-elements-of-the-logical-viewpoint). _Plugin usage_: this information is stored in the SpesML LogicalToFunctional Matrix. More information on this can be found [here](https://spesml.github.io/plugin/logical_viewpoint.html#spesml-logicaltofunctional-matrix).

## Technical Context Modeling (TTM) 
This focus area is concerned with the context modeling (i.e.,  actors, other systems) of the technical viewpoint.

### TTM A: The  system under development (i.e., the top-level technical component) is modeled by a composition of all technical components.
The SuD inner details are described by the models of its technical child-components.

### TTM B: Actors  of the operational context (e.g., external systems or users) are modeled with a syntactic interface (inputs and outputs). 
The context is fully modeled and their interfaces are connected to the SuD interfaces.

## Modeling of SW Execution Platform  (HAM)	
This focus area is concerned with the execution platform, i.e., hardware elements, and the allocation of software elements.

### HAM A: Necessary HW elements of the execution platform are modeled.
This capabilities was created to consider the modeling of the hardware elements of the execution platform.

### HAM B: The properties and resource of the communication links (e.g., bandwidth) are modeled.
The communication links characteristics are defined when this capability is implemented. The criticality of these elements can vary for different kind of systems.

### HAM C: The SW architecture (BaseSW, middleware, RTE, application SW) on an execution element is modeled.
This capability describes the modeling of all software elements on an execution element.

### HAM D: The properties and resources of the execution elements (e.g., CPU, RAM, ROM) are modeled. PreReq: HAM A
This capability recommends the modeling of the execution elements properties. These properties have direct impact on the SuD properties, such as processing time. 

## SW Architecture Modeling (SAM)	
This focus area is concerned with the decomposition of the software subsystem into tasks and respective allocation in the execution platform elements. 

### SAM A: The decomposition of the software subsystem into tasks is modeled.
The software subsystem is decomposed in the least granular form, namely tasks. 

### SAM B: The mapping of SW tasks to elements of the execution platform is modeled.
The tasks created from the decomposition of the software subsystems is mapped to the elements of the execution platform. 
