---
layout: default
title: Expressions
nav_order: 11
parent: SpesML Plugin
permalink: /plugin/expressions.html
---

# Expressions

An expression computes a single strongly typed value and consists of operands, 
operators, and executable functions.

```
switchPosition == POS.OFF || output.current > 0
```

The above example is a boolean expression, i.e., an expression producing a 
boolean value. It produces the logical disjunction, i.e., logical `OR` (`||`) 
between it's left and right hand side. On the left hand side, the expressions 
references the `switchPosition` toggle and checks whether the switch is in the 
`OFF` position. On the right hand side, the output current is checked to be 
greater then `0`.

## Operands

The operands in expressions can be either of the following:
- basic literals such as `1`, `"message in a bottle"` or enumeration literals 
such as `POS.OFF`
- references to contextually available handles such as [value properties](
/plugin/spes_sysml_mapping.html#universal-interface-model), [ports and their
channels](/plugin/universal_interface_model.html), and [local variables](/plugin
/executable_functions.html#let-in-expressions)
- expressions themselves, allowing complex formulations

## Operators

Operators perform operations on their operands. Operators define the number
and type of their arguments, as well as their return type. Any non type-
correct use of an operator or non-resolvable reference will lead to validation
failured.

`switchPos == POS.OFF` will raise a validation error because the reference to
`switchPosition` is spelled incorrectly.

`switchPosition == DIRECTION.UP` will raise a validation error because the
types of left and right hand side are not compatible.

Operators evaluate in a specific order that is determined by their precedence 
and associativity. The operator with the higher precedence evaluates first. For 
example, multiplication has higher precedence than addition.

`1 + 2 * 3` evaluates as `1 + (2 * 3)` which is `7`.

If two operators have the same precedence, then the operators are applied in 
order of associativity. For example, multiplication and division have the same 
precedence. The associativity of these operators is left to right; therefore, 
the operator on the left evaluates first.

`6 / 2 * 3` evaluates as `(6 / 2) * 3` which is `9`.

Operators are classified into arithmetic, assignment, comparison, and logical 
operators.

### Arithmetic Operators

Arithmetic operators perform mathematical operations. They apply to numbers and 
return a number.

| Operator | Name | Example | Description |
| :------: | :--: | :-----: | :---------: |
| `+` | Addition | `a + b` | Addition `a` and `b` |
| `-` | Subtraction | `a - b` | Substract `b` from `a` |
| `*` | Multiplication | `a * b` | Multiply `a` and `b` |
| `/` | Division | `a / b` | Devide `a` by `b`|
| `%` | Moduls | `a % b` | Reminder of deviding `a` by `b` |
| `++` | Increment | `++a` | Increment `a` by `1` |
| `--` | Decrement | `--a` | Decrement `a` by `1` |

### Assignment Operators

An assignment operator assigns a value to a variable or port.
The variable or port the value is assigned to is defined on the left-hand side.
The value is defined on the right-hand side.
The variable or port and assigned value must have compatible types.

`a = 2` assigns the value `2` to a variable or port called `a`.

Variations of the assignment operator abbreviate combinations of assignment and 
other operators.

| Operator | Example | Abbreviation for |
| :------: | :-----: | :--------------: |
| `=` | `a = 5` | `a = 5` | 
| `+=` | `a = 5` | `a = a + 5` | 
| `-=` | `a = 5` | `a = a - 5` | 
| `*=` | `a = 5` | `a = a * 5` | 
| `/=` | `a = 5` | `a = a / 5` | 
| `%=` | `a = 5` | `a = a % 5` | 

### Comparison Operators

Comparison operators compare two values.
They apply to primitives and return boolean values.

| Operator | Name | Example | Description |
| :------: | :--: | :-----: | :---------: |
| `==` | Equal to | `a == b` | `true` if `a` is equal to `b` |
| `!=` | Not equal to | `a != b` | `true` if `a` is not equal to `b` |
| `>` | Greather than | `a > b` | `true` if `a` is greather than `b` |
| `<` | Less than | `a < b` | `true` if `a` is less than `b` |
| `>=` | Greather than or equal to | `a >= b` | `true` if `a` is greather than or equal to `b` |
| `<=` | Less than or equal to | `a <= b` | `true` if `a` is less than or equal to `b` |

### Logical Operators

Logical operators compare two variables or values.
They apply and return boolean values.

| Operator | Name | Example | Description |
| :------: | :--: | :-----: | :---------: |
| `&&` | Logical and | `a && b` | `true` if both `a` and `b` are `true` |
| `||` | Logical or | `a || b` | `true` if `a` or `b` is `true` |
| `!` | Logical not | `!a` | `true` if `a` is `false` |

## Executable Functions

[Executable functions](/plugin/executable_functions.html) serve as means to 
store functionality. This functionality can then be accessed in expressions by
calling the functions.

The expression `ArithmeticModule.abs(-4) == 4` calls a function `abs` stored in the 
module `ArithmeticModule` with input value `-4`. The computed absolute value is then 
compared to the desired outcome, `4`.

## Automatic Checks (Well-formedness Rules)

This list is limited, as it only applies to the most general expressions. Find
detailed explanations pertaining to specific use cases in the respective 
chapters:
* [State Machines](/plugin/state_machines.html)
* [Executable Functions](/plugin/executable_functions.html)

| Error Description | Solution | 
| :---------------: | :------: | 
| Type of expr. could not be determined | Make sure that referenced context elements exists |
|                                       | Make sure referenced elements are of compatible types |
|                                       | Make sure to formulate type-correct expressions |

## Further Thoughts

* Bit expressions
* Short circuit
