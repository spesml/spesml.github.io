---
layout: default
title: Executable Functions
nav_order: 5
parent: General Overlapping Concepts
grand_parent: SpesML Plugin
permalink: /plugin/general_concepts/executable_functions.html
---
# Executable Functions

This document overviews the textual SpesML sublanguage ```SpesMLFunctions``` for
defining executable functions. The language is intended to be used for defining
functions that are hard or impossible to directly express in state machines.
The models of the language can be imported by state machines to use the functions
in the guards and effects of the state machine's transitions. 

[[_TOC_]]

## Modules 

The ```SpesMLFunctions``` models are called _modules_. Each module optionally
starts with a _package declaration_, followed by arbitrarily many _import
statements_, and the _module definition_. For instance, the following listing
depicts an excerpt of a module. The package of the module is `a.b.c`. The module
imports the two modules `a.b.c.module1` and `a.b.module2`. The name of the
module is `module3`. Its fully qualified name is `a.b.c.module3`. The body of
the module is defined after the modules name. It is enclosed by curly brackets.

```java
package a.b.c;

import a.b.c.module1;
import a.b.module2;

montifun module3 {
  // this is a single line comment
  // ... more code ...
}
```

## Functions

Each module consists of a set of functions. The functions are define inside of
the module's body. The definition of a function starts with the function's
return type, followed by the function's name. The name is followed by a
comma-separated list of parameter definitions, which is enclosed in round brackets.
Afterwards, the body of the function is defined in curly brackets. 

For example, the following listing depicts the module `sums`, which contains the
two functions `sum`. The return type of the function
`sum1` is `Integer`. The function has one parameter called `input`. 
The type of the parameter is ```FStream<Integer>```.  

```java
montifun sums {

  Integer sum(Integer x, Integer y) =
    x + y;

  Float sum(Float x, Float y) =
    x + y;

}
```

The body of each function consists of a list of an expression.
Allowed expressions are:

- constants like `5` or `"Hello"`
- type casting like `(Integer) 4.0f`
- function usage like `foo(bar, 3)`,

- operator usage like `bar * 3`   
  operator behaviour is comparable to most widely used languages   
  available on numbers: `+`, `-`, `*`, `/`, `<<`, `>>`, `%` (modulo)   
  available on String: `+`   
  available on booleans: `!`, `&&`, `||`   
  comparisons: `==`, `!=`, `<`, `<=`, `>`, `>=`   
  


- `if`-expressions: The `condition` is an expression that evaluates to a `boolean` value. If and only if the expression evaluates to `true`, the value of `expression 1`  will be returned. Should it evaluate to `false`, the value of `expression 2` will be returned instead.   
Note that the results of `expression 1` and `expression 2` must be convertable to the same type (e.g. `Integer` and `Float`).

  ```java
  if   // condition
  then // expression 1
  else // expression 2
  ```

Example usage:
  ```java
  Integer abs(Integer x) =
    if x >= 0
    then x
	else -x;
  ```
  
- `let-in`-expressions: The `assignee X` has the value of the expression `assignor X` inside the `in-expression`. `let-in`-expressions can be used to create temporary values.

  ```java
  let /*assignee 1*/ = /*assignor 1*/;
      /*assignee 2*/ = /*assignor 2*/
  in  // in-expression (using assignees)
  ```
  
Example usage:
  ```java 
  Float pq1(Float p, Float q) =
    let Float p2 = p / 2
	int -p2 + sqrt(pow(p2, 2) - q);
  ```
  
## Data Types

- Data types are not defined by models of this language.
- Data types are defined by value types in the containment tree in SpesML. 
- Value types cannot be generic.
- There are built-in generic types in this language: List\<E\>, Set\<E\>, Map\<E,F\>.
- all built-in generic types provide the methods TODO
- Types are used in the same way as in the Java programming langauge.