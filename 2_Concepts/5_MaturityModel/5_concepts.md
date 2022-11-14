---
layout: default
title: Concepts
nav_order: 1
parent: SpesML Maturity Model
grand_parent: SpesML Concepts
permalink: /concepts/maturity_model/concepts.html
---

# Introduction
On this page, we describe the SpesML Maturity Model (SpesML MM) whose goal is to help teams adopting the SpesML methodology. The SpesML MM helps to achieve this first by mapping their current Model-based Systems Engineering (MBSE) processes using the SpesML MM, to figure out which activities are in place and must be *adapted* to the SpesML methodology. And second, by finding out unimplemented capabilities that must be *adopted* anew to reach the desired maturity level for the organization.

The SpesML MM is based on the Model-based Systems Engineering Maturity Model (MBSE MM) developed in the context of the SPEDIT project. The MBSE MM was designed having the SPES methodology as a reference framework. 

## Focus area maturity models
Maturity models are used to assess the process maturity of a development team, thus guiding further process improvement. Two approaches for implementing maturity models exist. With a top-down approach, a fixed number of maturity stages or levels is specified first and further corroborated with characteristics (typically in the form of specific assessment items) that support the initial assumptions about how maturity evolves. Prominent examples are CMMI or SPICE. 

When using a bottom-up approach, distinct characteristics or assessment items are determined first and clustered in a second step into maturity levels to induce a more general view of the different steps of maturity evolution. They are distinguished from fixed-level maturity models, such as CMMI, in that they are suited to the incremental improvement of functional domains. One class of these bottom-up maturity models is the Focus Area type, where capabilities are defined for different focus areas and arranged in a progressing order that can be mapped to maturity levels. Focus area maturity models are especially effective at providing organizations with implementable practices and processes. The capabilities are grouped in focus area which in turn are grouped in functional domains. The capabilities are positioned against each other in a maturity matrix and assigned letters according to their position (i.e., maturity progression) being the first letters of the alphabet with less maturity than letters that appear closer to the end (i.e., capability B is less mature than a capability D).  The SpesML MM is a focus area maturity model. 

![Focus area maturity model meta-model](/images/focusamm-example.png){:class="img-responsive"}

Regarding its possible use, maturity models can be descriptive, prescriptive, or comparative. A maturity model is said to be descriptive when used for assessing the development team's current state. If it suggests improvements, the model is prescriptive, and when it can be used to compare the processes of different organizations, it is also comparative. 

## MBSE Maturity Model

The  Model-based Systems Engineering Maturity Model (MBSE MM) was created during the project [SPES2020](http://spes2020.informatik.tu-muenchen.de/spes%5C_xt-home.html). It is a focus area maturity model which uses the SPES methodology as a reference framework. In the MBSE MM, functional domains are named engineering functions to emphasize the relation to engineering phases in the development process. The MBSE MM has six engineering functions that group a total of fifteen focus areas addressing the different activities that models can support. The focus areas have different capabilities amount, as modeling is not equally distributed over different engineering functions. For instance, Requirements Modeling has many practices while System Testing and Integration has only a tiny amount. The maturity level describes how well MBSE practices are implemented. 

The MBSE MM is fully descriptive, partially prescriptive, and partially comparative. Partially prescriptive because the model diminish the solution space as an assessment tool. But it lacks guidance on selecting the subsequent capabilities to implement. The model is partially comparative because comparisons can be made only at the focus area level. There is no global maturity level requiring certain capabilities and teams might need different kind of needs.

Despite the use of a reference framework, the MBSE MM is not tied to any specific development model (e.g., v-model, waterfall). The maturity levels are described in terms of generic artifacts (i.e., information bites)  generated in the development process (e.g., description of functions' interfaces), and capabilities enhancements (e.g., automatic analysis). More information on the MBSE MM can be found [here](https://www.fortiss.org/fileadmin/user_upload/05_Veroeffentlichungen/Whitepaper/fortiss_MBSE_whitepaper_web.pdf).

# The SpesML Maturity Model

The SpesML MM was created with the goal to help team in smooth adopting the SpesML methodology and tools. It helps through identification of similarities between current MBSE activities and the capabilities described in the SpesML MM. It is smooth because the capabilities are defined in small chunks that do not overburden the team during the process. 

The _Functional Domains_ of the SpesML MM were defined based on the four viewpoints supported by the SpesML Modeling Framework, namely Requirements, Functional, Logical, and Technical Viewpoints. 

There are two types of capabilities, namely the normal type and the *Conceptual* type. Capabilities of the later kind are part of the SpesML theoretic framework but the plugin provides no support for it. These are signaled with a '( C)' at the end of its description.	
