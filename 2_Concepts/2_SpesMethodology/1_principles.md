---
layout: default
title: SPES Principles
nav_order: 1
parent: SPES Methodology
grand_parent: SpesML Concepts
permalink: /concepts/methodology/principles.html
---
# SPES Principles

The SPES framework introduces a set of fundamental modeling principles.
These principles aim at establishing specific ways of thinking to be
applied when performing the modeling activities suggested by the
engineering process for software-intensive embedded systems in order to
meet the requirements from the application domains and the
characteristics of such systems.

-   *Decomposition* plays an important role as a lever to master complexity in nearly all engineering activities. The scientific foundation of the SPES methodology ensures that composition of the individual parts yield the properties of the SuD again. The principle of decomposition is applied on two different levels: Firstly, architecture elements will be recursively decomposed into more fine grained architectures along the SPES viewpoints. And secondly, the scope of the SuD may be changed using the concept of granularity layers.

-   The concept of *granularity layers*, allows to recursively apply the SPES concepts and viewpoints to selected architecture elements (*subsystems*) which leads to a nesting of architecture descriptions. Note: As only selected elements of an architecture may become subsystems, the set of all subsystems will not form a decomposition of the SuD, in general. It is a means to decouple the engineering processes and divide them into a number of individual fine-grained engineering processes, complemented by certain activities to support the integration of the various engineering artifacts. This enables, for example, component reuse and the integration of a supplier relation into the engineering process.

-   *Refinement* is a powerful concept to successively add more details to the models and to define relations between the models within a view, across architectures in different views, and models on different layers of granularity.

-   *Layers of Abstraction*: Models are always modelled on certain levels of abstraction. During the course of the development more detail is added to the models and the levels of abstraction decreases. The concept of interface refinement relates different layers of abstraction to each other.

The SPES framework defines a methodological toolkit for MBSE that allows
efficient model-based development of cyber-physical systems (CPS).
Remarkably, the toolkit is based on a solid scientific foundation with a
special focus on consistency and semantic coherence. The SPES
methodology is built on three principles of outstanding importance:

-   Consistent consideration of interfaces along the design process

-   Decomposition of the interface behavior and

-   The description of systems via subsystems and components at
    different layers of granularity

In SPES, a *system model* is a conceptual ("generic") model of systems
and their properties. It describes what constitutes a system as the
result of a conceptualization. System models define the components of
systems, the structure, essential properties, and other aspects that
have to be considered during development. Among other things, system
models define what requirements refer to, i.e. they specify what the subject of discourse is. In
SPES, the comprehensive system model consists of:

-   An operational context that represents what is outside the system but
    influences or is influenced by the system at runtime

-   A syntactic interface that clearly separates the system from its
    operational context and describes the options of interaction between
    the system and its operational context (indicated by arrows at the
    interface)

-   A behavior of the system that can be observed at the interface
    described by a relation between the input and output streams

-   An inner structure of interrelated and communicating elements
    (architecture), which are themselves systems that may be described
    by state machines

![Overview over the system context](/images/principles/image1.png){:class="img-responsive"}

The system is embedded in its context and communicates with other
systems in the context. We call this the system’s *operational context*.
The system under consideration interacts with its operational context
which in turn influences or is influenced by the system at runtime. The system’s
behavior, essential system properties, and other aspects that have to be
considered during development are represented by this interaction as it
can be observed by an external observer at the system interface.
This separates the system from its operational context and constitutes the
*black box* view on the system on a given level of abstraction.

Relations between the models at the same or different grades of
refinement and levels of abstraction yield consistency of the system
specification. The system specification is documented by a set of
artifacts which must be validated and verified to guarantee said consistency.
Hereby the grade of formalization determines automatic validation and
verification options.

Central part of the universal system model is the universal interface
model (UIM), which is applied to essential elements of the SPES modeling
approach. The universal interface model is based on the  <span class="smallcaps">Focus</span>[^1] theory (see
<a href="https://spesml.github.io/concepts/modeling_framework/uim.html">
Universal Interface Model (UIM)</a>).
The system under development (SuD) is then modelled by a stepwise
decomposition into a network of communicating subsystems
(architectures), whose behavior can then again be described by the
universal interface model. The UIM guarantees the semantically correct
composition and decomposition of the model elements.

The degree of detail with which the syntactical interface is modelled
determines the *level of abstraction* of the models. Typically,
development starts on a higher level (i.e. with a coarser syntactic
interface) and is refined during later stages of development. As a
consequence, as the syntactic interface of the SuD to its context will
change in different views, the views will generally model the SuD on
different layers of abstraction. The SPES framework provides several
mechanisms to specify interface behavior, e.g. state machines or
interface assertions.

The SPES framework defines an MBSE artifact model which widely follows 
the same concepts as the architecture framework defined in the 
ISO 42010 standard. The aim of the concept of
viewpoints is to separate the various concerns of different stakeholders
and serves as a construct to manage the different artifacts during the
engineering process. Each viewpoint in the SPES framework predefines a
set of models and model elements for the SuD, which represent / specify
its properties relevant to model under the respective system view.
Correspondence rules are defined between the models of a single
viewpoint as well as across viewpoints. In particular, the SPES
framework predefines four basic viewpoints that structure the models and
allows for defining additional viewpoints if necessary ((see
<a href="https://spesml.github.io/concepts/methodology/views_and_viewpoints.html">
Views and Viewpoints</a>)). In addition to the viewpoints, the SPES modelling framework
includes the concept of a hierarchy of granularity layers:

The topmost layer of granularity represents the models of the SuD.
Components of the technical architecture can be selected and engineered
as stand-alone systems with an own context, which will be different from
the context of the SuD, using an independent development process. The
development process of such stand-alone systems may follow any
development methodology as long as the resulting system interface model
of this stand-alone system adheres to the Universal Interface Model
introduced above. In particular, the concept of granularity layers
allows iterative applications of the SPES modeling and refinement
concepts to work out viewpoints for selected architecture elements
leading to nestings of architecture descriptions and hierarchies of
granularity layers.

The selected technical components are treated as independent sub-systems
which may have a contextual relationship to each other. Their models
make up the next layer of granularity in the development. Note, as only 
some elements of the technical architecture may be
selected, the set of all such components will not necessarily
form a complete decomposition of the SuD.

Layers of granularity provide a means to decouple engineering processes
and divide them into a number of individual fine-grained engineering
processes, complemented by certain activities to support the integration
of the various engineering artifacts. This enables, for example,
component reuse and the implementation of a supplier relation into the
engineering process on the level of the technical architecture.

[^1]: For Details on the FOCUS theory see Broy, M.: “A Logical Basis for
    Component-Oriented Software and Systems Engineering”, Springer, 2010.
