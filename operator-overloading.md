# Operator Overloading

The following operators should be overloadable, with the following names:

- `[]`: `__set` and `__get` (as l-value and r-value)
- `**`: `__pow`
- `+`: `__pos` (unary), `__add` (binary)
- `-`: `__neg` (unary), `__sub` (binary)
- `len`: `__len`
- `^`: `__bnot` (unary), `__bxor` (binary)
- `*`: `__mul`
- `/`: `__div`
- `//`: `__idiv`
- `%`: `__mod`
- `<<`: `__bshl`
- `>>`: `__bshr`
- `&`: `__band`
- `&^`: `__bandnot`
- `|`: `__bor`
- `~`: `__concat`

In the future, the following could also be overloaded:
- `()`: `__call`
- `<`: `__lt`
- `<=`: `__le`
- `>`: `__gt`
- `>=`: `__ge`
- `==`: `__eq`
- `!=`: `__ne`
