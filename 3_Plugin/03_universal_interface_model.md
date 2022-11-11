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
<div align="center">
<img src="../3_Plugin/images/universal_interface_model/spes_interface_model.png">
<br><b>Figure 1:</b> 
Model elements for interface, in brackets the names in the logical viewpoint as examples.
</div><br>

## How to model

## Elements






# Attic - to be integrated in the text above

## Modeling Elements

The above concepts are reflected by SPES ML model elements. As SPES ML builds upon SysML these are all SysML modeling elements. However, as SPES ML user you will never create the generic model elements listed below, but instead specific model elements for the different views. Nevertheless, keeping in mind how the theoretic concepts map to SysML modeling elements may be helpful, especially for those who are already familiar with SysML.

### Data Type
Data types in SPES ML are represented by SysML **Value Types**. 
A value type in SysML can be one of the following:
- **Primitive Value Type**, types which are values types predefined by SysML. 
- **Enumeration**, defining a set of value literals to choose from  (e.g. enumeration `Status` with enumeration literals `ON` and `OFF`)
- **Structured Type**, defining a type that consists of several attributes, each having a certain type and multiplicity (e.g. `Location` consisting of `x` and `y` each with type `Real`)

The predefined value types are `Integer`, `Real`, `String`, `Boolean`, `Complex`, and the predefined SI value types according to ISO-80000. The type `Integer` represents unbounded integer numbers and the type `Real` represents the 
mathematical concepts of real numbers. `String` and `Boolean` are defined as usual. The type `Complex` represents complex numbers, each consisting of a `realPart` and and `imaginaryPart`, 
both of type `Real`. For each SI unit quantity and each possible unit for the quantity, modelers can select a corresponding type for each attribute. Each quantity (e.g., length) can be measured using a unit (e.g, millimeter).
The possible multiplicities for attributes are `0`, `1`, `0..1`, `1..*`, and `*`. 

In MagicDraw, value types are directly created and modeled in the containment tree. 
Block Definition Diagrams are not used for the creation of value types.
For example, the following figure depicts an excerpt of a containment tree in MagicDraw.
The package `data` contains the enumeration `Direction` and the structured value types `Node` and `Screw`. 
The enumeration consists of the four enumeration literals `UP`, `DOWN`, `LEFT`, and `RIGHT`.
The structured value type `Node` has the two attributes `children` and `value`. 
The attribute `children` is of type `Node` and has the multiplicity `*`.
The attribute `value` is of type `Integer` and has the multiplicity `1`. Thus, a `Node` instance can be interpreted to be the node of a directed graph that has an `Integer` `value` and is connected via other nodes according to its `children` attribute. The structured value type `Screw` has the two attributes `length` and `diameter`. Both are of type `length[millimeter]`. The quantity is `length` and `millimeter` is the unit. 

<div align="center">
<img width="450" src="../../2_Concepts/3_ModelingFramework/images/universal_interface_model/valuetypes.png">
<br><b>Figure 5:</b> 
Definition of value types in the containment tree of a MagicDraw model.
</div><br>

### Channel
A channel in the universal interface model is represented by a SysML **flow
property**. A flow property must be typed with an **interface block**. The name of a flow property and its
corresponding interface block define the channel's name. The type of the flow
property models the channel's type. In SpesML, the direction of all flow
properties must be *out*. Whether the channels are used as an input or an output
channel by a system element is determined by the proxy port that is typed with
the interface block containing the channel. In SpesML, each interface block has
a name and consists of an arbitrary number of flow properties. Each flow
properties of each interface block defines a channel.

In MagicDraw, interface blocks are directly created and modeled in the
containment tree. Block Definition Diagrams are not used for the creation of
interface blocks. For instance, the following figure depicts the interface block
`MyInterface` containing the two flow properties `channel1` and `channel2`. The
flow property `channel1` is of type `String` and the flow property `channel2` is
of type `Integer`. Conceptually, the interface block can be interpreted to
define the two channels `MyInterface.channel1` and `MyInterface.channel2`. 

<div align="center">
<img width="200" src="../../2_Concepts/3_ModelingFramework/images/universal_interface_model/interfaceblock.png">
<br><b>Figure 6:</b> 
An interface block with two flow properties defines two channels.
</div><br>

Note that an interface block in SPES ML may only contain channels and must own at least one channel.

### Sub-Interface
Sub-interfaces of system elements are modeled with **proxy ports**. Each proxy
port has a name and is typed with an interface block. As each interface block defines a set of
channels, an interface block can be conceptually interpreted to be a type of
sub-interfaces. Each proxy port must be owned by a block (described in detail
below).

