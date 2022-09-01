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

## Universal Interface Model
<table>
    <tr>
        <th>Modeling Concept</th><th>UML/SysML Element</th><th>Stereotype name in SpesML plugin</th><th>Shown Name (GUI) in MagicDraw</th>
    </tr>
    <tr>
        <td rowspan="2">System Element </td>
        <td>Block (to define a type of system element)</td><td>(Viewpoint-Specific)</td><td>(Viewpoint-Specific)</td>
    </tr>
    <tr>
       <td>Part (to designate a system element of a defined type)</td><td>(Viewpoint-Specific)</td><td>(Viewpoint-Specific)</td>
    </tr>
    <tr>
        <td>Channel</td><td>Flow Property</td><td>SpesML Channel</td><td>Channel</td>
    </tr>
    <tr>
        <td>Channel direction</td><td>Attribute "direction" + Port Conjugation </td><td>Direction (default value = out)</td><td>Direction (default value = out)</td>
    </tr>
    <tr>
        <td rowspan="2">Sub-Interface</td>
        <td>Proxy Port</td><td>SpesML Interface[^1]</td><td>Interface[^1]</td>
    </tr>
    <tr>
       <td>Interface Block (can be conceptually interpreted to be a type that defines sub-interfaces)</td><td> - </td><td> - </td>
    </tr>
    <tr>
        <td>Syntactic Interface</td><td>None (Syntactic interface of a system element is defined by set of its channels. In SysML: Syntactic Interface of part is defined by set of instances of ports (precisely: elements aggregated by the port) corresponding to the block of the part)</td><td>SpesML Interface Type[^1]</td><td>Interface Type[^1]</td>
    </tr>
    <tr>
        <td>Channel matching (renaming)</td><td>Connector</td><td>no specific SpesML Stereotype</td><td>Connector</td>
    </tr>
    <tr>
        <td>Data Type</td><td>Value type + attributes of value types including types and cardinalities</td><td>no specific SpesML Stereotype</td><td>Value Type / Enumeration</td>
    </tr>
    <tr>
        <td rowspan="2">Composition Operator (decomposition)</td>
        <td>Connector (to connect channels of system elements)</td><td>-</td><td>-</td>
    </tr>
    <tr>
       <td>Part (instances of system elements in specific roles)</td><td> - </td><td> - </td>
    </tr>
    <tr>
        <td>State Machine (Mealy/Moore)</td><td>State Machine</td><td>SpesML State Machine</td><td>State Machine</td>
    </tr>
    <tr>
        <td></td><td>SysML State Machine Diagram</td><td>SpesML State Machine Diagram</td><td>SpesML State Machine Diagram</td>
    </tr>
    <tr>
        <td>State Symbol</td><td>State</td><td>no specific SpesML Stereotype</td><td>State</td>
    </tr>
    <tr>
        <td>Extended State Variable</td><td>Value Property</td><td>no specific SpesML Stereotype</td><td>Value Property</td>
    </tr>
    <tr>
        <td>Transition</td><td>Transition/Guard/Effect with Opaque Behavior</td><td>no specific SpesML Stereotype</td><td>Transition</td>
    </tr>
    <tr>
        <td>Delay</td><td> -</td><td>TODO</td><td>TODO</td>
    </tr>

</table>

[^1]: Note: Defined as an **abstract** stereotype




## Requirements Viewpoint
<table>
    <tr>
        <th>Modeling Concept</th><th>UML/SysML Element</th><th>Stereotype name in SpesML plugin</th><th>Shown Name (GUI) in MagicDraw</th>
    </tr>
    <tr>
        <td>-</td><td>Package</td><td>SpesML Requirements Viewpoint</td><td>Requirements Viewpoint</td>
    </tr>  
    <tr>
        <td>Model group (to structure/organize models)</td><td>Package</td><td>SpesML Requirements Tracing Package</td><td>Requirements Tracing Package</td>
    </tr>      
    <tr>
        <td>Model group (to structure/organize models)</td><td>Package</td><td>SpesML Requirements Package</td><td>Requirements Package</td>
    </tr>   
    <tr>
        <td>Requirement</td><td>Requirement</td><td>SpesML Requirement</td><td>SpesML Requirement</td>
    </tr>  
    <tr>
        <td>-</td><td>Generic Table</td><td>SpesML Requirements Table</td><td>SpesML Requirements Table</td>
    </tr>  
    <tr>
        <td>Related to tracing</td><td>Relation Map</td><td>SpesML Requirements Impact Map</td><td>SpesML Requirements Impact Map</td>
    </tr> 
    <tr>
        <td>Related to tracing</td><td>Dependency Matrix</td><td>SpesML RequirementsToRequirements Matrix</td><td>SpesML RequirementsToRequirements Matrix</td>
    </tr>     
