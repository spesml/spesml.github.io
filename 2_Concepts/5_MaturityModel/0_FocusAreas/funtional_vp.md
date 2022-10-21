---
layout: default
title: Functional Viewpoint
nav_order: 2
parent: Capability description
grand_parent: SpesML Maturity Model
permalink: /concepts/maturity_model/focus_areas/functional_vp.html
---

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
