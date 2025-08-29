---
title: 'OEL'
description: 'Orka Expression Language'
icon: 'chevrons-left-right-ellipsis'
---

## Introduction

Orka's Expression Language provides a powerful way to work with dynamic data in your workflows. It allows you to reference variables, perform calculations, manipulate strings, and make decisions based on conditions—all without writing complex code. The expression language is based on the `expr-lang` package, which provides a robust and flexible expression evaluation engine.

## Expression Syntax

Expressions in Orka can be used in two main ways:

1. Interpolation: Using double curly braces `{{ }}` to insert dynamic values into strings
2. Direct evaluation: Used in nodes like If Node and Set Variable Node for condition checking and variable assignment.

### Basic syntax:

```
{{ expression }}
```

Where expression can be a simple variable reference, a mathematical calculation, a string operation, or a complex condition.

### Variable Interpolation

Variable interpolation allows you to insert dynamic values into strings. This is particularly useful for HTTP requests, messages, and other text-based operations.

#### Examples

```
"Hello, {{name}}!"
"Your order #{{orderId}} has been processed."
"Total amount: ${{price * quantity}}"
```

During workflow execution, these expressions are replaced with their evaluated values based on the current execution context.

### Expression Evaluation

Expressions are evaluated at runtime using the current execution context, which includes:

1. Workflow variables: Variables defined in the workflow
2. Node output: Values produced by previous nodes
3. Initial variables: Variables set when the workflow is triggered

The evaluation process follows these steps:

1. Parse the expression
2. Compile it against the current variable environment
3. Execute the compiled expression
4. Return the result

### Supported Operations

Orka's expression language supports a wide range of operations:

#### Arithmetic Operations

```
5 + 3        // Addition: 8
10 - 4      // Subtraction: 6
6 * 7        // Multiplication: 42
15 / 3       // Division: 5
10 % 3       // Modulo: 1
2 ** 3      // Exponentiation: 8
```

#### Comparison Operations

```
x > y       // Greater than
x >= y      // Greater than or equal to
x < y      // Less than
x <= y // Less than or equal to
x == y // Equal to
x != y // Not equal to      // Not equal to
```

#### Logical Operations

```
x && y // Logical AND
x || y // Logical OR
!x     // NOT x       // Logical NOT
```

#### String Operations

```
"Hello, " + name           // Concatenation
message.contains("error")    // String contains
message.startsWith("Hello")  // String starts with
message.endsWith("!")        // String ends with
message.length()            // String length
```

#### Conditional Expressions

```
condition ? trueValue : falseValue
```

#### Objects & Arrays

```
user.name            // Object property access
items[0]             // Array index access
data["key"]          // Map key access
```

### Built-in Functions

```
len(array) // Length of array
abs(-10)   // Absolute value: 10
round(3.7) // Round: 4
floor(3.7) // Floor: 3
ceil(3.7)  // Ceiling: 4
```

### Working with Secrets

Orka provides special syntax for securely accessing secrets:

```
{{ secrets.API_KEY }}
```

When a secret reference is used, the engine:

1. Recognizes the secrets. prefix
2. Securely resolves the secret value
3. Inserts the value without storing it in the execution context

This ensures that sensitive information is never persisted in logs or execution history.