# YASL Enhancements
This repo keeps track of potential and planned features for YASL, to avoid cluttering the main repo.

Possible future features:

REPL:
- ~add a REPL~ (added in v0.3.6)

Strings:
- ~add `string.count` method.~ (added in v0.3.4)
- add `string.reverse` method.
- add string metatable.
- other types of string literals somehow: `"AB CD EF 00 11"x` for string from hex, `"0011 0011"b` for string from binary, `"你好"u` for unicode, etc.
- implement string interning with all literals.
- `s[a:b]` notation for slice.
- rename `string.repeat` to `string.rep`. [BREAKING]
- change string concatenation to `a @ b` (from `a ~ b`). [BREAKING]

Numbers:
- ~[allow underscores in numeric literals](underscores-in-numeric-literals.md) (these are simply ignored). Not allowed at start of number or directly after decimal place. e.g. (10_000, 0x_10)~ (added in v0.3.5)
- [Add exponential notation for floats](exponential-notation.md). e.g. 1e100
- Move `inf` and `nan` to `math` library. [BREAKING]
- ~add `int.toint` and `float.tofloat` (both do nothing, just for duck-typing).~ (added in v0.3.5)

Lists:
- ~method to sort lists in-place~ (added in v0.3.4)
- list concat with `+` (so that string concat always concatenates).
- list metatable.
- `l[a:b]` notation for slice.

Tables:
- metatables, to allow lookups in a second table if first look-up fails.

Userdata:
- metatables

Modules:
- `foo = require('bar.yasl')` should import the contents of `bar.yasl` and store them in a variable named `foo`. Details [here](modules.md).

`in` operator:
- check list and table containment. complement is `!in`.

For loops:
- allow iterating over two values instead of just 1. `for let i, v <- [2, 3, 5, 7] {}` would have `i` iterate over the keys, (0, 1, 2, 3) and `v` iterate over the values (2, 3, 5, 7).

Operator overloading:
- [most operators should be overloadable, using special method names](operator-overloading.md).

Libraries:
- ~[math library](std-math.md) (`math`), including things like `exp`, `sin`, `sqrt`, etc.~ (added in v0.3.4)
- UTF8 library (`utf8`), including string functions on utf8 strings.
- [I/O library](std-io.md) (`io`), including file I/O and stdin, stdout, stderr.
- coroutine library (`coroutine`), for concurrency.
- [collections library](std-collections.md) (`collection`), including collections such as `set`, `multiset`, and typed arrays.
- regex library (`re`). Something like PCRE is likely too big for usage in the standard library.

Functions:
- Implement full lexical closures.
- allow unnamed functions using `fn(a, b) { return a + b }`.
- allow `fn f.name(a, b, c) { .... }` style declarations (for tables).
- allow `expr string-literal` as a function call. e.g. `utf8'string'` would be the same as `utf8('string')`. `utf8'string'->toint()` would be the same as `utf8('string')->toint`. This would allow something similar to the string prefixes found in Python, without having to add too much to YASL.

Sequences:
- "sequences" should be added to YASL. sequences live only on the stack. Trying to use a sequence in an expression will shrink or expand the sequence to the appropriate size. e.g. if `f()` returns `1, 2`, `x, y = f()` will use both values. `x = f()` will shrink `1, 2` to fit the context it is used in, to `1` in this case. `x, y, z = f()` would expand `1, 2` to the context it is used in, filling with `undef`, so `x` would get a value of 1, `y` a value of 2, and `z` a value of `undef`.

Comprehensions:
- comprehensions should be more general, returning a sequence. This would allow stuff like `max(x for x <- ls if x > 0)`, and `set(x for x <- ls)`.
- If iterating over multiple values is allowed, comprehensions should also support this.

Loops:
- Optional `else` clause, executed if the main loop _doesn't_ `break` out.

Variables:
- Allow multiple assignments of the form `x, y, z := 1, 2, 3`. Allow `const x, y, z := 1, 2, 3` as well, which makes the first of them `const`.

Generators:
- `fn* gen(a) { /* body */ }` to declare a generator (compare with notation for function declarations).
- `-x for* x <- ls` to declare a generator from an existing iterable (compare with notation for comprehensions).
