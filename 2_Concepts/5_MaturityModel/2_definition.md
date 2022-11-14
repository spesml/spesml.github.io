---
layout: default
title: Capability description
nav_order: 3
parent: SpesML Maturity Model
grand_parent: SpesML Concepts
has_children: false
has_toc: true
permalink: /concepts/maturity_model/definition.html
---
# Capability description

- [Requirements Viewpoint](#requirements-viewpoint)
- [Functional Viewpoint](#functional-viewpoint)
- [Logical Viewpoint](#logical-viewpoint)
- [Technical Viewpoint](#technical-viewpoint)

# Requirements Viewpoint
The Requirements Viewpoint is the functional domain of the SpesML MM concerned with the definition of requirements. There are three focus areas in this Viewpoint: the Requirements Elicitation (REE), the Requirements Specification (RES), and the Requirements Refinement (RER). More information on the Requirements Viewpoint can be found [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html).  

##  Requirements Elicitation (REE): 
This focus area is the smallest of this Viewpoint, having only two capabilities. 

### REE A: Requirements are modeled by a distinct Requirement Element per requirement.
This capability states that requirements should be modeled in the SpesML plugin using the Requirement Element. *Plugin usage*: The engineer should right click the containment tree in the RequirementsViewpoint folder, and select create element->create a SpesML Requirement element. The REE A is the most basic capability from this functional domain. Because of this, all the other capabilities from this Viewpoint requires it.  More information on the Requirement Element can be found [here](https://spesml.github.io/plugin/requirements_viewpoint.html#elements).

###  REE B: Requirements are categorized into one of the categories: Capability, Functional, Quality, Constraint.
This capability can be considered implemented when the Requirement Element category is defined. The categories supported by the SpesML Modeling Framework are described [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html#modeling-elements). *Plugin usage*: The requirements category is symbolized trough the capital letter in the requirements icon and can be selected in the Specification window.
## Requirements Specification (RES)

This focus area has three capabilities, two of them are of Conceptual kind. 

### RES A: Requirements are equipped with attributes containing meta-information including: name, category, status, rationale, and source. 
The SpesML Modeling framework supports a number of attributes, which serves as template, and segregate information from the requirement description, improving readability. *Plugin usage*: The attributes of a requirements can be accessed through right click menu->Specification. The image below depicts how they are presented in the plugin.
Additional information on requirement attributes can be found [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html#requirements-attributes).

### RES B: Requirements text is formulated following certain sentence templates (e.g., EARS or Sophist MasterTemplate) ( C).
Sentence template require extra effort to achieve compliance at the initial phases, but prevents rework in future phases. Although the SpesML MF do not suggest using a specific template, it does suggest they should be used to attend the organization's needs (e.g, domain, project size). This is a *Conceptual* capability

### RES C: The requirements text is aligned with modeling elements that they are related to (e.g., naming of ports or internal states) ( C).
This capability is related to the documentation of architecture elements within a requirement description (e.g., the naming of ports). This capability requires the LCM C capability. This is a *Conceptual* capability.

###  RES D: The requirement is formalized in a formal specification language (e.g., temporal logic) ( C).
This capability characterizes requirements described using formal representations, for instance in the property specification language which is being looked into in a separate project activity, or as formulas in a temporal logic. Formal representations typically are required to be reviewed in order to ensure that architectural model and property specification are consistent. This is a *Conceptual* capability.

## Requirements Refinement (REF)
The capabilities in this focus area represent types of tracing relations that exist between requirements, and between requirements and architectural elements. More on requirements tracing relations can be seen [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html#tracing-relationships).

### REF A: If a low-level requirement is derived from a high-level requirement, they are related by a derived relation. Note: Both requirements must address the same system scope.
The derive relationship is used to add detail or to include certain design decisions to a requirement. Unlike RES C, where the design decisions are included in the requirement description, REF A is about two different requirements related by this specific tracing relation. It is a common pattern that an architectural element satisfies a requirements, which itself is derived from a more high-level requirement. More information on the derive relationship can be found [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html#tracing-relationships). *Plugin usage*: This capability is realized in the SpesML RequirementToRequirement Matrix. More information on this can be found [here](https://spesml.github.io/plugin/requirements_viewpoint.html#spesml-requirementtorequirement-matrix).

### REF B: If a system requirement is broken down into several component requirements, the system requirement is related to the component requirements by a decompose relation.
This capability describe the decompose relation, which connects requirements as explained [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html#co-evolution-of-requirements-and-architecture).

### REF C: If a requirement satisfies a property that is required in another requirement, the requirements are related by a Match relation.
The *match* relation traces architectural elements (functions or components) which satisfy or require requirements. And requirements "required" by an architectural element must be discharged by matching them with "satisfied" requirements of another architectural element. More information on this can be found [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html#development-against-assumed-requirements).

# Functional Viewpoint
The Functional Viewpoint functional domain of the SpesML MM is concerned with the modeling of the SuD functions, sub-functions, and functional architecture. The Functional Viewpoint has four focus area: System Function Modeling (SFM), White-box Modeling (WBM), Functional Context Modeling (FTM), and Mode Modeling (MOM). More on the functional viewpoint can be found [here](https://spesml.github.io/concepts/modeling_framework/functional_viewpoint.html).

## System Function Modeling (SFM)
This focus area is concerned with the modeling of system functions, their interfaces, and behavior.

### SFM A: System functions are modeled with a syntactic interface (inputs and outputs).
This capability describes that systems functions are modeled with their respective syntactic interface.
*Plugin usage*: Instructions can be found [here](https://spesml.github.io/plugin/functional_viewpoint.html#how-to-create-system-functions).

### SFM B: System functions are related with a satisfy or require relationship to requirements they satisfy or assume.
The satisfy relation traces the requirement to a function, which is useful to identify whether there are requirements not addressed by any function, or if there are functions that do not fulfill any requirement. More information can be found [here](https://spesml.github.io/plugin/functional_viewpoint.html#spesml-functiontorequirement-matrix).

### SFM C: The behavior of the system functions is modeled by a state machine or decomposed in a white-box model.  
This capability is related to the behavior of the system function, which can be described using state machines at the system function level, or from the state machines of the white-boxes that decompose the system function.

### SFM D: The model of the system functions can be simulated together with a description of the context.
When the behavior of the system function is fully modeled, the next step is to be able to simulate its behavior together with the context behavior. This is the most mature capability in this functional domain. *Plugin usage*: More information on this can be found [here](https://spesml.github.io/concepts/modeling_framework/simulation.html).

## White-box Modeling (WBM)
The capabilities of this focus area are related to the modeling of the white-box functions. These decompose the system functions.

### WBM A: The white-box functions that implement a system function are modeled with a syntactic interface (inputs and outputs). 
This capability describes the definition of white-box functions and their respective syntactic interface.
*Plugin usage*: How to create white-box function can be found [here](https://spesml.github.io/plugin/functional_viewpoint.html#how-to-create-white-box-functions). 

###  WBM  B: White-box functions are related with a satisfy or require relationship to requirements they satisfy or assume.
This capability describe the satisfy tracing relationship between requirements and white-box functions satisfying these requirements. 

###  WBM  C: The behavior of the white-box functions is modeled. 
Using state machines, the behavior of the white-box function should be modeled in order to have this capability present in a development team. More on state machines can be found [here](https://spesml.github.io/plugin/state_machines.html).

## Functional Context Modelling (FTM)
The SuD context, inside (FTM A), outside (FTM B), and its behavior (FTM C) are contemplated by this focus area. 

### FTM A: The system under development (i.e., the top-level system function) is modeled by a composition of all system functions.


### FTM B: Functions of the operational context (e.g., external inputs) are modeled with a syntactic interface (inputs and outputs). Note: Functions do not need to be allocated to actors yet.
To have this capability implemented, the operational context functions are modeled with respective syntactic interface.

### FTM C: For each function in the operational context, the behavior is modeled.
Using state machines, the functions' behavior of the operational context is modeled.

## Mode Modeling (MOM)
This focus area describes the implementation of system modes of the SuD as described [here](https://spesml.github.io/concepts/modeling_framework/functional_viewpoint.html#mode-model).

###  MOM A: The operating modes of a system are modeled in terms of a state machine. 
Using state machines, the operating modes the SuD are described. *Plugin usage*: In this [link](https://spesml.github.io/plugin/functional_viewpoint.html#how-to-create-a-mode-model) is described how to put this capability into practice.

### MOM B: The operating modes in the mode model are consistent with the mode channels between the system's functions.
The interfaces between system functions (i.e., model channels) and the operating modes are consistent with each other.

# Logical Viewpoint
The Logical Viewpoint functional domain of the SpesML MM is concerned with the modeling of the logical components. There are four focus areas in this Viewpoint: the Logical Component Modeling (LCM), the Logical Architecture Modeling (LAM), the Logical Context Modeling (LTM), and the Logical Physical Modeling (LPM). More information on the Logical Viewpoint can be found [here](https://spesml.github.io/concepts/modeling_framework/logical_viewpoint.html).

## Logical Component Modeling (LCM)
This focus area address the component modeling in the logical viewpoint.

### LCM A: For logical components, their interface is modeled with associated input and output signals. 
This capability describes the modeling of logical components with respective interfaces. This is the most basic capability of this focus area, and functional domain. The other capabilities require this capability to be implemented. *Plugin usage*: In the plugin the interfaces are defined using Logical Interfaces with Logical Interface Types. How to use in the plugin is described [here](https://spesml.github.io/plugin/logical_viewpoint.html#how-to-model). 

### LCM B: The behavior of the logical components is modeled.  
This capability describes that the logical components have their behavior modeled. *Plugin usage*: In the plugin, state machines are used to model the behavior of components. More information on this can be found [here](https://spesml.github.io/plugin/state_machines.html). Another possibility is to use the state machines from the Functional Viewpoint using a Functional-Logical Adpater. More information on this can be found [here](https://spesml.github.io/plugin/logical_viewpoint.html#functional-logical-adapter).

### LCM C: Logical components and requirements they satisfy are related by a satisfy or require relation.
This capability requires that the *satisfy* relations between  components and requirements are explicitly defined in the models. *Plugin usage*: The SpesML plugin uses a tracing matrix to model this. On how to trace components and requirements using the satisfy relationship in the plugin can be found [here](https://spesml.github.io/plugin/logical_viewpoint.html#spesml-logicaltorequirement-matrix). 

## Logical Architecture Modeling (LAM)
This focus area is concerned with the modeling of the relations between components, which form the logical architecture.

### LAM A: The logical components and their dependencies are modeled.
This capability prescribe the connection between modeled components by signal lines. 

### LAM B: Logical components are related to white-box functions that they implement by a realize relation.
The components of the logical viewpoint implement the white-box functions and this is made explicit through a *realize* relation. More on tracing between logical components and functions can be found [here](https://spesml.github.io/concepts/modeling_framework/functional_viewpoint.html#tracing-between-functions-and-elements-of-the-logical-viewpoint).
*Plugin usage*: this information is stored in the SpesML LogicalToFunctional Matrix. More information on this can be found [here](https://spesml.github.io/plugin/logical_viewpoint.html#spesml-logicaltofunctional-matrix).

## Logical conText Modeling (LTM)
In this focus area, the relevant context elements for the logical viewpoint are modeled.

### LTM A: The system under development (i.e., the top-level logical component) is modeled by a composition of all logical components (i.e., internal context).
To have this capability implemented, all components and their dependencies must be modeled, thus allowing the SuD to be modeled as a composition of all components. This is related to the internal context of the SuD. 
Pre-req: LAM A and LCM A.

### LTM B: Actors of the operational context (e.g., external systems or users) are modeled with a syntactic interface (inputs and outputs).  
This capability demands the modeling of the operational (i.e., external) context, which encompasses external systems and users. 

### LTM C: For each actor in the operational context, the behavior is modeled.
This capability describes that the actors have their behavior modeled. *Plugin usage*: In the plugin, state machines are used to model the behavior of actors. More information on this can be found [here](https://spesml.github.io/plugin/state_machines.html). Another possibility is to use the state machines from the respective elements previously defined the Functional Viewpoint using a Functional-Logical Adapter. More information on this can be found [here](https://spesml.github.io/plugin/logical_viewpoint.html#functional-logical-adapter).

## Logical Physical Modelling (LPM)  
In the SpesML methodology, physical and mechanical properties of the system and the interaction between physical and cyber components are described in the Logical Viewpoint. This focus area describes the possible levels of maturity a development team can achieve when modelling physical information for a SuD. 

### LPM A: Physical components and cyber components (SW-Subsystem) are identified and modeled as separate components in the logical structure. 
Special elements are used to identify and model physical and cyber components in the logical viewpoint.

### LPM B: Interface behavior between the physical components and the SW-Subsystem is modeled on a high level of abstraction.
The interface behavior of the physical and cyber components are modeled on a high level of abstraction.

### LPM C: Physical behaviour of the SUD and Context elements are modeled on a high level of abstraction.  
This capability requires that the physical behavior of both SuD and Context elements are modeled.

### LPM D: Aspects of the physical behaviour of the SuD are included when simulating the logical components.
The simulation of the logical components includes the aspects of the physical behavior of the SuD.


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
