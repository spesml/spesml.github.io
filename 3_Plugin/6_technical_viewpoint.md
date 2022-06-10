---
layout: default
title: Technical Viewpoint
nav_order: 6
parent: SpesML Plugin
permalink: /plugin/technical_viewpoint.html
---
# ![Technical Viewpoint](/images/technical_viewpoint/TechnicalViewpoint.png){:height="30px" width="30px"}{:class="img-responsive"}SpesML Plugin - Technical Viewpoint

## Overview
The Technical Viewpoint is the last step on the way to platform-specific models. Here, technical elements represent the system finally for specific platforms while logical components of platform-independent models of the [Logical Viewpoint](/plugin/logical_viewpoint.html) can be mapped to tasks deployed on execution units of these specific platforms. This is needed to be able to generate code out of the models and enable further system engineering activities including task optimization/scheduling.

For a better understanding of the concept of the Technical Viewpoint, please have a look at the respective [theoretical concept documentation](/concepts/modeling_framework/technical_viewpoint.html). In the following, we will explain the realization/implementation of the Technical Viewpoint within our SpesML plugin.

## Method
The Technical Viewpoint models technical architectures. Technical architectures can be composed of various component types to represent the technical specifications of a system. Logical components of the [Logical Viewpoint](/plugin/logical_viewpoint.html) can then be mapped onto these technical components. A technical architecture can not only represent mechanical, electronic or mechatronic elements (or any generic technical element) but also a software subsystem. A software subsystem is a model of the pure software part of the system including its execution elements. It contains a task architecture with tasks onto which the software relevant logical components of the [Logical Viewpoint](/plugin/logical_viewpoint.html) are mapped. Furthermore, it contains an execution platform consisting of execution units like ECUs and communication elements like buses. An allocation of tasks to execution units realizes the deployment.

TODO: add image like in the logical viewpoint documentation!

Regarding the development process, one step is to build the technical part of the system with all available components of the Technical Viewpoint (as far as needed). This should include at least one software subsystem. To model such a software subsystem with all its tasks and execution units is another step. Since the logical architetcure should be mapped next with the technical architecture, we recommend to already build the logical and now the technical architecture in a way that a 1:1 mapping is possible between logical and technical components. In addition, it simplifies the process when already in the Logical Viewpoint the pure software related logical components are separated from the other logical components. Then, it is easy to map them directly to a technical component representing the software subsystem and internally to the defined (software) tasks. However, we do not force a 1:1 mapping and it is also very usual that some technical components exist that do not have a match within the logical architecture, because they were not needed for a platform independent model but still contribute to the technical representation of an actual platform. After the mapping of logical to technical components (including the tasks), the final deployment needs to be done by mapping the tasks to the added execution units. It should be said that the development is not a strict step by step process, but usually building the technical architecture with components and elements of the software subsystem alternates or is in parallel with creating the matching between Logical and Technical Viewpoint and within the Technical Viewpoint regarding the deployment.

