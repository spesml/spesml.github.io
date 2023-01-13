---
layout: default
title: Logical Viewpoint
nav_order: 8
parent: SpesML Plugin
permalink: /plugin/logical_viewpoint.html
---
# ![Logical Viewpoint](/images/logical_viewpoint/LogicalViewpoint.png){:height="30px" width="30px"}{:class="img-responsive"}SpesML Plugin - Logical Viewpoint

## Overview
In order to realize the desired functionality that is specified in the models of the functional viewpoint, the system under development is decomposed into a network of communicating logical components. The result is a logical architecture model which is independent of any technological constraints and which can be reused for multiple platforms.  
  
The Logical Components within the Logical Component Architecture provide a syntactic interface and a behavior specified by state automata. To compose the individual logical components to a logical architecture, the interfaces of the components are connected via connectors. Every such connection specifies which output channels will provide values to input channels.

## Method
The elements from the [functional architecture](https://spesml.github.io/plugin/functional_viewpoint.html) are mapped onto the components of the logical architecture. In general, this mapping is n:m. We recommend designing the functional white-box models already with the component architecture in mind, to achieve an n:1 mapping of elementary functions onto logical components.  
  
The platform-independent logical components of the Logical Component Architecture will be mapped to technical components of the [technical architecture](https://spesml.github.io/plugin/technical_viewpoint.html) in order to come to a platform-dependent implementation of the component.  
  
The following figure illustrates these relations:  
  
![Logical Architecture Concept](/images/logical_viewpoint/logical_architecture_concept.png){:class="img-responsive"}

## Structure
The Logical Architecture is modeled in the Logical Viewpoint folder of a SpesML Project. This diagram can be defined inside any logical (sub-)system (i.e. logical component).  
  
The following figure shows how the logical architecture of an exemplary window lifter system is embedded in the model:  
  
![Logical Architecture Window Lifter Containment](/images/logical_viewpoint/logical_architecture_window-lifter_containment.png){:class="img-responsive"}  
  
Inside the SpesML Logical Internal Component Diagram the modeler can use all *Logical Components* to model the actual Logical Component Architecture. The *Logical Interfaces* of these components can then be connected via *Connectors*. In the following figure you can see how the logical architecture of the window lifter system is modeled:  

![Logical Architecture Window Lifter](/images/logical_viewpoint/logical_architecture_window-lifter.png){:class="img-responsive"}

## How to model
To create the logical architecture of the exemplary Window Lifter above, you can start by following these steps:
1. Navigate to the component in the containment tree, for which you want to model the logical architecture.
2. Perform a right-click on this component and select *Create Diagram*:  
  
      ![Create Diagram](/images/logical_viewpoint/create_diagram.png){:class="img-responsive"}  
  
3. A dialog will open in which you can select the kind of diagram you want to create. Select *SpesML Logical Internal Component Diagram*:  
  
      ![Select Diagram](/images/logical_viewpoint/create_diagram_select.png){:class="img-responsive"}  
  
4. Another dialog will open that lets you choose, which elements of the selected components you immediately want to display in the new diagram. For our components, this means that we can select which of the interfaces we want to see represented in the diagram. Keep all of them selected and click *OK*:  
  
      ![Create Diagram Ports](/images/logical_viewpoint/create_diagram_ports.png){:class="img-responsive"}  
  
5. An editor window with the new diagram will open. It contains only those elements which were already selected in the previous dialog - in our case the three interfaces.
6. You can add Parts for the components that you need to model the logical architecture. To do so, drag the components from the containment tree and drop them into the diagram.
7. To display the interfaces of the new part, select the part and click on *Display all Ports*:  
  
      ![Display all ports](/images/logical_viewpoint/create_diagram_parts_ports.png){:class="img-responsive"}  
  
8. Connections between interfaces are created in a similar way: Select the port of an interface you want to connect and click on *Connector* in the menu next to the port:  
  
      ![Create Diagram Connections](/images/logical_viewpoint/create_diagram_connections.png){:class="img-responsive"}  
  
9. Your cursor will become the connector tool with which you can easily navigate to the target port for the connection:  
  
      ![Create Diagram Connection](/images/logical_viewpoint/create_diagram_connection.png){:class="img-responsive"}  
  
10. Using these mechanisms, you can create the logical architecture of the system:  
  
      ![Logical Architecture Window Lifter](/images/logical_viewpoint/logical_architecture_window-lifter.png){:class="img-responsive"}

## Elements

### ![Logical Viewpoint](/images/logical_viewpoint/LogicalViewpoint.png){:class="img-responsive"}Logical Viewpoint
This element is a *UML/SysML Package* with a dedicated stereotype that allows to define an adequate SpesML model structure and guides users by restricting what elements and diagrams can be created below this package.

### ![Logical Tracing Package](/images/logical_viewpoint/LogicalTracingPackage.png){:class="img-responsive"}Logical Tracing Package
This element is a *UML/SysML Package* with a dedicated stereotype that allows to define an adequate SpesML model structure and guides users by restricting what elements and diagrams can be created below this package. This package usually contains only tracing-related relation maps and matrixes.

### ![Logical Interface Types Package](/images/logical_viewpoint/LogicalInterfaceTypesPackage.png){:class="img-responsive"}Logical Interface Types Package
Insert text here

### Logical Test Case Package
Insert text here (TODO: add correct icon)

### ![Logical Package](/images/logical_viewpoint/LogicalPackage.png){:class="img-responsive"}Logical Package
Insert text here

### ![Logical Context](/images/logical_viewpoint/LogicalContext.png){:class="img-responsive"}Logical Context
Insert text here

### ![Logical Actor](/images/logical_viewpoint/LogicalActor.png){:class="img-responsive"}Logical Actor
Insert text here

### ![Logical Component](/images/logical_viewpoint/LogicalComponent.png){:class="img-responsive"}Logical Component

This element is based on a *SysML Block* with a dedicated stereotype that allows to define where the element. In addition, it restricts that only certain sub-elements can be created below a *Logical Component*. *Logical Components* provide a syntactic interface and a behavior specified by state automata. The syntactic interface can be specified by using [Logical Interface Types](https://spesml.github.io/plugin/logical_viewpoint.html#logical-interface-type) and [Channels](https://spesml.github.io/plugin/logical_viewpoint.html#channel).

### ![Logical Component Part](/images/logical_viewpoint/LogicalComponentPart.png){:class="img-responsive"}Logical Component Part
Insert text here

### Logical Component with Functions
Insert text here (TODO: add correct icon)

### Functional-Logical Adapter
Insert text here (TODO: add correct icon)

### Logical Test Case Component
Insert text here (TODO: add correct icon)

### ![Logical Interface Type](/images/logical_viewpoint/LogicalInterfaceType.png){:class="img-responsive"}Logical Interface Type
Insert text here

### ![Logical Interface](/images/logical_viewpoint/LogicalInterface.png){:class="img-responsive"}Logical Interface 
Insert text here

### ![Channel](/images/universal_interface_model/Channel.png){:class="img-responsive"}Channel
Insert text here

## Diagrams

### ![Logical Impact Map](/images/diagrams/map.png){:class="img-responsive"}SpesML Logical Impact Map
This relation map shows [Logical Component](https://spesml.github.io/plugin/logical_viewpoint.html#logical-component) and what elements from the [Technical Component](https://spesml.github.io/plugin/technical_viewpoint.html) are tracing to these elements. By default, all Logical Components are shown but it is also possible to drag & drop a single Logical Component to the relation map to show only the particular relationships.

### ![LogicalTracing Map](/images/diagrams/map.png){:class="img-responsive"}SpesML Logical Tracing Map
This relation map shows [Logical Component](https://spesml.github.io/plugin/logical_viewpoint.html#logical-component) and to what [Requirements](https://spesml.github.io/plugin/requirements_viewpoint.html#requirement) or [Functional Component](https://spesml.github.io/plugin/functional_viewpoint.html#function) these elements are tracing to. By default, all Logical Components are shown but it is also possible to drag & drop a single Logical Component to the relation map to show only the particular relationships.

### ![LogicalToFunctional Matrix](/images/diagrams/matrix.png){:class="img-responsive"}SpesML LogicalToFunctional Matrix
This matrix allows to create relationships between elements of the [Logical Viewpoint](https://spesml.github.io/plugin/logical_viewpoint.html#logical-viewpoint) and elements of the [Functional Viewpoint](https://spesml.github.io/plugin/functional_viewpoint.html).

### ![LogicalToRequirement Matrix](/images/diagrams/matrix.png){:class="img-responsive"}SpesML LogicalToRequirement Matrix
This matrix allows to create relationships between elements of the [Logical Viewpoint](https://spesml.github.io/plugin/logical_viewpoint.html#logical-viewpoint) and [Requirements](https://spesml.github.io/plugin/requirements_viewpoint.html#requirements).

### ![Logical Internal Component Diagram](/images/diagrams/composite_structure.png){:class="img-responsive"}SpesML Logical Internal Component Diagram
This diagram is based on a *UML Composite Structure Diagram/SysML Internal Block Diagram* and provides a reduced diagram toolbar related to SpesML. Note that intentionally [Logical Component Parts](https://spesml.github.io/plugin/logical_viewpoint.html#logical-component-part) cannot be created using the diagram toolbar. Instead, it is recommended to create these elements by dragging/dropping a Logical Component into the diagram.
