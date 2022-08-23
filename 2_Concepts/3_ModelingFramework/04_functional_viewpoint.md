---
layout: default
title: Functional Viewpoint
nav_order: 4
parent: SpesML Modeling Framework
grand_parent: SpesML Concepts
permalink: /concepts/modeling_framework/functional_viewpoint.html
---
# Functional Viewpoint


The _Functional Viewpoint_ contains three model types that can be used to describe the desired functionality of a system on a _system_ level (i.e., primarily from the perspective of external actors such as users or external systems).

In the center of the Functional Viewpoint is the concept of _system functions_. A system function describes a coherent set of interactions between a system and its external actors. The granularity of a system function is comparable to that of a [Use Case](https://en.wikipedia.org/wiki/Use_case). A system with several system functions can be called a _multifunctional system_. In general, system functions describe system behavior, which is largely independent of each other, however, system functions may also influence each other in specific cases. In the Functional Viewpoint, these influences are modeled by so-called _mode channels_ between system functions.  

The Functional Viewpoint then consists of three model types:

- Functional Black-box Model: Contains all system functions and structures them in a hierarchy
- Functional White-box Model: Describes the decomposition of one particular system function into a set of related white-box functions
- Mode Model: Describes operational states of the system. These operational states can be referenced in mode channels that describe dependencies between system functions.

In the following, we describe the three model types and how we represent them in SpesML using the [universal interface model](./uim.html).

# Modeling Elements

## Functional Context: The System and its Context in the Functional Viewpoint

Just like all other viewpoints, the functional viewpoint refers to a specific system scope, i.e., there is a clear notion of what is part of the "system" currently under development and what is considered as the context of that system. It is important to note that the system boundary in the functional viewpoint is conceptually the same as the boundary in all the other viewpoints. Any context object that occurs, for example, in the context of the logical viewpoint must all occur in the context of the functional viewpoint and vice versa. 

The system boundary and the system context are specified in the `Functional Context`. This diagram contains one specific `Function` that represents the entire System-under-Development (SuD).  

The following figure shows the `WindowLifterSystem` in its functional context


![Functional Context](/images/functional_viewpoint/functional-context.png){:class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 1: </b><em>Functional Context</em></div>


## System Function
A system function describes a coherent set of interactions between a system and its external actors. For this purpose, it uses the modeling elements of the [universal interface model](./uim.html). That means a system function is described by a specific `SysML block` called `Function`. Each system function has a syntactic interface defined by a `Functional Interface`, i.e., a set of input and output ports with associated types. 


The following figure shows the system function `CentralWindowFunction` with its associated interface consisting of input and output ports. 

![System Function](/images/functional_viewpoint/system-function.png){:width="500" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 2: </b><em>System Function</em></div>

## System Function Hierarchy
A system can have several system functions that are structured in a system function hierarchy. To model this hierarchy, a system function can be described by a composition of system functions. To model this composition, a `SysML block` that represents a system function can have `parts`, which again represent system functions. The `proxy ports` of the `parts` can be connected by `flow properties`. Such connections between system functions describe functional dependencies between system functions (e.g., a specific state of one system function affects the behavior of another system function). These dependencies should be considered with care as a primary design goal is to specify system functions as independently from each other as possible.  
Remember that system functions describe interactions between a system and its external actors. That means, a decomposition into system functions must not result in *internal* functions, which have no interface to the context of the system. The system function that represents the *root* of the system function hierarchy specifies the interface of the entire system from a functional point of view (i.e., by a vocabulary and on a granularity level that is close to the functional system requirements).  

The following figure shows the system function hierarchy of the `WindowLifter`. In this example, the system contains three system functions (`CentralWindowFunction`, `TunnelWindowClosingFunction`, and `BatteryVoltageFunction`). There are dependencies between the functions (`tunnelWindowClosingMode` and `BatteryMode`) that are used to describe that the window lifter control is influenced by a (low) battery state and by being in a tunnel. 

![System Function Hierarchy](/images/functional_viewpoint/system-function-hierarchy.png){:width="1200" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 3: </b><em>System Function Hierarchy</em></div>

## White-box Functions
A white-box function (_"Teilfunktion"_) describes a unit of behavior that is necessary to realize a [system function](system-function). For this purpose, it uses the modeling elements of the [universal interface model](./uim.html). 
That means a white-box function is described by a `SysML block` with an associated syntactic interface defined by `proxy ports`.
The behavior of a white-box function can be specified by any type of behavior specification that relates input streams received on the input ports to output streams produced on the output ports (e.g., state machines). 


## Functional White-Box Model of a System Function
A [system function](system-function) is realized by a set of communicating white-box function (cf. _glass-box refinement_) that may again be decomposed into smaller white-box functions. To model this hierarchy, a system function is related (via a _refinement_ relation) to exactly one _functional white-box model_ that describes a composition of white-box functions. To model this composition, a `SysML block` that represents a white-box function can have `parts`, which again represent white-box functions. The `proxy ports` of the `parts` can be connected by `flow properties`. The resulting "chain" of white-box functions for a system function is sometimes also called a causal chain (_"Wirkkette"_). In contrast to system functions, the majority of white-box functions will only have "internal" ports, i.e., output ports are connected to input ports of other white-box functions. Only a few white-box function will have input or output ports that are _not_ connected to other white-box function. These "external" ports must reflect the syntactic interface of the corresponding system function. 

Note: For input ports, multiple white-box functions may be listening at the same "external" port, e.g. if messages from that port need to be processed by multiple white-box functions independently. For output ports, only one white-box function can write to this port. If multiple white-box functions need to write to the same port, a coordination white-box function is needed. Such a coordination function can either be an additional white-box function or belong to one of the white-box functions that need to write to the port. 

The following figure shows the functional white-box model of the system function `CentralWindowFunction `. It defines six white-box functions that specify the necessary steps to realize the system function.

![Functional White-Box Model](/images/functional_viewpoint/functional_viewpoint/white-box-model.png){:width="900" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 4: </b><em>Functional White-Box Model</em></div>


## Mode Model
As described above, system functions can influence the behavior of other system functions. In the functional black-box model, we describe these influences by ports and channels between two system functions. The messages sent over these channels often describe certain operational states (a.k.a. _system modes_) that influence the behavior of other system functions. Therefore, channels between system functions in the functional black-box model are called _mode channels_. 

In addition to the functional black-box model, we can also describe a _mode model_ that focuses exclusively on the modes and possible transitions between mode values. A mode model is a state machine where the states represent values that can be sent over a mode channel in the functional black-box model.

In our example of the Window Lifter, we had two mode channels (`tunnelWindowClosingMode` and `BatteryMode`) between the two system functions. The port associated with the `tunnelWindowClosingMode` channel has the type `ActivatedDeactivated` that defines two possible values to be transmitted over this channel (`ACTIVATED` and `DEACTIVATED`; see figure below). The port associated with the `BatteryMode` channel has the type `BatteryStatus` that defines two possible values to be transmitted over this channel (`OK` and `notOK`; see figure below). From this information, we can create a mode model that contains a state for each of the values. In addition to the states, we can also specify transitions between the states to define allowed mode sequences (see figure below). 
In the example, we specify that only specific mode sequences are allowed to be transmitted over mode channels with the specific mode types. System functions that have an outgoing mode channel with such types must adhere to the allowed mode transitions (e.g., `TunnelWindowClosingFunction` must not define behavior that sends a sequence like `<..., ACTIVATED, DEACTIVATED,...>` over the mode channel `TunnelWindowClosingMode` after a message `notOK` has been sent over the mode channel `BatteryMode`). Thus, the mode model defines a kind of mode protocol that all functions must adhere to. 


![Data type and possible values of a mode channel](/images/functional_viewpoint/mode_datatypes.png){:width="250" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 5: </b><em>Data type and possible values of a mode channel</em></div>


![Mode model based on the data type of the mode channel.](/images/functional_viewpoint/mode-model.png){:width="400" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 6: </b><em>Mode model based on the data type of the mode channel</em></div>


# Structuring of Models in the Containment Tree

The different models of the Functional Viewpoint are structured in the Containment Tree of a project. There is a top-level node called `Functional Viewpoint` that contains all elements of this viewpoint (see figure below). 

![Elements of the Functional VP in the Containment Tree](/images/functional_viewpoint/containment-tree.png){:width="400" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 7: </b><em>Elements of the Functional VP in the Containment Tree</em></div>

Below this node, there are the following specific subnodes:

- **System Functions**: This package contains all _system function_ elements. The functional white-box model of each system function is located below the system function element.
- **White-box Functions**: This package contains all _white-box function_ elements.
- **System**: This package contains the functional black-box model and the mode model of the system.
- **Functional Context**: This package contains the top-level view of the functional viewpoint and contains a diagram of the system under development in the context of its surrounding external systems and actors.


![Elements of the Functional VP in the Containment Tree](/images/functional_viewpoint/containment-tree-expanded.png){:width="500" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 8: </b><em>Elements of the Functional VP in the Expanded Containment Tree</em></div>




# Tracing Relations between Functions and other Elements
## Tracing between Functions and Elements of the Logical Viewpoint

In general, it is possible to design a logical architecture that does not take into account design decisions from the functional architecture view. In those cases, the relation between system functions and logical architecture components will be n:m in general.

The SPES methodology suggests a design pattern that provides a closer connection between the system function models in the FVP and the structure of the logical architecture by using the concept of system function white-box models, which yields a meaningful tracing relationship between the model elements of the views:

The white-box models of the system functions in the FVP are constructed with the structure of the logical architecture in mind and build a bridge between the functional and the logical architectures. In a design decision, a structural architecture is developed from the set of white-box functions of the FVP by uniquely mapping white-box functions to logical components (see figure below).

![Mapping of functional architecture to logical components](/images/functional_viewpoint/architecture_mapping.png){:width="700" :class="img-responsive" style="display:block; margin-left:auto; margin-right:auto"}
<div align="center"><b>Figure 9: </b><em>Mapping of functional architecture to logical components</em></div>

It is important to note that the same white-box function can occur multiple times in the white-box models of different system functions. For resolving this conflict two options are available:

1. Multiple white-box functions are removed from the chains of effects and defined as independent components in the logical view. Those components' interfaces are induced by the interfaces of the corresponding chains of effects.
2. The functionality of such multiple white-box functions will be realized redundantly by different logical components. The corresponding components are given unique names for this purpose and the original structure of the causal chains is retained.

This results in a network of communicating logical components to which each white-box function of the functional view of the SuD is uniquely assigned. The interfaces of such components (syntactically and semantically) are derived from the interfaces of the white-box function via a refinement relation.

The logical architecture can also contain further subcomponents that are defined by additional requirements (i.e. requirements that are not covered by functions in the FVP). Those components will not have a direct tracing relation to a white-box function. An example of these are requirements that arise through design decisions.



# Modeling Guidelines

## System Functions

- [The interface of each system function must have at least one output port or one output port that is part of the interface of the top-level system](Functional-VP-WFRs.md#wf-1-system-functions-have-to-contribute-at-least-one-output-port-to-the-overall-sud).

## White-Box Functions
- [Each functional white-box model must be related to exactly one system function](Functional-VP-WFRs.md#wf-3-each-functional-white-box-model-must-be-related-to-exactly-one-system-function).
- [Each system function must be related to at most one functional white-box model](Functional-VP-WFRs.md#wf-4-each-system-function-must-be-related-to-at-most-one-functional-white-box-model).
- [The interface of a system function (i.e., inputs and outputs) must be reflected in its related functional white-box model, i.e., each input and output port of the system function must also be a _free_ input or output port in the functional white-box model (i.e., a port without any flow property)](Functional-VP-WFRs.md#wf-5-ports-of-system-functions-have-to-match-the-ports-of-the-associated-white-box-model). <br>_Hint: In a first version, this _port matching_ may be achieved by a convention of matching port names_.
- [Each white-box function must be related to at most one logical component that implements this white-box function](Functional-VP-WFRs.md#wf-10-at-most-one-logical-component-per-white-box-function).

## Mode Model
- [Each value that can be sent over a mode channel (i.e., a channel between system functions in the functional black-box model) must have a corresponding state in the mode model](Functional-VP-WFRs.md#wf-6-mode-states-exactly-match-the-set-of-allowed-messages-on-mode-channels).
- [Transitions in the mode model do not have any guards or actions as they simply define potential sequences of modes](Functional-VP-WFRs.md#wf-8-transitions-in-the-mode-model-do-not-have-any-guards-or-actions).
- [A mode model has an initial state but no final state](Functional-VP-WFRs.md#wf-9-a-mode-model-has-an-initial-state-but-no-final-state). 




