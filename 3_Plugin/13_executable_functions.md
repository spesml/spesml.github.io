---
layout: default
title: Executable Functions
nav_order: 13
parent: SpesML Plugin
permalink: /plugin/executable_functions.html
---

# Executable Functions 

This document overviews the textual SpesML sublanguage ```SpesMLFunctions``` for
defining executable functions. The language is intended to be used for defining
functions that are hard or impossible to directly express in state machines. The
models of the language can be imported by state machines to use the functions in
the guards and effects of the state machine's transitions. 

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

Each module consists of a set of functions. The functions are defined inside of
the module's body. The definition of a function starts with the function's
return type, followed by the function's name. The name is followed by a
comma-separated list of parameter definitions, which is enclosed in round brackets.
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

The body of each function consists of an [expression](/plugin/expressions.html).
In the executable expression language, further expressions may be used than in state machines:

### `if`-expressions

The `condition` is an expression that evaluates to a `boolean` value. If and only if the condition evaluates to `true`, the value of `expression 1` will be returned. Should it evaluate to `false`, `expression 2` will be returned instead.

```java
if /*condition*/ 
then
  //code 1
else
  //code 2
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

## Data Types

- Data types are not defined by models of this language.
- Data types are defined by value types in the containment tree in SpesML. 
- Value types cannot be generic.
- There are built-in generic types in this language: `List\<E\>`, `Set\<E\>`.
- all built-in generic types provide the same methods as the corresponding Java types.

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



## Grammar

An explanation of the MontiCore grammar format can be found [here](https://www.monticore.de/handbook.pdf).
The MontiCore grammar of the ```SpesMLFunctions``` language can be found [here](https://git.rwth-aachen.de/spesmlgroup/spesml/-/blob/master/04_Arbeitspakete/Tooling/prototypen/textual-languages/src/main/grammars/de/monticore/SpesMLFunctions.mc4). 
The grammar (transitively) extends the other
- expression grammars
    - ```SpesMLExpressions```, which can be found [here](https://git.rwth-aachen.de/spesmlgroup/spesml/-/blob/master/04_Arbeitspakete/Tooling/prototypen/textual-languages/src/main/grammars/de/monticore/SpesMLExpressions.mc4)
    - ```CommonExpressions```, which can be found [here](https://github.com/MontiCore/monticore/blob/dev/monticore-grammar/src/main/grammars/de/monticore/expressions/CommonExpressions.mc4)
    - ```AssignmentExpressions```, which can be found [here](https://github.com/MontiCore/monticore/blob/dev/monticore-grammar/src/main/grammars/de/monticore/expressions/AssignmentExpressions.mc4)
    - ```ExpressionsBasis```, which can be found [here](https://github.com/MontiCore/monticore/blob/dev/monticore-grammar/src/main/grammars/de/monticore/expressions/ExpressionsBasis.mc4)
- literal grammars
    - ```MCLiteralsBasis```, which can be found [here](https://github.com/MontiCore/monticore/blob/dev/monticore-grammar/src/main/grammars/de/monticore/literals/MCLiteralsBasis.mc4)
    - ```MCCommonLiterals```, which can be found [here](https://github.com/MontiCore/monticore/blob/dev/monticore-grammar/src/main/grammars/de/monticore/literals/MCCommonLiterals.mc4)

- type grammars
    - ```MCBasicTypes```, which can be found [here](https://github.com/MontiCore/monticore/blob/dev/monticore-grammar/src/main/grammars/de/monticore/types/MCBasicTypes.mc4)
    - ```MCSimpleGenericTypes```, which can be found [here](https://github.com/MontiCore/monticore/blob/dev/monticore-grammar/src/main/grammars/de/monticore/types/MCSimpleGenericTypes.mc4)
    - ```MCCollectionTypes```, which can be found [here](https://github.com/MontiCore/monticore/blob/dev/monticore-grammar/src/main/grammars/de/monticore/types/MCCollectionTypes.mc4)

- statement grammars
    - ```MCCommonStatements```, which can be found [here](https://github.com/MontiCore/monticore/blob/dev/monticore-grammar/src/main/grammars/de/monticore/statements/MCCommonStatements.mc4)
    - ```MCVarDeclarationStatements```, which can be found [here](https://github.com/MontiCore/monticore/blob/dev/monticore-grammar/src/main/grammars/de/monticore/statements/MCVarDeclarationStatements.mc4)
    - ```MCStatementsBasis```, which can be found [here](https://github.com/MontiCore/monticore/blob/dev/monticore-grammar/src/main/grammars/de/monticore/statements/MCStatementsBasis.mc4)
    - ```MCReturnStatements```, which can be found [here](https://github.com/MontiCore/monticore/blob/dev/monticore-grammar/src/main/grammars/de/monticore/statements/MCReturnStatements.mc4)
- symbol grammars 
    - ```OOSymbols```, which can be found [here](https://github.com/MontiCore/monticore/blob/dev/monticore-grammar/src/main/grammars/de/monticore/symbols/OOSymbols.mc4)
   - ```BasicSymbols```, which can be found [here](https://github.com/MontiCore/monticore/blob/dev/monticore-grammar/src/main/grammars/de/monticore/symbols/BasicSymbols.mc4)
- and the basic grammar ```MCBasics```, which can be found [here](https://github.com/MontiCore/monticore/blob/dev/monticore-grammar/src/main/grammars/de/monticore/MCBasics.mc4)
