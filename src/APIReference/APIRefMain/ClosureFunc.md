# Closure Functions

## Check Caller:
```lua
<bool> checkcaller(<void>)
```
Returns `true` if the current thread was created by Krnl.

---

## Get Script Closure:
```lua
<function> getscriptclosure(<Instance> Script)
```
Returns a new copy of `Script`'s closure.

---

## New C Closure:
```lua
<function> newcclosure(<function> f)
```
Pushes a new C closure that invokes the function `f` upon call.

---

## Hook Function:
```lua
<function> hookfunction(<function> Old, <function> New)
Aliases: hookfunc
```
Hooks function `Old`, replacing it with the function `New`. The old function is returned, you must use this function in order to call the original function.

`New` must be a Lua closure.

`New` cannot have more upvalues than `Old`.

### Example:
```lua
local old
old = hookfunction(print, function(text)
    return old(text:reverse())
end)

print("123")
```
```txt
-- Output
321
```

---

## Is C Closure:
```lua
<bool> iscclosure(<function> f)
```
Returns `true` if `f` is a C closure.

---

## Is Lua Closure:
```lua
<bool> islclosure(<function> f)
```
Returns `true` if `f` is a Lua closure.

---

## Is Krnl Closure:
```lua
<bool> iskrnlclosure(<function> f)
Aliases: checkclosure, isexecutorclosure
```
Returns `true` if `f` is a Krnl closure. 

This is a custom function integrated with Krnl.

---

## Get Calling Script:
```lua
<Instance> getcallingscript(<void>)
```
Returns the script that is calling the current function.