---
layout: default
title: Technical Viewpoint
nav_order: 6
parent: SpesML Modeling Framework
grand_parent: SpesML Concepts
permalink: /concepts/modeling_framework/technical_viewpoint.html
---
# Technical Viewpoint

*Content:*
- [Technical Viewpoint](#technical-viewpoint)
  - [General Concept of the Technical Viewpoint](#general-concept-of-the-technical-viewpoint)
  - [Technical Viewpoint Models on the System Layer](#technical-viewpoint-models-on-the-system-layer)
    - [Elements and Structure of the Technical Viewpoint](#elements-and-structure-of-the-technical-viewpoint)
    - [Assumptions for the Technical Viewpoint and its Tracing Relations](#assumptions-for-the-technical-viewpoint-and-its-tracing-relations)
    - [Redundancy in the Technical Viewpoint](#redundancy-in-the-technical-viewpoint)
  - [Technical Viewpoint Models of the Software Subsystem](#technical-viewpoint-models-of-the-software-subsystem)
    - [Run-time Software Architecture Models](#run-time-software-architecture-models)
    - [Design-time Software Architecture Models](#design-time-software-architecture-models)
    - [Execution Platform Models](#execution-platform-models)
    - [Allocation Models](#allocation-models)


## General Concept of the Technical Viewpoint

The technical viewpoint is mostly concerned with the question of how to get from the platform independent models of the logical viewpoint (logical components) to platform-specific models (technical components). In the following, we describe all models of the technical viewpoint including the software subsystem. 

In general, we see generic technical models on the first granularity layer (the overall system), which can then be refined to more specialized models on the next granularity layer(s). An example for such a refinement/specialization is the software subsystem. This is why we divide this chapter of the technical viewpoint into two parts. First, the [more generic models of the technical viewpoint on system layer](#technical-viewpoint-models-on-the-system-layer) and afterwards, the [models of the software subsystem on lower granularity layers](#technical-viewpoint-models-of-the-software-subsystem). However, we come to the conclusion that in some cases, it makes more sense to directly model the software subsystem on the first granularity layer and it is also the case that all generic models, which we will mention for the first granularity layer, are often needed on all lower layers and thus can be built there as well. Therefore, the match of a technical model to a specific granularity layer as indicated by the following section headers is not binding but rather a design recommendation. In the end, all technical models can exist on all granularity layers.  

The presented approach targets various scenarios that may emerge in systems engineering.

1. Integration of technical components from various engineering disciplines. For instance, integration of a mechatronic component (incl. mechanics, electronics, and software). Such a scenario can be supported by specific technical components and their dedicated interfaces to other technical components.
2. Engineering a new system architecture in terms of hardware topology. Engineering a more centralized architecture requires an overview of computation resources and communication resources that are intended for the new system.

We also envision combinations of these. The proposed approach enables that.

The following sections will, as already mentioned, cover first the more general technical elements (mainly on the system granularity layer) and then the software subsystem in detail. 
To understand the relations and possibilities of the technical viewpoint, the following [Figure 1](#figureOverview) gives an overview. In addition, we provide in [Figure 2](#figureExample) an abstract example of how a technical architecture can look like across granularity layers.
 
<a name="figureOverview"></a>
![Overview](/images/technical_viewpoint/TVP_Element_Overview.png){:class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 1: </b><em>Overview over all elements of the Technical Viewpoint.</em></div>



## Technical Viewpoint Models on the System Layer

### Elements and Structure of the Technical Viewpoint

**Components.** On the system granularity layer, the technical architecture of the system is described using components. These components represent the system either in a generic way or more specific using models of the respective technical engineering disciplines. The generic component is called _Technical Component_ and can be used for everything in any discipline. If the content of a component can be assigned completely to one specific discipline, a more specific component type can be chosen to represent this. Referring to this, available disciplines are mechanical engineering with the _Mechanical Component_, electrical engineering with the _Electronic Component_, the combination of them with the _Mechatronic Component_ and the pure software engineering with the _Software Component_. The Software Component is the container for the software subsystem, which has more internal component types. More on that in the [related section](#technical-viewpoint-models-of-the-software-subsystem).

**Interfaces.** All these components can interact with other components via (syntactic) interfaces that are modeled from an implementation point of view. Only one interface type exists in the technical viewpoint, which is the generic interface called _Technical Interface_ that connects every component type with every other one (Technical, Mechanical, Electronic, Mechatronic, and Software Component).

**Hierarchy.** Components may be decomposed into further subcomponents within the same granularity layer, e.g., the system layer. The purpose of such hierarchical decompositions is usually to gain a better overview, especially for large, complex systems. It is possible to decompose a Technical Component into any combination of any other subcomponents. The other more specific components can only be decomposed in subcomponents of their own type, i.e., a Mechanical Component can only contain more Mechanical Components, and an Electronic Component only more Electronic Components. Mechatronic Components can also contain more Mechatronic Components, but in addition it is possible to specialize the combination even more with Mechanical and/or Electronic Components. An exception is the Software Component. The content of such a software subsystem is described in its own models (see [section](#technical-viewpoint-models-of-the-software-subsystem)) including Task Architectures and Execution Platforms. Note that it is not possible to decompose a Software Component into other component types like Technical, Mechanical, Electronic, and Mechatronic Components. In any case, we recommend to leave the Software Component empty on its granularity layer and refine it on the next granularity layer. 

**Technical Context.** Similar to the functional and logical viewpoint, a context can be modeled within the technical viewpoint as well. With such a _Technical Context_ it is possible to place the current system under development (SuD) in relation to connected (external) systems and _Technical Actors_. The Technical Context contains the current SuD and exactly all technical systems and actors that are connected with the SuD via at least one direct Technical Interface. This way it is possible to display where the system inputs are coming from and where the system outputs are going to without explicitly modeling all the external systems.

**Design Recommendations.** As the purpose and abstraction of specific engineering disciplines are highly heterogeneous, such models differ accordingly. Whether a component is further refined as an independent subsystem on the next granularity layer depends on the specific development project. We consider the possibility of having multiple components of a certain engineering discipline. As already mentioned, we recommend refining Software Components, which represent software subsystems, on the next granularity layer by models representing the software architecture, hardware architecture and their corresponding allocation.


### Assumptions for the Technical Viewpoint and its Tracing Relations
The relationship between logical and technical architectural components is n:m in general if the technical architecture is designed without the logical architecture in mind. 

Our overall approach is to provide meaningful tracing relationships between the model elements of the views. Therefore, we suggest developing an initial architecture in the technical view that has the same component structure as the logical architecture, which yields a 1:1 tracing relation between logical and technical components on this layer of abstraction. 

Even when using a 1:1 tracing relation between logical and technical components, it is important to notice that in advance we recommend structuring the logical viewpoint in terms of grouping logical subcomponents that are realized in the software subsystem. This enables for a meaningful 1:1 trace relation. Note that even if we propose a 1:1 relationship between logical and technical components, the interface refinement has a large impact on the details of the technical architecture.
 
Other relationships are possible, but we strongly encourage to manifest engineering decision in terms of a proper logical systems architecture that enables for a 1:1 relationship.

### Redundancy in the Technical Viewpoint
Applying redundancy (patterns) is necessary in systems engineering for many reasons. Redundancy realized in concrete technical components, however, can be already modeled in the logical viewpoint, yielding a 1:1 mapping to technical components. Furthermore, it is also possible that logical components occur multiple times in the technical architecture, meaning to model redundancy in the technical view for the first time. These logical components manifest themselves in a 1:n relation in technical components.

***

<a name="figureExample"></a>
![Example](/images/technical_viewpoint/technical_overview.png){:class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 2: </b><em>An example of how the technical elements can be composed inclusive different granularity layers.</em></div>

***

## Technical Viewpoint Models of the Software Subsystem
When a software subsystem is refined on the next granularity layer, a set of models can be used to describe the software subsystem. This section provides an overview of possible models and their relations. 
As part of the software subsystem, the execution platform represents everything that is needed to execute the software of the system. It describes a hardware topology of digital subsystems in terms of execution as well as communication resources. Another part of the software subsystem is the software architecture representing the pure software part of the system. The software architecture has both dynamic parts, represented by dedicated run-time software models like task architectures, as well as static parts, namely design-time software models, like middlewares and operating systems. Relations between software architecture and execution platform describe potential allocations of software artifacts to hardware computing (execution) resources.

In SpesML, a Software Component, which represents a software subsystem, can contain _Task Architectures_ (for the run-time software), _>TBD<_ (for the design-time software), _Execution Platforms_ (for the hardware/execution topology) and _Allocations_ between them. 
In the following sections, we describe these models in more detail.


### Run-time Software Architecture Models

Run-time software models represent the dynamic part of the software architecture. For instance, run-time software can be described by a set of (executable) tasks (e.g., an AutoSAR runnable), which processes information from its inputs to its outputs, and a bus message catalogue, which contains all messages representing the technical dataflow between these tasks. In SpesML, we use a _Task Architecture_, which is part of a Software Component representing the software subsystem, to model the structure of such _Tasks_, which can communicate via _Messages_ containing _Signals_:

- _Task_: Tasks are entities of the technical (software) architecture to which components of the logical architecture are mapped during deployment. We are recommending a 1:1 mapping between logical components:tasks, which is why you need to refine the logical components as much as needed to get to this 1:1 mapping. A task defines how to process (possible) incoming information and create (possible) outgoing information. The interface of a task is modeled with ports for input and output. Messages containing information are received and/or sent by these ports. These software tasks will be deployed onto the execution units of an execution platform, which we explain in a separate [section](#execution-platform-models).

- _Message_: Task ports can be connected to model an information flow between tasks via messages. An input port can only be connected to exactly one output port of the same message type. An output port can be connected to multiple input ports of the same message type. Messages contain information that is sent between tasks to process it there. The actual information is transported via signals and since a message can have multiple signals as payload, a message can just be seen as container for signals. In SpesML, we are using _Technical Interfaces_ to define these messages. These Technical Interfaces are also used as connection possibility between all other technical elements as described in [this previous section](#elements-and-structure-of-the-technical-viewpoint).

- _Signal_: A signal represents information transported between tasks and is always part of a message. Multiple signals can be sent together from task/port to task/port via a message. In SpesML, each signal has its own _Channel_ (per message/interface).


| Concept | SysML Construct | Stereotype / Name in SpesML plugin (MagicDraw) | Shown Name (GUI) in SpesML plugin (MagicDraw)|
| ------ | ------ | ------ | ------ |
| Task | Block | SpesML Task | Task |
| Task Message/Interface | Proxy Port | SpesML Technical Interface | Technical Interface |
| Signal (Channel) | Flow Property | (SpesML Channel)<sup>1</sup> | (Channel)<sup>1</sup> |

<sup>1</sup> Inherited from Universal Interface Model


### Design-time Software Architecture Models

Conceptually, SpesML also supports for design-time software models as being part of the software architecture. These models include models representing specific middleware aspects and operating system models and thus are representing the static parts of the software architecture. For instance, design-time software models comprise of models representing certain middleware aspects, including, for instance, virtualization aspects and potential OS-related models. Software partitions are one example of artifacts that can be described here. 

These models are usually modeled as black-box models that describe the syntax of such architectures. 

As for now, this concept is not implemented in the SpesML plugin.


### Execution Platform Models

The _Execution Platform_ enables the description of a hardware topology of digital subsystems. We call it execution platform, because it mostly represents execution units (see below) and we want to clearly distinguish this architecture/platform from a more general hardware architecture that could imply containing, e.g., mechanical components.
Since the digital subsystem exclusively consists of tasks, which are components realized in software, the execution platform needs to specify the hardware resources which are necessary for the execution of these software parts.
The most prominent hardware components hereby are execution units like Electrical Control Units (ECUs) that can execute software tasks.
However, also technical communication units such as bus systems are highly relevant for the software execution in distributed technical architectures. Therefore, execution platforms can contain _Execution_ as well _Communication Components_ to represent these two entity types.

For actually gaining an added value for systems engineering, an important aspect is to capture more than the structure of the hardware topology alone. The specification of relevant attributes of all technical entities is the key to enable verification and analysis of the technical architecture.
For execution components, this might entail to capture the available memory and computational power.
For communication components, the usual technical aspects are bandwidth, real time capabilities and similar quality of service attributes.
All of these entities and attributes are finally relevant for the allocation models.

The connection between execution units, communication units and external entities outside the execution platform like actuators and sensors can be modeled with the generic _Technical Interface_, which we already introduced earlier for all technical components on all granularity layers including the system layer.

| Concept | SysML Element | Stereotype / Name in SpesML plugin (MagicDraw) | Shown Name (GUI) in SpesML plugin (MagicDraw)|
| ------ | ------ | ------ | ------ |
| Platform/Container for execution and communication units | Part | SpesML Execution Platform | Execution Platform |
| Execution Unit (e.g., ECU) | Part | SpesML Execution Component | Execution Component |
| Communication Unit (e.g., bus) | Part | SpesML Communication Component | Communication Component |
| Communication/Bus Message/Interface | Proxy Port | SpesML Technical Interface | Technical Interface |
| Communication/Bus Connection | Connector | (no specific SpesML Stereotype) | Connector |


### Allocation Models
 
A software allocation model realizes a mapping of tasks from the task architecture to execution components of the execution platform. Thereby, it is an integrated platform-specific solution model for the software subsystem. 
Such an allocation is necessary to identify the respective execution (and communication) resources for given software architecture artifacts, e.g., an allocation of a set of software tasks to a certain ECU. This allocation enables further system engineering activities, e.g., scheduling analysis tasks.

All allocations of tasks to execution components in the software deployment model must be of cardinality n:1. This means, that each task can only be deployed to exactly one ECU, while each ECU can execute several (n) tasks.

When integrating design-time software models (e.g., software partitions) it is important to note that this consequently has an effect on the allocation models as well, as models from the run-time software (e.g., tasks) can conceptually be allocated to models of the design-time software (e.g., software partitions) which in turn will be allocated to execution platform models. 

In SpesML, we are using the SysML Allocation Matrix as basis for such an allocation model. Since SysML has the concept of types/blocks and instances/parts, in SpesML the creation of Allocation Matrices is enabled for both ways: allocation of task types to execution component types and of task instances to execution component instances. Furthermore, we are supporting the allocation of task ports to execution component ports.

| Concept | SysML Element | Stereotype / Name in SpesML plugin (MagicDraw) | Shown Name (GUI) in SpesML plugin (MagicDraw)|
| ------ | ------ | ------ | ------ |
| Task Instance to Execution Component Instance Mapping | Allocation Matrix | SpesML TaskInstanceToExecution Allocation Matrix | TaskInstanceToExecution Allocation Matrix |
| Task Type to Execution Component Type Mapping | Allocation Matrix | SpesML TaskTypeToExecution Allocation Matrix | TaskTypeToExecution Allocation Matrix |
| Task Port to Execution Component Port Mapping | Allocation Matrix | SpesML PortToExecution Allocation Matrix | PortToExecution Allocation Matrix |
| Task to Partition Component Mapping | Allocation Matrix | SpesML TaskPartition Allocation | TaskPartition Allocation |
| Partition to Execution Component Mapping | Allocation Matrix | SpesML Partition Allocation | Partition Allocation |



