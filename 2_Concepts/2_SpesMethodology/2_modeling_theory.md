---
layout: default
title: Underlying Modeling Theory
nav_order: 2
parent: SPES Methodology
grand_parent: SpesML Concepts
permalink: /concepts/methodology/modeling_theory.html
---
# Underlying Modeling Theory

Modeling theories comprise a number of modelling techniques. Modelling
techniques usually offer syntactic forms, in the end modelling
languages, the meaning of which may be formalized by giving semantics to
the syntactic forms. In addition to concrete syntax, abstract syntax may
be described. Semantics may be formally given by mathematical
constructs, mathematical elements, sets, relations, functions,
predicates plus a logical calculus to derive logical properties from the
syntactic forms. This is what we call *abstract formal models*. Concrete
and abstract syntax and the corresponding abstract formal models
together with a logical calculus form a *modelling theory*.

*An abstract formal model (or in short “abstract model”) is a formal
model without concrete syntax.*

*A modelling theory is provides a concept with a modelling language,
whose models are formulated in some mathematical or logical way, that
allow us to manipulate, transform, and reason about these models in
semantically useful ways.*

### Model Based System Development

It is the ultimate goal of modelling techniques to describe properties
of real life systems. The understanding of syntactic forms as well as
their semantics as descriptions of properties of real life systems is
called the pragmatics of the modelling theories.

Typically, a family of different modelling techniques are used to
describe a set of views. In an approach to model based system
development, a set of views is defined that are to be worked out in the
course of system development. Typically, views may overlap and be in
relationships to each other. This has to be reflected in the modeling
theories, its models, and their mutual dependencies.

In the end, system modelling development frameworks define a number of
views based on modelling theories that capture all aspects of system
development. Typically, some of the modelling techniques are used in a
number of views.

### Model Oriented Description Techniques

For model oriented description techniques, we find similar structures as
for modelling theories.

*The concrete syntax of a modelling language is used to describe the
concrete representation of the models and is used by humans to read,
understand, and create models. The concrete syntax must be sufficiently
formal to be processable by tools.*

A model oriented description technique may have several concrete
representations and therefore different forms of concrete syntax.

*The abstract syntax of a modeling language contains the essential
information of a model, disregarding all details of the concrete syntax
that do not contribute to the model’s purpose. It is of particular
interest for use by software tools and semantic definitions.*

A model oriented description technique thus needs an abstract syntax. In
for example SysML and UML, this is defined using metamodeling
techniques.

*A metamodel is a model describing the abstract syntax of a language.
Metamodels are usually defined using a class diagram, a grammar, or a
mathematical structure.*

Class diagrams are well suited and precisely defined to define such an
abstract syntax, but exhibit some challenges when defining semantics,
and logical calculus for properties and reasoning. For that purpose, a
mathematical structure, such as e.g. mathematical and logical
descriptions of state machines are better suited.

### Expressive Power

A highly relevant aspect is the expressive power of a description
technique and the related modeling theory. There are many different
aspects and properties of systems. In principle, we may talk about all
of those by using natural language, however, rarely in sufficient
precision. Modeling theories and formal description techniques are much
more precise. However, they always address only a subset of the
properties of systems. This defines their expressive power. Moreover,
only pragmatics supports the interpretation of the descriptions in terms
of properties of real world systems.

## The SPES Approach

The SPES approach is based on a number of specific scientific modeling
theories and calculi for the modeling of systems. Apart from meanwhile
well-established ways of specifying and describing data structures,
apart from general ideas of typing, in particular, strong typing, and
the related calculi and formalisms, one of the key concepts of SPES is a
specific notion of a system, being an interactive entity that operates
and interacts concurrently with other systems including its context and
users by exchanging messages over its interfaces.

In principle, there are a number of different possibilities to provide a
fundamental scientific theory and framework for systems. Within SPES,
the modeling technique <span class="smallcaps">Focus</span>[^1] is used.
We just give a brief overview on the concepts used in the theory. An
in-depth description of the theory can be found in the literature.

The following essentials of the modeling approach are briefly outlined:

-   Untimed and timed Streams

-   System Specification

    -   Syntactic Interfaces

    -   Interface Behavior

