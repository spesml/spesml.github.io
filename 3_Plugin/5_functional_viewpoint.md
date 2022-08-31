---
layout: default
title: Functional Viewpoint
nav_order: 5
parent: SpesML Plugin
permalink: /plugin/functional_viewpoint.html
---
# ![Functional Viewpoint](/images/functional_viewpoint/FunctionalViewpoint.png){:height="30px" width="30px"}{:class="img-responsive"}SpesML Plugin - Functional Viewpoint

## Overview

## Method

## Structure

The different models of the Functional Viewpoint are structured in the Containment Tree of a project. There is a top-level node called `Functional Viewpoint` that contains all elements of this viewpoint (see figure below). 

![Elements of the Functional VP in the Containment Tree](/images/functional_viewpoint/containment-tree.png){:width="400" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><em>Elements of the Functional VP in the Containment Tree</em></div>

Below this node, there are the following specific subnodes:

- **System Functions**: This package contains all _system function_ elements. The functional white-box model of each system function is located below the system function element.
- **White-box Functions**: This package contains all _white-box function_ elements.
- **System**: This package contains the functional black-box model and the mode model of the system.
- **Functional Context**: This package contains the top-level view of the functional viewpoint and contains a diagram of the system under development in the context of its surrounding external systems and actors.


![Elements of the Functional VP in the Containment Tree](/images/functional_viewpoint/containment-tree-expanded.png){:width="500" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><em>Elements of the Functional VP in the Expanded Containment Tree</em></div>

Tracing information is gathered in the `Functional Tracing Package`, consisting of traceability matrices and impact maps.

## How to Model

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
The Functional Context represents the top-level view of the system under development. It contains a single [system function](#function) that represents the system under development and that must be marked as such by setting the property `system under development` to `yes` (see below).

![Marking a system function as *system under development*](/images/functional_viewpoint/sud-property.png){:width="400" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><em>Marking a system function as *system under development*</em></div>

Additonaly, the Functional Context contains a number of [Functional Actors](#functional-actor) and [external functions](#function) that represent elements of the context. 
A function can be defined as external by changing the property `external` of this component from `no` to `yes` (see below). 

![Marking a function as *external* function](/images/functional_viewpoint/external-property.png){:width="400" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><em>Marking a function as *external* function</em></div>

The root function that represents the system under development contains a [Functional Internal Function Diagram](#functional-internal-function-diagram), which contains all system functions of the SuD. 

### ![Functional Actor](/images/functional_viewpoint/FunctionalActor.png){:class="img-responsive"}Functional Actor
Functional Actors represent human users in the [Functional Context](#functional-context) with which the system under development is interacting at runtime. 

### ![Function](/images/functional_viewpoint/Function.png){:class="img-responsive"}Function
The *Function* is the central element of the functional viewpoint. After creating a `Function` element, the developer has to decide whether the function is a [System Function](/concepts/modeling_framework/functional_viewpoint.html#system-function) or a [White-box Function](/concepts/modeling_framework/functional_viewpoint.html#white-box-functions). This can be done by setting the property `Function type` (see below).

![Property `Function type`](/images/functional_viewpoint/function-type.png){:width="400" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><em>By setting the property `Function type`, a function can either be a system function or a white-box function</em></div>


### ![Functional Part](/images/functional_viewpoint/FunctionPart.png){:class="img-responsive"}Functional Part
Functions (i.e., system functions and white-box functions) can be decomposed into a set of smaller interconnected functions. Any `Function` can become a `Functional Part` by dragging it to a [Functional Internal Function Diagram](#functional-internal-function-diagram) (see below). Note that system function decomposition is quite different from white-box function decomposition (as described in the [Functional Viewpoint concept](/concepts/modeling_framework/functional_viewpoint.html)).  

![`Functional parts`](/images/functional_viewpoint/system-function-hierarchy.png){:width="400" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><em>A system function is decomposed into three system functions, which become `Functional Parts` of the decomposed system function.</em></div>

### ![Functional Interface Type](/images/functional_viewpoint/FunctionalInterfaceType.png){:class="img-responsive"}Functional Interface Type
This element is based on a *SysML Interface Block* with a dedicated stereotype that allows defining where the element can be placed and other specifications.
A Functional Interface Type is used to specify the type of a [Functional Interface](#functional-interface). It needs to be defined separately in a [Functional Interface Types Package](#functional-interface-types-package) and can then be used to fill the *Type* property of a [Functional Interface](#functional-interface).
A Functional Interface Type can either contain a Value Property (e.g., a specific enumeration) or a [Channel](#channel) (or multiple ones). 

### ![Functional Interface](/images/functional_viewpoint/FunctionalInterface.png){:class="img-responsive"}Functional Interface
This element is based on a *SysML Proxy Port* with a dedicated stereotype that allows defining where the element can be placed and other specifications.
A Functional Interface is used to connect different functional elements generically. 
It can be specified further by using [Functional Interface Types](#functional-interface-type) and [Channels](#channel) to model the connection and information flow between the elements (via  channels).
A Functional Interface is nothing more than a port that can be attached to a [function](#function). If another function has also such a port/interface with the same [Functional Interface Type](#functional-interface-type)], the user can connect these two ports with a *Connector* line.

### ![Channel](/images/universal_interface_model/Channel.png){:class="img-responsive"}Channel
This element is based on a *SysML Flow Property* with a dedicated stereotype that allows for defining the flow direction and other specifications. Its concept is explained in the [Universal Interface Model](/concepts/modeling_framework/uim.html). It can be added as an element to a [Functional Interface Type](#functional-interface-type). Channels enable signal/information transport between elements that are connected with an interface connection that has such an interface type (with a channel). A channel has a type (the type of the transported signal/information), which can be any pre-defined basic data type or a new user-defined data type (see [Data Types](/plugin/data_types.html)).

## Diagrams

### ![Functional Impact Map](/images/diagrams/map.png){:class="img-responsive"}SpesML Functional Impact Map
This relation map shows [Functions](#function) and what elements from the [Logical Viewpoint](/plugin/technical_viewpoint.html) are tracing these elements. By default, all Functions are shown but it is also possible to drag & drop a single Function to the relation map to show only the particular relationships.

### ![Functional Tracing Map](/images/diagrams/map.png){:class="img-responsive"}SpesML Functional Tracing Map
This relation map shows [Functions](#function) and to what [Requirements](https://spesml.github.io/plugin/requirements_viewpoint.html#requirement) these elements trace. By default, all Functions are shown but it is also possible to drag & drop a single Function to the relation map to show only the particular relationships.

### ![FunctionToRequirement Matrix](/images/diagrams/matrix.png){:class="img-responsive"}SpesML FunctionToRequirement Matrix
This diagram can be used to create and visualize trace relations between [functions](#function) and [requirements](/plugin/requirements_viewpoint.html#requirement). Possible trace relations are [*satsify*](/concepts/modeling_framework/requirements_viewpoint.html#tracing-relationships) and [*requires*](/concepts/modeling_framework/requirements_viewpoint.html#tracing-relationships)

### ![Functional Internal Function Diagram](/images/diagrams/composite_structure.png){:class="img-responsive"}SpesML Functional Internal Function Diagram
This diagram is based on a *UML Composite Structure Diagram/SysML Internal Block Diagram* and provides a reduced diagram toolbar related to SpesML. Note that intentionally [Functional Parts](#functional-part) cannot be created using the diagram toolbar. Instead, it is recommended to create these elements by dragging/dropping a Function to the diagram.