By default, all the channels of the subinterface defined by a proxy port are
output channels of the system element modeled by the block that owns the port.
In order to represent the inverse of the syntactic sub-interface represented by
a proxy port, the attribute **Is Conjugated** of the proxy port is set to
_true_. This is visually displayed by a `~` symbol as a prefix to the name of
the port. Thus, if the conjugated property of a proxy port is set to _true_,
then it models a sub-interface solely containing input channels.

Strong causality modulo some output channels can be introduced by delaying the
outputs of the channels (cf. Formal Foundations sections). To this effect, the
SpesML language profile adds the **Initial Sequences for Delay** property to the
SysML of MagicDraw. All channels represented by a proxy port can be delayed by
adding a value to the ```Initial Sequences for Delay``` property. The property
can be found in the specification of proxy ports. The ```Initial Sequences for
Delay``` property can only be given a value for ports where the conjugated
property is set to _false_, i.e., only output channels can be delayed. If the
property is given a value in a port, then all channels represented by the port
are delayed. 

The sequences of messages initially communicated via the delayed channels is
defined by the value of the property ```Initial Sequences for Delay```. Values
of the property ```Initial Sequences for Delay``` are finite sequences of the
form _flowProp_ ```= ```_Expr_```;``` where _flowProp_ is the name of a flow
property of the port (representing a channel) and _Expr_ is an expression
evaluating to a value of the flow property's type. The expression cannot
reference any variables. Every flow property may be used on the left-hand side
at most once. If a flow property is not used on the left-hand side at all, then
the empty sequence is initially communicated via the corresponding channel.   

For example, the figure below depicts an excerpt of the specification of the
proxy port ```p1```. The port is not conjugated. Thus, all of its flow
properties represent output channels. The initial outputs on the channels
corresponding to the flow properties are defined by the property ```Initial
Sequences```. In this case, the initial output on ```channel1``` is the sequence
```"Hello", "World"```.

For every cycle of connected parts (see below) there must be at least one delay.

<div align="center">
<img width="700" src="../../2_Concepts/3_ModelingFramework/images/universal_interface_model/portSpec.png">
<br><b>Figure 7:</b> 
A proxy port with initial sequences.
</div><br>


### Remark: Direction of Flow Properties

We restrict each interface block to only have flow properties with direction
_out_ (see above). The direction of a channel is determined by the value of the
conjugated property of the corresponding proxy port. The rationale for this
restriction is to enable the modeler to easily grasp which proxy ports
represent inputs and which represent outputs. In the following example, the
system element (type) `WindowLifterController` has three channels, one input
channel `temperature` and two output channels for controlling the front and rear
window actuator.


<div align="center">
<img width="900" src="../../2_Concepts/3_ModelingFramework/images/universal_interface_model/WindowLifterSystem.jpg">
<br><b>Figure 8:</b> 
An IBD modeling a window lifter system.
</div><br>


### Syntactic Interface

The syntactic interface of a system element is defined by its sub-interfaces, that means its (possibly conjugated) proxy ports with associated interface blocks.
In SpesML, a syntactic interface is always assembled from sub-interfaces. 
In the extreme case, a system element may only possess a single sub-interface. 

### System Element
System Elements (modeling functions, logical components or technical components respectively) are represented as SysML **blocks** as well as **parts**.
The formal foundations of system elements do not distinguish between the definitions of a system element and their roles or instances. 

In SysML, this distinction is made:
- A **block** defines a type of a system element. With this, it defines the interface and the behavior of all of its instances.   
    - Each block owns at least one proxy port. Each proxy port defines a sub-interface of the system elements modeled by the block. 
    - A block models composed system elements if it owns at least one part property. Then, it is called composed. Otherwise, it models atomic system elements and is called atomic. The part properties model the subelements of the system elements modeled by the block. Each part has a name and a type. The name of the part represents the name of the subelement of the system elements modeled by the block. The type of a part is a block. With this, each part can be interpreted to be an instance of a block.  
    - Composed Blocks must own exactly one Internal Block Diagram that has the same name as the block. The Internal Block Diagrams shows the connections between the ports of the parts of the block. Thus, it models the connections between the subelements of the system elements modeled by the block. Blocks modeling atomic system elements must not own Internal Block Diagrams.  
    - An atomic block may own *value properties*. Each value property has a name and a type. These properties represent the internal data state of instances of the block. Control states and behavior referencing the data states can be added, for instance, via state machines as discussed in one of the following sections.
    - A block can be used in different roles, e.g., a window-lifter-controler could be used in the roles *front-window-controler* and *back-window-controler*.
