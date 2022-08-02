---
layout: default
title: SPES System Model
nav_order: 3
parent: SPES Methodology
grand_parent: SpesML Concepts
permalink: /concepts/methodology/system_model.html/
---
# SPES System Model

The SPES approach provides a general schematic framework for
model-based development, which based on a scientifically sound modeling theory.

The pattern is always the same: The more strongly the different
components of modeling theory, viewpoints, and the connection to the
physical system are implemented, and the more densely and coherently
they describe the connections, the more useful is the modeling theory
(provided that it can be applied in practice) for its methodical
implementation and also as a basis for tool support.

The scientific basis for our approach to system development is a
modeling theory that defines the basic models for systems, regardless
of where and how these individual models are used in development to
describe certain aspects ("views") of systems. 

The SPES approach provides abstract
formal models and rules that describe their relationships. These are
usually formed by mathematical structures consisting of sets, relations,
and functions that can represent certain relationships, perspectives, and
properties of systems.

We start to briefly introduce the basic models which make up
the SPES methodology, how they are interrelated and how they are
refined and realized.

We start to define a *concept model* (see [Fig. 1](#figureBlueprint)) to describe a system under
consideration: This concept model describes what constitutes a system
and its properties as the result of a conceptualization.

From a very abstract point of view, the system we are interested in is
embedded in its environment and communicates with other systems in the
environment. We call this the system’s *operational context*. The system
under consideration interacts with its operational context that
influences or is influenced by the system at runtime. The system’s
behavior, essential system properties, and other aspects that have to be
considered during development are represented by this interaction can be
observed by an external observer at the system interface, separating the
system from its operational context. This seprartion constitutes the *black box*
view of the system at the given level of abstraction.

<a name="figureBlueprint"></a>
![Blueprint](/images/spesml_system_model/image1.png){:class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 1: </b><em>System modeling blueprint (visualized as concept model)</em></div>

The *glass box* view reveals the system's *inner structure* (architecture)
consisting of connected and interacting elements (components and
sub-systems), which can be considered systems by themselves, with
contexts and observable behavior and properties at their interface. This
way, the abstract model is applied recursively.

To specify a system, our approach provides different views on the
system’s architecture:

-   Functional View (describing the systems's functions as seen from an outside observer)

-   Logical Component View (providing the internal system structure
    while abstracting from implementation details)

-   Technical Component View (modeling implementation details)

During the course of a system's development, more and more detail is
added to the specifications. Three refinementconcepts model this process:

-   *Glass box refinement* defines the transition from a black
    box view to the glass box view by decomposing the system (or a system
    element) into a distributed network of elements (e.g., functions,
    components), which again can have an internal structure
    (system sub-models). The refinement of system sub-models leads to a
    refinement of the overall system (*modularity*).

-   *Property refinement* models the transition between models or model
    specifications. Hereby, the refined models have all the properties of
    the initial models and some more. This process restricts the set of
    specified models. For example, this allows adding requirements to a 
	specification or further restricting the possible behavior of the 
	system as described by the specifications

-   *Interaction refinement* as a transition from one model or one model
    specification in a model class (for example, interface
    specifications) to another model or another model specification of
    another model class changes the granularity of the interaction, the
    channels of the interface, and their message types. The syntactic interface
    of the system in a system model (an
    architecture) defines the *level of abstraction* at which the model is
    considered. The system can be described independently at different
    abstraction levels for each system model. Interaction refinement
    changes the syntactic interface of the system and thus the
    abstraction level on which the system is modeled in the current
    architecture view or maps the system interface of different
    architecture views to each other.

Relations between the models yield consistency in the system
specification. This holds between models at the same grade of
refinement and levels of abstraction, as well as for models that
respresent different levels of abstractions. The system specification 
is documented by a set ofartifacts, which must be validated and 
verified to guarantee consistency. Hereby the grade of formalization 
determines automatic validation and verification options.
