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

<div align="center">
![Technical Architecture Concept](/images/technical_viewpoint/TVP_Element_Overview.png){:class="img-responsive"}
<br>
<b>Figure 1:</b> 
<em>The concept of the implemented Technical Viewpoint.</em>
</div>
<br>

Regarding the development process, one step is to build the technical part of the system with all available components of the Technical Viewpoint (as far as needed). This should include at least one software subsystem. To model such a software subsystem with all its tasks and execution units is another step. Since the logical architetcure should be mapped next with the technical architecture, we recommend to already build the logical and now the technical architecture in a way that a 1:1 mapping is possible between logical and technical components. In addition, it simplifies the process when already in the Logical Viewpoint the pure software related logical components are separated from the other logical components. Then, it is easy to map them directly to a technical component representing the software subsystem and internally to the defined (software) tasks. However, we do not force a 1:1 mapping and it is also very usual that some technical components exist that do not have a match within the logical architecture, because they were not needed for a platform independent model but still contribute to the technical representation of an actual platform. After the mapping of logical to technical components (including the tasks), the final deployment needs to be done by mapping the tasks to the added execution units. It should be said that the development is not a strict step by step process, but usually building the technical architecture with components and elements of the software subsystem alternates or is in parallel with creating the matching between Logical and Technical Viewpoint and within the Technical Viewpoint regarding the deployment.