- A **part** represents a system element in a specific role (e.g. *the window-lifter-controler* or the *back-window-controler* of a car). Communication relationships (via SysML connectors) are defined on the level of parts.
If two distinct system elements have the same interface and behavior, this is represented by one block and two distinct parts. Each of the parts is an instance of the block in a different role. On the other hand, all parts must have a block as type.


In MagicDraw, blocks are directly created and modeled in the containment tree.
Block Definition Diagrams are not used for the creation of blocks.
For instance, the following figure depicts the blocks `Block1`, `Block2`, `Block3` and the interface block `MyInterface`. The interface block has already been described above. 
The block `Block1` has the ports `p1` and `p2`. The type of both ports is the interface block `MyInterface`. In contrast to the port `p1`, the port `p2` is conjugated. 
Thus, the sub-interfaces of the instances of `block1` that are defined by the port `p1` solely contain output channels.
In contrast, the sub-interface modeled by `p2` solely contains input channels. 
In the containment tree, this is indicated by the keywords `in` and `out` that appear in front of the ports' names.
The ports of the blocks `Block2` and `Block3` are defined analogously. The blocks `Block2` and `Block3` are atomic as they do not contain parts or Internal Block Diagrams.
In contrast, the block `Block1` is composed as it contains the two parts `part1` and `part2` as well as the IBD `Block1`.
The part `part1` is of type `Block2` whereas the part `part2` is of type `Block3`. 
The block `Block2` owns the value property `counter` of type `Integer`. Instances of `Block2` have concrete `Integer` values assigned to this property, which is accessible via its name `counter`. The Internal Block Diagram owned by `Block1` composes the parts of the block as described in the following section.

<div align="center">
<img width="250" src="../../2_Concepts/3_ModelingFramework/images/universal_interface_model/blocks.png">
<br><b>Figure 9:</b> 
Definition of blocks modeling system elements.
</div><br>

Each part and each block is required to have a name.

### Composition
System elements are composed by connecting their proxy ports with SysML **connectors**. 
Two ports may only be connected via a connector if they have the same types and their directions match.
The directions of two ports match iff one of the following conditions is satisfied:
1. One port is owned by the block and the other port is owned by a part and both ports are conjugated.
2. One port is owned by the block and the other port is owned by a part and both ports are not conjugated.
3. Both ports are owned by parts and one of the ports is conjugated and the other port is not conjugated.

The first condition corresponds to the case where messages are transmitted from an input port of the block to an input port of a part.
The seconds condition corresponds to the case where messages are transmitted from an output port of a part to an output port of a block.
The third condition corresponds to the case where messages are transmitted from an output port of a part to an input port of a part. 

For instance, the following figure depicts the Internal Block Diagram of the system element `Block1`.
It has the two parts `part1` and `part2` of types `Block2` and `Block3`. The input port `p2` of `Block1`
is connected to the input port `p7` of `part2`. This corresponds to the first condition for matching directions.
The connection between the ports `p4` of `part1` and `p1` of `Block1` corresponds to the second condition.
Similarly, the connection between the ports `p8` of `part2` and `p3` of `part1` corresponds to the third condition.  

<div align="center">
<img width="650" src="../../2_Concepts/3_ModelingFramework/images/universal_interface_model/Block1.png">
<br><b>Figure 10:</b> 
Internal Block Diagram connecting proxy ports of parts.
</div><br>

From a theoretical viewpoint, connecting two ports via a connector renames the corresponding channels such that they have the same identity.
This ensures that the one system element receives the messages sent by the other system element via the corresponding channel.
Therefore, connecting two ports in SysML corresponds to the concept of channel renaming in the foundations. 

[Broy10]:https://academic.oup.com/comjnl/article-abstract/53/10/1758/359930?redirectedFrom=fulltext

## Well-formedness Rules

### General Rules 
* Parts, ports and proxy ports must be named

### Blocks and interfaces
* Blocks need to specify at least one proxy port (subinterface) 
* Proxy ports are required to have an interface block as type
* Flow Properties have the direction "out"
* Flow Properties need to have a data type, see [Data Types Documentation](https://spesml.github.io/plugin/data_types.html)

### Structure
* If a block is a composition (i.e. it has parts and an IBD) it may not own any behavior (e.g. a statemachine). It may only own ports, parts and connectors.
* If a block is atomic (e.g. has a statemachine) it may not own any parts or IBDs
* Only atomic blocks may have value properties
* Value properties must have an associated type, see [Data Types Documentation](https://spesml.github.io/plugin/data_types.html)
* All parts must have a block as type
* Connectors must only connect ports with same type.
* Connectors must always connect outgoing with incoming ports.
* Cycles in an IBD must contain a delay of at least 1 unit.
