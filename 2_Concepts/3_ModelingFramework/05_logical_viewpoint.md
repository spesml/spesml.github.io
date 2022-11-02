---
layout: default
title: Logical Viewpoint
nav_order: 5
parent: SpesML Modeling Framework
grand_parent: SpesML Concepts
permalink: /concepts/modeling_framework/logical_viewpoint.html
---

# Logical Viewpoint

This document describes the basic concepts that will be covered in the _Logical Viewpoint_ and how they are mapped to `SysML elements`.

*Content:*
- [Logical Viewpoint](#logical-viewpoint)
  - [Logical Viewpoint: Overview](#logical-viewpoint-overview)
  - [Logical Components and their relations to other model elements of the Logical Viewpoint](#logical-components-and-their-relations-to-other-model-elements-of-the-logical-viewpoint)
  - [Logical Context: The System and its Context in the Logical Viewpoint](#logical-context-the-system-and-its-context-in-the-logical-viewpoint)
  - [Modeling Interfaces and behavior of Logical Components](#Modeling-Interfaces-and-behavior-of-Logical-Components)
  - [Decomposition of Logical Components](#Decomposition-of-Logical-Components)
  - [Tracing Relations between Logical Components and other Elements](#Tracing-Relations-between-Logical-Components-and-other-Elements)
  - [Modelling the Transition to the Technical Viewpoint](#Modelling-the-Transition-to-the-Technical-Viewpoint)

# Logical Viewpoint: Overview
The Logical Viewpoint (LVP) describes how the system under development (SuD) can be structured in order to achieve the behavior which is specified in the [Functional Viewpoint](https://spesml.github.io/concepts/modeling_framework/functional_viewpoint.html). 
To do so, the LVP defines models to describe the [logical system context](https://spesml.github.io/concepts/modeling_framework/logical_viewpoint.html#Logical-Context-The-System-and-its-Context-in-the-Logical-Viewpoint), the [decomposition](https://spesml.github.io/concepts/modeling_framework/logical_viewpoint.html#Decomposition-of-Logical-Components) of the SuD in logical components and sub-components and their respective interface behavior. 
In the following we describe the basic concepts and models for the LVP.

# Logical Components and their relations to other model elements of the Logical Viewpoint
The central modelling concept of the Logical Viewpoint are the so-called Logical Components. 
They strictly follow the [Universal Interface Model](https://spesml.github.io/concepts/modeling_framework/uim.html) including syntactic and semantic interface, causality and compositionality. 
Hereby, the components of the LVP are intended to be modelled independently of the future technical realization.
In the SpesML tooling a Logical Component is represented as a dedicated `SysML Block` as can be seen in the example in Figure 1:

![Logical Component](/images/logical_viewpoint/logical-component.png){:width="400" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 1: </b><em>A SysML Block representing a Logical Component</em></div>

# Logical Context: The System and its Context in the Logical Viewpoint
The _logical context_ specifies the interface of the SuD to the operational context on a logical (i.e. technology independent) level. 
Hereby, it refines the context model of the [functional context](https://spesml.github.io/concepts/modeling_framework/functional_viewpoint.html#functional-context-the-system-and-its-context-in-the-functional-viewpoint) in the FVP. 
In SysML, the logical context is modelled using a specific `SysML Internal Block Diagram (IBD)` that can be created in the respective package as can be seen in Figure 2:

![Logical Context in the Logical Viewpoint](/images/logical_viewpoint/logical-context_creation.png){:width="250" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 2: </b><em>The Logical Context diagram can be modeled in the dedicated package of the Logical Viewpoint.</em></div>

As for all other viewpoints, the logical context defines the scope of what is _inside_ the system boundaries and what is _outside_.  
To classify logical components as being outside the system boundary (i.e. in the actual context), there is a dedicated property _external_ to specify this. 
The Logical Components for the SuD and the context elements are connected in the SpesML SysML-profile and plugin in the logical context diagram as can be seen in Figure 3:

![Logical Context](/images/logical_viewpoint/logical-context.png){:width="800" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 3: </b><em>An example for a logical system context.</em></div>

More information on modelling the system context can be found [here](https://spesml.github.io/concepts/modeling_framework/context.html)

# Modeling Interfaces and behavior of Logical Components
As already mentioned, also the Logical Viewpoint is based on the concepts of the [Universal Interface Model](https://spesml.github.io/concepts/modeling_framework/uim.html) and it’s mapping to SysML. 
This means, that interfaces of logical components consist of a _syntactical_ and a _semantical_ interface.

The _syntactical_ interfaces consist of _Logical Interfaces_ which are represented by `SysML Proxy Ports`. 
Hereby, every Logical Interface needs to be assigned a _Logical Interface Type_ which is defined as a set of `SysML Channels`. 
An exemplary definition of a Logical Interface and Interface Types can be seen in Figures 4 and 5:


![Logical Interface Type](/images/logical_viewpoint/logical-intreface-type.png){:width="300" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 4: </b><em>Exemplary definition of a SpesML Logical Interface Type</em></div>

![Logical Interface](/images/logical_viewpoint/logical-intreface.png){:width="400" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 5: </b><em>Exemplary definition of a SpesML Logical Interface</em></div>

The _semantical_ interface of Logical Components is modelled by means of State Machines that operate base on the component’s input streams and produce the components output streams.
More information on SpesML state machines can be found, [here](https://spesml.github.io/concepts/modeling_framework/state_machines.html). Figure 6 gives an example in the SpesML tool. 
Hereby, the guards and actions can also use executable functions, as ca be seen [here](https://spesml.github.io/concepts/modeling_framework/executable_functions.html).

![State Machine](/images/logical_viewpoint/state-machine.png){:width="800" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 6: </b><em>An example for a SpesML state machine.</em></div>

# Decomposition of Logical Components
To structure the logical system architecture and to reduce complexity, all Logical Components can be decomposed into sub-components. 
Conceptually, this means that a set of sub-components is modeled and connected in such a way, that their composed behavior results in the behavior of the decomposed component. 
In the SpesML SysML-profile and plugin, decomposition is modeled by means of dedicated `SysML Internal Block Diagrams (IBDs)` in which `SysML Parts` are instantiated and connected for the subcomponents as can be seen in Figure 7:

![Composition](/images/logical_viewpoint/decomposition.png){:width="800" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 7: </b><em>Decomposition of a Logical Component into sub-components.</em></div>

This also applies for the syntactic and semantic interface of components and sub-components: 
Here, all inputs of the component need to be connected to an input of a sub-component and all outputs of a component need to be connected to an output of a subcomponent. 
More detailed information can be found in the documentation of the [Universal Interface Model](https://spesml.github.io/concepts/modeling_framework/uim.html).

# Tracing Relations between Logical Components and other Elements
The logical components are traced to the whitebox functions which they _realize_ with a respective tracing matrix. 
Hereby, we recommend to trace n Whitebox-Functions of the FVP to exactly _one_ Logical Component (n:1 tracing).
In the SpesML Profile and Plugin, we use `SysML Matrixes` for this tracing as can be seen in Figure 8:

![Tracing from FVP to LVP](/images/logical_viewpoint/tracing_fvp-lvp.png){:width="600" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 8: </b><em>Tracing from the Functional to the Logical Viewpoint.</em></div>

The technical realization of Logical Components will be described by in the [Technical Viewpoint](https://spesml.github.io/concepts/modeling_framework/technical_viewpoint.html). 
Hereby, we recommend to trace every Logical Components to exactly one Technical Component (1:1 tracing).
More detailed (general) information on tracing in SpesML can be found [here](https://spesml.github.io/concepts/modeling_framework/tracing.html)

# Modelling the Transition to the Technical Viewpoint
As is introduced [here](https://spesml.github.io/concepts/modeling_framework/tracing.html#definition-of-software-components-in-the-logical-architecture) in more detail, the Logical Viewpoint can also explicitly model certain aspects of the transition from the logical to the technical viewpoint. 
In particular the identification of future software sub-systems can be modelled here, by decomposing Logical Components into different sub-components for software and non-software aspects. 
These sub-components can then be regrouped in separate Logical Components that can then be technically modelled accordingly in the [Technical Viewpoint](https://spesml.github.io/concepts/modeling_framework/technical_viewpoint.html).
`TODO: Add screenshot of re-structuring implementation in SysML.`
