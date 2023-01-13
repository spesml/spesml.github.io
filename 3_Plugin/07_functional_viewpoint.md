---
layout: default
title: Functional Viewpoint
nav_order: 7
parent: SpesML Plugin
permalink: /plugin/functional_viewpoint.html
---
# ![Functional Viewpoint](/images/functional_viewpoint/FunctionalViewpoint.png){:height="30px" width="30px"}{:class="img-responsive"}SpesML Plugin - Functional Viewpoint

## Overview

The _Functional Viewpoint_ contains three model types that can be used to describe the desired functionality of a system on a _system_ level (i.e., primarily from the perspective of external actors such as users or external systems).

In the center of the Functional Viewpoint is the concept of _system functions_. A system function describes a coherent set of interactions between a system and its external actors. The granularity of a system function is comparable to that of a [Use Case](https://en.wikipedia.org/wiki/Use_case). A system with several system functions can be called a _multifunctional system_. In general, system functions describe system behavior, which is largely independent of each other, however, system functions may also influence each other in specific cases. In the Functional Viewpoint, these influences are modeled by so-called _mode channels_ between system functions.  

The Functional Viewpoint then consists of three model types:

- **Functional Black-box Model**: Contains all system functions and structures them in a hierarchy
- **Functional White-box Model**: Describes the decomposition of one particular system function into a set of related white-box functions
- **Mode Model**: Describes operational states of the system. These operational states can be referenced in mode channels that describe dependencies between system functions.

## Method

System functions structure and formalize the functional requirements of a system. An engineer can either start from existing functional requirements and structure them according to system functions or, start from a set of desired system functions and then specify detailed requirements for them. In a second step, the engineer may decompose system functions into a set of connected white-box functions to assign smaller units of functionality to logical components that satisfy the functionality specified by a white-box function. Besides specifying system functions, an engineer can also specify distinct modes of operations that a system may be in (called *system modes*). System modes can be influenced by behavior specified in system functions. On the other hand, a change in a system mode can also influence the behavior of system functions.  

The following figure illustrates these relations:
![Functional Architecture Concept](/images/functional_viewpoint/functional-architecture-concept.png){:width="500" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><em>Elements of the Functional VP and their relations to elements of other viewpoints</em></div>


## Structure

The different models of the Functional Viewpoint create a functional view of a system that is structured in the Containment Tree of a project. A top-level node called `FunctionalView` contains all elements of this view (see figure below). 

![Elements of the Functional View in the Containment Tree](/images/functional_viewpoint/containment-tree.png){:width="400" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><em>Elements of the Functional View in the Containment Tree</em></div>

Below this node, there are the following specific subnodes:

- **Elements -> System Functions**: This package contains all _system function_ elements. The functional white-box model of each system function is located below the system function element.
- **Elements -> White-box Functions**: This package contains all _white-box function_ elements.
- **System**: This package contains the functional black-box model and the mode model of the system.
- **Functional Context**: This package contains the top-level view of the functional viewpoint and contains a diagram of the system under development in the context of its surrounding context functions.


![Elements of the Functional VP in the Containment Tree](/images/functional_viewpoint/containment-tree-expanded.png){:width="500" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><em>Elements of the Functional VP in the Expanded Containment Tree</em></div>

Tracing information is gathered in the `Functional Tracing Package`, consisting of traceability matrices and impact maps.

## How to Model

### How to create System Functions

To specify a system function with inputs and outputs, follow these steps:

1. Navigate to the `System Functions` folder under `FunctionalView -> Elements` (or create it if it does not exist)

2. Right-click on the folder and select *Create Element*. A dialog will open in which you can select elements you want to create. Select *Function*:  
  
      ![Select Element](/images/functional_viewpoint/create_function_select.png){:width="400" :class="img-responsive"}  

3. You are asked to choose a name for the system function:
      
      ![Name Element](/images/functional_viewpoint/create_function_name.png){:width="400" :class="img-responsive"} 

4. To add inputs and outputs to the system function, right-click on the system function, select *Create Element*, and select *Functional Interface* 

      ![Add Interface](/images/functional_viewpoint/create_interface.png){:width="400" :class="img-responsive"} 

5. Give the created port a name.

6. Assign a type to the port by selecting a defined type in the *Type property* field ([see here how to create types](/plugin/data_types.html)).
    
     ![Add Type](/images/functional_viewpoint/create_type.png){:width="400" :class="img-responsive"} 

7. Decide whether the port is an input or output port of the system function. Set the *Is Conjugated* property to `true` if the port is an input and to `false` if it is an output.

     ![Add Direction](/images/functional_viewpoint/create_direction.png){:width="300" :class="img-responsive"} 



### How to add a System Functions to a Functional Black-box Model

To create a functional black box model of a system, you can start by following these steps:

1. Navigate to the function in the containment tree, for which you want to model the functional black-box model (usually, this is the system function marked as *[system under development](#functional-context)*).

2. Right-click on this function and select *Create Diagram*:  
  
      ![Create Diagram](/images/functional_viewpoint/create_diagram.png){:width="400" :class="img-responsive"}  
  
3. A dialog will open in which you can select the kind of diagram you want to create. Select *SpesML Functional Internal Function Diagram*:  
  
      ![Select Diagram](/images/functional_viewpoint/create_diagram_select.png){:width="300" :class="img-responsive"}  
  
4. Another dialog will open that lets you select the elements of the function that you immediately want to display in the new diagram. For our function, we can select which of the interfaces we want to see in the diagram. Keep all of them selected and click *OK*:  
  
      ![Create Diagram Ports](/images/functional_viewpoint/create_diagram_ports.png){:width="500" :class="img-responsive"}  
  
5. The new diagram will open in the editor. It contains only the elements we selected in the previous dialog - in our case the ports of the function.

6. You can add system functions to the diagram by dragging the functions from the containment tree and dropping them into the diagram.

7. Specify the function as a *system function* by setting the *Function type* property to `System Function`.

      ![Set System Function](/images/functional_viewpoint/function-type.png){:width="300" :class="img-responsive"}  

8. To display the interfaces of the new part, select the part and click on *Display all Ports*:  
  
      ![Display all ports](/images/functional_viewpoint/create_diagram_parts_ports.png){:width="400" :class="img-responsive"}  
  
9. Connections between interfaces are created similarly: Select the port of an interface you want to connect to and click on *Connector* in the menu next to the port:  
  
      ![Create Diagram Connections](/images/functional_viewpoint/create_diagram_connections.png){:width="400" :class="img-responsive"}  
  
10. Your cursor will become the connector tool with which you can easily navigate to the target port for the connection:  
  
      ![Create Diagram Connection](/images/functional_viewpoint/create_diagram_connection.png){:width="400" :class="img-responsive"}  
  
11. Using these mechanisms, you can create the functional architecture of the system:  
  
      ![Functional Architecture Window Lifter](/images/functional_viewpoint/system-function-hierarchy.png){:width="500" :class="img-responsive"}


### How to create White-box Functions

To decompose a system function into a set of white box functions, follow these steps:

1. Creating white-box functions works exactly the same as [creating system functions](#how-to-create-system-functions). However, we recommend creating the white-box functions in a separate folder called *White-Box Functions* (or even in another sub-folder named after the system function for which the white-box function is created).

  ![Create White-Box Function](/images/functional_viewpoint/create_wb_function.png){:width="300":class="img-responsive"}  

2. Navigate to the system function in the containment tree, for which you want to specify the functional white-box model.

3. Right-click on the system function and select *Create Diagram*:  
  
      ![Create Diagram](/images/functional_viewpoint/create_diagram.png){:width="400" :class="img-responsive"}  
  
4. A dialog will open in which you can select the kind of diagram you want to create. Select *SpesML Functional Internal Function Diagram*:  
  
      ![Select Diagram](/images/functional_viewpoint/create_diagram_select.png){:width="300" :class="img-responsive"}  
  
5. Another dialog will open that lets you select the elements of the function that you immediately want to display in the new diagram. For our function, we can select which of the interfaces we want to see in the diagram. Keep all of them selected and click *OK*:  
  
      ![Create Diagram Ports](/images/functional_viewpoint/create_diagram_ports.png){:width="500" :class="img-responsive"}  
  
6. The new diagram will open in the editor. It contains only the elements we selected in the previous dialog - in our case all ports of the function.

7. You can add white-box functions to the diagram by dragging the functions from the containment tree and dropping them into the diagram.

8. Specify the function as a *white-box function* by setting the *Function type* property to `Whitebox Function`.

      ![Set White-box Function](/images/functional_viewpoint/create_wb_function_property.png){:width="300" :class="img-responsive"}  

9. To display the interfaces of the new white-box function, select the function and click on *Display all Ports*:  
  
      ![Display all ports](/images/functional_viewpoint/create_diagram_parts_ports.png){:width="500" :class="img-responsive"}  
  
10. Connections between interfaces are created similarly: Select the port of an interface you want to connect to and click on *Connector* in the menu next to the port:  
  
      ![Create Diagram Connections](/images/functional_viewpoint/create_diagram_connections.png){:width="500" :class="img-responsive"}  
  
11. Your cursor will become the connector tool with which you can easily navigate to the target port for the connection:  
  
      ![Create Diagram Connection](/images/functional_viewpoint/create_diagram_connection.png){:width="500" :class="img-responsive"}  
  
12. Using these mechanisms, you can create a *functional white-box model* for a system function:  
  
      ![Functional White Box Model](/images/functional_viewpoint/wb-model.png){:width="500" :class="img-responsive"}



### How to create a Mode Model
To create a mode model of a system, you can start by following these steps:

1. Navigate to the function in the containment tree, for which you want to model the mode model (usually, this is the system function marked as *[system under development](#functional-context)*).

2. Right-click on this function and select *Create Element*. A dialog will open in which you can select the kind of element you want to create. Select *Mode Model*:  
  
      ![Select Element](/images/functional_viewpoint/create_mm_element.png){:width="400" :class="img-responsive"}  

3. You are asked to choose a name for the element. You may simply call this element *mode model*:
      
      ![Name Element](/images/functional_viewpoint/create_mm_name.png){:width="300" :class="img-responsive"} 
 
4. Right-click on the *mode model* element and select *Create Diagram* to create a *SpeML State Machine Diagram*:  
  
      ![Create Diagram](/images/functional_viewpoint/create_sm_diagram.png){:width="300":class="img-responsive"}  
  
5. The state machine will open in the editor. Specify the mode model by [creating a state machine](/plugin/state_machines.html). 

## Elements

### ![Functional Viewpoint](/images/functional_viewpoint/FunctionalViewpoint.png){:class="img-responsive"}Functional Viewpoint
This is the top-level structuring element of the Functional Viewpoint; it can contain other structuring elements ('Interface Types' Package, `Functional Elements` Package, or Functional Tracing Package).

There is exactly one Functional Viewpoint in a SpesML project.

### ![Functional Tracing Package](/images/functional_viewpoint/FunctionalTracingPackage.png){:class="img-responsive"}Functional Tracing Package
The `Functional Tracing Package` contains traceability matrices and impact maps. It especially contains a diagram for tracing [functions](#function) to [requirements](/plugin/requirements_viewpoint.html#requirement)
 
### ![Functional Interface Types Package](/images/functional_viewpoint/FunctionalInterfaceTypesPackage.png){:class="img-responsive"}Functional Interface Types Package
The `Functional Interface Types Package` contains all [Functional Interface Types](#functional-interface-type)

### ![Functional Package](/images/functional_viewpoint/FunctionalPackage.png){:class="img-responsive"}Functional Package
The `Functional Package` contains all elements of the Functional Viewpoint including [System Functions](/concepts/modeling_framework/functional_viewpoint.html#system-function), [White-box Functions](/concepts/modeling_framework/functional_viewpoint.html#white-box-functions), [Functional Actors](#functional-actor).


### ![Functional Context](/images/functional_viewpoint/FunctionalContext.png){:class="img-responsive"}Functional Context
The Functional Context represents the top-level view of the system under development. It contains a single [system function](#function) that represents the system under development and that must be marked as such by setting the property `system under development to `yes` (see below).

![Marking a system function as *system under development*](/images/functional_viewpoint/sud-property.png){:width="400" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><em>Marking a system function as *system under development*</em></div>

Additionally, the Functional Context contains a number of [Functional Actors](#functional-actor) and [external functions](#function) that represent elements of the context. 
A function can be defined as external by changing the property `external` from `no` to `yes` (see below). 

![Marking a function as *external* function](/images/functional_viewpoint/external-property.png){:width="400" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><em>Marking a function as *external* function</em></div>

The root function that represents the system under development contains a [Functional Internal Function Diagram](#functional-internal-function-diagram), which contains all system functions of the SuD. 

### ![Functional Actor](/images/functional_viewpoint/FunctionalActor.png){:class="img-responsive"}Functional Actor
Functional Actors represent human users in the [Functional Context](#functional-context) with which the system under development is interacting at runtime. 

### ![Function](/images/functional_viewpoint/Function.png){:class="img-responsive"}Function
The *Function* is the central element of the functional viewpoint. After creating a `Function` element, the developer has to decide whether the function is a [System Function](/concepts/modeling_framework/functional_viewpoint.html#system-function) or a [White-box Function](/concepts/modeling_framework/functional_viewpoint.html#white-box-functions). This can be done by setting the property `Function type` (see below).

![Property `Function type`](/images/functional_viewpoint/function-type.png){:width="400" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><em>By setting the property `Function type`, a function can either be a system function or a white-box function</em></div>


### ![Function Part](/images/functional_viewpoint/FunctionPart.png){:class="img-responsive"}Function Part
Functions (i.e., system functions and white-box functions) can be decomposed into a set of smaller interconnected functions. Any `Function` can become a `Function Part` by dragging it to a [Functional Internal Function Diagram](#functional-internal-function-diagram) (see below). Note that system function decomposition is quite different from white-box function decomposition (as described in the [Functional Viewpoint concept](/concepts/modeling_framework/functional_viewpoint.html)).  

![`Functional parts`](/images/functional_viewpoint/system-function-hierarchy.png){:width="700" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><em>A system function is decomposed into three system functions, which become `Functional Parts` of the decomposed system function.</em></div>

### ![Functional Interface Type](/images/functional_viewpoint/FunctionalInterfaceType.png){:class="img-responsive"}Functional Interface Type
This element is based on a *SysML Interface Block* with a dedicated stereotype that allows defining where the element can be placed and other specifications.
A Functional Interface Type is used to specify the type of a [Functional Interface](#functional-interface). It needs to be defined separately in a [Functional Interface Types Package](#functional-interface-types-package) and can then be used to fill the *Type* property of a [Functional Interface](#functional-interface).
A Functional Interface Type can either contain a Value Property (e.g., a specific enumeration) or a [Channel](#channel) (or multiple ones). 

### ![Functional Interface](/images/functional_viewpoint/FunctionalInterface.png){:class="img-responsive"}Functional Interface
This element is based on a *SysML Proxy Port* with a dedicated stereotype that allows defining where the element can be placed and other specifications.
A Functional Interface is used to connect different functional elements generically. 
It can be specified further by using [Functional Interface Types](#functional-interface-type) and [Channels](#channel) to model the connection and information flow between the elements (via channels).
A Functional Interface is nothing more than a port that can be attached to a [function](#function). If another function has also such a port/interface with the same [Functional Interface Type](#functional-interface-type)], the user can connect these two ports with a *Connector* line.

### ![Channel](/images/universal_interface_model/Channel.png){:class="img-responsive"}Channel
This element is based on a *SysML Flow Property* with a dedicated stereotype that allows for defining the flow direction and other specifications. Its concept is explained in the [Universal Interface Model](/concepts/modeling_framework/uim.html). It can be added as an element to a [Functional Interface Type](#functional-interface-type). Channels enable signal/information transport between elements that are connected with an interface connection that has such an interface type (with a channel). A channel has a type (the type of the transported signal/information), which can be any pre-defined basic data type or a new user-defined data type (see [Data Types](/plugin/data_types.html)).

## Diagrams

### ![Functional Impact Map](/images/diagrams/map.png){:class="img-responsive"}SpesML Functional Impact Map
This relation map shows [Functions](#function) and what elements from the [Logical Viewpoint](/plugin/technical_viewpoint.html) are tracing these elements. By default, all Functions are shown but it is also possible to drag & drop a single Function to the relation map to show only the particular relationships.

### ![Functional Tracing Map](/images/diagrams/map.png){:class="img-responsive"}SpesML Functional Tracing Map
This relation map shows [Functions](#function) and to what [Requirements](https://spesml.github.io/plugin/requirements_viewpoint.html#requirement) these elements trace. By default, all Functions are shown but it is also possible to drag & drop a single Function to the relation map to show only the particular relationships.

### ![FunctionToRequirement Matrix](/images/diagrams/matrix.png){:class="img-responsive"}SpesML FunctionToRequirement Matrix
This diagram can be used to create and visualize trace relations between [functions](#function) and [requirements](/plugin/requirements_viewpoint.html#requirement). Possible trace relations are [*satisfy*](/concepts/modeling_framework/requirements_viewpoint.html#tracing-relationships) and [*requires*](/concepts/modeling_framework/requirements_viewpoint.html#tracing-relationships)

### ![Functional Internal Function Diagram](/images/diagrams/composite_structure.png){:class="img-responsive"}SpesML Functional Internal Function Diagram
This diagram is based on a *UML Composite Structure Diagram/SysML Internal Block Diagram* and provides a reduced diagram toolbar related to SpesML. Note that intentionally [Functional Parts](#functional-part) cannot be created using the diagram toolbar. Instead, it is recommended to create these elements by dragging/dropping a Function to the diagram.

## Modeling Rules (Well-formedness Rules)

### Functional Context

- The functional context must include exactly one system function that represents the SuD. 

### System Functions

- System functions must have at least one output port connected to an output port of the overall SuD or at least one input port connected to an input port of the overall SuD.
- _Recommendation:_ A system function models behavior, so the name should begin with a verb (e.g., controlWindows)

### System Function Hierarchies

- There exists exactly one root system function, the SuD

### White-Box Functions

- Each functional white-box model must be related to exactly one system function.
- Each system function must be related to at most one functional white-box model.
- The interface of a system function (i.e., inputs and outputs) must be reflected in its related functional white-box model, i.e., each input and output port of the system function must also be a _free_ input or output port in the functional white-box model (i.e., a port without any flow property). 
- Each white-box function must be related to at most one logical component that implements this white-box function.

### Mode Model

- There is at most one mode model per system.
- Each value that can be sent over a mode channel (i.e., a channel between system functions in the functional black-box model) must have a corresponding state in the mode model.
- Transitions in the mode model do not have any guards or actions as they simply define potential sequences of modes.
- A mode model has an initial state but no final state. 


