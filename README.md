# YASL Enhancements
This repo keeps track of potential and planned features for YASL, to avoid cluttering the main repo.

Possible future features:

Strings:
- ~make strings iterable (iterating over each 'character').~ (added in v0.3.0)
- add `string.count` method.
- add `string.reverse` method.
- add string metatable.
- other types of string literals somehow: `"AB CD EF 00 11"x` for string from hex, `"0011 0011"b` for string from binary, `"你好"u` for unicode, etc.

Numbers:
- [allow underscores in numeric literals](underscores-in-numeric-literals.md) (these are simply ignored). Not allowed at start of number or directly after decimal place. e.g. (10_000, 0x_10)
- Add exponential notation for floats. e.g. 1e100

Lists:
- method to sort lists in-place
- method to join list elements into a single string.
- `tostr` and printing should show contents instead of memory address.
- list concat with `+` (so that string concat always concatenates).
- `list.clear` method.

Tables:
- `tostr` and printing should show contents instead of memory address.'
- metatables, to allow lookups in a second table if first look-up fails.
- `table.clear` method.

Userdata:
- metatables

Modules:
- `require 'path'` should import the contents of `path` and put them into a table. (Tables can be used instead of another module system.)

`in` operator:
- check list and table containment. complement is `!in`.

For loops:
- allow iterating over two values instead of just 1. `for let i, v <- [2, 3, 5, 7] {}` would have `i` iterate over the keys, (0, 1, 2, 3) and `v` iterate over the values (2, 3, 5, 7).

Operator overloading:
- [most operators should be overloadable, using special method names](operator-overloading.md).

Libraries:
- [math library](std-math.md) (`math`), including things like `exp`, `sin`, `sqrt`, etc.
- UTF8 library (`utf8`), including string functions on utf8 strings.
- [I/O library](std-io.md) (`io`), including file I/O and stdin, stdout, stderr.
- coroutine library (`coroutine`), for concurrency.
- [collections library](std-collections.md) (`collection`), including collections such as `set`, `multiset`, and typed arrays.
- regex library (`re`). Something like PCRE is likely too big for usage in the standard library.

Functions:
- Implement full lexical closures.
- allow unnamed functions using `fn(a, b) { return a + b }`.
- `const` functions.
- `const` function parameters.
- allow `fn f.name(a, b, c) { .... }` style declarations (for tables).

Sequences:
- "sequences" should be added to YASL. sequences live only on the stack. Trying to use a sequence in an expression will shrink or expand the sequence to the appropriate size. e.g. if `f()` returns `1, 2`, `x, y = f()` will use both values. `x = f()` will shrink `1, 2` to fit the context it is used in, to `1` in this case. `x, y, z = f()` would expand `1, 2` to the context it is used in, filling with `undef`, so `x` would get a value of 1, `y` a value of 2, and `z` a value of `undef`.

Comprehensions:
- comprehensions should be more general, returning a sequence. This would allow stuff like `max(x for x <- ls if x > 0)`, and `set(x for x <- ls)`.
- If iterating over multiple values is allowed, comprehensions should also support this.

Loops:
- Optional `else` clause, executed if the main loop _doesn't_ `break` out.

Generators:
- `fn* gen(a) { /* body */ }` to declare a generator (compare with notation for function declarations).
- `-x for* x <- ls` to declare a generator from an existing iterable (compare with notation for comprehensions).
