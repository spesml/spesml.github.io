---
layout: default
title: Requirements Viewpoint
nav_order: 3
has_children: true
has_toc: false
parent: SpesML Modeling Framework
grand_parent: SPES Concepts
permalink: /modeling_framework/requirements_viewpoint.html
---
# Requirements Viewpoint

Requirements are an over-arching topic for SPES architectural models. Requirements – at different levels of precision – link the needs of stakeholders and the obligations arising from the development context with the architectural elements of the functional, logical, and technical viewpoints. 

In this documentation section, we first describe the general apprach to the handling of requirements in SpesML, and then describe the modeling elements - first requirements, then tracing relations - used to represent this approach in SpesML modeling. Finally, we give some methodological advice on requirements modeling in SpesML.

## General Approach

It is common to differentiate requirements according on the aspects they address. In SpesML we roughly distinguish between:

* Capability requirements, concerning stakeholders' demands for the system to be able to perform a certain functionality.
* Functional requirements, concerning the input/output behavior of functions and components.
* Quality requirements, concerning software and product quality characteristics such as the well-known “ilities”.
* Constraints, concerning side conditions to be observed during development.

As detailed in the next section, some of these categories can be further refined - for instance, there are differnt kinds of constraints, depending on whether it is a physical entitfy to be constrainted (e.g., its weight), architectural design decisions (e.g., notational conventions), or the development process (e.g., the need to for certain analyses or tests). 

In constrast with the elements of the functional, logical or technical viewpoints, requirements as such are not given a formal semantics. in SpesML. One reason is that for most categories, the Universal Interface Model - on which the formalization of the other viewpoints is based - is not a suitable mathematical basis. The second reason is that even for functional requirements, where such a formalization is intuitively possible, formalized requirements have little use in SpesML. Instead, the black-box functions of the functional viewpoint can be seen as formalized behavior descriptions of a group of related functional requirements. In practice, this gives a better understanding of the intended functionality tha isolated partial behavior specifications. 

Requirements are connected to architectural elements or to other requirements through various tracing relations, again addressing different aspects, for instance, whether an architectural element is intended to *satisy* a requirement or whether a requirement is *derived* from another requirement.

Although requirements themselves in SpesML have, for the reasons discussed above, no mathematical semantics in the underlying Universal Interface Model, it is still possible to derive methodically useful properties at the level of the traceability graph consisting of linked requirements and architectural elements. For instance, it is possible to discover unimplemented stakeholder requirements or unmotivated derived requirements; it is also possible to construct lists of verification obligations arising from the graph structure.

## Modeling Elements

As discussed above, SpesML has different requirements categories aiming at different engineering aspects. These categories are also encoded in the SpesML plugin, so that they can be used for e.g. automated consistency checks. The SpesML requirements taxonomy is shown in the figure below: 

![SpesML Requirements Taxonomy](/modelling_framework/images/requirements_viewpoint/taxonomy.png){:class="img-responsive"}

The following table summarizes the categories:

| Name        | Description                                                  | Assignable Elements                            |
| ----------- | ------------------------------------------------------------ | ---------------------------------------------- |
| Requirement | No specific interpretation, catch-all type and root of other requirements classes. | Any architectural model element                |
| Functional  | Requirement that specifies an operation or behavior that a system, or part of a system, must perform. | Function in FVP, system/components in LVP/TVP. |
| Interface   | Interaction over interfaces (e.g. protocols, timing, value interdependencies, invariants) | Ports or interfaces                            |
| Operational | Expected behavior of human actors, e.g. as input for testing and simulation, possibly also for user manuals. | Human actors in context of FVP/LVP             |
| Constraint  | Requirement that specifies a constraint on the implementation of the system or system part, such as the system must use a commercial off the shelf component. | Any architectural model element                |
| Physical    | Requirement that specifies physical characteristics and/or physical constraints of the system, or a system part. | Function in FVP, system/components in LVP/TVP. |
| Capability  | Capability requirements describe functions and operations needed by users. | Function in FVP, system/components in LVP/TVP. |
| Quality     | Catch-all category for quality requirements (as in ISO 25010); except perhaps functional correctness and performance (for which we have dedicated categories), these aspects are not further in the scope of SpesML. | Any architectural model element                |
| Process     | Demands of compliance to process norms or requirements on application of development steps or methods, e.g. particular analyses | Any architectural model element                |



