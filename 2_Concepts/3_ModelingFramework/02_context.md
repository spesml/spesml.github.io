---
layout: default
title: Context
nav_order: 2
parent: SpesML Modeling Framework
grand_parent: SpesML Concepts
permalink: /concepts/modeling_framework/context.html
---
# Context
## The system and its context

A SPES system model (LINK: Principles) also defines the environment in which it operates. The environment is part of the system definition, meaning the system is always embedded in its so called “context” and communicates and inter-acts with specific context elements. 
Elements of this context can be of various types. Each element that is identified as a context element must have a direct interface with the System under Development (SuD), we call this a relation of first grade. This interaction is defined through an interface that follows all principles of the universal interface model (UIM) (com-pare LINK: Modeling Theory). This enables an interaction of the SuD with its context.
In general, we distinguish between two different types of context:
* Knowledge Context: This type of context may contain standards, regula-tions (e.g. ISO26262, DO-178B) and other forms of documentation. This type of context influences the system at design time. 
* Operational Context: An operational context may contain various ele-ments that interact with the system during runtime (these elements are described in section 5.2).

In the following, we focus on the operational context and especially on its ele-ments and relations to the SuD.

## Elements of the operational context 
The operational context consists of the following system elements 
* System under Development (SuD): The system the is currently being engineering, resp. in focus of an engineering step.
* Context Elements: System elements as described below.
* Interfaces between context elements and the SuD. 

In SPES each element is modeled by applying the UIM, i.e. the elements have a syntactic and a semantic interface. When modeling the operational context on system level, the following modeling guidelines must be followed:
* A context model of each view shall contain exactly one SuD.
* The SuD on different views remains the same, meaning the SuD does not change, for instance, with respect to granularity.
* Each context element is modeled via the UIM and shall have at least one channel to the SuD, being an context element of 1st grade.
* Each context element shall be of one of the following types:
** Human Actors Context Elements: These elements describe human interaction with the system across a human-computer in-terface
** External System Context Elements: These elements describe system-to-system communication 
** Physical Context Elements: These elements may represent the impact of physical processes onto the system (e.g. hydraulics, gravitational forces, …). 

Such elements, however, also apply the UIM can be modelled the same way as  physical components that are part of the SuD. Such elements have further properties on their interface description (cf. LINK: Modeling Physical Sys-tems)
 
(Figure 5 1 Context and System) 

Surely, there are a lot of elements that do not have relations (even not related relations through other context elements) with the SuD. These elements do not at all interact with the SuD and can be considered as non-relevant part of the context, meaning being outside of the context border and thus not considered for context (and SuD) modeling. The explicit distinction between relevant and non-relevant elements is a first abstraction in systems modeling, helping to better understand the necessary system interfaces. Figure 5 1 Context and System illustrates the var-ious types of context elements.

## Different dimensions in context modeling
We distinguish two different dimensions for modeling systems and their con-text elements: 
* Horizontal: As SPES offers different viewpoints (and their correspond-ing views) on the system, this results in different context elements per view. The SuD, however, remains the same in all views, e.g. the same SuD is considered in the functional and in the logical view on system level and does not change, w.r.t. to its granularity.
* Vertical: The scope of the SuD changes, by using the concept of granu-larity levels (LINK: Granularity Levels). This consequently, results in different operational contexts for the new SuD, meaning different context elements. 
In the following, we describe both context dimensions in detail.

