---
layout: default
title: SPES Concept Mapping To SysML
nav_order: 2
parent: SpesML Plugin
permalink: /plugin/spes_sysml_mapping.html
---
# SPES Concept Mapping To SysML
The purpose of the following table is to give the complete collection of all realized/implemented elements in the SpesML Plugin of MagicDraw. For each of these elements we have added the related UML/SysML element to which the SpesML element can be mapped. Furthermore, we have added the corresponding model concept to each of these elements if this was possible.

Please be aware that not all theoretical concepts are represented by this table and that we do not explain the concepts, elements and their relation in this table. Explanations, relation details and more can be found in the corresponding documentation sections, either of the [theoretical concepts](/concepts/modeling_framework.html/) or their actual realization inside the [SpesML Plugin](/plugin.html/).

Note that SpesML uses the SysML type/property concept for model elements (functions, logical & technical components) of the SpesML viewpoints. The model elements are created as *SysML Block* elements with a SpesML specific stereotype applied. These model elements can be decomposed by creating SpesML specific *SysML Internal Block Diagrams* and *SysML Part Property* elements with an SpesML specifc stereotype applied as sub-elements. These *SpesML Part Properties* may then have additional SpesML specific tags. Using the example of the Functional Viewpoint, it looks like this:
* In a first step *SpesML Function* elements (*SysML Block* elements with a *SpesML Function* stereotype applied) are created. These *SpesML Function* elements are neutral i.e. it is not defined if they are *System Functions* or *Whitebox Functions*. 
* In a second step *SpesML Function* elements can be decomposed by creating a *SpesML Functional Internal Function Diagram* (equivalent to a *SysML Internal Block Diagram*) and creating *SpesML Function Part* elements (*SysML Part Property* elements with a *SpesML Function Part* stereotype applied) of *SpesML Functions* as sub-elements. 
* In a third step these *SpesML Part Properties* can then be tagged as being a *System Function* or *Whitebox Function* using the *Function type* tag.

## Universal Interface Model

| Implemented Modeling Element (GUI Name in MagicDraw) | Stereotype Name in SpesML plugin | Related UML/SysML Element | Related Modeling Concept |
|---|---|---|---|
| (viewpoint-specific, see following tables) | (viewpoint-specific, see following tables) | Block (to define a type of system element) | System Element  |
| (viewpoint-specific, see following tables) | (viewpoint-specific, see following tables) | Part (to designate a system element of a defined type) | System Element |
| Channel | SpesML Channel | Flow Property | Channel |
| Direction (default value = out) | Direction (default value = out) | Attribute "direction" + Port Conjugation  | Channel direction |
| Interface (1) | SpesML Interface (1) | Proxy Port | Sub-Interface |
| Interface Type (1) | SpesML Interface Type (1) | None (Syntactic interface of a system element is defined by set of its channels. In SysML: Syntactic Interface of part is defined by set of instances of ports (precisely: elements aggregated by the port) corresponding to the block of the part) | Syntactic Interface |
| Connector | no specific SpesML Stereotype | Connector | Channel matching (renaming) |
| Value Type / Enumeration | no specific SpesML Stereotype | Value type + attributes of value types including types and cardinalities | Data Type |
| State Machine | SpesML State Machine | State Machine | State Machine (Mealy/Moore) |
| SpesML State Machine Diagram | SpesML State Machine Diagram | SysML State Machine Diagram | - |
| State | no specific SpesML Stereotype | State | State Symbol |
| Value Property | no specific SpesML Stereotype | Value Property | Extended State Variable |
| Transition | no specific SpesML Stereotype | Transition/Guard/Effect with Opaque Behavior | Transition |

(1): Note: Defined as an **abstract** stereotype




## Requirements Viewpoint

