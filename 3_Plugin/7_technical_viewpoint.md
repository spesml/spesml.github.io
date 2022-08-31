---
layout: default
title: Technical Viewpoint
nav_order: 7
parent: SpesML Plugin
permalink: /plugin/technical_viewpoint.html
---
# ![Technical Viewpoint](/images/technical_viewpoint/TechnicalViewpoint.png){:height="30px" width="30px"}{:class="img-responsive"}SpesML Plugin - Technical Viewpoint

## Overview
The Technical Viewpoint is the last step on the way to platform-specific models. Here, technical elements represent the system finally for specific platforms while logical components of platform-independent models of the [Logical Viewpoint](/plugin/logical_viewpoint.html) can be mapped to tasks deployed on execution units of these specific platforms. This is needed to be able to generate code out of the models and enable further system engineering activities including task optimization/scheduling.

For a better understanding of the concept of the Technical Viewpoint, please have a look at the respective [theoretical concept documentation](/concepts/modeling_framework/technical_viewpoint.html). In the following, we will explain the realization/implementation of the Technical Viewpoint within our SpesML plugin.

## Method
The Technical Viewpoint models technical architectures. Technical architectures can be composed of various component types to represent the technical specifications of a system (see the concept in [Figure 1](#figureConcept)). Logical components of the [Logical Viewpoint](/plugin/logical_viewpoint.html) can then be mapped onto these technical components. A technical architecture can not only represent mechanical, electronic, or mechatronic elements (or any generic technical element) but also a software subsystem. A software subsystem is a model of the pure software part of the system including its execution elements. It contains a task architecture with tasks onto which the software-relevant logical components of the [Logical Viewpoint](/plugin/logical_viewpoint.html) are mapped. Furthermore, it contains an execution platform consisting of execution units like ECUs and communication elements like buses. An allocation of tasks to execution units realizes the deployment.

<a name="figureConcept"></a>
![Technical Architecture Concept](/images/technical_viewpoint/TVP_Element_Overview.png){:class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 1: </b><em>The concept of the implemented Technical Viewpoint.</em></div>

Regarding the development process, one step is to build the technical part of the system with all available components of the Technical Viewpoint (as far as needed). This should include at least one software subsystem. To model such a software subsystem with all its tasks and execution units is another step. Since the logical architecture should be mapped next with the technical architecture, we already recommended building the logical and now the technical architecture in a way that a 1:1 mapping is possible between logical and technical components. In addition, it simplifies the process when already in the Logical Viewpoint the pure software-related logical components are separated from the other logical components. Then, it is easy to map them directly to a technical component representing the software subsystem and internally to the defined (software) tasks. However, we do not force a 1:1 mapping and it is also very usual that some technical components exist that do not have a match within the logical architecture, because they were not needed for a platform-independent model but still contribute to the technical representation of an actual platform. After the mapping of logical to technical components (including the tasks), the final deployment needs to be done by mapping the tasks to the added execution units. It should be said that the development is not a strict step-by-step process, but usually building the technical architecture with components and elements of the software subsystem alternates or is in parallel with creating the matching between Logical and Technical Viewpoint and within the Technical Viewpoint regarding the deployment.

We recommend that the software subsystem is modeled on a separate (lower) granularity level ([theoretical concept](/concepts/modeling_framework/technical_viewpoint.html)). How to create a new granularity level is described [here](/plugin/general_concepts/granularity_transitions.html). However, we also allow in the tool that the internal software subsystem with its task architecture(s) and execution platform(s) can be modeled on the same level (just hierarchical), i.e., in the same MagicDraw project directly inside the [Software Component](#software-component) representing the software subsystem (see next section).

## Structure
The SpesML plugin has a separate folder for the Technical Viewpoint (see [Figure 2](#figureElements)). Within this folder, it is possible to create folders for technical components ([Technical Package](#technical-package)), for technical interfaces types ([Technical Interface Types Package](#technical-interface-types-package)), and for technical tracing ([Technical Tracing Package](#technical-tracing-package)). Inside the Technical Tracing Package, all diagrams regarding tracing can be created: [Technical Tracing Map](#technical-tracing-map), [TechnicalToLogical Matrix](#technicaltological-matrix), and [TechnicalToRequirement Matrix](#technicaltorequirement-matrix). Inside the Technical Interface Types Package, all possible interface types can be created that are usable for the interfaces between technical elements ([Technical Interface](#technical-interface)), and further Technical Interface Types Packages for a better organization. 

Inside the Technical Package, other Technical Packages can be created as well for better organization, but more important are the possibilities of the component creations. The generic [Technical Component](#technical-component) can be used for everything. If something more specific is needed, then the [Mechanical](#mechanical-component), [Electronic](#electronic-component) or [Mechatronic Components](#mechatronic-component) are available. In addition, the modeler can define a [Technical Context](#technical-context) inside a Technical Package. The Technical Context behaves like a Technical Component, but can already be placed in the Technical Viewpoint folder to create a starting point for the system and a possibility to represent the connected external systems and [Technical Actors](#technical-actor), which can be created in a Technical Package as well. To indicate that a component is representing an external (sub-)system, the corresponding "External" part property can be set to "Yes". 

Now, only the software subsystem is missing. For better guidance, it is only possible to create first a [Software Package](#Software-Package) inside a Technical Package. Within a Software Package, the modeler can then create [Software Components](#software-component), which represent software subsystems. Task architectures and execution platforms are needed to define a software subsystem. Therefore, a Software Package can also contain [Task Architecture Packages](#task-architecture-package) and [Execution Platform Packages](#execution-platform-package) (besides more Software Packages). Inside the Task Architecture Packages, [Task Architectures](#task-architecture) and [Tasks](#task) can be created. Inside the Execution Platform Packages, [Execution Platforms](#execution-platform), [Execution Components](#execution-component) and [Communication Components](#communication-components) can be created.

<a name="figureElements"></a>
![Technical Elements Of The Plugin](/images/technical_viewpoint/TVP_elements_in_plugin.png){:class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 2: </b><em>An example collection of all technical elements implemented inside the SpesML plugin.</em></div>

Every component (and the Technical Context) can have its own [Technical Internal Component Diagram](#technical-internal-component-diagram). Depending on the owner of the diagram, only some internal components can be placed in the diagram:
- The Technical Component as well as the Technical Context can contain Technical, Mechanical, Electronic, Mechatronic, and Software Components. 
- Mechatronic Components can contain Mechanical and Electronic Components. 
- Mechanical and Electronic Components can only contain internal components of their type. 
- Software Components can contain Task Architectures and Execution Platforms. 
- Task Architectures can contain Tasks. 
- Execution Platforms can contain Execution Component and Communication Component. 

No behavior is modeled inside the Technical Viewpoint, which is why the composition of the components inside the (nested) diagrams is the main part of the Technical Viewpoint, together with the component mapping and the allocation of Tasks to Execution Components for the deployment.

To connect this composition of technical elements, it is possible to place interfaces (proxy ports) on every element and connect them with a Connector if both ports have the same interface type (defined in a Technical Interface Types Package). All elements can be connected via a generic [Technical Interface](#technical-interface), which is defined by its Technical Interface Type. Technical Interface Types can have [Channels](#channel), which are inherited from the [Universal Interface Model](/concepts/modeling_framework/uim.html). Therefore it is possible, that the model communication flows between technical elements. An exception is the Task Architecture because it does not make sense to connect Tasks in Task Architectures with the physical elements outside of Task Architectures. However, the Tasks themselves inside Task Architecture can be connected among each other again with Technical Interfaces.



## How to model
TODO: Should be done if the Technical Viewpoint is completely realized in the plugin (and in a final state).




## Elements
### ![Technical Viewpoint](/images/technical_viewpoint/TechnicalViewpoint.png){:class="img-responsive"}Technical Viewpoint
This element is a *UML/SysML Package* with a dedicated stereotype that allows defining an adequate SpesML model structure and guides users by restricting what elements and diagrams can be created below this package for the [Technical Viewpoint](/plugin/technical_viewpoint.html). This package usually contains only further packages to separate different purpose categories within the Technical Viewpoint. In addition, it is already possible to create a [Technical Context](#technical-context) as a starting point.

### ![Technical Tracing Package](/images/technical_viewpoint/TechnicalTracingPackage.png){:class="img-responsive"}Technical Tracing Package
This element is a *UML/SysML Package* with a dedicated stereotype that allows defining an adequate SpesML model structure and guides users by restricting what elements and diagrams can be created below this package for the [Technical Viewpoint](/plugin/technical_viewpoint.html). This package usually contains only tracing-related relation maps and matrixes.

### ![Technical Interface Types Package](/images/technical_viewpoint/TechnicalInterfaceTypesPackage.png){:class="img-responsive"}Technical Interface Types Package
This element is a *UML/SysML Package* with a dedicated stereotype that allows defining an adequate SpesML model structure and guides users by restricting what elements and diagrams can be created below this package for the [Technical Viewpoint](/plugin/technical_viewpoint.html). This package usually contains only interface types that can be used for [Technical Interfaces](#technical-interface).

### ![Technical Package](/images/technical_viewpoint/TechnicalPackage.png){:class="img-responsive"}Technical Package
This element is a *UML/SysML Package* with a dedicated stereotype that allows defining an adequate SpesML model structure and guides users by restricting what elements and diagrams can be created below this package for the [Technical Viewpoint](/plugin/technical_viewpoint.html). This package usually contains only standard technical components like [Technical](#technical-component), [Mechanical](#mechanical-component), [Electronic](#electronic-component) and [Mechatronic Components](#mechatronic-component), and context-related elements like [Technical Contexts](#technical-context) and [Technical Actors](#technical-actor). In addition, it can also contain [Software Packages](#Software-Package), which are the entry point for software subsystems.

### ![Software Package](/images/technical_viewpoint/SoftwarePackage.png){:class="img-responsive"}Software Package
This element is a *UML/SysML Package* with a dedicated stereotype that allows defining an adequate SpesML model structure and guides users by restricting what elements and diagrams can be created below this package for the [Technical Viewpoint](/plugin/technical_viewpoint.html). This package usually contains only elements regarding the software subsystem. It includes [Software Components](#software-component), which represent software subsystems, and packages for further software subsystem related elements like [Task Architecture Packages](#task-architecture-package) and [Execution Platform Packages](#execution-platform-package).

### ![Task Architecture Package](/images/technical_viewpoint/TaskPackage.png){:class="img-responsive"}Task Architecture Package
This element is a *UML/SysML Package* with a dedicated stereotype that allows defining an adequate SpesML model structure and guides users by restricting what elements and diagrams can be created below this package for the [Technical Viewpoint](/plugin/technical_viewpoint.html). This package usually contains only elements to create a task architecture for a software subsystem, i.e., [Task Architectures](#task-architecture) and [Tasks](#task).

### ![Execution Platform Package](/images/technical_viewpoint/ExecutionPackage.png){:class="img-responsive"}Execution Platform Package
This element is a *UML/SysML Package* with a dedicated stereotype that allows defining an adequate SpesML model structure and guides users by restricting what elements and diagrams can be created below this package for the [Technical Viewpoint](/plugin/technical_viewpoint.html). This package usually contains only elements to create an execution platform for a software subsystem, i.e., [Execution Platforms](#execution-platform), [Execution Components](#execution-component) and [Communication Components](#communication-components).


### ![Technical Context](/images/technical_viewpoint/TechnicalContext.png){:class="img-responsive"}Technical Context
The Technical Context is a separate element but it mainly behaves as a standard [Technical Component](#technical-component) like containing a [Technical Internal Component Diagram](#technical-internal-component-diagram). 
Its purpose is to act as a starting point for the system model, where the system under development is represented as only one component, usually a [Technical Component](#technical-component), and the connected external systems and [Technical Actors](#technical-actor) can be modeled to show the environment/context of the system under development. 
A component can be defined as external (in a specific diagram like the one from the Technical Context) by changing the property *external* of this component from *No* to *Yes*. Another property is *system under development* with which the modeler can specify if a component is the current system under development or not (the latter is the default). 
To support the purpose as starting point and initial overview, the Technical Context is the only element (besides packages) that can be directly placed below the [Technical Viewpoint](#technical-viewpoint). If a user opens the Technical Viewpoint, it will directly see the Technical Context element and can open it to see first the context and then go deeper into the system under development.

### ![Technical Actor](/images/technical_viewpoint/TechnicalActor.png){:class="img-responsive"}Technical Actor
This element is based on a *SysML Block* with a dedicated stereotype that allows defining where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it. 
In the case of the Technical Actor, it prevents the creation of any sub-element below it including any diagram except [Technical Interfaces](#technical-interface). 
The Technical Actor just indicates an actor that has a connection to the system under development without any further modeling of this actor. Therefore, the Technical Actor makes in most cases only sense to be placed in the [Technical Context](#technical-context). 
To model the connections with the system under development, it is possible to add [Technical Interfaces](#technical-interface) to the Technical Actor and connect them with Technical Interfaces of other components, usually, the one representing the system under development.

### ![Technical Component](/images/technical_viewpoint/TechnicalComponent.png){:class="img-responsive"}Technical Component
This element is based on a *SysML Block* with a dedicated stereotype that allows defining where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it. 
A Technical Component is a generic component and can represent everything. It can be used as a placeholder and if it is not needed to specify the modeled element further with it or if it is a container for components of different disciplines.
A Technical Component can be further specified by adding a [Technical Internal Component Diagram](#technical-internal-component-diagram) to it. With such an owner it is possible to place [Technical](#technical-component), [Mechanical](#mechanical-component), [Electronic](#electronic-component), [Mechatronic](#mechatronic-component) and [Software Components](#software-component) in this diagram. 
A Technical Component can provide a syntactic interface via [Technical Interfaces](#technical-interface), which can be used to connect this component to other components (to model just the composition or to model actual information flow if the used [Technical Interface Type](#technical-interface-type) contains [Channels](#channel)).

### ![Software Component](/images/technical_viewpoint/SoftwareComponent.png){:class="img-responsive"}Software Component
TODO: update needed
This element is based on a *SysML Block* with a dedicated stereotype that allows defining where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
A Software Component is a container representing the software subsystem (see [Technical Viewpoint concept](/concepts/modeling_framework/technical_viewpoint.html)). It is used by the software engineering discipline to model the software part of the system (and its execution environment). 
A Software Component can be further specified by adding a [Technical Internal Component Diagram](#technical-internal-component-diagram) to it. With such an owner it is possible to place [Task Architectures](#task-architecture) and [Execution Platforms](#execution-platform) in this diagram. 
A Software Component can provide a syntactic interface via [Technical Interfaces](#technical-interface), which can be used to connect this component to other components (to model just the composition or to model actual information flow if the used [Technical Interface Type](#technical-interface-type) contains [Channels](#channel)).

### ![Mechanical Component](/images/technical_viewpoint/MechanicalComponent.png){:class="img-responsive"}Mechanical Component
This element is based on a *SysML Block* with a dedicated stereotype that allows defining where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
A Mechanical Component is a specific component of the mechanical engineering discipline. It can be used to model mechanical parts of the system, like e.g., the mechanical presence of a door or a motor shaft.
A Mechanical Component can be further specified by adding a [Technical Internal Component Diagram](#technical-internal-component-diagram) to it. With such an owner it is possible to place [Mechanical Components](#mechanical-component) in this diagram. 
A Mechanical Component can provide a syntactic interface via [Technical Interfaces](#technical-interface), which can be used to connect this component to other components (to model just the composition or to model actual information flow if the used [Technical Interface Type](#technical-interface-type) contains [Channels](#channel)).

### ![Mechatronic Component](/images/technical_viewpoint/MechatronicComponent.png){:class="img-responsive"}Mechatronic Component
This element is based on a *SysML Block* with a dedicated stereotype that allows defining where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
A Mechatronic Component is a specific fusion component of the mechanical and electrical engineering disciplines. It can be used to model parts of the system that have mechanical as well as electrical shares, like e.g., an electrical motor. It usually represents a container that you can (theoretically) refine even more into (in the end) [Mechanical](#mechanical-component) and [Electronic Components](#electronic-component).
A Mechatronic Component can be further specified by adding a [Technical Internal Component Diagram](#technical-internal-component-diagram) to it. With such an owner it is possible to place [Mechanical](#mechanical-component), [Electronic](#electronic-component) and [Mechatronic Components](#mechatronic-component) in this diagram. 
A Mechatronic Component can provide a syntactic interface via [Technical Interfaces](#technical-interface), which can be used to connect this component to other components (to model just the composition or to model actual information flow if the used [Technical Interface Type](#technical-interface-type) contains [Channels](#channel)).

### ![Electronic Component](/images/technical_viewpoint/ElectronicComponent.png){:class="img-responsive"}Electronic Component
This element is based on a *SysML Block* with a dedicated stereotype that allows defining where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
An Electronic Component is a specific component of the electrical engineering discipline. It can be used to model electrical parts of the system, like e.g., a light or a sensor. Often, electrical parts contain already mechanical parts (like the case), which is why they can also be modeled as [Mechatronic Components](#mechatronic-component). The user can then decide what part should be viewed/identified.
An Electronic Component can be further specified by adding a [Technical Internal Component Diagram](#technical-internal-component-diagram) to it. With such an owner it is possible to place [Electronic Components](#electronic-component) in this diagram. 
An Electronic Component can provide a syntactic interface via [Technical Interfaces](#technical-interface), which can be used to connect this component to other components (to model just the composition or to model actual information flow if the used [Technical Interface Type](#technical-interface-type) contains [Channels](#channel)).

### ![Task Architecture](/images/technical_viewpoint/TaskArchitecture.png){:class="img-responsive"}Task Architecture
This element is based on a *SysML Block* with a dedicated stereotype that allows defining where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
A Task Architecture is a container element for [Tasks](#task) to represent the software part of a software subsystem (represented by [Software Components](#software-component)).
A Task Architecture can be further specified by adding a [Technical Internal Component Diagram](#technical-internal-component-diagram) to it. With such an owner it is possible to place [Tasks](#task) in this diagram. 
A Task Architecture does NOT provide any syntactic interface via e.g., [Technical Interfaces](#technical-interface). It is only used as a virtual container for all the [Tasks](#task) and does not need to have any connection with other (physical) elements.

### ![Task](/images/technical_viewpoint/TaskComponent.png){:class="img-responsive"}Task
This element is based on a *SysML Block* with a dedicated stereotype that allows defining where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
A Task is a specific (atomic) component representing a single software task that was mapped from the [Logical Viewpoint](/plugin/logical_viewpoint.html) and should be executed on an execution unit represented by an [Execution Component](#execution-component).
A Task cannot be further specified by adding a diagram to it. It is an atomic unit on which software-related Logical Components of the [Logical Viewpoint](/plugin/logical_viewpoint.html) can be mapped, and which itself can then be mapped on [Execution Components](#execution-component) to realize the final (software) deployment with such an allocation.
A Task can provide a syntactic interface via [Technical Interfaces](#technical-interface), which can be used to connect this component to other components, in this case, other Tasks (to model actual information flow if the used [Technical Interface Type](#technical-interface-type) contains [Channels](#channel)).

### Software Execution Subsystem
TODO: update needed
This element is based on a *SysML Block* with a dedicated stereotype that allows defining where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
An Execution Platform is a container element for [Execution](#execution-component) and [Communication Components](#communication-components) to represent the execution environment of a software subsystem (represented by [Software Components](#software-component)). 
An Execution Platform can be further specified by adding a [Technical Internal Component Diagram](#technical-internal-component-diagram) to it. With such an owner it is possible to place [Execution](#execution-component) and [Communication Components](#communication-components) in this diagram. 
An Execution Platform can provide a syntactic interface via [Technical Interfaces](#technical-interface), which can be used to connect this component to other components, in this case internal [Execution](#execution-component) and [Communication Components](#communication-components), or to its container, the [Software Component](#software-component) (to model just the composition or to model actual information flow if the used [Technical Interface Type](#technical-interface-type) contains [Channels](#channel)).

### ![Execution Component](/images/technical_viewpoint/ExecutionComponent.png){:class="img-responsive"}Execution Component
This element is based on a *SysML Block* with a dedicated stereotype that allows defining where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
An Execution Component is a specific (atomic) component of the software subsystem that represents an execution unit, like an ECU, on which [Tasks](#task) can be deployed and executed.
An Execution Component cannot be further specified by adding a diagram to it. It is an atomic unit on which [Tasks](#task) can be mapped to realize the (software) deployment.
An Execution Component can provide a syntactic interface via [Technical Interfaces](#technical-interface), which can be used to connect this component to other components, in this case other [Execution Components](#execution-component) or [Communication Components](#communication-components) (to model just the composition or to model actual information flow if the used [Technical Interface Type](#technical-interface-type) contains [Channels](#channel)).

### ![Communication Component](/images/technical_viewpoint/CommunicationComponent.png){:class="img-responsive"}Communication Component
This element is based on a *SysML Block* with a dedicated stereotype that allows defining where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
A Communication Component is a specific (atomic) component of the software subsystem that represents a communication unit, like a CAN bus, connecting [Execution Components](#execution-component). However, it is not needed to have always specifically modeled Communication Components between [Execution Components](#execution-component).
A Communication Component cannot be further specified by adding a diagram to it. It is an atomic unit that can mainly be used to indicate/model communication elements between [Execution Components](#execution-component) (if wanted).
A Communication Component can provide a syntactic interface via [Technical Interfaces](#technical-interface), which can be used to connect this component to other components, in this case [Execution Components](#execution-component) (to model just the composition or to model actual information flow if the used [Technical Interface Type](#technical-interface-type) contains [Channels](#channel)).


### ![Technical Interface](/images/technical_viewpoint/TechnicalInterface.png){:class="img-responsive"}Technical Interface
This element is based on a *SysML Proxy Port* with a dedicated stereotype that allows defining where the element can be placed and other specifications.
A Technical Interface is used to connect different technical elements/components generically. 
It can be specified further by using [Technical Interface Types](#technical-interface-type) and [Channels](#channel) to model the connection between the elements and even actual information flows (via the channels).
A Technical Interface is nothing else than a port that can be placed on a technical element. If another technical element has also such a port/interface with the same [Technical Interface Type](#technical-interface-type)], the user can connect these two ports with a *Connector* line.

### ![Technical Interface Type](/images/technical_viewpoint/TechnicalInterfaceType.png){:class="img-responsive"}Technical Interface Type
This element is based on a *SysML Interface Block* with a dedicated stereotype that allows defining where the element can be placed and other specifications.
A Technical Interface Type is used to specify the type of a [Technical Interface](#technical-interface). It needs to be defined separately in a [Technical Interface Types Package](#technical-interface-types-package) and can then be used to fill the *Type* property of a [Technical Interface](#technical-interface).
A Technical Interface Type can either contain a Value Property (e.g., a specific enumeration) or a [Channel](#channel) (or multiple ones). 

### ![Channel](/images/universal_interface_model/Channel.png){:class="img-responsive"}Channel
This element is based on a *SysML Flow Property* with a dedicated stereotype that allows for defining the flow direction and other specifications. Its concept is explained in the [Universal Interface Model](/concepts/modeling_framework/uim.html). It can be added as an element to a [Technical Interface Type](#technical-interface-type). Channels enable signal/information transport between elements that are connected with an interface connection that has such an interface type (with a channel). A channel has a type (the type of the transported signal/information), which can be any pre-defined basic data type or a new user-defined data type (see [Data Types](/plugin/data_types.html)).



## Diagrams
### ![Technical Tracing Map](/images/diagrams/map.png){:class="img-responsive"}SpesML Technical Tracing Map
This relation map shows technical elements like Technical Components, Mechanical Components, etc. and to what [Requirements](/plugin/requirements_viewpoint.html#requirement), [Functional Component](/plugin/functional_viewpoint.html#function) or [Logical Components](/plugin/logical_viewpoint.html#logical-component) these elements are tracing to. By default, all technical elements are shown but it is also possible to drag & drop a single technical element to the relation map to show only the particular relationships.

### ![TechnicalToLogical Matrix](/images/diagrams/matrix.png){:class="img-responsive"}SpesML TechnicalToLogical Matrix
This matrix allows to create relationships between elements of the [Technical Viewpoint](/plugin/technical_viewpoint.html#technical-viewpoint) and elements of the [Logical Viewpoint](/plugin/logical_viewpoint.html#logical-viewpoint).

### ![TechnicalToRequirement Matrix](/images/diagrams/matrix.png){:class="img-responsive"}SpesML TechnicalToRequirement Matrix
This matrix allows to create relationships between elements of the [Technical Viewpoint](/plugin/technical_viewpoint.html#technical-viewpoint) and [Requirements](/plugin/requirements_viewpoint.html#requirements).

### ![Technical Internal Component Diagram](/images/diagrams/composite_structure.png){:class="img-responsive"}SpesML Technical Internal Component Diagram
This diagram is based on a *UML Composite Structure Diagram/SysML Internal Block Diagram* and provides a reduced diagram toolbar related to SpesML for the [Technical Viewpoint](/plugin/technical_viewpoint.html). Note that intentionally any technical components cannot be created using the diagram toolbar. Instead, it is recommended to create these elements by dragging/dropping a technical component into the diagram. Depending on the owner of the diagram, only certain elements are allowed to be placed in this diagram. For example, for a Technical Internal Component Diagram of a Mechanical Component, it is only allowed to place further Mechanical Component, for a Technical Internal Component Diagram of an Execution Platform it is only allowed to place Execution Components and Communication Components, etc. If you drag and drop a wrong element inside a diagram, you will get a warning message that will tell you which elements are allowed for this specific diagram.

### ![TaskInstanceToExecution Allocation Matrix](/images/diagrams/matrix.png){:class="img-responsive"}TaskInstanceToExecution Allocation Matrix
This matrix allows to create relationships between [Tasks](#task) in [Task Architectures](#task-architecture) and [Execution Components](#execution-component) in [Execution Platforms](#execution-platform). This creates an allocation between Tasks and Execution Components that represents the deployment of these software tasks on these execution units. All of this happens on the instance level, meaning that every instance/part of a Task and an Execution Component can be allocated separately. To use this matrix, a scope needs to be set (above the matrix diagram). As the description at the bottom of the matrix diagrams indicates, the row scope should be the Task Architecture of the wanted Tasks and the column scope the Execution Platform of the wanted Execution Components.

### ![TaskTypeToExecution Allocation Matrix](/images/diagrams/matrix.png){:class="img-responsive"}TaskTypeToExecution Allocation Matrix
This matrix allows to create relationships between [Tasks](#task) in [Task Architectures](#task-architecture) and [Execution Components](#execution-component) in [Execution Platforms](#execution-platform). This creates an allocation between Tasks and Execution Components that represents the deployment of these software tasks on these execution units. All of this happens on the type level, meaning that only the defined types/blocks of a Task and an Execution Component can be allocated (instances of them cannot be allocated separately!). To use this matrix, a scope needs to be set (above the matrix diagram). As the description at the bottom of the matrix diagrams indicates, the row scope should be the package in which the wanted Tasks are defined, and the column scope the package in which the wanted Execution Components are defined.

### ![PortToExecution Allocation Matrix](/images/diagrams/matrix.png){:class="img-responsive"}PortToExecution Allocation Matrix
This matrix allows to create relationships between [Technical Interfaces](#technical-interface) (ports) of [Tasks](#task) in [Task Architectures](#task-architecture) and [Technical Interfaces](#technical-interface) (ports) of [Execution Components](#execution-component) in [Execution Platforms](#execution-platform). This creates an allocation between Tasks ports and Execution Components ports, which supports the deployment of these software tasks on these execution units. To use this matrix, a scope needs to be set (above the matrix diagram). As the description at the bottom of the matrix diagrams indicates, the row scope should be the package in which the wanted Tasks ports are defined, and the column scope is the package in which the wanted Execution Components ports are defined. The port allocation is only needed on the type level because together with a [TaskInstanceToExecution Allocation Matrix](#taskinstancetoexecution-allocation-matrix), it is then always possible which port instances (depending on the task and execution component instance) are meant to be mapped.