## Structure
The SpesML plugin has a separate folder for the Technical Viewpoint. Within this folder, it is possible to create folders for technical components (Technical Package), for technical interfaces types (Technical Interface Types Package), and for technical tracing ([Technical Tracing Package](#technical-package)). Inside the Technical Tracing Package, all diagrams regading tracing can be created: Technical Tracing Map, TechnicalToLogical Matrix, and TechnicalToRequirement Matrix. Inside the Technical Interface Types Package, all possible interface types can be created that are usable for the interfaces between technical elements (Technical Interface and Task Interface), and further Technical Interface Types Packages for a better organization. 

Inside the Technical Package, other Technical Packages can be created as well for better organization, but more important are the possibilities of the component creations. The generic Technical Component can be used for everything. If something more specific is needed, then the Mechanical, Electronic or Mechatronic Components are available. In addition, the modeler can define a Technical Context inside a Technical Package. The Technical Context behaves like a Technical Component, but can already be placed in the Technical Viewpoint folder to create a starting point for the system and a possibility to represent the connected external systems and Technical Actors, which can be created in a Technical Package as well. To indicate that a component is representing an external (sub-)system, the corresponding "External" part property can be set to "Yes". 

Now, only the software subsystem is missing. For a better guidance, it is only possible to create first a Software Package inside a Technical Package. Within a Software Package, the modeler can then create Software Components, which represent software subsystems. Task architectures and execution platforms are needed to define a software subsystem. Therefore, a Software Package can also contain Task Architecture Packages and Execution Platform Packages (besides more Software Packages). Inside the Task Architecture Packages, Task Architectures and Tasks can be created. Inside the Execution Platform Packages, Execution Platforms, Execution Components and Communication Components can be created.

Every component (and the Technical Context) can have an own Technical Internal Component Diagram. Depending on the owner of the diagram, only some internal components can be placed in the diagram:
- The Technical Component as well as the Technical Context can contain Technical, Mechanical, Electronic, Mechatronic, and Software Components. 
- Mechatronic Components can contain Mechanical and Electronic Components. 
- Mechanical as well as Electronic Components can only contain internal components of their own type. 
- Software Components can contain Task Architectures and Execution Platforms. 
- Task Architectures can contain Tasks. 
- Execution Platforms can contain Execution Component and Communication Component. 

No behavior is modeled inside the Technical Viewpoint, which is why the composition of the components inside the (nested) diagrams is the main part of the Technical Viewpoint, together with the component mapping and the allocation of Tasks to Execution Components for the deployment.

To connect this composition of components, it is possible to place interfaces (ports) on every component and connect them with a Connector if both ports have the same interface type (defined in a Technical Interface Types Package). All components can be connected via a generic Technical Interface. Tasks can be connected via a Task Interface. Task Interfaces are special, because their Task Interface Types can have Channels, which are inherited from the [Universal Interface Model](/concepts/modeling_framework/uim.html). Therefore it is possible, the model communication flows between Tasks.

## How to model
TODO: Should be done if the Technical Viewpoint is completely realized in the plugin (and in a final state).

## Elements
### ![Technical Viewpoint](/images/technical_viewpoint/TechnicalViewpoint.png){:class="img-responsive"}Technical Viewpoint
Insert Text here.

### ![Technical Tracing Package](/images/technical_viewpoint/TechnicalTracingPackage.png){:class="img-responsive"}Technical Tracing Package
Insert Text here.
### ![Technical Interface Types Package](/images/technical_viewpoint/TechnicalInterfaceTypesPackage.png){:class="img-responsive"}Technical Interface Types Package
Insert Text here.
### ![Technical Package](/images/technical_viewpoint/TechnicalPackage.png){:class="img-responsive"}Technical Package
Insert text here.
### ![Software Package](/images/technical_viewpoint/SoftwarePackage.png){:class="img-responsive"}Software Package
Insert text here.
### ![Task Architecture Package](/images/technical_viewpoint/TaskPackage.png){:class="img-responsive"}Task Architecture Package
Insert text here.
### ![Execution Platform Package](/images/technical_viewpoint/ExecutionPackage.png){:class="img-responsive"}Execution Platform Package
Insert text here.

### ![Technical Context](/images/technical_viewpoint/TechnicalContext.png){:class="img-responsive"}Technical Context
Insert text here.
### ![Technical Actor](/images/technical_viewpoint/TechnicalActor.png){:class="img-responsive"}Technical Actor
Insert text here.

### ![Technical Component](/images/technical_viewpoint/TechnicalComponent.png){:class="img-responsive"}Technical Component
Insert text here.
### ![Software Component](/images/technical_viewpoint/SoftwareComponent.png){:class="img-responsive"}Software Component
Insert text here.
### ![Mechanical Component](/images/technical_viewpoint/MechanicalComponent.png){:class="img-responsive"}Mechanical Component
Insert text here.
### ![Mechatronic Component](/images/technical_viewpoint/MechatronicComponent.png){:class="img-responsive"}Mechatronic Component
Insert text here.
### ![Electronic Component](/images/technical_viewpoint/ElectronicComponent.png){:class="img-responsive"}Electronic Component
Insert text here.
### ![Task Architecture](/images/technical_viewpoint/TaskArchitecture.png){:class="img-responsive"}Task Architecture
Insert text here.
### ![Task Component](/images/technical_viewpoint/TaskComponent.png){:class="img-responsive"}Task Component
Insert text here.
### ![Execution Platform](/images/technical_viewpoint/ExecutionPlatform.png){:class="img-responsive"}Execution Platform
Insert text here.
### ![Execution Component](/images/technical_viewpoint/ExecutionComponent.png){:class="img-responsive"}Execution Component
Insert text here.
### ![Communication Component](/images/technical_viewpoint/CommunicationComponent.png){:class="img-responsive"}Communication Component
Insert text here.

### ![Technical Interface](/images/technical_viewpoint/TechnicalInterface.png){:class="img-responsive"}Technical Interface
Insert text here.
### ![Task Interface](/images/technical_viewpoint/TaskInterface.png){:class="img-responsive"}Task Interface
Insert text here.

### ![Channel](/images/universal_interface_model/Channel.png){:class="img-responsive"}Channel
Insert text here.

## Diagrams
### ![Technical Tracing Map](/images/diagrams/map.png){:class="img-responsive"}SpesML Technical Tracing Map
### ![TechnicalToLogical Matrix](/images/diagrams/matrix.png){:class="img-responsive"}SpesML TechnicalToLogical Matrix
### ![TechnicalToRequirement Matrix](/images/diagrams/matrix.png){:class="img-responsive"}SpesML TechnicalToRequirement Matrix
### ![Technical Internal Component Diagram](/images/diagrams/composite_structure.png){:class="img-responsive"}SpesML Technical Internal Component Diagram