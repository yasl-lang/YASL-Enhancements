# YAEP 100

| YAEP | 100 |
|------|---|
| Title | Multiple Assignments for YASL |
| Version | 1 |
| Author | CTE |
| Status | Proposed |
| Type | Enhancement |

## Introduction
This YAEP describes the _multiple assignments_ proposal for YASL.

## Proposed Semantics
The following code would be legal in YASL if this proposal is accepted:

    x, y, z = 1, 2, 3
    let x, let y, let z = 1, 2, 3
    x, let y, z = 1, 2, 3
    const x, y, let z = 1, 2, 3

In the first example, all variables have previously been declared. 
In the second, no variables have previously been declared.
In the third, `y` is declared, but `x` and `z` are not.
In the final example, `x` is const, `y` was previously declared, 
and `z` is newly declared.

Note that if _multiple assignments_ are used with `let` or `const`, the `let` or `const` applies _only_ to the variable 
directly to the right of it.

Multiple assignments features indexing are also possible: `x[1], y = 1, 2` is allowed, for example.
