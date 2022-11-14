---
layout: default
title: Modeling Interfaces
nav_order: 3
parent: SpesML Plugin
permalink: /plugin/universal_interface_model.html
---

# Modeling Interfaces

## Overview
In all viewpoints (i.e. Functional VP, Logical VP, Technical VP) the available models allow to describe the interface of the respective system elements (i.e. functions, logical components, technical components).  In the SPES ML plugin, modeling the interfaces in all views follows the same method using the same concepts. The only difference is that the model elements have different names (e.g. "Functional Interface" vs. "Logical Interface").

## Method
### General
<div align="center">
<img src="../3_Plugin/images/universal_interface_model/spes_interface_model.png">
<br><b>Figure 1:</b> 
Model elements for interface, in brackets the names in the logical viewpoint as examples.
</div><br>

Figure 1 shows the modeling elements for the interfaces. 

* **Interface:** A system element (e.g. a logical component from the logical view or a (black-box/white-box) function from the functional view) owns one ore more interfaces. In the different views, the interfaces are named "Logical Interface", "Functional Interface", etc. An interface can be either a source interface (messages are flowing out of the owning system element) or a target interface (messages are flowing into the owning system element). To mark an interface as a target interface, the interface must be *conjugated*. 
* **Interface Type:** An interface is always typed. That means, it is associated with an interface type. Again, in the different views an interface type is termed "Logical Interfact Type", "Functional Interface Type" etc. An interface type must always be named and may only contain channels as sub-elements.
* **Channel:** The interface type describes what can flow out of a system element by the means of channels. Therefore each interface type owns one or more channels. Channels always are named and represent unidirectional communication from the source interface to the target interface. Although a channel has a direction, this direction must always be set to "out". this restriction makes it possible to clearly see which information is flowing in which direction.
* **Data Type:** Each channel again is typed with a data type, describing what kind of messages are exchanged via this channel. Details on data types can be found [here](https://spesml.github.io/plugin/data_types.html)
* **Connector:** Two interfaces may be connected using a connector, which describes that messages can flow between the interfases.

To specify that two system elements interact, their interfaces may be connected by *connectors*.

### Strong Causality
Strong causality modulo some output channels can be introduced by delaying the outputs of an interface. An interface can be delayed by
adding a value to the ```Initial Sequences for Delay``` property.  The ```Initial Sequences for
Delay``` property can only be given a value for interfaces where the conjugated
property is set to _false_, i.e., only output channels can be delayed. If the
property is given a value in an interface, then all channels represented by the port
are delayed. 

The sequences of messages initially communicated via the delayed channels is
defined by the value of the property ```Initial Sequences for Delay```. Values
of the property ```Initial Sequences for Delay``` are finite sequences of the
form _channel_ ```= ```_Expr_```;``` where _channel_ is the name of a channel and _Expr_ is an expression
evaluating to a value of the channel's type. The expression cannot
reference any variables. Every channel may be used on the left-hand side
at most once. If a channel is not used on the left-hand side at all, then
the empty sequence is initially communicated via the corresponding channel.  

### Composition
System elements are composed by connecting their interfaces with **connectors**. 
Two interfaces may only be connected via a connector if they have the same types and their directions match.
The directions of two interfaces match if one of the following conditions is satisfied:
1. Both interfaces are either conjugated or not conjugated but one interface is owned by the system element above in the composition hierarchy. This represents the situation where message are routed inside into to outside from a system element. 
2. One of the interfaces is conjugated and the other interface is not conjugated and both owning system elements are on the same level in the composition hierarchy.

## How to Model

### How to Create an Interface
1. Select an system element for which you want to create an interface in the containment tree  (e.g. a logical component). 
Model elements for interface, in brackets the names in the logical viewpoint as examples.

2. Right-click the system element and select "Create Element".
 
   <img src="../3_Plugin/images/universal_interface_model/spes_create_element.png" />
   
3. From the popup, choose the appropriate interface (e.g. "Logical Interface" for a logical component)

   <img src="../3_Plugin/images/universal_interface_model/spes_create_interface.png" />
   
4. Name the interface  

   <img src="../3_Plugin/images/universal_interface_model/spes_create_interface2.png" />

5. If the newly created interface represents an input interface, set the interface as conjugated. This can be done by opening the specification window for the newly created interface (Right-Click -> Specification) and setting the property "Is Conjugated" to true.

   <img src="../3_Plugin/images/universal_interface_model/spes_create_interface3.png" />

## Well-formedness Rules

### General Rules 
* Interfaces, Interface types, and channels must be named

### Interfaces
* System elements need to specify at least one interface
* Interfaces are required to have an interface type
* Channels have the direction "out"
* Channels need to have a data type, see [Data Types Documentation](https://spesml.github.io/plugin/data_types.html)

### Composition
* Connectors must only connect interfaces with same type.
* Connectors must always connect interfaces with matching directions (see above).
