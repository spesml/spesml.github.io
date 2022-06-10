---
layout: default
title: Requirements Viewpoint
nav_order: 3
parent: SpesML Plugin
permalink: /plugin/requirements_viewpoint.html
---
# ![Requirements Viewpoint](/images/requirements_viewpoint/RequirementsViewpoint.png){:height="30px" width="30px"}{:class="img-responsive"}SpesML Plugin - Requirements

## Overview

In order to motivate and justify architectural decisions, SpesML models include explicit requirements and design constraints. These requirements and constraints are linked with the architectural elements of the functional, logical, and technical viewpoints through tracing relations. Requirements in SpesML are described as plain natural-language statements; in contrast with e.g. the functions of the functional viewpoint or the components of the logical viewpoint, they have no formal semantics based on the [Universal Interface Model](/concepts/modeling_framework/uim.html). 

The [SpesML Concepts](/concepts.html) section of this documentation has some additional information about the [Requirements Viewpoint in the SpesML modeling framework](/concepts/modeling_framework/requirements_viewpoint.html).

## Method

Requirements are described as natural language statements. They may be allocated to architectural elements (modeled through a *satisfy* relation from the architectural element to the requirement), or refined into more detailed requirements (modeled through a *derived* relation from the more detailed requirement). The combination of satisfy and derive allows the representation of justification chains linking architectural elements to high-level stakeholder needs or to obligations arising from the development context, such as compliants 

![Derive and satisfy relationships](/images/requirements_viewpoint/derive-satisfy.png){:class="img-responsive" width="400px"}

Other tracing relations can be used in the context of modular subsystem development or to link simulation setups as verification evidence or explanatory information to requirements; the details of these use cases are still to be defined, however.

As the main focus of SpesML is on the architectural models of the functional, logical and technical viewpoints, SpesML prescribes no specific requriements engineering method. Nevertheless, it is good practice to follow certain guidelines; for example, the requirements guidelines of INCOSE are a suitable starting point.

## Structure

Requirements are described in the Requirements Viewpoint folder of a SpesML project:

![Requirements folder](/images/requirements_viewpoint/requirements-structure.png){:class="img-responsive" width="200px"}

For better comprehensibiltiy and maintainability of the set of requirements, requirements can be grouped into Requirements Packages, such as the package for technical design constraints in the figure above.

Tracing information is gathered in Requirements Tracing Packages, consisting of traceability matrices and impact maps.

## How to model

??? Wollen wir hier wirklich eine Anleitung auf Mausklickebene haben? Reicht es nicht, wenn wir die Elemente erklären?  ???

## Elements

### ![Requirements](/images/requirements_viewpoint/RequirementsViewpoint.png){:class="img-responsive"}Requirements Viewpoint
This is the top-level structuring element of  the Requirements Viewpoints; it can contain other structuring elements (Requirements Packages or Requirements Tracing Packages), requirements themselved and overview lists of requirements (Requirements Tables).

There is exactly one Requirements Viewpoint in a SpesML project.

### ![Requirements Package](/images/requirements_viewpoint/RequirementsPackage.png){:class="img-responsive"}Requirements Package

Requirements Packages are structuring elements to group related requirements together. They are used to improve comprehensibiltiy and maintainability of the set of requirements. Requirements Packages can be nested, and they can also contain Requirements Tables as  overview lists of requirements.

### ![Requirements Tracing Package](/images/requirements_viewpoint/RequirementsTracingPackage.png){:class="img-responsive"}Requirements Tracing Package

Requirements Tracing Packages contain traceability matrices and impact maps.

### ![Requirement](/images/requirements_viewpoint/Requirement.png){:class="img-responsive"}Requirement
Requirements elements hold the textual descriptions of requirements; they also have additional attributes that encode the requirements categories (e.g., capability requirement, functional requirement, design constraint). The requirements category is also symbolized trough the captal letter in the requirements icon (see for instance the Requirements Table further down on this page).

## Diagrams

### ![Requirements Impact Map](/images/diagrams/map.png){:class="img-responsive"}SpesML Requirements Impact map

### ![RequirementToRequirement Matrix](/images/diagrams/matrix.png){:class="img-responsive"}SpesML RequirementToRequirement Matrix

This is a traceability matrix for relations between requirements. With a right-button-click into a matrix cell, one can select the tracing relation between source (vertical axis) and target (horizontal axis) requirement.

![Requirements Matrix](/images/requirements_viewpoint/req-to-req-matrix.png){:class="img-responsive"}

There are similar traceability matrices in the other viewpoints, e.g. to relate functions with requirements.

### ![Requirements Table](/images/diagrams/table.png){:class="img-responsive"}SpesML Requirements Table

Requirements Tables give a concise summary of a list of requirements and their attributes, e.g: 

![Requirements Table](/images/requirements_viewpoint/requirements-table.png){:class="img-responsive"}
