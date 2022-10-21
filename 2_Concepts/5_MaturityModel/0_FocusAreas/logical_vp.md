---
layout: default
title: Logical Viewpoint
nav_order: 3
parent: Capability description
grand_parent: SpesML Maturity Model
permalink: /concepts/maturity_model/focus_areas/logical_vp.html
---

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
In the SpesML methdology, physical units are described in the Logical Viewpoint. This focus area describes the possible levels of maturity a development team can achieve when modelign physical information
##### LPM A: Physical units are defined as using numeric values. 
##### LPM B: Physical Quantities are assigned to external logical components. 
##### LPM C: The precison of these units is...
##### Physical quantities are modeled using the specific elements of the plugin.
