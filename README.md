# YASL Enhancements
This repo keeps track of potential and planned features for YASL, to avoid cluttering the main repo.

Possible future features:

Strings:
- add `string.reverse` method.
- add string metatable.
- add `\uNNNN` escapes in string literals.
- add `\UNNNNNNNN` escapes in string literals.
- change string concatenation to `a @ b` (from `a ~ b`). [BREAKING]

Numbers:
- ~[Add exponential notation for floats](exponential-notation.md). e.g. 1e100~ (added in v0.5.0)
- add "character literals". These would have type `int`, based on the character code given. examples would be `?a` for `0x61`, `?\n` for `0x0A`, or `??` for `0x3F` (all assuming we're using ASCII).

Lists:
- list metatable.

Tables:
- metatables, to allow lookups in a second table if first look-up fails.

Userdata:
- metatables

`in` operator:
- check list and table containment. complement is `!in`.

For loops:
- allow iterating over two values instead of just 1. `for let i, v <- [2, 3, 5, 7] {}` would have `i` iterate over the keys, (0, 1, 2, 3) and `v` iterate over the values (2, 3, 5, 7).

Operator overloading:
- [most operators should be overloadable, using special method names](operator-overloading.md).

Libraries:
- UTF8 library (`utf8`), including string functions on utf8 strings.
- [I/O library](std-io.md) (`io`), including file I/O and stdin, stdout, stderr.
- coroutine library (`coroutine`), for concurrency.
- [collections library](std-collections.md) (`collection`), including collections such as `set`, `multiset`, and typed arrays.
- regex library (`re`). Something like PCRE is likely too big for usage in the standard library.

Functions:
- Implement full lexical closures.
- allow unnamed functions using `fn(a, b) { return a + b }`.
- ~allow `fn f.name(a, b, c) { .... }` style declarations (for tables).~ (added in v0.5.0)
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

Internal Changes:
- Fold method calls involving literals at compile time.
- Fold anything involving `const` variables that can be determined at compile time.
- Fold conditionals at compile time.
- implement string interning with all literals.
