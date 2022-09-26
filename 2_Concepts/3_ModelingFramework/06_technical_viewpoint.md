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
  - [Technical Viewpoint Models of the Software Execution Subsystem](#technical-viewpoint-models-of-the-software-execution-subsystem)
    - [Run-time Software Models](#run-time-software-models)
    - [Design-time Software Models](#design-time-software-models)
    - [Execution Platform Models](#execution-platform-models)
    - [Allocation Models](#allocation-models)


## General Concept of the Technical Viewpoint

The technical viewpoint is mostly concerned with the question of how to get from the platform independent models of the logical viewpoint (logical components) to platform-specific models (technical components). In the following, we describe all models of the technical viewpoint including the software execution subsystem. 

In general, we see generic technical models on the first granularity layer (the overall system), which can then be refined to more specialized models on the next granularity layer(s). An example for such a refinement/specialization is the software execution subsystem. This is why we divide this chapter of the technical viewpoint into two parts. First, we present the [more generic models of the technical viewpoint on system layer](#technical-viewpoint-models-on-the-system-layer) and afterwards, the [models of the software execution subsystem on lower granularity layers](#technical-viewpoint-models-of-the-software-execution-subsystem).

The presented approach targets various scenarios that may emerge in systems engineering.

1. Integration of technical components from various engineering disciplines. For instance, integration of a mechatronic component (incl. mechanics, electronics, and software). Such a scenario can be supported by specific technical components and their dedicated interfaces to other technical components.
2. Engineering a new system architecture in terms of hardware topology. Engineering a more centralized architecture requires an overview of computation resources and communication resources that are intended for the new system.

We also envision combinations of these. The proposed approach enables that.

The following sections will, as already mentioned, cover first the more general technical elements (mainly on the system granularity layer) and then the software execution subsystem in detail. 
To understand the relations and possibilities of the technical viewpoint, the following [Figure 1](#figureOverview) gives an overview. In addition, we provide in [Figure 2](#figureExample) an abstract example of how a technical architecture can look like across granularity layers.
 
<a name="figureOverview"></a>
![Overview](/images/technical_viewpoint/TVP_Element_Overview.png){:class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 1: </b><em>Overview over all elements of the Technical Viewpoint.</em></div>



## Technical Viewpoint Models on the System Layer

### Elements and Structure of the Technical Viewpoint

**Components.** On the system granularity layer, the technical architecture of the system is described using components. These components represent the system either in a generic way or more specific using models of the respective technical engineering disciplines. The generic component is called _technical component_ and can be used for everything in any discipline. If the content of a component can be assigned completely to one specific discipline, a more specific component type can be chosen to represent this. Referring to this, available disciplines are mechanical engineering with the _mechanical component_, electrical engineering with the _electronic component_, the combination of them with the _mechatronic component_ and the pure software engineering with the _software execution subsystem_. The software execution subsystem is a container element for all the models/elements of the software execution subsystem, which is explained in the [related section](#technical-viewpoint-models-of-the-software-execution-subsystem).

**Interfaces.** All these components can interact with other components via (syntactic) interfaces that are modeled from an implementation point of view. Only one interface type exists in the technical viewpoint, which is the generic interface called _technical interface_ that connects every component type with every other one (technical, mechanical, electronic, mechatronic components, and the software execution subsystem).

**Hierarchy.** Components may be decomposed into further subcomponents within the same granularity layer, e.g., the system layer. The purpose of such hierarchical decompositions is usually to gain a better overview, especially for large, complex systems. It is possible to decompose a technical component into any combination of any other subcomponents. The other more specific components can only be decomposed in subcomponents of their own type, i.e., a mechanical component can only contain more mechanical components, and an electronic component only more electronic components. Mechatronic components can also contain more mechatronic components, but in addition it is possible to specialize the combination even more with mechanical and/or electronic components. An exception is the software execution subsystem. The content of such a software execution subsystem is described in its own models (see [section](#technical-viewpoint-models-of-the-software-execution-subsystem)) including task architectures and execution platforms. Note that it is not possible to decompose a software execution subsystem into other component types like technical, mechanical, electronic, and mechatronic components. In any case, we recommend to leave the software execution subsystem empty on its granularity layer and refine it on the next granularity layer. 

**Technical Context.** Similar to the functional and logical viewpoint, a context can be modeled within the technical viewpoint as well. With such a _technical context_ it is possible to place the current system under development (SuD) in relation to connected (external) systems and _technical actors_. The technical context contains the current SuD and exactly all technical systems and actors that are connected with the SuD via at least one direct technical interface. This way it is possible to display where the system inputs are coming from and where the system outputs are going to without explicitly modeling all the external systems.

**Design Recommendations.** As the purpose and abstraction of specific engineering disciplines are highly heterogeneous, such models differ accordingly. Whether a component is further refined as an independent subsystem on the next granularity layer depends on the specific development project. We consider the possibility of having multiple components of a certain engineering discipline. As already mentioned, we recommend refining software execution subsystems on the next granularity layer by models representing the software architecture, hardware architecture and their corresponding allocation.


### Assumptions for the Technical Viewpoint and its Tracing Relations
The relationship between logical and technical architectural components is n:m in general if the technical architecture is designed without the logical architecture in mind. 

Our overall approach is to provide meaningful tracing relationships between the model elements of the views. Therefore, we suggest developing an initial architecture in the technical view that has the same component structure as the logical architecture, which yields a 1:1 tracing relation between logical and technical components on this layer of abstraction. 

Even when using a 1:1 tracing relation between logical and technical components, it is important to notice that in advance we recommend structuring the logical viewpoint in terms of grouping logical subcomponents that are realized in the software execution subsystem. This enables for a meaningful 1:1 trace relation. Note that even if we propose a 1:1 relationship between logical and technical components, the interface refinement has a large impact on the details of the technical architecture.
 
Other relationships are possible, but we strongly encourage to manifest engineering decision in terms of a proper logical systems architecture that enables for a 1:1 relationship.

### Redundancy in the Technical Viewpoint
Applying redundancy (patterns) is necessary in systems engineering for many reasons. Redundancy realized in concrete technical components, however, can be already modeled in the logical viewpoint, yielding a 1:1 mapping to technical components. Furthermore, it is also possible that logical components occur multiple times in the technical architecture, meaning to model redundancy in the technical view for the first time. These logical components manifest themselves in a 1:n relation in technical components.

***

<a name="figureExample"></a>
![Example](/images/technical_viewpoint/technical_overview.png){:class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 2: </b><em>An example of how the technical elements can be composed inclusive different granularity layers.</em></div>

***

## Technical Viewpoint Models of the Software Execution Subsystem
When a software execution subsystem is refined on the next granularity layer, a set of models can be used to describe it. This section provides an overview of possible models and their relations. We call it software execution subsystem, because it is a subsystem that not only models the software of the system but also the execution of the software including the hardware that is needed for this. [Figure 3](#figureOverviewSES) shows how we divide the software execution subsystem.
As part of the software execution subsystem, the execution platform models represent everything that is needed to execute the software of the system. Its main model is the execution platform, which describes a hardware topology of digital subsystems in terms of execution as well as communication resources. Another part of the software subsystem are the software models representing the pure software part of the system. The software models have both dynamic parts, represented by dedicated run-time software models like task architectures, as well as static parts, namely design-time software models, like middlewares and operating systems. Relations between software architecture and execution platform describe potential allocations of software artifacts to hardware computing (execution) resources.

In SpesML, a _software execution subsystem_ is a container element for all model elements of the corresponding concept (of the software execution subsystem) and can contain _task architectures_ (for the run-time software), _>TBD<_ (for the design-time software), _execution platforms_ (for the hardware/execution topology) and _allocations_ between them. 
In the following sections, we describe these models in more detail.

<a name="figureOverviewSES"></a>
![Overview SES](/images/technical_viewpoint/SES_Overview.png){:class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 3: </b><em>Overview over the models of the software execution subsystem.</em></div>


### Run-time Software Models

Run-time software models represent the dynamic part of the software models (of the software execution subsystem). For instance, run-time software can be described by a set of (executable) tasks (e.g., an AutoSAR runnable), which processes information from its inputs to its outputs, and a bus message catalogue, which contains all messages representing the technical dataflow between these tasks. In SpesML, we use a _task architecture_, which is part of a software execution subsystem, to model the structure of such _tasks_, which can communicate via _messages_:

- _Task_: Tasks are entities of the technical (software) architecture to which subcomponents of the logical architecture are mapped during deployment. The mapping between logical components, containing logical subcomponents for software, and software execution subsystems, containing software tasks, is 1:1. The mapping of logical subcomponent to tasks of such a pair of a logical component and a software execution subsystem is n:m, although we are recommending again a 1:1 mapping as well. A task defines how to process (possible) incoming information and create (possible) outgoing information. The interface of a task is modeled with ports for input and output. Messages containing information are received and/or sent by these ports. These software tasks will be deployed onto the execution units of an execution platform, which we explain in a separate [section](#execution-platform-models).

- _Message_: Task ports can be connected to model an information flow between tasks via messages. An input port can only be connected to exactly one output port of the same message type. An output port can be connected to multiple input ports of the same message type. Messages contain information that is sent between tasks to process it there. In SpesML, we are using _technical interfaces_ to define the ports and specify the messages that can be sent via these ports. Following the [Universal Interface Model](/concepts/modeling_framework/uim.html), each technical interface can have multiple channels. Each channel has a type that defines which type of information can be sent via the channel (and the interface). Note that we do not explicitly model the behavior of ports. The same technical interfaces are also used as connection possibility between all other technical elements besides tasks as described in [this previous section](#elements-and-structure-of-the-technical-viewpoint).

The following table shows the mapping between the previously describe concepts (tasks, interfaces and channels) and the SysML construct we used to realize it in SpesML (together with the names in the MagicDraw tool).  

| Concept | SysML Construct | Stereotype / Name in SpesML plugin (MagicDraw) | Shown Name (GUI) in SpesML plugin (MagicDraw)|
| ------ | ------ | ------ | ------ |
| Container for tasks (task architecture) | Definition: Block, Instance: Part | [SpesML Task Architecture](/plugin/technical_viewpoint.html#task-architecture) | Task Architecture |
| Task | Definition: Block, Instance: Part | [SpesML Task](/plugin/technical_viewpoint.html#task) | Task |
| Task Message/Interface | Proxy Port | [SpesML Technical Interface](/plugin/technical_viewpoint.html#technical-interface) | Technical Interface |
| Channel | Flow Property | [SpesML Channel](/plugin/technical_viewpoint.html#channel)<sup>1</sup> | Channel<sup>1</sup> |

<sup>1</sup> Inherited from Universal Interface Model


### Design-time Software Models

Conceptually, SpesML also supports design-time software models as being part of the software models (of the software execution subsystem). These models include models representing specific middleware aspects and operating system models and thus are representing the static parts of the software models. For instance, design-time software models comprise of models representing certain middleware aspects, including, for instance, virtualization aspects and potential OS-related models. Software partitions are one example of artifacts that can be described here. 

Design-time software models are usually modeled as black-box models that describe the syntax of such software models.


### Execution Platform Models

The _execution platform_ enables the description of a hardware topology of digital subsystems. We call it execution platform, because it mostly represents execution units (see below) and we want to clearly distinguish this architecture/platform from a more general hardware architecture that could imply containing, e.g., mechanical components.
Since the digital subsystem exclusively consists of tasks, which are components realized in software, the execution platform needs to specify the hardware resources which are necessary for the execution of these software parts.
The most prominent hardware components hereby are execution units like Electrical Control Units (ECUs) that can execute software tasks.
However, also technical communication units such as bus systems are highly relevant for the software execution in distributed technical architectures. Therefore, execution platforms can contain _execution_ as well _communication components_ to represent these two entity types.

For actually gaining an added value for systems engineering, an important aspect is to capture more than the structure of the hardware topology alone. The specification of relevant attributes of all technical entities is the key to enable verification and analysis of the technical architecture.
For execution components, this might entail to capture the available memory and computational power.
For communication components, the usual technical aspects are bandwidth, real time capabilities and similar quality of service attributes.
All of these entities and attributes are finally relevant for the allocation models.

Actuators and sensor will be modeled outside the execution platform as part of mechatronic components, but it is often needed that they are connected to some execution components. This is why execution platforms and the contained execution and communication components can be connected with other technical/mechatronic components like actuators and sensors with the generic _technical interface_, which we already introduced earlier for all technical components on all granularity layers.

The following table shows the mapping between the previously describe concepts (execution platform, execution and communication components) and the SysML construct we used to realize it in SpesML (together with the names in the MagicDraw tool).  

| Concept | SysML Element | Stereotype / Name in SpesML plugin (MagicDraw) | Shown Name (GUI) in SpesML plugin (MagicDraw)|
| ------ | ------ | ------ | ------ |
| Platform/Container for execution and communication units | Definition: Block, Instance: Part | (is in our implementation identical with the [software execution subsystem](/plugin/technical_viewpoint.html#software-execution-subsystem)) | (is in our implementation identical with the [software execution subsystem](/plugin/technical_viewpoint.html#software-execution-subsystem)) |
| Execution Unit (e.g., ECU) | Definition: Block, Instance: Part | [SpesML Execution Component](/plugin/technical_viewpoint.html#execution-component) | [Execution Component](/plugin/technical_viewpoint.html#execution-component) |
| Communication Unit (e.g., bus) | Definition: Block, Instance: Part | [SpesML Communication Component](/plugin/technical_viewpoint.html#communication-component) | [Communication Component](/plugin/technical_viewpoint.html#communication-component) |
| Communication Message/Interface | Proxy Port | [SpesML Technical Interface](/plugin/technical_viewpoint.html#technical-interface) | Technical Interface |


### Allocation Models
 
A software allocation model realizes a mapping of tasks from the task architecture to execution components of the execution platform. Thereby, it is an integrated platform-specific solution model for the software execution subsystem. 
Such an allocation is necessary to identify the respective execution (and communication) resources for given software architecture artifacts, e.g., an allocation of a set of software tasks to a certain ECU. This allocation enables further system engineering activities, e.g., scheduling analysis tasks.

All allocations of tasks to execution components in the software deployment model must be of cardinality n:1. This means, that each task can only be deployed to exactly one execution component, while each execution component can execute several (n) tasks.

In SpesML, we not only have one allocation type for the mapping of tasks to execution components but two. The reason is that SysML has the concept of type definitions ("blocks") and instances ("parts"). For example, an execution component representing a special ECU needs to be defined once as a "block", but this "block" can then be instantiated several times in the diagrams as "parts" to model that this special ECU exists several times in the actual system as well (always as the same type / with the same definition). To support this concept, we have two allocations for tasks to execution components in SpesML: a _task instance to execution component instance mapping_ (for allocations between instances) and a _task type to execution component type mapping_ (for allocations between types/definitions).

Furthermore, we are supporting the allocation of task ports to execution component ports. This _task port to execution component port mapping_ might be needed to specify which port of a task refers/maps to which port of an execution component. It is, for example, possible that several task ports needs to be mapped on the same execution component port, because the latter is a bus port on which the messages of multiple task ports are transported.

When integrating design-time software models, e.g., software partitions, it is important to note that this consequently has an effect on the allocation models as well, as models from the run-time software, e.g., tasks, can conceptually be allocated to models of the design-time software, e.g., software partitions, which in turn will be allocated to execution platform models. This means there are _task to partition component mappings_ and _partition to execution component mappings_.

The following table shows the mapping between the previously describe mapping concepts and the SysML construct we used to realize it in SpesML (together with the names in the MagicDraw tool).  

| Concept | SysML Element | Stereotype / Name in SpesML plugin (MagicDraw) | Shown Name (GUI) in SpesML plugin (MagicDraw)|
| ------ | ------ | ------ | ------ |
| Task Instance to Execution Component Instance Mapping | Allocation Matrix | [SpesML TaskInstanceToExecution Allocation Matrix](/plugin/technical_viewpoint.html#taskinstancetoexecution-allocation-matrix) | [TaskInstanceToExecution Allocation Matrix](/plugin/technical_viewpoint.html#taskinstancetoexecution-allocation-matrix) |
| Task Type to Execution Component Type Mapping | Allocation Matrix | [SpesML TaskTypeToExecution Allocation Matrix](/plugin/technical_viewpoint.html#tasktypetoexecution-allocation-matrix) | [TaskTypeToExecution Allocation Matrix](/plugin/technical_viewpoint.html#tasktypetoexecution-allocation-matrix) |
| Task Port to Execution Component Port Mapping | Allocation Matrix | [SpesML PortToExecution Allocation Matrix](/plugin/technical_viewpoint.html#porttoexecution-allocation-matrix) | [PortToExecution Allocation Matrix](/plugin/technical_viewpoint.html#porttoexecution-allocation-matrix) |
| Task to Partition Component Mapping | Allocation Matrix | SpesML TaskPartition Allocation | TaskPartition Allocation |
| Partition to Execution Component Mapping | Allocation Matrix | SpesML Partition Allocation | Partition Allocation |



