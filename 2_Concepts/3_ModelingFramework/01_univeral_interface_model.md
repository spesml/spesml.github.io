---
layout: default
title: Universal Interface Model
nav_order: 1
parent: SpesML Modeling Framework
grand_parent: SpesML Concepts
permalink: /concepts/modeling_framework/uim.html
---
# Universal Interface Model

The universal interface model (UIM) delivers the foundation for describing interfaces and behavior across all viewpoints. As such, as SPES ML modeler, you will never explicitely instantiate elements of the UIM, as you will instead create elements of the functional, logical and technical viewpoints. However, as the UIM is the basis for all interfaces in each viewpoint, you will implicitely use the UIM all the time. The following section describe the concepts of the UIM and how they map to SPES ML model elements of the different viewpoints.

## General Concepts
### System Elements

A system element models the behaviors of (a part of) a system. Each system element consists of a syntactic and a semantic interface. An example for a system element in the logical viewpoint is a logical component.

The *syntactic interface* describes the system element's input and output channels where each channel is a typed communication link between system elements.
In the context of the communication between system elements, the instances of the data types are called *messages*. 
For example, the instance ```5``` of the data type ```int``` is said to be a message when it is communicated over a channel.
Only messages of a channel's data type may be communicated via the channel.

A system element is called *atomic* if it has no subelements. Otherwise, it is called *composed*.
Atomic system elements are not further composed and directly have behavior descriptions linked to them (e.g. state machine models). 
The following figure depicts the relation between system elements, channels, and data types. 

<div align="center">
<img width="350" src="images/universal_interface_model/systemelement.png">
<br><b>Figure:</b> 
Relation between system elements, channels, and data types.
</div><br>

System elements interact via sending and receiving typed messages via their input and output channels.
The *semantic interface* defines the behavior of the system element by relating streams of messages received by the system element on its input channels to the
streams of messages emitted by the system element via its output channels. 
As described in the following, the semantic interface of an atomic system element can, inter alia, be defined by a state machine. The semantic interface of a composed system element is always defined by the composition of the semantic interfaces of its subelements.
 
### Syntactic Interface
The _syntactic interface_ $I \blacktriangleright O$  of a system element is defined by a set of input channels $I$ and a set of output channels  $O$ . 
A syntactic interface can be given in terms of sub-interfaces $(I_1 \blacktriangleright O_1), \ldots,(I_n \blacktriangleright O_n)$, where the sets of input channels respectively the sets of output channels are mutually exclusive. 
The resulting syntactic interface then is $\bigcup_i I_i \blacktriangleright \bigcup_j O_j$. Finally, the _inverse_ to a syntactic interface  $I \blacktriangleright O$ is the syntactic interface  $O \blacktriangleright I$

For instance, the following figure schematically depicts the system element $F$. The syntactic interface of $F$ is $\{ c1, c2 \} \blacktriangleright \{ c3,c4,c5 \}$.
The channel $c1$ is of type $T$. It is abstracted from the definition of the type $T$ in the picture.  

<div align="center">
<img width="350" src="images/universal_interface_model/uim.png">
<br><b>Figure:</b> 
A system element and its syntactic interface.
</div><br>


### Semantic Interfaces
The _semantic interface_ (or interface behavior) of a system element with the syntactic interface $I \blacktriangleright O$ is given by a function mapping an input communication history to a set of output communication histories $F: \overrightarrow{I}\rightarrow \wp (\overrightarrow{O})$. 
For each possible input $x \in \overrightarrow{I}$ on the channels contained in $I$, the function specifies all possible outputs $F(x)$ for the input. Thus, the function $F$ represents
an underspecified behavior of a system element with the syntactic interface $I \blacktriangleright O$.

### Causality
A semantic interface $F: \overrightarrow{I}\rightarrow \wp (\overrightarrow{O})$ is called _weakly causal_ (_strongly causal_), if the output up to time-point $t$ only depends on the input received until $t$ (until $t-1$ in case of _strongly causal_ behavior).
Formally, 
* a function $F: \overrightarrow{I}\rightarrow \wp (\overrightarrow{O})$ is called weakly causal if it holds that $\forall t \in \mathcal{N}: \forall x,y \in \overrightarrow{I}: x \downarrow t = y \downarrow t \Rightarrow F(x) \downarrow t = F(y) \downarrow t$.
* a function $F: \overrightarrow{I}\rightarrow \wp (\overrightarrow{O})$ is called strongly causal if it holds that $\forall t \in \mathcal{N}: \forall x,y \in \overrightarrow{I}: x \downarrow t = y \downarrow t \Rightarrow F(x) \downarrow (t +1) = F(y) \downarrow (t + 1)$.

If a semantic interface is not weakly causal, then it cannot be realized by any system element. 
This holds because semantic interfaces that are not weakly causal can be interpreted to model behaviors that can react to events (receiving of messages)
that happen in the future. Stated differently, if a semantic interface is not weakly causal, then the system element can already react in a time unit $`t`$ 
to an input that it receives in a later time unit $t'$ with $t' > t$ (for at least one input communication history).

Strongly causal semantic interfaces are even more restricted in the sense that every strongly causal semantic interface is also weakly causal. For strongly causal
interface behaviors, the output in a time unit $t + 1$ only depends on the messages received up to and including the time unit $t$. Thus, without even
receiving a message in a time unit, the component can already determine its possible outputs for the time unit. 
Every strongly causal semantic interface is also weakly causal.
Strongly causal semantic interfaces are useful 
in the context of the composition of system elements. The composition of a strongly causal system element with another system elements guarantees nice properties
in the sense that the compostion is guaranteed to be a well-defined system element. This is explained in the following sections in more detail.  

## Model Elements