### Requirements Attributes

Each requirement has a set of attributes, capturing the requirement statement itself, as well as some meta-information:

| Identifier          | Unique identifier                                            | Core |
| ------------------- | ------------------------------------------------------------ | ---- |
| Name                | Readable name of the requirement, serves as an abstraction of the full requirments text. | x    |
| Identifier          | Unique identifier of the requirement                         |      |
| Category            | Requirements category (see above).                           | x    |
| Text                | Requirements content (see next section).                     | x    |
| Status              | Degree of maturity and validity of the requirement; for example *proposed*, *accepted*, *reviewed*, *implemented*, *verified*. | x    |
| Rationale           | Explanation of the need of the requirement; this in particular of interest if a requirement does not directly or indirectly originate from a stakeholder, but from a process activity (e.g., a safety analysis) or from an architectural decision. | x    |
| States and modes    | The state or mode of the system to which the requirement applies. Some systems have various states and modes, each having a different set of requirements that apply to the specific state or mode. |      |
| Verification method | How to demonstrate that the requirement holds - e.g., analysis, inspection, description of test method and test case derivation/partitioning, reference to external authorities, … |      |
| Source              | Origin of the requirement, e.g. a stakeholder or a normative document. | x    |
| ASIL                | For automotive systems, the Automotive Safety Integrity Level. Similar attributes are relevant for other domains, such as Safety Integrity Level or Design Assurance Level. In addition similar attributes may be needed to capture security requirements (Cybersecurity Assurance Level) or other kinds of criticality, e.g. business or legal risks. |      |

The attributes marked as core attributes are included in to the SpesML plugin. 

The other attributes are optional and may be added to the plugin for specific organizations. Also, the information stored in the attributes may be organization-specific. For instance, status information should be included, but the choice of values may vary. It is good practice, however, to be able to represent the two-level verification obligation typically needed for requirements:

* Review of requirements: Do we accept the requirement and agree with it?
* Verification of the system against requirements: Does the system satisfy the requirement?

Note that we treat safety (represented here through the "ASIL" attribute) not as a requirements category, but rather as additional, orthogonal, attributes. This allows easy extension for, say, security, environmental or legal requirements, and offers more flexibility when it is not a priory clear whether there will not be any overlap between e.g. safety and security, or security and legal requirements.

### Requirements Representation

While requirements are essentially just textual objects (stored in the requirements attribute "text", see the table in the previous section), the representation may be more restricted than natural language alone. In increasing degree of formality, one might envision:

1. *Free-form natural language descriptions*. However, even for free-from natural language, it is recommended to follow a style guide, such as the INCOSE recommendations..

2. *Constrained content*. For requirements allocated to, for instance, a part of an IBD, it is desirable that the requirement references and constrains phenomena in the scope of the model element it is allocated to, such as ports or internal state variables. In most cases, this will imply a review obligation.

3. *Sentence templates*, for instance in the style of EARS or the Sophist Group's requirements boilerplates.

4. *Formal representations*, for instance in the property specification language which is being looked into in a separate project activity, or as formulas in a temporal logic. Formal representations typically are required to be constrained in the sense of Item 2 of this list, in order to ensure that architectural model and property specification are consistent.

Clearly, the more formal the representation, the higher the potential for automated consistency and correctness checks. While within the SpesML project there are no plans to deeply integrate such checks, they are an obvious extension point for further work.

## Tracing Relationships

Requirements are not isolated model elements, but are typically related to other requirements and other model elements through tracing relationships. The following table lists the tracing relationships used in SpesML. The right-most column ("Tracing") shows the model elements connected by the requirement ("source/destination"): 

* *Req*: Requirements
* *Arch*: Main architectural elements of the viewpoints, i.e., functions in the functional viewpoint or components in the logical or technical viewpoints.
* *Any*: Either requriements or main architectural elements. 

