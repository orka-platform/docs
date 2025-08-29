# Condition (If) Node

        Enables branching based on a boolean expression.

        ## Expression Engine
        - JavaScript‑like syntax via `expr-lang`
        - Accesses workflow variables and execution context
        - Evaluated at runtime

        ## Properties
        - **Expression** — uses expr‑lang. You can reference execution variables.

        ### Operators & Functions (examples)
        ```
// Numeric
age >= 18
score > 80
count <= 100

// String
status == "active"
role != "admin"
name != ""

// Boolean
isEnabled
!isBlocked
hasPermission == true

// Logical
isActive && hasPermission
isVIP || orderTotal > 1000
!isBlocked

// Math
total + tax
price * quantity
score / maxScore
attempts % maxAttempts

// Built-ins
len(name) > 0
contains(email, "@")
startsWith(role, "admin")
endsWith(filename, ".txt")
abs(score); min(a,b); max(a,b); round(pct)
        ```
