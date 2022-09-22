---
layout: default
title: Interface Refinement in SPES and SpesML
nav_order: 6
parent: SPES Methodology
grand_parent: SpesML Concepts
permalink: /concepts/methodology/interface_refinement.html
---

# Interface Refinement in SPES and SpesML
We define a concept model in [Figure 1](#figure1) to describe a system under consideration: This concept model describes what constitutes a system and its properties as the result of a conceptualization. 

*A concept model is a model informally visualizing the concepts and their connections described in this text.*

From a very abstract point of view the system we are interested in is embedded in its environment and communicates with other systems in the environment. We call this the system’s *operational context*. The system under consideration interacts with its operational context that influences or is influenced by the system at runtime. The system’s behavior, essential system properties, and other aspects that have to be considered during development are represented by this interaction can be observed by an external observer at the system interface, separating the system from its operational context. This constitutes the *black box* view on the system on given level of abstraction.

<a name="figure1"></a>
![System modeling blueprint](/images/interface_refinement/context_and_interfaces.png){:class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 1: </b><em>System modeling blueprint (visualized as concept model).</em>
</div>

The *glass box* view reveals the *inner structure* (architecture) of the system consisting of connected and interacting elements (components and sub-systems), which can be considered as systems by themselves, with contexts and observable behavior and properties at their interface. This way the abstract model is applied recursively.

Our approach provides different views on the system’s architecture to specify a system:
- Functional View 
- Logical Component View (providing the internal system structure while abstracting from implementation details)
- Technical Component View (modeling implementation details)

During the course of the system development more and more detail is added to the specifications. This concepts is defined as one of the following types of refinement:
- *Glass box refinement* is the transition from a black box view to the glass box view. Here, we decompose the system (or a system element) into a distributed network of elements (e.g. functions, components), which again can have an internal structure (e.g. sub-functions, sub-components). The refinement of system sub-models leads to a refinement of the overall system (*modularity*). Transitioning from a black box view (e.g. a function or a component) to some form of implementation, e.g., a state machine, is another common instance of glass box refinement.
- *Property refinement* is the transition between model elements (e.g., components, functions) or model specifications (e.g. requirements), where the refined models have all the properties of the initial models and some more (e.g., when adding requirements). This process restricts the set of specified models. This also allows to further restrict the possible behavior of the system described by the specifications.
- *Interaction refinement* is the transition from one model element (for example, a function describing a mathematical multiplication with two inputs and one output) to another model element of the same model element type (e.g., the same function, but the mulitplication happens through only one input, where both values are communicated sequentially) or even a model element of another model element type (a logical component with the aforementioned behavior). This transition may change the granularity of the interaction, the channels of the interface, and their message types. However, the refinement relationship implies that one can specify the relationship of the inputs and outputs between the refining and the refined element. We refer to the syntactic interface of the system in a system model (an architecture) as the *level of abstraction* at which the model is considered. The system can be described independently at different abstraction levels for each system model. Interaction refinement changes the syntactic interface of the system and thus the abstraction level on which the system is modeled in the current architecture view or maps the system interface of different architecture views to each other.

Relations between the models at the same or different grades of refinement and levels of abstraction yield consistency of the system specification. The system specification is documented by a set of artefacts which must be validated and verified to guarantee consistency. Hereby the grade of formalization determines automatic validation and verification options.

# How do you handle refinement in SpesML?
Refinement in SpesML is implicitly modelled in the following ways:
*Glass box refinement* is modelled as part of the decomposition as described in the section on [Layers of Granularity](https://spesml.github.io/concepts/methodology/subsystems_and_granularity.html).
*Property refinement*  in SpesML is part of the continuous update of the SpesML interfaces as well as the installed versioning system, such as Teamwork Cloud. Finally, *interaction refinement*, is not explicitly managed due to the principle of simplicity in the tracing concept. It can be, to some extent reconstructed from the model: One option is to reconstruct the refinement over time through manual analysis. One could also imagine an automatic analysis that could help for this activity, e.g. based on existing traces. Since this was not part of the initial project we leave such a reconstruction of the refinement to future work.

Refinement in SpesML is explicitly modelled in both horizontal (between viewpoints) and vertical direction, as described in the section on [Tracing](https://spesml.github.io/concepts/modeling_framework/tracing.html).
