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
<table>
    <tr>
        <th>Modeling Concept</th><th>UML/SysML Element</th><th>Stereotype name in SpesML plugin</th><th>Shown Name (GUI) in MagicDraw</th>
    </tr>
    <tr>
        <td>-</td><td>Package</td><td>SpesML Logical Viewpoint</td><td>Logical Viewpoint</td>
    </tr> 
    <tr>
        <td>Model group (to structure/organize models)g</td><td>Package</td><td>SpesML Logical Tracing Package</td><td>Logical Tracing Package</td>
    </tr>         
    <tr>
        <td>Model group (to structure/organize models)</td><td>Package</td><td>SpesML Logical Package</td><td>Logical Package</td>
    </tr>    
    <tr>
        <td>Model group (to structure/organize models)</td><td>Package</td><td>SpesML Logical Interface Types Package</td><td>Logical Interface Types Package</td>
    </tr>
     <tr>
        <td>Model group (to structure/organize models)</td><td>Package</td><td>SpesML Logical Test Case Package</td><td>Logical Test Case Package</td>
    </tr>        
    <tr>
        <td>Component for Logical Architecture</td><td>Block</td><td>SpesML Logical Component</td><td>Logical Component</td>
    </tr>
     <tr>
        <td>Component for Logical Architecture</td><td>Part Property</td><td>SpesML Logical Component Part</td><td>Logical Component Part</td>
    </tr>  
    <tr>
        <td>Component for Logical Architecture</td><td>Block</td><td>SpesML Functional-Logical Adapter</td><td>Functional-Logical Adapter</td>
    </tr>
     <tr>
        <td>Component for Logical Architecture</td><td>Part Property</td><td>SpesML Functional-Logical Adapter Part</td><td>Functional-Logical Adapter Part</td>
    </tr>
    <tr>
        <td>Component for Logical Architecture</td><td>Block</td><td>SpesML Logical Component with Functions</td><td>Logical Component with Functions</td>
    </tr>
     <tr>
        <td>Component for Logical Architecture</td><td>Part Property</td><td>SpesML Logical Component with Functions Part</td><td>Logical Component with Functions Part</td>
    </tr>
    <tr>
        <td>Related to testing</td><td>Block</td><td>SpesML Logical Test Case Component</td><td>Logical Test Case Component</td>
    </tr>
     <tr>
        <td>Related to testing</td><td>Part Property</td><td>SpesML Logical Test Case Component Part</td><td>Logical Test Case Component Part</td>
    </tr>
    <tr>
        <td>Message Connection</td><td>Connector</td><td>no specific SpesML Stereotype</td><td>Connector</td>
    </tr>   
    <tr>
        <td>Related to context</td><td>Class</td><td>SpesML Logical Context</td><td>Logical Context</td>
    </tr>       
    <tr>
        <td>Interface</td><td>Proxy Port</td><td>SpesML Logical Interface</td><td>Logical Interface</td>
    </tr>
    <tr>
        <td>Interface</td><td>Interface Block</td><td>SpesML Logical Interface Type</td><td>Logical Interface Type</td>
    </tr>  
    <tr>
        <td>Actor (for context)</td><td>Block</td><td>SpesML Logical Actor</td><td>Logical Actor</td>
    </tr> 
    <tr>
        <td>Actor (for context)</td><td>Property</td><td>SpesML Logical Actor Part</td><td>Logical Actor Part</td>
    </tr> 
    <tr>
        <td>Behavior</td><td>State Machine</td><td>SpesML State Machine</td><td>State Machine</td>
    </tr>    
    <tr>
        <td>-</td><td>State Machine Diagram</td><td>SpesML State Machine Diagram</td><td>SpesML State Machine Diagram</td>
    </tr>           
    <tr>
        <td>-</td><td>SysML Internal Block Diagram</td><td>SpesML Logical Internal Component Diagram</td><td>SpesML Logical Internal Component Diagram</td>
    </tr>    
    <tr>
        <td>Related to tracing</td><td>Relation Map</td><td>SpesML Logical Impact Map</td><td>SpesML Logical Impact Map</td>
    </tr> 
     <tr>
        <td>Related to tracing</td><td>Relation Map</td><td>SpesML Logical Tracing Map</td><td>SpesML Logical Tracing Map</td>
    </tr>    
    <tr>
        <td>Related to tracing</td><td>Dependency Matrix</td><td>SpesML LogicalToRequirements Matrix</td><td>SpesML LogicalToRequirements Matrix</td>
    </tr>      
    <tr>
        <td>Related to tracing</td><td>Dependency Matrix</td><td>SpesML LogicalToFunctional Matrix</td><td>SpesML LogicalToFunctional Matrix</td>
    </tr>        
</table>





