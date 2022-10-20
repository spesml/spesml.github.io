---
layout: default
title: Definition
nav_order: 2
parent: SpesML Maturity Model
grand_parent: SpesML Concepts
permalink: /concepts/maturity_model/definition.html
---
## Capability description

In the following, we describe each capability in detail, grouped by respective Viewpoint and Focus area. Additionally, we describe how the capability is used in the [plugin](https://spesml.github.io/plugin.html/).

### Requirements Viewpoint
There are three focus areas in this Viewpoint: the Requirements Elicitation (REE), the Requirements Specification (RES), and the Requirements Refinement (RER). More information on the Requirements Viewpoint can be found [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html).  

####  Requirements Elicitation (REE): 
This focus area is the smallest of this Viewpoint, having only two capabilities. 

##### REE A: Requirements are modeled by a distinct Requirement Element per requirement.
This capability describes that requirements are modeled in the SpesML plugin using the Requirement Element. *Plugin usage*: The engineer should right click the containment tree in the RequirementsViewpoint folder, and select create element->create a SpesML Requirement element as depicted in the image below.

![REE A example](/images/reea-example.png){:class="img-responsive"}

The REE A is a very basic capability. Despite having the lowest maturity in this Viewpoint, all the other capabilities from this Viewpoint requires it.  More information on the Requirement Element can be found [here](https://spesml.github.io/plugin/requirements_viewpoint.html#elements).

#####  REE B: Requirements are categorized into one of the categories: Capability, Functional, Quality, Constraint.
This capability can be considered implemented when the Requirement Element category is defined. The categories supported by the SpesML Modeling Framework are described [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html#modeling-elements). *Plugin usage*: The requirements category is symbolized trough the capital letter in the requirements icon.
#### Requirements Specification (RES)

This focus area has four capabilities. Three of them are of Conceptual kind. 

##### RES A: Requirements are equipped with attributes containing meta-information including: name, category, status, rationale, and source. 
The SpesML Modeling framework supports a number of attributes and serving as template, which segregate information from the requirement description, improving readability. *Plugin usage*: The attributes of a requirements can be accessed through right click menu->properties. The image below depicts how they are presented in the plugin.

![REE A example](/images/car-attributes.png){:class="img-responsive"}

Additional information on requirement attributes can be found [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html#requirements-attributes).

##### RES B: Requirements text is formulated following certain sentence templates (e.g., EARS or Sophist MasterTemplate) ( C).
Sentence template require extra effort to achieve compliance at the initial phases, but prevents rework in future phases. Although the SpesML MF do not suggest using a specific template, it does suggest they should be used, whichever better fits the organization's needs (e.g, domain, project size). This is a *Conceptual* capability

##### RES C: The requirements text is aligned with modeling elements that they are related to (e.g., naming of ports or internal states) ( C).
This capability is related to the documentation of architecture elements within a requirement description (e.g., the naming of ports). This capability requires (?) the LCM C. This is a *Conceptual* capability.

#####  RES D: The requirement is formalized in a formal specification language (e.g., temporal logic) ( C).
This capability characterizes requirements described using formal representations, for instance in the property specification language which is being looked into in a separate project activity, or as formulas in a temporal logic. Formal representations typically are required to be reviewed in order to ensure that architectural model and property specification are consistent. This is a *Conceptual* capability.


Capabilities RES B, C, and D are Conceptual, hence the plugin does not provide support (e.g, automated consistency and correctness). More information on these properties can be seen [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html#requirements-representation).

#### Requirements Refinement (REF)
The capabilities in this focus area represent types of tracing relations that exist between requirements, and between requirements and architectural elements. More on requirements tracing relations can be seen [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html#tracing-relationships).

##### REF A: If a low-level requirement is derived from a high-level requirement, they are related by a derived relation. Note: Both requirements must address the same system scope.
The derive relationship is used to add detail or to include certain design decisions to a requirement. Unlike RES C, where the design decisions are included in the requirement description, REF A is about two different requirements related by this specific tracing relation. It is a common pattern that an architectural element satisfies a requirements, which itself is derived from a more high-level requirement. More information on the derive relationship can be found [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html#tracing-relationships). *Plugin usage*: This capability is realized in the SpesML RequirementToRequirement Matrix. More information on this can be found [here](https://spesml.github.io/plugin/requirements_viewpoint.html#spesml-requirementtorequirement-matrix).

##### REF B: If a system requirement is broken down into several component requirements, the system requirement is related to the component requirements by a decompose relation.
The decompose relation traces related requirements. Unlike REF A, these requirements do not necessarily belong to the the same systems scope. 
The decompose relation is further explained [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html#co-evolution-of-requirements-and-architecture).

##### REF C: If a requirement satisfies a property that is required in another requirement, the requirements are related by a Match relation.
The *match* relation traces an architectural element to a requirement of type *Requirement*.  One instance of Match relation is the one used in requirement defining safety contracts for dynamic systems of systems. In this kind of systems, some specific levels of safety assurance are required to guarantee safety of the whole system.

 
### Functional Viewpoint
The Functional Viewpoint has four focus area.
More on the Functional Viewpoint can be seen [here](https://spesml.github.io/concepts/modeling_framework/functional_viewpoint.html).

#### System Function Modeling (SFM)

##### SFM A: System functions are modeled with a syntactic interface (inputs and outputs).
*Plugin usage*: Instructions can be found [here](https://spesml.github.io/plugin/functional_viewpoint.html#how-to-create-system-functions).

##### SFM B: System functions are related with a satisfy or require relationship to requirements they satisfy or assume.
The satisfy relation traces the requirement to a function, which is useful to identify whether there are requirements not addressed by any function, or if there are functions that do not fulfill any requirement. *Plugin usage*: This relation is described with a table as depicted in the figure below. More information can be found [here](https://spesml.github.io/plugin/functional_viewpoint.html#spesml-functiontorequirement-matrix).

![changeHere](/images/sfmb-wbfb-example.png){:class="img-responsive"}


##### SFM C: The behavior of the system functions is modeled by a state machine or decomposed in a white-box model.  
This capability is related to 

##### SFM D: The model of the system functions can be simulated together with a description of the context.


#### White-box Modeling (WBM)
The capabilities of this focus area are related to the modeling of the white-box functions.

##### WBM A: The white-box functions that implement a system function are modeled with a syntactic interface (inputs and outputs).  
*Plugin usage*: How to create white-box function can be found [here](https://spesml.github.io/plugin/functional_viewpoint.html#how-to-create-white-box-functions). 

![changeHere](/images/wbfa-example.png){:class="img-responsive"}

#####  WBM  B: White-box functions are related with a satisfy or require relationship to requirements they satisfy or assume.
The image of SMF B also depicts this capability.

#####  WBM  C: The behavior of the white-box functions is modeled. 
Using state machines, the behavior of the white-box function should be modeled in order to have this capability present in a development team. More on state machines can be found [here](https://spesml.github.io/plugin/state_machines.html).
![changeHere](/images/wbfc-example.png){:class="img-responsive"}

#### Mode Modeling (MOM)
This focus area describes the implementation of modes of the SUD as described [here](https://spesml.github.io/concepts/modeling_framework/functional_viewpoint.html#mode-model).

#####  MOM A: The operating modes of a system are modeled in terms of a state machine. 
*Plugin usage*: In this [link](https://spesml.github.io/plugin/functional_viewpoint.html#how-to-create-a-mode-model) is described how to execute this capability.

![REE A example](../3_ModelingFramework/images/functional_viewpoint/mode-model.png{:class="img-responsive"}

##### MOM B: The operating modes in the mode model are consistent with the mode channels between the system's functions.


#####  MOM C: It is automatically analyzed whether transitions between operating states are correctly maintained by the system functions ( C).
This is a *Conceptual* capability. 

#### Functional conText Modelling (FTM)
The SUD context, inside (FTM A), outside (FTM B), and its behavior (FTM C) are contemplated by this focus area. 

##### FTM A: The system under development (i.e., the top-level system function) is modeled by a composition of all system functions.
The GIF below shows inside the system functions inside the SUD in the plugin. FIXME
![changeHere](/images/ftma-example.gif){:class="img-responsive"}

##### FTM B: Functions of the operational context (e.g., external inputs) are modeled with a syntactic interface (inputs and outputs). Note: Functions do not need to be allocated to actors yet 

##### FTM C: For each function in the operational context, the behavior is modeled.
Sister capabilities are LTM C and TTM C.

### Logical Viewpoint

More on the Logical Viewpoint can be found [here](https://spesml.github.io/concepts/modeling_framework/logical_viewpoint.html).

#### Logical Component Modeling (LCM)

##### LCM A: For logical components, their interface is modeled with associated input and output signals.  
*Plugin usage*: More information can be found [here](https://spesml.github.io/plugin/logical_viewpoint.html#how-to-model).

![changeHere](/images/lcma-example.png){:class="img-responsive"}

##### LCM B: The behavior of the logical components is modeled.  

##### LCM C: Logical components and requirements they satisfy are related by a satisfy or require relation.

![changeHere](/images/lcmc-example.png){:class="img-responsive"}

#### Logical Architecture Modeling (LAM)

##### LAM A: The logical components and their dependencies are modeled.
![changeHere](/images/lama-example.png){:class="img-responsive"}

##### LAM B: Logical components are related to white-box functions that they implement by a realize relation.
*Plugin usage*: More information can be found [here](https://spesml.github.io/plugin/logical_viewpoint.html#spesml-logicaltofunctional-matrix).

![changeHere](/images/lamb-example.png){:class="img-responsive"}

More on tracing between logical components and functions can be found [here](https://spesml.github.io/concepts/modeling_framework/functional_viewpoint.html#tracing-between-functions-and-elements-of-the-logical-viewpoint).

#### Logical conText Modeling (LTM)

##### LTM A: The system under development (i.e., the top-level logical component) is modeled by a composition of all logical components.


##### LTM B: Actors of the operational context (e.g., external systems or users) are modeled with a syntactic interface (inputs and outputs).  
The image below depicts the WindoLifterSytem in the Logical Context view.
![changeHere](/images/ltmb-example.png){:class="img-responsive"}

##### LTM C: For each actor in the operational context, the behavior is modeled.

![changeHere](/images/ltmc-example.png){:class="img-responsive"}

The actor also includes external logical components (e.g., BrightnessSensor in the image above)

#### Logical Physical Modeling (LPM)
tbd...
##### LPM A: Physical Quantities are assigned to external logical components. 

##### LPM B:...

### Technical Viewpoint
#### Technical Component Modeling (TCM)                                    
##### TCM A: For technical components, their interface is modeled with associated input and output  signals.
##### TCM B: The behavior of the technical components is modeled.                                                                                                                          
##### TCM C: technical components and requirements they satisfy are related by a satisfy or require  relation.                                                                                                     
#### Technical Architecture Modeling (TAM)                                 
##### The technical components and their dependencies are modeled.
##### Technical components are related to logical components that they implement by a realize relation.           
#### Technical conText Modelling (TTM)                                
##### TTM A: The   system under development (i.e., the top-level technical component) is modeled by a composition of all technical components.

##### TTM B: Actors  of the operational context (e.g., external systems or users) are modeled with   a syntactic interface (inputs and outputs). 

##### TTM C: For  each actor in the operational context, the behavior is modeled.