### Horizontal Context Dimension in SPES
Each viewpoint in the SPES framework allows to model various concerns for the viewpoint-specific stakeholders using a dedicate SPES viewpoint (compare LINK: View and Viewpoints).  
This means that without changing the SuD, each viewpoint provides a set of predefined models and model elements to model the SuD and, as a consequence, also for its context elements. As discussed in the chapter LINK: Modeling Theo-ry, the scientific foundations of the SPES methodology ensure the semantically correct composition and decomposition of the SuD as well as of all of its context elements. However, one exception has been made in the Technical View, where context elements only rely on the syntactic part of the UIM (compare section 5.3.1.3).
In general, context elements can be directly connected to the SuD (we call these 1st grade context elements) or transitively, meaning through composition with 1st grade context element. We call these elements context elements of 2nd grade. In the SpesML project we explicitly focus in 1st grade relations. However, the operation-al context conceptually even includes 2nd grade elements through the consequent application of the UIM. Thus, 2nd grade element are influence the SuD behavior through the interfaces of the 1st grade elements. 
Figure 5 2 illustrates a 1st grade element in the functional view, namely the Con-text Function A and 2nd grade element, namely Context Function B.

(Figure 5 2 Context elements of 1st and 2nd grade)

The SPES methodology, namely the UIM explicitly supports such purposes, as the behavior is transitively observable at the 1st grade elements. Furthermore, the UIM guarantees the semantically correct composition and decomposition of such elements. In the following we provide an overview of the SPES viewpoints and their dedicated context elements that appear, without changing the system scope, i.e. there is a clear notion of what is part of the SuD and what is considered the context of that system.

#### Functional Context
The context described in the functional view focuses on functions (i.e., chunks of behavior), representing a functional perspective of the SuD context, rather than entities. The system boundary and the system context are specified in the Functional Context Diagram. This diagram contains one specific element that represents the entire SuD and additional elements modeling functional context el-ements, named context functions outside the SuD. These context functions de-scribe the functional interactions between the SuD and the context. 
 
(Figure 5 3 Example of Context functions interaction with the SuD)

Figure 5 3 illustrate 3 different context functions in the technical view that may represent the 3 different types of context elements, e.g. an Human Actor, an Ex-ternal system or an external system context element. To be more precisely, the be-havior of context functions can be again modelled by applying the UIM (Link: Modeling Theory), i.e. the elements have a syntactic and a semantic interface. This includes the possibility of decomposing context functions, however, the black-box of context elements provides all necessary syntactical and semantical in-formation, due to the UIM conformance. For Detailed modeling instructions for the SuD of the functional view can be found in chapter (Link: FVP).

#### Context in the Logical Viewpoint
The logical context focusses on modeling the environment in which the SuD shall operate on a logical level. Therefore, context elements in the logical viewpoint are called context systems. The system boundary and the system context are specified in the Logical Context Diagram. Again, context system can be of various types, e.g. human actors, that interact with the SuD or external system or an physical context element. One main objective in modeling the logical context is also to specify the logical interface of the SuD according to the abstraction of the logical view (Link: LVP). 

(Figure 5 4 Example of context systems in the logical view)

Figure 5 4 illustrates three different context systems in the logical view inter-acting with the SuD in a relationship of 1st grade. Again, comparably to the func-tional context, the behavior of context systems in the logical view can be mod-elled by applying the UIM, i.e. the context systems are having a syntactic and a semantic interface. This, again, enables for decomposing context systems or re-structuring (de/composing) them, if necessary.
In SpesML, we are often interested to model the behavior of the SuD, some-times especially interested in the control parts of the SuD. We provide an ap-proach to define a central SW-Subsystem Architecture already in the logical view (compare section LINK: Definition of SW in Logical Architecture). This results in two different logical architectures, namely a central SW-Subsystem architecture as a refinement of the initial logical architecture. Due to the consequent usage of the UIM this is syntactically and semantically possible and has no effect of the con-text of the SuD in the logical view.

#### Technical Viewpoint
Similar to the functional and logical view, a context can be modeled within the technical view. The technical context focusses on modeling the current SuD in re-lation to technical relevant context elements, e.g. human actors, technical external systems, or physical context element. The technical system boundary and the technical context are specified in the Technical Context Diagram. We call ele-ments of the technical context technical context systems.
  
(Figure 5 5 Example of technical context system)

Figure 5 5 illustrates three technical context systems. On the right hand side various more specific external elements are illustrated, e.g. external mechanical component, or external mechatronic component, representing the possibility in the technical viewpoint to consider more engineering domain-specific modeling arti-facts (compare section LINK: Technical Viewpoint)