We recommend that the software subsystem is modeled on a separate (lower) granularity level ([theoretical concept](/concepts/modeling_framework/technical_viewpoint.html)). How to create a new granularity level is described [here](/plugin/general_concepts/granularity_transitions.html). However, we also allow in the tool that the internal software subsystem with its task architecture(s) and execution platform(s) can be modeled on the same level (just hierarchical), i.e., in the same MagicDraw project directly inside the [Software Component](#software-component) representing the software subsystem (see next section).

## Structure
The SpesML plugin has a separate folder for the Technical Viewpoint. Within this folder, it is possible to create folders for technical components ([Technical Package](#technical-package)), for technical interfaces types ([Technical Interface Types Package](#technical-interface-types-package)), and for technical tracing ([Technical Tracing Package](#technical-tracing-package)). Inside the Technical Tracing Package, all diagrams regading tracing can be created: [Technical Tracing Map](#technical-tracing-map), [TechnicalToLogical Matrix](#technicaltological-matrix), and [TechnicalToRequirement Matrix](#technicaltorequirement-matrix). Inside the Technical Interface Types Package, all possible interface types can be created that are usable for the interfaces between technical elements ([Technical Interface](#technical-interface)), and further Technical Interface Types Packages for a better organization. 

Inside the Technical Package, other Technical Packages can be created as well for better organization, but more important are the possibilities of the component creations. The generic [Technical Component](#technical-component) can be used for everything. If something more specific is needed, then the [Mechanical](#mechanical-component), [Electronic](#electronic-component) or [Mechatronic Components](#mechatronic-component) are available. In addition, the modeler can define a [Technical Context](#technical-context) inside a Technical Package. The Technical Context behaves like a Technical Component, but can already be placed in the Technical Viewpoint folder to create a starting point for the system and a possibility to represent the connected external systems and [Technical Actors](#technical-actor), which can be created in a Technical Package as well. To indicate that a component is representing an external (sub-)system, the corresponding "External" part property can be set to "Yes". 

Now, only the software subsystem is missing. For a better guidance, it is only possible to create first a [Software Package](#Software-Package) inside a Technical Package. Within a Software Package, the modeler can then create [Software Components](#software-component), which represent software subsystems. Task architectures and execution platforms are needed to define a software subsystem. Therefore, a Software Package can also contain [Task Architecture Packages](#task-architecture-package) and [Execution Platform Packages](#execution-platform-package) (besides more Software Packages). Inside the Task Architecture Packages, [Task Architectures](#task-architecture) and [Tasks](#task) can be created. Inside the Execution Platform Packages, [Execution Platforms](#execution-platform), [Execution Components](#execution-component) and [Communication Components](#communication-components) can be created.

<div align="center">
![Technical Elements Of The Plugin](/images/technical_viewpoint/TVP_elements_in_plugin.png){:class="img-responsive"}
<br>
<b>Figure 1:</b> 
<em>An example collection of all technical elements implemented inside the SpesML plugin.</em>
</div>
<br>

Every component (and the Technical Context) can have an own [Technical Internal Component Diagram](#technical-internal-component-diagram). Depending on the owner of the diagram, only some internal components can be placed in the diagram:
- The Technical Component as well as the Technical Context can contain Technical, Mechanical, Electronic, Mechatronic, and Software Components. 
- Mechatronic Components can contain Mechanical and Electronic Components. 
- Mechanical as well as Electronic Components can only contain internal components of their own type. 
- Software Components can contain Task Architectures and Execution Platforms. 
- Task Architectures can contain Tasks. 
- Execution Platforms can contain Execution Component and Communication Component. 

No behavior is modeled inside the Technical Viewpoint, which is why the composition of the components inside the (nested) diagrams is the main part of the Technical Viewpoint, together with the component mapping and the allocation of Tasks to Execution Components for the deployment.

To connect this composition of technical elements, it is possible to place interfaces (proxy ports) on every element and connect them with a Connector if both ports have the same interface type (defined in a Technical Interface Types Package). All elements can be connected via a generic [Technical Interface](#technical-interface), which is defined by its Technical Interface Type. Technical Interface Types can have [Channels](#channel), which are inherited from the [Universal Interface Model](/concepts/modeling_framework/uim.html). Therefore it is possible, the model communication flows between technical elements. An exception is the Task Architecture, because it does not make sense to connect Tasks in Task Architectures with the physical elements outside of Task Architectures. However, the Tasks themselves inside Task Architecture can be connected among each other again with Technical Interfaces.



## How to model
TODO: Should be done if the Technical Viewpoint is completely realized in the plugin (and in a final state).




## Elements
### ![Technical Viewpoint](/images/technical_viewpoint/TechnicalViewpoint.png){:class="img-responsive"}Technical Viewpoint
This element is a *UML/SysML Package* with a dedicated stereotype that allows to define an adequate SpesML model structure and guide users by restricting what elements and diagrams can be created below this package for the [Technical Viewpoint](/plugin/technical_viewpoint.html). This package usually contains only further packages to separate different purpose categories within the Technical Viewpoint. In addition, it is already possible to create a [Technical Context](#technical-context) as a starting point.

### ![Technical Tracing Package](/images/technical_viewpoint/TechnicalTracingPackage.png){:class="img-responsive"}Technical Tracing Package
This element is a *UML/SysML Package* with a dedicated stereotype that allows to define an adequate SpesML model structure and guide users by restricting what elements and diagrams can be created below this package for the [Technical Viewpoint](/plugin/technical_viewpoint.html). This package usually contains only tracing related relation maps and matrixes.

### ![Technical Interface Types Package](/images/technical_viewpoint/TechnicalInterfaceTypesPackage.png){:class="img-responsive"}Technical Interface Types Package
This element is a *UML/SysML Package* with a dedicated stereotype that allows to define an adequate SpesML model structure and guide users by restricting what elements and diagrams can be created below this package for the [Technical Viewpoint](/plugin/technical_viewpoint.html). This package usually contains only interface types that can be used for [Technical Interfaces](#technical-interface).

### ![Technical Package](/images/technical_viewpoint/TechnicalPackage.png){:class="img-responsive"}Technical Package
This element is a *UML/SysML Package* with a dedicated stereotype that allows to define an adequate SpesML model structure and guide users by restricting what elements and diagrams can be created below this package for the [Technical Viewpoint](/plugin/technical_viewpoint.html). This package usually contains only standard technical components like [Technical](#technical-component), [Mechanical](#mechanical-component), [Electronic](#electronic-component) and [Mechatronic Components](#mechatronic-component), and context-related elements like [Technical Contexts](#technical-context) and [Technical Actors](#technical-actor). In addition, it can also contain [Software Packages](#Software-Package), which are the entry point for software subsystems.

### ![Software Package](/images/technical_viewpoint/SoftwarePackage.png){:class="img-responsive"}Software Package
This element is a *UML/SysML Package* with a dedicated stereotype that allows to define an adequate SpesML model structure and guide users by restricting what elements and diagrams can be created below this package for the [Technical Viewpoint](/plugin/technical_viewpoint.html). This package usually contains only elements regarding the software subsystem. It includes [Software Components](#software-component), which represent software subsystems, and packages for further software subsystem related elements like [Task Architecture Packages](#task-architecture-package) and [Execution Platform Packages](#execution-platform-package).

### ![Task Architecture Package](/images/technical_viewpoint/TaskPackage.png){:class="img-responsive"}Task Architecture Package
This element is a *UML/SysML Package* with a dedicated stereotype that allows to define an adequate SpesML model structure and guide users by restricting what elements and diagrams can be created below this package for the [Technical Viewpoint](/plugin/technical_viewpoint.html). This package usually contains only elements to create a task archiecture for a software subsystem, i.e., [Task Architectures](#task-architecture) and [Tasks](#task).

### ![Execution Platform Package](/images/technical_viewpoint/ExecutionPackage.png){:class="img-responsive"}Execution Platform Package
This element is a *UML/SysML Package* with a dedicated stereotype that allows to define an adequate SpesML model structure and guide users by restricting what elements and diagrams can be created below this package for the [Technical Viewpoint](/plugin/technical_viewpoint.html). This package usually contains only elements to create a execution platform for a software subsystem, i.e., [Execution Platforms](#execution-platform), [Execution Components](#execution-component) and [Communication Components](#communication-components).


### ![Technical Context](/images/technical_viewpoint/TechnicalContext.png){:class="img-responsive"}Technical Context
Insert text here.

### ![Technical Actor](/images/technical_viewpoint/TechnicalActor.png){:class="img-responsive"}Technical Actor
This element is based on a *SysML Block* with a dedicated stereotype that allows to define where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
TODO

### ![Technical Component](/images/technical_viewpoint/TechnicalComponent.png){:class="img-responsive"}Technical Component
This element is based on a *SysML Block* with a dedicated stereotype that allows to define where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it. 
*Technical Components* provide a syntactic interface via [Technical Interfaces](#technical-interface).

### ![Software Component](/images/technical_viewpoint/SoftwareComponent.png){:class="img-responsive"}Software Component
This element is based on a *SysML Block* with a dedicated stereotype that allows to define where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
TODO

### ![Mechanical Component](/images/technical_viewpoint/MechanicalComponent.png){:class="img-responsive"}Mechanical Component
This element is based on a *SysML Block* with a dedicated stereotype that allows to define where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
TODO

### ![Mechatronic Component](/images/technical_viewpoint/MechatronicComponent.png){:class="img-responsive"}Mechatronic Component
This element is based on a *SysML Block* with a dedicated stereotype that allows to define where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
TODO

### ![Electronic Component](/images/technical_viewpoint/ElectronicComponent.png){:class="img-responsive"}Electronic Component
This element is based on a *SysML Block* with a dedicated stereotype that allows to define where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
TODO

### ![Task Architecture](/images/technical_viewpoint/TaskArchitecture.png){:class="img-responsive"}Task Architecture
This element is based on a *SysML Block* with a dedicated stereotype that allows to define where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
TODO

### ![Task](/images/technical_viewpoint/TaskComponent.png){:class="img-responsive"}Task
This element is based on a *SysML Block* with a dedicated stereotype that allows to define where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
TODO

### ![Execution Platform](/images/technical_viewpoint/ExecutionPlatform.png){:class="img-responsive"}Execution Platform
This element is based on a *SysML Block* with a dedicated stereotype that allows to define where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
TODO

### ![Execution Component](/images/technical_viewpoint/ExecutionComponent.png){:class="img-responsive"}Execution Component
This element is based on a *SysML Block* with a dedicated stereotype that allows to define where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
TODO

### ![Communication Component](/images/technical_viewpoint/CommunicationComponent.png){:class="img-responsive"}Communication Component
This element is based on a *SysML Block* with a dedicated stereotype that allows to define where the element can be placed and other specifications. In addition, it restricts that only certain sub-elements can be created below it.
TODO


### ![Technical Interface Type](/images/technical_viewpoint/TechnicalInterfaceType.png){:class="img-responsive"}Technical Interface Type
This element is based on a *SysML Interface Block* with a dedicated stereotype that allows to define where the element can be placed and other specifications.
TODO

### ![Technical Interface](/images/technical_viewpoint/TechnicalInterface.png){:class="img-responsive"}Technical Interface
This element is based on a *SysML Proxy Port* with a dedicated stereotype that allows to define where the element can be placed and other specifications.
TODO: can be specified by using [Technical Interface Types](#technical-interface-type) and [Channels](#channel).

### ![Channel](/images/universal_interface_model/Channel.png){:class="img-responsive"}Channel
This element is based on a *SysML Flow Property* with a dedicated stereotype that allows to define the flow direction and other specifications.



## Diagrams
### ![Technical Tracing Map](/images/diagrams/map.png){:class="img-responsive"}SpesML Technical Tracing Map
This relation map shows technical elements like Technical Components, Mechanical Components, etc. and to what [Requirements](/plugin/requirements_viewpoint.html#requirement), [Functional Component](/plugin/functional_viewpoint.html#function) or [Logical Components](/plugin/logical_viewpoint.html#logical-component) these elements are tracing to. By default, all technical elements are shown but it is also possible to drag & drop a single technical element to the relation map to show only the particular relationships.

### ![TechnicalToLogical Matrix](/images/diagrams/matrix.png){:class="img-responsive"}SpesML TechnicalToLogical Matrix
This matrix allows to create relationships between elements of the [Technical Viewpoint](/plugin/technical_viewpoint.html#technical-viewpoint) and elements of the [Logical Viewpoint](/plugin/logical_viewpoint.html#logical-viewpoint).

### ![TechnicalToRequirement Matrix](/images/diagrams/matrix.png){:class="img-responsive"}SpesML TechnicalToRequirement Matrix
This matrix allows to create relationships between elements of the [Technical Viewpoint](/plugin/technical_viewpoint.html#technical-viewpoint) and [Requirements](/plugin/requirements_viewpoint.html#requirements).

### ![Technical Internal Component Diagram](/images/diagrams/composite_structure.png){:class="img-responsive"}SpesML Technical Internal Component Diagram
This diagram is based on a *UML Composite Structure Diagram/SysML Internal Block Diagram* and provides a reduced diagram toolbar related to SpesML for the [Technical Viewpoint](/plugin/technical_viewpoint.html). Note that intentionally any technical components cannot be created using the diagram toolbar. Instead, it is recommended to create these elements by dragging/dropping a technical component to the diagram.

### ![TaskInstanceToExecution Allocation Matrix](/images/diagrams/matrix.png){:class="img-responsive"}TaskInstanceToExecution Allocation Matrix
This matrix allows to create relationships between [Tasks](#task) in [Task Architectures](#task-architecture) and [Execution Components](#execution-component) in [Execution Platforms](#execution-platform). This creates an allocation between Tasks and Execution Components that represents the deployment of these software tasks on these execution units. All of this happens on the instance level, meaning that every instance/part of a Task and an Execution Component can be allocated separately. To use this matrix, a scope needs to be set (above the matrix diagram). As the description at the bottom of the matrix diagrams indicates, the row scope should be the Task Architecture of the wanted Tasks and the column scope the Execution Platform of the wanted Execution Components.

### ![TaskTypeToExecution Allocation Matrix](/images/diagrams/matrix.png){:class="img-responsive"}TaskTypeToExecution Allocation Matrix
This matrix allows to create relationships between [Tasks](#task) in [Task Architectures](#task-architecture) and [Execution Components](#execution-component) in [Execution Platforms](#execution-platform). This creates an allocation between Tasks and Execution Components that represents the deployment of these software tasks on these execution units. All of this happens on the type level, meaning that only the defined types/blocks of a Task and an Execution Component can be allocated (instances of them cannot be allocated separately!). To use this matrix, a scope needs to be set (above the matrix diagram). As the description at the bottom of the matrix diagrams indicates, the row scope should be the package in which the wanted Tasks are defined and the column scope the package in which the wanted Execution Components are defined.

### ![PortToExecution Allocation Matrix](/images/diagrams/matrix.png){:class="img-responsive"}PortToExecution Allocation Matrix
This matrix allows to create relationships between [Technical Interfaces](#technical-interface) (ports) of [Tasks](#task) in [Task Architectures](#task-architecture) and [Technical Interfaces](#technical-interface) (ports) of [Execution Components](#execution-component) in [Execution Platforms](#execution-platform). This creates an allocation between Tasks ports and Execution Components ports, which supports the deployment of these software tasks on these execution units. To use this matrix, a scope needs to be set (above the matrix diagram). As the description at the bottom of the matrix diagrams indicates, the row scope should be the package in which the wanted Tasks ports are defined and the column scope the package in which the wanted Execution Components ports are defined.
