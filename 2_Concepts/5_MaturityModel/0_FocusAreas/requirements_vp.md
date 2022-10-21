---
layout: default
title: Requirements Viewpoint
nav_order: 1
parent: Capability description
grand_parent: SpesML Maturity Model
permalink: /concepts/maturity_model/focus_areas/requirements_vp.html
---

# Requirements Viewpoint
The Requirements Viewpoint is the functional domain of the SpesML MM concerned with the definition of requirements. There are three focus areas in this Viewpoint: the Requirements Elicitation (REE), the Requirements Specification (RES), and the Requirements Refinement (RER). More information on the Requirements Viewpoint can be found [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html).  

##  Requirements Elicitation (REE): 
This focus area is the smallest of this Viewpoint, having only two capabilities. 

### REE A: Requirements are modeled by a distinct Requirement Element per requirement.
This capability states that requirements should be modeled in the SpesML plugin using the Requirement Element. *Plugin usage*: The engineer should right click the containment tree in the RequirementsViewpoint folder, and select create element->create a SpesML Requirement element. The image below show the menu where the SpesML Requirement can be selected.

![REE A example](../images/reea-example.png){:class="img-responsive"}

The REE A is the most basic capability from this functional domain. Because of this, all the other capabilities from this Viewpoint requires it.  More information on the Requirement Element can be found [here](https://spesml.github.io/plugin/requirements_viewpoint.html#elements).

###  REE B: Requirements are categorized into one of the categories: Capability, Functional, Quality, Constraint.
This capability can be considered implemented when the Requirement Element category is defined. The categories supported by the SpesML Modeling Framework are described [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html#modeling-elements). *Plugin usage*: The requirements category is symbolized trough the capital letter in the requirements icon and can be selected in the Specification window.
## Requirements Specification (RES)

This focus area has four capabilities. Three of them are of Conceptual kind. 

### RES A: Requirements are equipped with attributes containing meta-information including: name, category, status, rationale, and source. 
The SpesML Modeling framework supports a number of attributes, which serves as template, and segregate information from the requirement description, improving readability. *Plugin usage*: The attributes of a requirements can be accessed through right click menu->Specification. The image below depicts how they are presented in the plugin.
Additional information on requirement attributes can be found [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html#requirements-attributes).

![REE A example](../images/car-attributes.png){:class="img-responsive"}

### RES B: Requirements text is formulated following certain sentence templates (e.g., EARS or Sophist MasterTemplate) ( C).
Sentence template require extra effort to achieve compliance at the initial phases, but prevents rework in future phases. Although the SpesML MF do not suggest using a specific template, it does suggest they should be used to attend the organization's needs (e.g, domain, project size). This is a *Conceptual* capability

### RES C: The requirements text is aligned with modeling elements that they are related to (e.g., naming of ports or internal states) ( C).
This capability is related to the documentation of architecture elements within a requirement description (e.g., the naming of ports). This capability requires the LCM C capability. This is a *Conceptual* capability.

###  RES D: The requirement is formalized in a formal specification language (e.g., temporal logic) ( C).
This capability characterizes requirements described using formal representations, for instance in the property specification language which is being looked into in a separate project activity, or as formulas in a temporal logic. Formal representations typically are required to be reviewed in order to ensure that architectural model and property specification are consistent. This is a *Conceptual* capability.

## Requirements Refinement (REF)
The capabilities in this focus area represent types of tracing relations that exist between requirements, and between requirements and architectural elements. More on requirements tracing relations can be seen [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html#tracing-relationships).

### REF A: If a low-level requirement is derived from a high-level requirement, they are related by a derived relation. Note: Both requirements must address the same system scope.
The derive relationship is used to add detail or to include certain design decisions to a requirement. Unlike RES C, where the design decisions are included in the requirement description, REF A is about two different requirements related by this specific tracing relation. It is a common pattern that an architectural element satisfies a requirements, which itself is derived from a more high-level requirement. More information on the derive relationship can be found [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html#tracing-relationships). *Plugin usage*: This capability is realized in the SpesML RequirementToRequirement Matrix. More information on this can be found [here](https://spesml.github.io/plugin/requirements_viewpoint.html#spesml-requirementtorequirement-matrix).

### REF B: If a system requirement is broken down into several component requirements, the system requirement is related to the component requirements by a decompose relation.
This capability describe the decompose relation, which connects requirements as explained [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html#co-evolution-of-requirements-and-architecture).

### REF C: If a requirement satisfies a property that is required in another requirement, the requirements are related by a Match relation.
The *match* relation traces an architectural element to a requirement of type *Requirement*.  One instance of Match relation is the one used in requirement defining safety contracts for dynamic systems of systems. In this kind of systems, some specific levels of safety assurance are required to guarantee safety of the whole system. More information on this can be found [here](https://spesml.github.io/concepts/modeling_framework/requirements_viewpoint.html#development-against-assumed-requirements).