## Technical Viewpoint
<table>
    <tr>
        <th>Modeling Concept</th><th>UML/SysML Element</th><th>Stereotype name in SpesML plugin</th><th>Shown Name (GUI) in MagicDraw</th>
    </tr>
    <tr>
        <td>-</td><td>Package</td><td>SpesML Technical Viewpoint</td><td>Technical Viewpoint</td>
    </tr>  
    <tr>
        <td>Model group (to structure/organize models)</td><td>Package</td><td>SpesML Technical Tracing Package</td><td>Technical Tracing Package</td>
    </tr>    
    <tr>
        <td>Model group (to structure/organize models)</td><td>Package</td><td>SpesML Technical Interface Types Package</td><td>Technical Interface Types Package</td>
    </tr>   
    <tr>
        <td>Model group (to structure/organize models)</td><td>Package</td><td>SpesML Technical Package</td><td>Technical Package</td>
    </tr>    
    <tr>
        <td>Model group (to structure/organize models)</td><td>Package</td><td>SpesML Software Execution Package</td><td>Software Execution Package</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Block</td><td>SpesML Technical Component</td><td>Technical Component</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Part Property</td><td>SpesML Technical Component Part</td><td>Technical Component Part</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Block</td><td>SpesML Mechanical Component</td><td>Mechanical Component</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Part Property</td><td>SpesML Mechanical Component Part</td><td>Mechanical Component Part</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Block</td><td>SpesML Mechatronic Component</td><td>Mechatronic Component</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Part Property</td><td>SpesML Mechatronic Component Part</td><td>Mechatronic Component Part</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Block</td><td>SpesML Electronic Component</td><td>Electronic Component</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Part Property</td><td>SpesML Electronic Component Part</td><td>Electronic Component Part</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Block</td><td>SpesML Software Execution Subsystem</td><td>Software Execution Subsystem</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Part Property</td><td>SpesML Software Execution Subsystem Part</td><td>Software Execution Subsystem Part</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Block</td><td>SpesML Execution Component</td><td>Execution Component</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Part Property</td><td>SpesML Execution Component Part</td><td>Execution Component Part</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Block</td><td>SpesML Communication Component</td><td>Communication Component</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Part Property</td><td>SpesML Communication Component Part</td><td>Communication Component Part</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Block</td><td>SpesML Task Architecture</td><td>Task Architecture</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Part Property</td><td>SpesML Task Architecture Part</td><td>Task Architecture Part</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Block</td><td>SpesML Task</td><td>Task</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Part Property</td><td>SpesML Task Part</td><td>Task Part</td>
    </tr>
    <tr>
        <td>Message Connection</td><td>Connector</td><td>no specific SpesML Stereotype</td><td>Connector</td>
    </tr>       
    <tr>
        <td>Related to context</td><td>Class</td><td>SpesML Technical Context</td><td>Technical Context</td>
    </tr> 
    <tr>
        <td>Interface</td><td>Proxy Port</td><td>SpesML Technical Interface</td><td>Technical Interface</td>
    </tr>
    <tr>
        <td>Interface</td><td>Interface Block</td><td>SpesML Technical Interface Type</td><td>Technical Interface Type</td>
    </tr>     
    <tr>
        <td>Actor (for context)</td><td>Block</td><td>SpesML Technical Actor</td><td>Technical Actor</td>
    </tr> 
    <tr>
        <td>Actor (for context)</td><td>Property</td><td>SpesML Technical Actor Part</td><td>Technical Actor Part</td>
    </tr>  
    <tr>
        <td>-</td><td>SysML Internal Block Diagram</td><td>SpesML Technical Internal Component Diagram</td><td>SpesML Technical Internal Component Diagram</td>
    </tr>        
    <tr>
        <td>Related to tracing</td><td>Relation Map</td><td>SpesML Technical Tracing Map</td><td>SpesML Technical Tracing Map</td>
    </tr>    
    <tr>
        <td>Related to tracing</td><td>Dependency Matrix</td><td>SpesML TechnicalToRequirements Matrix</td><td>SpesML TechnicalToRequirements Matrix</td>
    </tr>      
    <tr>
        <td>Related to tracing</td><td>Dependency Matrix</td><td>SpesML TechnicalToLogical Matrix</td><td>SpesML TechnicalToLogical Matrix</td>
    </tr>          
</table>

<!--
## Operational Context
Notiz: Es muss einen Scope / eine Domain geben, alle Elemente des operational context haben eine part-of relation zum Oberelement (zur Klammer).
(The remaining elements are defined as in the logical architecture)

<table>
    <tr>
        <th>Modeling Concept</th><th>UML/SysML Element</th><th>Stereotype name in SpesML plugin</th><th>Shown Name (GUI) in MagicDraw</th>
    </tr>
    <tr>
        <td>System under Development (SuD)</td><td>SpesML Logical Component</td><td>SpesML System under Development (SuD)</td><td>SuD</td>
    </tr>  
    <tr>
        <td>Human Actor Context Element</td><td>SpesML Logical Component</td><td>SpesML Human Actor Context Element</td><td>Human Actor Context Element</td>
    </tr> 
    <tr>
        <td>System Context Element</td><td>SpesML Logical Component</td><td>SpesML System Context Element</td><td>System Context Element</td>
    </tr> 
    <tr>
        <td>Physical Context Element</td><td>SpesML Logical Component</td><td>SpesML Physical Context Element</td><td>Physical Context Element</td>
    </tr>    
</table>

## Integration of Mechanical Elements
Notiz: Das Thema geht über den logischen VP hinaus. Die Konzepte betreffen nicht nur die Integration mechanischer Komponenten. Ggfs. muss mam die Konzepte zu einem späteren Zeitpunkt nochmal neu einsortieren.

<table>
    <tr>
        <th>Modeling Concept</th><th>SysML Element</th><th>Stereotype name in SpesML plugin</th><th>Shown Name (GUI) in MagicDraw</th>
    </tr>
    <tr>
        <td>User Function</td><td></td><td></td><td></td>
    </tr>
    <tr>
        <td>Functional White-Box Model</td><td></td><td></td><td></td>
    </tr>  
    <tr>
        <td>Granularity Layer</td><td></td><td></td><td></td>
    </tr> 
    <tr>
        <td>Software Subsystem</td><td></td><td></td><td></td>
    </tr> 
    <tr>
        <td>Physical Context Element</td><td>SpesML Logical Component</td><td>SpesML Physical Context Element</td><td>Physical Context Element</td>
    </tr>    
</table>
-->