#### Relations between context elements
Model elements of different view can in general have tracing relations. (com-pare LINK: Tracing Chapter), meaning that a model element in one view can be “implemented” or “realized” by elements of another view. This hold not only for elements of the SuD, as described in LINK: Tracing Chapter but also for context elements, as these elements are obviously not independent from each other. Im-portant to mentions the SuD remains the conceptually the same between these dif-ferent views.

(Figure 5 6 Relations between context elements (horizontal dimension))

Figure 5 6 illustrated the relations between context elements of the different view. In the horizontal dimension a context function from the functional view (e.g. Context Function A, is related to a context system, namely Context System A. The tracing relations between context functions and context systems are analog to the relations between systems functions and logical components. We can make use of the same principles not only because context elements as well as SuD ele-ments rely on the UIM. Context systems, thus, realize context functions or if context systems provide redundancy relations, we can make use of a realize re-dundant relationship. The argumentation is comparable to elements relations of the SuD between functional and logical view. 
Note that – as a design recommendation – we strongly recommend modeling the structural context in the logical view in such a way that there is a N:1 relation between context functions and context systems, corresponding to a white-box de-composition in the functional view. More details about relations / traces can be found in LINK: Tracing.

Furthermore, there may be context systems in the logical view that do not have a relation to context functions (e.g. Context Systems Y in Figure 5 6). These con-text systems may be added due to implementation or technical reasons. Also in the technical viewpoint there may such technical context systems with no relation to context systems (e.g. technical context systems X) for the same reason.

A context system (e.g. Context System A) can be further traced to technical context element of the technical view. We make use of the same tracing relations, as already know from SuD elements, namely either realize or realized redundant respectively. At the highest level of abstraction, we recommend a 1:1 relationship between context systems and technical context systems. More details about rela-tions / traces can be found in LINK: Tracing

### Vertical dimensions in SPES
Across granularity layers, e.g. from a system level to subsystem level, the scope of the SuD may change. In SpesML, we allow the technical components in the technical view to be viewed as independent subsystems on the next granularity level. 
Figure 5 7 illustrate such a new view of Technical Component B  of the SuD to be further engineered on the next granularity level. This can, but not necessarily need to be done, by applying SPES. If possible, than all the concepts of SPES can be applied on this granularity level as well (compare LINK: Granularity Lev-els). In such a situation, Technical Component B’ has a new scope on the subsys-tem granularity level, meaning that this component becomes the new SuD. 

 It is important to state that the new SuD, namely Technical Component B` on subsystem level may not be the exact component from the system layer, however, it is important that the interfaces remains stable.
 
(Figure 5 7 Relations between context elements in the vertical dimension)

From a context point of view, with a change of scope, meaning with a new SuD, the context elements change as well. In such a situation of a change of scope, the operational context is always defined with a reference to the SuD. In this case, there are a set of technical context systems on subsystem level. More precisely: Technical components of the SuD (e.g. Technical Component A be-comes a Technical Context System A`) on the next granularity level). This hold for all 1st grade components of the Technical Component B, including both, all tech-nical components of the SuD on system level with a direct relation to Technical Component B, as well as all 1st grade elements that have been a technical context system on system level (e.g. Technical Component D becoming Technical Com-ponent D`). 
Furthermore, as possible on all granularity levels, new technical context sys-tems (e.g. Technical Context System X) can be added due to engineering / tech-nical reasons with no relations to other views on the same granularity level.

The new SuD itself is modelled on a new granularity layer again with all hori-zontal views of the SPES viewpoints. Figure 5 8 illustrates that also on the sub-system level we can apply the same tracing relations, namely realize and realize redundant between context elements of different views, as described in chapter 5.3.1.4. For instance, Context System A is realized by Technical Context System A (compare Figure 5 8). Figure 5 1Note that also design recommendations, w.r.t. mul
