# Modules

YASL modules should behave as follows:
1. `foo := require('module.yasl')` imports a module from file and stores it in a variable `foo`.
2. In `module.yasl`, we can have a `return` statement that determines what is returned from `require('module.yasl')`.
3. When `require('module.yasl')` is executed, the whole `module.yasl` is executed and the result of the return is returned from the call to `require`.

Example:
`module.yasl`:
```
# module.yasl

M := {}

/* 

Add a bunch of functions and fields to M here. 

*/

return M

```

`foo.yasl`:
```
module := require(`module.yasl`)

# assuming module.yasl defined M.bar(a):
module.bar(10)

```
