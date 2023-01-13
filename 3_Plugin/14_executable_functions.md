---
layout: default
title: Executable Functions
nav_order: 14
parent: SpesML Plugin
permalink: /plugin/executable_functions.html
---

# Executable Functions 

This document overviews the textual SpesML sublanguage ```SpesMLFunctions``` for
defining executable functions. The language is intended to be used for defining
functions that are hard or impossible to directly express in [state machines](/plugin/state_machines.html).
The models of the language can be imported by state machines to use the functions in
the guards and effects of the state machine's transitions. 

## Modules 

The ```SpesMLFunctions``` models are called _modules_. Each module optionally
starts with a _package declaration_, followed by arbitrarily many _import
statements_, and the _module definition_. For instance, the following listing
depicts an excerpt of a module. The package of the module is `a.b.c`. The module
imports the two modules `a.b.c.module1` and `a.b.module2`,
making their functions available in the current module.
The name of the
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

Each module consists of a set of functions. The functions are defined inside of
the module's body. The definition of a function starts with the function's
return type, followed by the function's name. The name is followed by a
comma-separated list of parameter definitions,
consisting of a [type](/plugin/data_types.html) and a name,
which is enclosed in round brackets.
Afterwards, the body of the function is defined between the equality sign and semicolon as a single expression. 

For example, the following listing depicts the module `sums`, which contains the
two functions `sum`. The return type of the first function is `Integer`, it has two parameters called `a, b` of type `Integer`. 
  
```java
module sums {

  Integer sum(Integer a, Integer b) =
    a + b;

  Set<Integer> sum(Set<Integer> a, Set<Integer> b) =
    a union b;

}
```

Calling a function in an expression can be done by passing parameters
according to the types listed in its definition.
E.g. using `sum` in an expression: `2 * sum(1, 3)`.

The body of each function consists of an [expression](/plugin/expressions.html).
In the executable expression language, more elaborate expressions may be used than in state machines:

### `if`-expressions

The `condition` is an expression that evaluates to a `boolean` value. If and only if the condition evaluates to `true`, the value of `expression 1` will be returned. Should it evaluate to `false`, `expression 2` will be returned instead.

```java
if /*condition*/ 
then
  //expression 1
else
  //expression 2
```

The `else`-part is not optional.
  
Example usage:
```java
Integer abs(Integer x) =
  if x >= 0
  then x
  else -x;
```
  
### `let-in`-expressions

The `assignee X` has the value of the expression `assignor X` inside the `in-expression`. `let-in`-expressions can be used to create temporary values.

```java
let /*assignee 1*/ = /*assignor 1*/;
    /*assignee 2*/ = /*assignor 2*/
in  // in-expression (using assignees)
```
  
Example usage:
```java 
Float pq1(Float p, Float q) =
  let Float p2 = p / 2
  in -p2 + sqrt(pow(p2, 2) - q);
```

## Packages

Function modules are managed in function (module) packages. Each package may contain any number of function modules and sub packages. They are used to structure functions and avoid naming conflicts. Thus they are comparable to packages of common programming languages like Java.

## Creating a function package

To create a function package you may use the following steps:

1. Navigate to the component in the containment tree which shall contain the function package.
2. Open the context menu and select *Create Element*:

![Create Element](/images/executable_functions_language/create_element.png){:width="617" :class="img-responsive"}

3. In the dialog that opens select to create a function package:

![Create Element](/images/executable_functions_language/create_function_package.png){:width="366" :class="img-responsive"}

4. Enter the packages name, in this example we choose *a*:

![Create Element](/images/executable_functions_language/created_package.png){:width="216" :class="img-responsive"}

### Creating a function sub package

To create a sub package, one may use the same steps as described above but select a function package in the containment tree to contain the new package.

Here we created sub package *b* contained in the package *a*:

![Create Element](/images/executable_functions_language/created_sub_package.png){:width="213" :class="img-responsive"}

## Creating a function module

Function modules must be contained within a package.

1. In the containment tree select a function package.
2. Open the context menu and select *Create Element*.
3. In the dialog that opens select to create a function module:

![Create Element](/images/executable_functions_language/create_function.png){:width="410" :class="img-responsive"}

4. Enter the name of the module, in this example we choose *m*:

![Create Element](/images/executable_functions_language/created_function_module.png){:width="122" :class="img-responsive"}

5. Select the newly created module by double clicking on it.
6. In the properties tab select the empty field right next to *Implementation Body*. A button with three dots will appear:

![Create Element](/images/executable_functions_language/select_body.png){:width="453" :class="img-responsive"}

7. Click on the button with the three dots to open a dialog:

![Create Element](/images/executable_functions_language/edit_body.png){:width="418" :class="img-responsive"}

8. Enter the executable function language code for the module. Note that the package declaration and name of the module must match the information stored in the containment tree; In our example the module `m` has the package declaration `a.b`:

9. Click OK to stop editing the code.

## Automatic Checks (Well-formedness Rules)

This list is limited, as it only applies to the error description
that are not applicable to [expressions](/plugin/expressions.html) in general.

| Error Description | Solution | 
| :---------------: | :------: | 
| unable to assign Type | Make sure that the type of the expression is assignable to the functions return type |
