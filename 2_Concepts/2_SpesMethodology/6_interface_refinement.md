---
layout: default
title: Interface Refinement in SPES and SpesML
nav_order: 6
parent: SPES Methodology
grand_parent: SpesML Concepts
permalink: /concepts/methodology/open_issues.html
---

# Interface Refinement in SPES and SpesML
We define a concept model in Fig. 1 to describe a system under consideration: This concept model describes what constitutes a system and its properties as the result of a conceptualization. 

*A concept model is a model informally visualizing the concepts and their connections described in this text.*

From a very abstract point of view the system we are interested in is embedded in its environment and communicates with other systems in the environment. We call this the system’s *operational context*. The system under consideration interacts with its operational context that influences or is influenced by the system at runtime. The system’s behavior, essential system properties, and other aspects that have to be considered during development are represented by this interaction can be observed by an external observer at the system interface, separating the system from its operational context. This constitutes the *black box* view on the system on given level of abstraction.


![](context_and_interfaces.png)
*Figure 1: System modeling blueprint (visualized as concept model)*

The *glass box* view reveals the *inner structure* (architecture) of the system consisting of connected and interacting elements (components and sub-systems), which can be considered as systems by themselves, with contexts and observable behavior and properties at their interface. This way the abstract model is applied recursively.

To specify a system our approach provides different views on the system’s architecture:
- Functional View 
- Logical Component View (providing the internal system structure while abstracting from implementation details)
- Technical Component View (modeling implementation details)

During the course of the system development more and more detail is added to the specifications. This process is modeled by the concept of refinements:
- *Glass box refinement* changes models the transition from a black box view to the glass box view decomposing the system (or a system element) into a distributed network of elements (e.g. functions, component architecture), which again can have an internal structure (system sub-models). The refinement of system sub-models leads to a refinement of the overall system (*modularity*).
- *Property refinement* models transition between models or model specifications, where the refined models have all the properties of the initial models and some more. This process restricts the set of specified models. For example, this allows to add additional requirements to a specification or further restrict possible behavior the system described by the specifications.
- *Interaction refinement* as a transition from one model or one model specification in a model class (for example, interface specifications) to another model or another model specification of another model class changes the granularity of the interaction, the channels of the interface, and their message types. We refer to the syntactic interface of the system in a system model (an architecture) as the *level of abstraction* at which the model is considered. The system can be described independently at different abstraction levels for each system model. Interaction refinement changes the syntactic interface of the system and thus the abstraction level on which the system is modeled in the current architecture view or maps the system interface of different architecture views to each other.

Relations between the models at the same or different grades of refinement and levels of abstraction yield consistency of the system specification. The system specification is documented by a set of artefacts which must be validated and verified to guarantee consistency. Hereby the grade of formalization determines automatic validation and verification options.

# How do you handle refinement in SpesML?
Refinement in SpesML is part of the continuous update of the SpesML interfaces as well as the installed versioning system, such as Teamwork Cloud. Due to the principle of simplicity in the tracing concept, refinement is not explicitly managed. One option is to reconstruct the refinement over time through manual analysis. One could also imagine an automatic analysis that could help for this activity. Since this was not part of the initial project we leave such a reconstruction of the refinement to future work.