-   System Composition and Decomposition

-   Refinement

    -   Property Refinement

    -   Representation Refinement

**Streams**<span class="smallcaps">. Focus</span> is based on streams.
Streams are finite or infinite sequences of messages where the
considered sets of messages can take a broad range – from signals,
simple messages to very complex ones such as data bases or screens and
much more.

Within SPES two types of streams are studied:

-   *time-free streams* which are finite or infinite sequences of
    messages, and

-   *time-dependent streams* represented an infinite number of time
    intervals of equal length with finite sequences of messages in each
    time interval. Each interval is identified by a positive natural
    number.

**System Specification, syntactic interfaces, interface behavior**.
Based on the ideas of streams the idea of a *syntactic interface* is
specified. The syntactic interface of a system is given by a set of
channels divided into two subsets, the set of input channels and the set
of output channels. For each channel a data type is specified.

For a channel set a *history* associates a stream with each channel
carrying messages of the specified type. The streams may be timed or
untimed leading to timed or untimed histories. A behavior is represented
by a function or a relation between the input and output histories.

Untimed behavior is represented in the deterministic case by *prefix
monotonic functions* from untimed input and output histories or in the
nondeterministic case by sets of such monotonic functions. For timed
streams special rules for the time flow are used. Timed behaviors are
represented by *strongly causal* and *fully realizable relations*.
Basically, strong causality requires that output till time t+1 may only
depend on input received till time t. Full realizability guarantees that
there exists a set of strongly causal functions that represent the
relation. In fact, this implies the existence of a strategy which
produces for a given input history interval-by-interval an output
history interval-by-interval which leads to infinite output histories
that fulfill the relation. For untimed streams we work with prefix
monotonicity, for timed streams strong causality, and full
realizability. System are specified by *interface assertions* which are
logical formulas with the channels as free, logical identifiers standing
for streams.

**System composition and decomposition**. Prefix monotonic functions or
fully realizable relations immediately guarantee the existence of
fixpoints which is essential for defining the *composition* of systems
including *feedback loops* and also to derive proof rules.

Systems are composed by linking their systems specifications. For system
behaviors which in the case of untimed streams are represented by sets
of monotonic functions or in the case of timed streams by specifications
by fully realizable relations composition is straightforward. Systems
are composed in terms of their syntactic interfaces. Systems are
*composable* if the subset of their set of output channels of the
systems to compose that match with input channels of the systems to
compose fit together with respect to their types. This requires that for
every input channel of one component that is identical to an output
channel of another component their data types are identical.

Sets of composable systems specified by interface assertions are
composed to *composite systems* specified by interface assertions being
the result of *the logical conjunction* of the interface assertions of
the systems to compose. Thus composition of system specifications is
achieved by the conjunction of the specifications for the systems where
the specification is written in terms of interface assertions that
relate input and output streams. If the system specifications of the
systems to compose are fully realizable then the specification of the
composite system resulting by logical conjunction is fully realizable.

**Refinement**. A refinement derives a more detailed specification from
a more abstract specification. A refinement thereby preserves certain
properties of the abstract specification in the concrete specification.
Thus, refinements introduce formal relationships between system
specifications. For systems specifications two concepts of *refinement*
are available.

**Property Refinement**. For a given system specification a *property
refinement* is obtained by adding additional properties to the system
specification such that a refined system specification is logically
stronger. Therefore, for a refined system all the properties that are
implied by the refined systems are also properties applied by the
original system or – putting it the other way – all the properties of
the original systems are implied by the refined system.

**Representation Refinement**. A more sophisticated form of refinement
is *representation refinement*. Hereby we replace the input and output
channels of the given system by different families of input and output
channels. For representation refinement, there are relations required
that relate the input histories of the original systems to the input
histories of the refined system and relations that relate the output
streams of the refined systems to those of the original system. In both
cases, relations specify the representations of the original histories
by refined ones. This way each behavior of the refined systems can be
related to a behavior of the original systems in terms of these
relations between the input and output histories. The system behaviors
related that way are required to be in the property refinement relation.

[^1]: For Details on the FOCUS theory see Broy, M.: “A Logical Basis for
    Component-Oriented Software and Systems Engineering”, Springer, 2010.
