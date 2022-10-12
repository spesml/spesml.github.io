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

You can find the concept of the Universal Interface Model [here](/concepts/modeling_framework/context.html).

| Implemented Modeling Element (GUI Name in MagicDraw) | Stereotype Name in SpesML plugin | Related UML/SysML Element | Related Modeling Concept |
|---|---|---|---|
| (viewpoint-specific, see following tables) | (viewpoint-specific, see following tables) | Block (to define a type of system element) | System Element  |
| (viewpoint-specific, see following tables) | (viewpoint-specific, see following tables) | Part (to designate a system element of a defined type) | System Element |
| Channel | SpesML Channel | Flow Property | Channel |
| Direction (default value = out) | Direction (default value = out) | Attribute "direction" + Port Conjugation  | Channel direction |
| Interface (1) | SpesML Interface (1) | Proxy Port | Sub-Interface |
| Interface Type (1) | SpesML Interface Type (1) | None (Syntactic interface of a system element is defined by set of its channels. In SysML: Syntactic Interface of part is defined by set of instances of ports (precisely: elements aggregated by the port) corresponding to the block of the part) | Syntactic Interface |
| Connector | no specific SpesML Stereotype | Connector | Channel matching (renaming) |
| [Value Type](/plugin/data_types.html#value-type) / [Enumeration](/plugin/data_types.html#enumeration) | no specific SpesML Stereotype | Value type + attributes of value types including types and cardinalities | Data Type |
| State Machine | SpesML State Machine | State Machine | State Machine (Mealy/Moore) |
| SpesML State Machine Diagram | SpesML State Machine Diagram | SysML State Machine Diagram | - |
| State | no specific SpesML Stereotype | State | State Symbol |
| Value Property | no specific SpesML Stereotype | Value Property | Extended State Variable |
| Transition | no specific SpesML Stereotype | Transition/Guard/Effect with Opaque Behavior | Transition |

(1): Note: Defined as an **abstract** stereotype




## Requirements Viewpoint

You can find the concept of the Requirement Viewpoint [here](/concepts/modeling_framework/requirements_viewpoint.html).

| Implemented Modeling Element (GUI Name in MagicDraw) | Stereotype Name in SpesML plugin | Related UML/SysML Element | Related Modeling Concept |
|---|---|---|---|
| [Requirements Viewpoint](/plugin/requirements_viewpoint.html#requirements-viewpoint) | SpesML Requirements Viewpoint | Package | - |
| [Requirements Tracing Package](/plugin/requirements_viewpoint.html#requirements-tracing-package) | SpesML Requirements Tracing Package | Package | Structure/organize models |
| [Requirements Package](/plugin/requirements_viewpoint.html#requirements-package) | SpesML Requirements Package | Package | Structure/organize models |
| [Requirement](/plugin/requirements_viewpoint.html#requirement) | SpesML Requirement | Requirement | Requirement |
| [SpesML Requirements Table](/plugin/requirements_viewpoint.html#spesml-requirements-table) | SpesML Requirements Table | Generic Table | - |
| [SpesML Requirements Impact Map](/plugin/requirements_viewpoint.html#spesml-requirements-impact-map) | SpesML Requirements Impact Map | Relation Map | Used for tracing |
| [SpesML RequirementsToRequirements Matrix](/plugin/requirements_viewpoint.html#spesml-requirementtorequirement-matrix) | SpesML RequirementsToRequirements Matrix | Dependency Matrix | Used for tracing |




## Functional Viewpoint

You can find the concept of the Functional Viewpoint [here](/concepts/modeling_framework/functional_viewpoint.html).

| Implemented Modeling Element (GUI Name in MagicDraw) | Stereotype Name in SpesML plugin | Related UML/SysML Element | Related Modeling Concept |
|---|---|---|---|
| [Functional Viewpoint](/plugin/functional_viewpoint.html#functional-viewpoint) | SpesML Functional Viewpoint | Package | - |
| [Functional Tracing Package](/plugin/functional_viewpoint.html#functional-tracing-package) | SpesML Functional Tracing Package | Package | Structure/organize models |
| [Functional Interface Types Package](/plugin/functional_viewpoint.html#functional-interface-types-package) | SpesML Functional Interface Types Package | Package | Structure/organize models |
| [Functional Package](/plugin/functional_viewpoint.html#functional-package) | SpesML Functional Package | Package | Structure/organize models |
| [Function](/plugin/functional_viewpoint.html#function) | SpesML Function | Block | Function |
| [Function Part](/plugin/functional_viewpoint.html#function-part) | SpesML Function Part | Property | Function |
| Connector | no specific SpesML Stereotype | Connector | Message Connection |
| [Functional Context](/plugin/functional_viewpoint.html#functional-context) | SpesML Functional Context | Class | Related to context |
| [Functional Interface](/plugin/functional_viewpoint.html#functional-interface) | SpesML Functional Interface | Proxy Port | Interface |
| [Functional Interface Type](/plugin/functional_viewpoint.html#functional-interface-type) | SpesML Functional Interface Type | Interface Block | Interface |
| [Functional Actor](/plugin/functional_viewpoint.html#functional-actor) | SpesML Functional Actor | Block | Actor (for context) |
| Functional Actor Part | SpesML Functional Actor Part | Property | Actor (for context) |
| Mode Model | SpesML Mode Model | State Machine | Behavior |
| State Machine | SpesML State Machine | State Machine | Behavior |
| SpesML State Machine Diagram | SpesML State Machine Diagram | State Machine Diagram | - |
| [SpesML Functional Internal Function Diagram](/plugin/functional_viewpoint.html#spesml-functional-internal-function-diagram) | SpesML Functional Internal Function Diagram | SysML Internal Block Diagram | - |
| [SpesML Functional Impact Map](/plugin/functional_viewpoint.html#spesml-functional-impact-map) | SpesML Functional Impact Map | Relation Map | Used for tracing |
| [SpesML Functional Tracing Map](/plugin/functional_viewpoint.html#spesml-functional-tracing-map) | SpesML Functional Tracing Map | Relation Map | Used for tracing |
| [SpesML FunctionalToRequirements Matrix](/plugin/functional_viewpoint.html#spesml-functiontorequirement-matrix) | SpesML FunctionalToRequirements Matrix | Dependency Matrix | Used for tracing |





## Logical Viewpoint

You can find the concept of the Logical Viewpoint [here](/concepts/modeling_framework/logical_viewpoint.html).

| Implemented Modeling Element (GUI Name in MagicDraw) | Stereotype Name in SpesML plugin | Related UML/SysML Element | Related Modeling Concept |
|---|---|---|---|
| [Logical Viewpoint](/plugin/logical_viewpoint.html#logical-viewpoint) | SpesML Logical Viewpoint | Package | - |
| [Logical Tracing Package](/plugin/logical_viewpoint.html#logical-tracing-package) | SpesML Logical Tracing Package | Package | Structure/organize models |
| [Logical Interface Types Package](/plugin/logical_viewpoint.html#logical-interface-types-package) | SpesML Logical Interface Types Package | Package | Structure/organize models |
| Logical Test Case Package | SpesML Logical Test Case Package | Package | Structure/organize models |
| [Logical Package](/plugin/logical_viewpoint.html#logical-package) | SpesML Logical Package | Package | Structure/organize models |
| [Logical Component](/plugin/logical_viewpoint.html#logical-component) | SpesML Logical Component | Block | Component for Logical Architecture |
| [Logical Component Part](/plugin/logical_viewpoint.html#logical-component-part) | SpesML Logical Component Part | Part Property | Component for Logical Architecture |
| [Logical Component with Functions](/plugin/logical_viewpoint.html#logical-component-with-functions) | SpesML Logical Component with Functions | Block | Component for Logical Architecture |
| Logical Component with Functions Part | SpesML Logical Component with Functions Part | Part Property | Component for Logical Architecture |
| [Functional-Logical Adapter](/plugin/logical_viewpoint.html#functional-logical-adapter) | SpesML Functional-Logical Adapter | Block | Component for Logical Architecture |
| Functional-Logical Adapter Part | SpesML Functional-Logical Adapter Part | Part Property | Component for Logical Architecture |
| [Logical Test Case Component](/plugin/logical_viewpoint.html#logical-test-case-component) | SpesML Logical Test Case Component | Block | Used for testing |
| Logical Test Case Component Part | SpesML Logical Test Case Component Part | Part Property | Used for testing |
| Connector | no specific SpesML Stereotype | Connector | Message Connection |
| [Logical Context](/plugin/logical_viewpoint.html#logical-context) | SpesML Logical Context | Class | Used for context |
| [Logical Interface](/plugin/logical_viewpoint.html#logical-interface) | SpesML Logical Interface | Proxy Port | Interface |
| [Logical Interface Type](/plugin/logical_viewpoint.html#logical-interface-type) | SpesML Logical Interface Type | Interface Block | Interface |
| [Logical Actor](/plugin/logical_viewpoint.html#logical-actor) | SpesML Logical Actor | Block | Actor (for context) |
| Logical Actor Part | SpesML Logical Actor Part | Property | Actor (for context) |
| State Machine | SpesML State Machine | State Machine | Behavior |
| SpesML State Machine Diagram | SpesML State Machine Diagram | State Machine Diagram | - |
| [SpesML Logical Internal Component Diagram](/plugin/logical_viewpoint.html#spesml-logical-internal-component-diagram) | SpesML Logical Internal Component Diagram | SysML Internal Block Diagram | - |
| [SpesML Logical Impact Map](/plugin/logical_viewpoint.html#spesml-logical-impact-map) | SpesML Logical Impact Map | Relation Map | Used for tracing |
| [SpesML Logical Tracing Map](/plugin/logical_viewpoint.html#spesml-logical-tracing-map) | SpesML Logical Tracing Map | Relation Map | Used for tracing |
| [SpesML LogicalToRequirements Matrix](/plugin/logical_viewpoint.html#spesml-logicaltorequirement-matrix) | SpesML LogicalToRequirements Matrix | Dependency Matrix | Used for tracing |
| [SpesML LogicalToFunctional Matrix](/plugin/logical_viewpoint.html#spesml-logicaltofunctional-matrix) | SpesML LogicalToFunctional Matrix | Dependency Matrix | Used for tracing |





## Technical Viewpoint

You can find the concept of the Technical Viewpoint [here](/concepts/modeling_framework/technical_viewpoint.html).

| Implemented Modeling Element (GUI Name in MagicDraw) | Stereotype Name in SpesML plugin | Related UML/SysML Element | Related Modeling Concept |
|---|---|---|---|
| [Technical Viewpoint](/plugin/technical_viewpoint.html#technical-viewpoint)] | SpesML Technical Viewpoint | Package | - |
| [Technical Tracing Package](/plugin/technical_viewpoint.html#technical-tracing-package) | SpesML Technical Tracing Package | Package | Structure/organize models |
| [Technical Interface Types Package](/plugin/technical_viewpoint.html#technical-interface-types-package) | SpesML Technical Interface Types Package | Package | Structure/organize models |
| [Technical Package](/plugin/technical_viewpoint.html#technical-package) | SpesML Technical Package | Package | Structure/organize models |
| [Software Execution Package](/plugin/technical_viewpoint.html#software-execution-package) | SpesML Software Execution Package | Package | Structure/organize models |
| [Technical Component](/plugin/technical_viewpoint.html#technical-component) | SpesML Technical Component | Block | Component for Technical Architecture |
| Technical Component Part | SpesML Technical Component Part | Part Property | Component for Technical Architecture |
| [Mechanical Component](/plugin/technical_viewpoint.html#mechanical-component) | SpesML Mechanical Component | Block | Component for Technical Architecture |
| Mechanical Component Part | SpesML Mechanical Component Part | Part Property | Component for Technical Architecture |
| [Mechatronic Component](/plugin/technical_viewpoint.html#mechatronic-component) | SpesML Mechatronic Component | Block | Component for Technical Architecture |
| Mechatronic Component Part | SpesML Mechatronic Component Part | Part Property | Component for Technical Architecture |
| [Electronic Component](/plugin/technical_viewpoint.html#electronic-component) | SpesML Electronic Component | Block | Component for Technical Architecture |
| Electronic Component Part | SpesML Electronic Component Part | Part Property | Component for Technical Architecture |
| [Software Execution Subsystem](/plugin/technical_viewpoint.html#software-execution-subsystem) | SpesML Software Execution Subsystem | Block | Component for Technical Architecture |
| Software Execution Subsystem Part | SpesML Software Execution Subsystem Part | Part Property | Component for Technical Architecture |
| [Execution Component](/plugin/technical_viewpoint.html#execution-component) | SpesML Execution Component | Block | Component for Technical Architecture |
| Execution Component Part | SpesML Execution Component Part | Part Property | Component for Technical Architecture |
| [Communication Component](/plugin/technical_viewpoint.html#communication-component) | SpesML Communication Component | Block | Component for Technical Architecture |
| Communication Component Part | SpesML Communication Component Part | Part Property | Component for Technical Architecture |
| [Task Architecture](/plugin/technical_viewpoint.html#task-architecture) | SpesML Task Architecture | Block | Component for Technical Architecture |
| Task Architecture Part | SpesML Task Architecture Part | Part Property | Component for Technical Architecture |
| [Task](/plugin/technical_viewpoint.html#task) | SpesML Task | Block | Component for Technical Architecture |
| Task Part | SpesML Task Part | Part Property | Component for Technical Architecture |
| Connector | no specific SpesML Stereotype | Connector | Message Connection |
| [Technical Context](/plugin/technical_viewpoint.html#technical-context) | SpesML Technical Context | Class | Used for context |
| [Technical Interface](/plugin/technical_viewpoint.html#technical-interface) | SpesML Technical Interface | Proxy Port | Interface |
| [Technical Interface Type](/plugin/technical_viewpoint.html#technical-interface-type) | SpesML Technical Interface Type | Interface Block | Interface |
| [Technical Actor](/plugin/technical_viewpoint.html#technical-actor) | SpesML Technical Actor | Block | Actor (for context) |
| Technical Actor Part | SpesML Technical Actor Part | Property | Actor (for context) |
| [SpesML Technical Internal Component Diagram](/plugin/technical_viewpoint.html#spesml-technical-internal-component-diagram) | SpesML Technical Internal Component Diagram | SysML Internal Block Diagram | - |
| [SpesML Technical Tracing Map](/plugin/technical_viewpoint.html#spesml-technical-tracing-map) | SpesML Technical Tracing Map | Relation Map | Used for tracing |
| [SpesML TechnicalToRequirements Matrix](/plugin/technical_viewpoint.html#spesml-technicaltorequirement-matrix) | SpesML TechnicalToRequirements Matrix | Dependency Matrix | Used for tracing |
| [SpesML TechnicalToLogical Matrix](/plugin/technical_viewpoint.html#spesml-technicaltological-matrix) | SpesML TechnicalToLogical Matrix | Dependency Matrix | Used for tracing |