| Implemented Modeling Element (GUI Name in MagicDraw) | Stereotype Name in SpesML plugin | Related UML/SysML Element | Related Modeling Concept |
|---|---|---|---|
| Requirements Viewpoint | SpesML Requirements Viewpoint | Package | - |
| Requirements Tracing Package | SpesML Requirements Tracing Package | Package | Structure/organize models |
| Requirements Package | SpesML Requirements Package | Package | Structure/organize models |
| Requirement | SpesML Requirement | Requirement | Requirement |
| SpesML Requirements Table | SpesML Requirements Table | Generic Table | - |
| SpesML Requirements Impact Map | SpesML Requirements Impact Map | Relation Map | Used for tracing |
| SpesML RequirementsToRequirements Matrix | SpesML RequirementsToRequirements Matrix | Dependency Matrix | Used for tracing |




## Functional Viewpoint

| Implemented Modeling Element (GUI Name in MagicDraw) | Stereotype Name in SpesML plugin | Related UML/SysML Element | Related Modeling Concept |
|---|---|---|---|
| Functional Viewpoint | SpesML Functional Viewpoint | Package | - |
| Functional Tracing Package | SpesML Functional Tracing Package | Package | Structure/organize models |
| Functional Package | SpesML Functional Package | Package | Structure/organize models |
| Functional Interface Types Package | SpesML Functional Interface Types Package | Package | Structure/organize models |
| Function | SpesML Function | Block | Function |
| Function Part | SpesML Function Part | Property | Function |
| Connector | no specific SpesML Stereotype | Connector | Message Connection |
| Functional Context | SpesML Functional Context | Class | Related to context |
| Functional Interface | SpesML Functional Interface | Proxy Port | Interface |
| Functional Interface Type | SpesML Functional Interface Type | Interface Block | Interface |
| Functional Actor | SpesML Functional Actor | Block | Actor (for context) |
| Functional Actor Part | SpesML Functional Actor Part | Property | Actor (for context) |
| Mode Model | SpesML Mode Model | State Machine | Behavior |
| State Machine | SpesML State Machine | State Machine | Behavior |
| SpesML State Machine Diagram | SpesML State Machine Diagram | State Machine Diagram | - |
| SpesML Functional Internal Function Diagram | SpesML Functional Internal Function Diagram | SysML Internal Block Diagram | - |
| SpesML Functional Impact Map | SpesML Functional Impact Map | Relation Map | Used for tracing |
| SpesML Functional Tracing Map | SpesML Functional Tracing Map | Relation Map | Used for tracing |
| SpesML FunctionalToRequirements Matrix | SpesML FunctionalToRequirements Matrix | Dependency Matrix | Used for tracing |





## Logical Viewpoint

| Implemented Modeling Element (GUI Name in MagicDraw) | Stereotype Name in SpesML plugin | Related UML/SysML Element | Related Modeling Concept |
|---|---|---|---|
| Logical Viewpoint | SpesML Logical Viewpoint | Package | - |
| Logical Tracing Package | SpesML Logical Tracing Package | Package | Structure/organize models |
| Logical Package | SpesML Logical Package | Package | Structure/organize models |
| Logical Interface Types Package | SpesML Logical Interface Types Package | Package | Structure/organize models |
| Logical Test Case Package | SpesML Logical Test Case Package | Package | Structure/organize models |
| Logical Component | SpesML Logical Component | Block | Component for Logical Architecture |
| Logical Component Part | SpesML Logical Component Part | Part Property | Component for Logical Architecture |
| Functional-Logical Adapter | SpesML Functional-Logical Adapter | Block | Component for Logical Architecture |
| Functional-Logical Adapter Part | SpesML Functional-Logical Adapter Part | Part Property | Component for Logical Architecture |
| Logical Component with Functions | SpesML Logical Component with Functions | Block | Component for Logical Architecture |
| Logical Component with Functions Part | SpesML Logical Component with Functions Part | Part Property | Component for Logical Architecture |
| Logical Test Case Component | SpesML Logical Test Case Component | Block | Used for testing |
| Logical Test Case Component Part | SpesML Logical Test Case Component Part | Part Property | Used for testing |
| Connector | no specific SpesML Stereotype | Connector | Message Connection |
| Logical Context | SpesML Logical Context | Class | Used for context |
| Logical Interface | SpesML Logical Interface | Proxy Port | Interface |
| Logical Interface Type | SpesML Logical Interface Type | Interface Block | Interface |
| Logical Actor | SpesML Logical Actor | Block | Actor (for context) |
| Logical Actor Part | SpesML Logical Actor Part | Property | Actor (for context) |
| State Machine | SpesML State Machine | State Machine | Behavior |
| SpesML State Machine Diagram | SpesML State Machine Diagram | State Machine Diagram | - |
| SpesML Logical Internal Component Diagram | SpesML Logical Internal Component Diagram | SysML Internal Block Diagram | - |
| SpesML Logical Impact Map | SpesML Logical Impact Map | Relation Map | Used for tracing |
| SpesML Logical Tracing Map | SpesML Logical Tracing Map | Relation Map | Used for tracing |
| SpesML LogicalToRequirements Matrix | SpesML LogicalToRequirements Matrix | Dependency Matrix | Used for tracing |
| SpesML LogicalToFunctional Matrix | SpesML LogicalToFunctional Matrix | Dependency Matrix | Used for tracing |





