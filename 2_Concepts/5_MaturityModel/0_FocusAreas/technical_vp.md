---
layout: default
title: Technical Viewpoint
nav_order: 4
parent: Capability description
grand_parent: SpesML Maturity Model
permalink: /concepts/maturity_model/focus_areas/technical_vp.html
---

# Technical Viewpoint
In this page we describe the Technical Viewpoint functional domain. There are three focus areas in this Viewpoint: the Technical Component Modeling, the Technical Architecture Modeling, and the Technical Context Modeling. This functional domain lacks 'behavior modeling' capabilities, the behavior modeling happens in the Functional and Logical Viewpoints. Modeling guideline for this functional domain can e seen [here](https://spesml.github.io/plugin/technical_viewpoint.html#how-to-model).
	
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
This focus area is concerned with the context modeling (i.e.,  actors, other systems).                               

### TTM A: The  system under development (i.e., the top-level technical component) is modeled by a composition of all technical components.
The SuD inner details are described by the models of its technical child-components.

### TTM B: Actors  of the operational context (e.g., external systems or users) are modeled with a syntactic interface (inputs and outputs). 
The context is fully modeled and their interfaces are connected to the SuD interfaces.
