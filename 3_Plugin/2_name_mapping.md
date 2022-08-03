---
layout: default
title: SPES Concept Mapping To SysML
nav_order: 2
parent: SpesML Plugin
permalink: /plugin/spes_sysml_mapping.html
---
# SPES Concept Mapping To SysML
The purpose of this document is to collect the modeling concepts, their proposed mapping to SysML and the proposed names in the SpesML plugin (MagicDraw). 

## Universal Interface Model


<table>
    <tr>
        <th>Modeling Concept</th><th>SysML Element</th><th>Stereotype / Name in SpesML plugin (MagicDraw)</th><th>Shown Name (GUI) in SpesML plugin (MagicDraw)</th>
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
        <td>Proxy Port</td><td>SpesML Interface (1)</td><td>Interface (1)</td>
    </tr>
    <tr>
       <td>Interface Block (can be conceptually interpreted to be a type that defines sub-interfaces)</td><td> - </td><td> - </td>
    </tr>
    <tr>
        <td>Syntactic Interface</td><td>None (Syntactic interface of a system element is defined by set of its channels. In SysML: Syntactic Interface of part is defined by set of instances of ports (precisely: elements aggregated by the port) corresponding to the block of the part)</td><td>SpesML Interface Type (1)</td><td>Interface Type (1)</td>
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

(1) Note: Defined as an **abstract** stereotype

## Logical Architecture

<table>
    <tr>
        <th>Modeling Concept</th><th>SysML Element</th><th>Stereotype / Name in SpesML plugin (MagicDraw)</th><th>Shown Name (GUI) in SpesML plugin (MagicDraw)</th>
    </tr>
    <tr>
        <td></td><td>Package</td><td>SpesML Logical Viewpoint</td><td>Logical Viewpoint</td>
    </tr>  
    <tr>
        <td></td><td>Package</td><td>SpesML Logical Package</td><td>Logical Package</td>
    </tr>    
    <tr>
        <td></td><td>Package</td><td>SpesML Logical Interface Types Package</td><td>Logical Interface Types Package</td>
    </tr>     
    <tr>
        <td> </td><td>Block</td><td>SpesML Logical Component</td><td>Logical Component</td>
    </tr>
     <tr>
        <td> </td><td>Part Property</td><td>SpesML Logical Component Part</td><td>Part Property</td>
    </tr>  
      <tr>
        <td> </td><td>Connector</td><td>no specific SpesML Stereotype</td><td>Connector</td>
    </tr>     
    <tr>
        <td></td><td>Proxy Port</td><td>SpesML Logical Interface (2)</td><td>Logical Interface (2)</td>
    </tr>
    <tr>
        <td></td><td>Interface Block</td><td>SpesML Logical Interface Type (2)</td><td>Logical Interface Type (2)</td>
    </tr>    
    <tr>
        <td></td><td>SysML Internal Block Diagram</td><td>SpesML Logical Internal Component Diagram</td><td>SpesML Logical Internal Component Diagram</td>
    </tr>      
</table>

(2) Note: These stereotypes inherit from the corresponding **abstract** stereotypes

## Operational Context
Notiz: Es muss einen Scope / eine Domain geben, alle Elemente des operational context haben eine part-of relation zum Oberelement (zur Klammer).
(The remaining elements are defined as in the logical architecture)

<table>
    <tr>
        <th>Modeling Concept</th><th>SysML Element</th><th>Stereotype / Name in SpesML plugin (MagicDraw)</th><th>Shown Name (GUI) in SpesML plugin (MagicDraw)</th>
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
        <th>Modeling Concept</th><th>SysML Element</th><th>Stereotype / Name in SpesML plugin (MagicDraw)</th><th>Shown Name (GUI) in SpesML plugin (MagicDraw)</th>
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