</table>




## Functional Viewpoint
<table>
    <tr>
        <th>Modeling Concept</th><th>UML/SysML Element</th><th>Stereotype name in SpesML plugin</th><th>Shown Name (GUI) in MagicDraw</th>
    </tr>
    <tr>
        <td>-</td><td>Package</td><td>SpesML Functional Viewpoint</td><td>Functional Viewpoint</td>
    </tr>  
    <tr>
        <td>Model group (to structure/organize models)</td><td>Package</td><td>SpesML Functional Tracing Package</td><td>Functional Tracing Package</td>
    </tr>      
    <tr>
        <td>Model group (to structure/organize models)</td><td>Package</td><td>SpesML Functional Package</td><td>Functional Package</td>
    </tr>    
    <tr>
        <td>Model group (to structure/organize models)</td><td>Package</td><td>SpesML Functional Interface Types Package</td><td>Functional Interface Types Package</td>
    </tr> 
    <tr>
        <td>Function</td><td>Block</td><td>SpesML Function</td><td>Function</td>
    </tr> 
    <tr>
        <td>Function</td><td>Property</td><td>SpesML Function Part</td><td>Function Part</td>
    </tr> 
    <tr>
        <td>Message Connection</td><td>Connector</td><td>no specific SpesML Stereotype</td><td>Connector</td>
    </tr>       
    <tr>
        <td>Related to context</td><td>Class</td><td>SpesML Functional Context</td><td>Functional Context</td>
    </tr> 
    <tr>
        <td>Interface</td><td>Proxy Port</td><td>SpesML Functional Interface</td><td>Functional Interface</td>
    </tr>    
    <tr>
        <td>Interface</td><td>Interface Block</td><td>SpesML Functional Interface Type</td><td>Functional Interface Type</td>
    </tr> 
    <tr>
        <td>Actor (for context)</td><td>Block</td><td>SpesML Functional Actor</td><td>Functional Actor</td>
    </tr> 
    <tr>
        <td>Actor (for context)</td><td>Property</td><td>SpesML Functional Actor Part</td><td>Functional Actor Part</td>
    </tr>   
    <tr>
        <td>Behavior</td><td>State Machine</td><td>SpesML Mode Model</td><td>Mode Model</td>
    </tr>  
    <tr>
        <td>Behavior</td><td>State Machine</td><td>SpesML State Machine</td><td>State Machine</td>
    </tr>      
    <tr>
        <td>-</td><td>State Machine Diagram</td><td>SpesML State Machine Diagram</td><td>SpesML State Machine Diagram</td>
    </tr> 
    <tr>
        <td>-</td><td>SysML Internal Block Diagram</td><td>SpesML Functional Internal Function Diagram</td><td>SpesML Functional Internal Function Diagram</td>
    </tr>       
    <tr>
        <td>Related to tracing</td><td>Relation Map</td><td>SpesML Functional Impact Map</td><td>SpesML Functional Impact Map</td>
    </tr> 
     <tr>
        <td>Related to tracing</td><td>Relation Map</td><td>SpesML Functional Tracing Map</td><td>SpesML Functional Tracing Map</td>
    </tr>    
    <tr>
        <td>Related to tracing</td><td>Dependency Matrix</td><td>SpesML FunctionalToRequirements Matrix</td><td>SpesML FunctionalToRequirements Matrix</td>
    </tr>         
</table>





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
        <td>Model group (to structure/organize models)</td><td>Package</td><td>SpesML Software Package</td><td>Software Execution Package</td>
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
        <td>Component for Technical Architecture</td><td>Block</td><td>SpesML Software Execution Subsystem</td><td>Execution Platform</td>
    </tr>
    <tr>
        <td>Component for Technical Architecture</td><td>Part Property</td><td>SpesML Software Execution Subsystem Part</td><td>Execution Platform Part</td>
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