## Technical Viewpoint
| Implemented Modeling Element (GUI Name in MagicDraw) | Stereotype Name in SpesML plugin | Related UML/SysML Element | Related Modeling Concept |
|---|---|---|---|
| Technical Viewpoint | SpesML Technical Viewpoint | Package | - |
| Technical Tracing Package | SpesML Technical Tracing Package | Package | Structure/organize models |
| Technical Interface Types Package | SpesML Technical Interface Types Package | Package | Structure/organize models |
| Technical Package | SpesML Technical Package | Package | Structure/organize models |
| Software Execution Package | SpesML Software Execution Package | Package | Structure/organize models |
| Technical Component | SpesML Technical Component | Block | Component for Technical Architecture |
| Technical Component Part | SpesML Technical Component Part | Part Property | Component for Technical Architecture |
| Mechanical Component | SpesML Mechanical Component | Block | Component for Technical Architecture |
| Mechanical Component Part | SpesML Mechanical Component Part | Part Property | Component for Technical Architecture |
| Mechatronic Component | SpesML Mechatronic Component | Block | Component for Technical Architecture |
| Mechatronic Component Part | SpesML Mechatronic Component Part | Part Property | Component for Technical Architecture |
| Electronic Component | SpesML Electronic Component | Block | Component for Technical Architecture |
| Electronic Component Part | SpesML Electronic Component Part | Part Property | Component for Technical Architecture |
| Software Execution Subsystem | SpesML Software Execution Subsystem | Block | Component for Technical Architecture |
| Software Execution Subsystem Part | SpesML Software Execution Subsystem Part | Part Property | Component for Technical Architecture |
| Execution Component | SpesML Execution Component | Block | Component for Technical Architecture |
| Execution Component Part | SpesML Execution Component Part | Part Property | Component for Technical Architecture |
| Communication Component | SpesML Communication Component | Block | Component for Technical Architecture |
| Communication Component Part | SpesML Communication Component Part | Part Property | Component for Technical Architecture |
| Task Architecture | SpesML Task Architecture | Block | Component for Technical Architecture |
| Task Architecture Part | SpesML Task Architecture Part | Part Property | Component for Technical Architecture |
| Task | SpesML Task | Block | Component for Technical Architecture |
| Task Part | SpesML Task Part | Part Property | Component for Technical Architecture |
| Connector | no specific SpesML Stereotype | Connector | Message Connection |
| Technical Context | SpesML Technical Context | Class | Used for context |
| Technical Interface | SpesML Technical Interface | Proxy Port | Interface |
| Technical Interface Type | SpesML Technical Interface Type | Interface Block | Interface |
| Technical Actor | SpesML Technical Actor | Block | Actor (for context) |
| Technical Actor Part | SpesML Technical Actor Part | Property | Actor (for context) |
| SpesML Technical Internal Component Diagram | SpesML Technical Internal Component Diagram | SysML Internal Block Diagram | - |
| SpesML Technical Tracing Map | SpesML Technical Tracing Map | Relation Map | Used for tracing |
| SpesML TechnicalToRequirements Matrix | SpesML TechnicalToRequirements Matrix | Dependency Matrix | Used for tracing |
| SpesML TechnicalToLogical Matrix | SpesML TechnicalToLogical Matrix | Dependency Matrix | Used for tracing |

X