| Relationship | Description                                                  | Tracing  |
| ------------ | ------------------------------------------------------------ | -------- |
| Containment  | Decomposition into sub-requirements. This is not really a tracing relationship, but instead part of the requirements meta model. It is frequently used for the co-evolution of architecture and requirements (see below). | Req/Req  |
| Derive       | Derivation of one or more requirements from a source requirement. This is related to the concept of refinement in Focus. | Req/Req  |
| Clarify      | Elaboration of a requirement by additional text or other models (e.g., state machines, sequence diagrams); conversely, elaborate architectural models by textual descriptions. | Any/Req  |
| Satisfy      | Relate requirement with architectural model elements that are intended to satisfy the requirement. | Arch/Req |
| Trace        | General-purpose relationship between a requirement and any other model element. The semantics of trace include no real constraints and therefore are quite weak. | Any/Req  |
| Verify       | Relate requirements with test or simulation scenarios or other model elements. | Any/Req  |
| Require      | Needed for A/C-like arguments. An architectural model element can *require* requirement to make explicit assumptions needed to *satisfy* other requirements. | Arch/Req |
| Matches      | In order to link assumptions of one model element with guarantees of another. | Req/Req  |

The most frequently used relationships are *Satisfy* and *Derive*. The *Satisfy* relationship is used to state that an architectural element should satisfy a requirement. Thus, a *Satisfy* relationship gives rise to the verification obligation of checking whether this in indeed the case. There are multiple ways to discharge such an obligation; in industry, functional requirements are typically verified by tests and constraints are verified by reviews. In some development process descriptions, the *Satisfy* relation is referred to as an *allocation* of requirements to architectural elements. 

The *Derive* relationship is used to add detail or to include certain design decisions. In the absence of formal requirements notations, *derive* does not have a formal semantics, but intuitively, if a requirement _R-m_ is derived from a requirements _R-n_, we would expect that when _R-m_ is valid for a given system, then so is _R-n_ (note that this is a more liberal demand than the universal "_R-m_ implies _R-n_"). Since in general it is not possible to automatically verify this expectation, the *Derive* relationship gives rise to a verification obligation that needs to be discharged during development (typically through a review).

It is a common pattern that an architectural element satisfies a requriements, which itself is derived from a more high-level requirement:

![SpesML Requirements Taxonomy](/modelling_framework/images/requirements_viewpoint/derive-satisfy.png){:class="img-responsive"}

Of course, there may be a longer chain of *derived* requirements, up to an initial stakeholder requirement.

## Modeling Guidelines

### Co-Evolution of Requirements and Architecture

Frequently, requirements and architecture co-evolve in the sense that not only are architectural decisions based on requirements, but also that vice versa requirements decomposition and derivation may depend on architecture. This "zigzagging" between requirements and architecture is also recognized by development standards, such as ISO 26262. 

It can be represented in SpesML through the common decomposition of requirements and architecture, as shown in the figure below:

![SpesML Requirements Taxonomy](/modelling_framework/images/requirements_viewpoint/containment-satisfy.png){:class="img-responsive"}

Note that requirements are decompsed through the *Containment* relationship, which is not not a proper trace relation. Instead, containment is encoded into the requirements model itself. It is used to divide a requirements into sub-requirements which can then be traced, allocated and verified independently. 

When using this co-evolution pattern, one would expect the following consistency conditions to hold: 

* Taken together, the sub-requirements must imply the parent requirement. 

* If the parent requirement is satisfied by a function (in the sense of an architectural element) *F* or by a logical or a technical component _E_, the sub-requirements must be satisfied by a white-box function of *F* or by sub-components of _E_, respectively.

### Derived requirements

The co-evolution is not restricted to the structure of requirements and architecture. For instance, new requirements may arise due to safety analyses, necessating additional functionality to mitigate newly discovered failure modes. Another reason for the introduction of new requirements may be architectural decisions that necessitate clarification of intended behavior beyond what can be inferred from stakeholder-derived requirements. In DO-178C, such requirements are referred to as "derived requirements". 

Methodologically, there are different ways to represent such derived requirements in SpesML:

1. One approach is to represent derived requirements as assumed (*required*) requirements. This is related to the power window example in the section about the Require and Matches relations above. The main advantage of this approach is that it is obvious that these requirements need to be clarified with stakeholders: A stakeholder requirement justifying the decision has  to be introduced and *matched* with the assumed requirement.
2. Alternatively, derived requirements can be introduced and linked to architectural elements (via *Satisfy*-traces) analogously to stakeholder-derived requirements. Since they are not traceable to a stakeholder requirement, however, in any case a rationale should be documented in the requirement and the source attribute of the requirement should state that this is a derived requirement. This approach is preferable for requirements justifying or constraining architectural decisions that do not need to be aligned with stakeholders.
