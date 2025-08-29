# OEL — Orka Expression Language

Based on `expr-lang`; supports interpolation and direct evaluation.

## Syntax
- **Interpolation**: `{{ expression }}`
- **Direct evaluation**: used in If/Set Variable etc.

### Examples
```
"Hello, {{name}}!"
"Order #{{orderId}} processed."
"Total: ${{price * quantity}}"
```

## Evaluation Context
- Workflow variables
- Node outputs
- Initial variables (at trigger)

Steps: parse → compile against env → execute → return result.

## Supported Operations (samples)
```
// Arithmetic
5 + 3; 10 - 4; 6 * 7; 15 / 3; 10 % 3; 2 ** 3

// Comparison
x > y; x >= y; x < y; x <= y; x == y; x != y

// Logical
x && y; x || y; !x

// Strings
"Hello, " + name
message.contains("error")
message.startsWith("Hello")
message.endsWith("!")
message.length()

// Objects & Arrays
user.name; items[0]; data["key"]
```

## Built‑in Functions
```
len(x); abs(-10); round(3.7); floor(3.7); ceil(3.7)
```

## Working with Secrets
```
{{ secrets.API_KEY }}
```
The engine resolves `secrets.*` securely at runtime without persisting values.
