# Debug Library

## Get Constant:
```lua
<variant> debug.getconstant(<function> f, <int> idx)
Aliases: getconstant
```
Returns the constant at index `idx` in `function` `f` or level `f`. 

### Example:
```lua
local idx = 1
local isReady = false
function f()
    if idx > 0 then
        print(isReady and 'Can initiate an ability' or 'Cannot initiate an ability')
    elseif idx == 0 then
        print('bruh moment')
    end
end
print(getconstant(f, 2))
```
```txt
-- Output
false
```

---

## Get Constants:
```lua
<table> debug.getconstants(<function> f)
Aliases: getconstants
```
Returns the constants in `function` `f` or at level `f`. 

### Example:
```lua
local idx = 1
local isReady = false
function f()
    if idx > 0 then
        print(isReady and 'Can initiate an ability' or 'Cannot initiate an ability')
    elseif idx == 0 then
        print('bruh moment')
    end
end

table.foreach(getconstants(f),print)
```
```txt
-- Output
1 0
2 print
3 Can initiate an ability
4 Cannot initiate an ability
5 bruh moment
```

---

## Set Constant:
```lua
<void> debug.setconstant(<function> f, <int> idx, union<number, bool, string> value)
Aliases: setconstant
```
Set constant `idx` to tuple `value` at level or `function` `f`.

---

## Get Upvalue:
```lua
<variant> debug.getupvalue(union<function, number> f, <number> idx)
Aliases: getupvalue
```
Returns the `upvalue` with name `idx` in `function` or level `f`.

### Example:
```lua
local usable = false;
local duration = 5;
local start = tick();

function f()
    if not usable then
        if duration > (tick()-start) then
            print('You cannot use this yet!')
            return
        end

        print('Executing the ability!')
    end
end

print(getupvalue(f, 1))
```
```txt
-- Output
false
```

---

## Get Upvalues:
```lua
<table> debug.getupvalues(<function> f)
Aliases: getupvalues
```
Retrieve the upvalues in `function` `f` or at level `f`.

### Example:
```lua
local idx = 1
local isReady = false
function f()
    if idx > 0 then
        print(isReady and 'Can initiate an ability' or 'Cannot initiate an ability')
    elseif idx == 0 then
        print('bruh moment')
    end
end

table.foreach(getupvalues(f),print)
```
```txt
-- Output
1 1
2 false
```

---

## Set Upvalue:
```lua
<void> debug.setupvalue(<function> f, <int> idx, <table> value)
Aliases: setupvalue
```
Set `upvalue` `idx` to `value` at level or `function` `f`.

### Example:
```lua
local usable = false;
local duration = 5;
local start = tick();

function f()
    if not usable then
        if duration > (tick()-start) then
            print('You cannot use this yet!')
            return
        end

        print('Executing the ability!')
    end
end

debug.setupvalue(f, 2, 0) -- on the index of 2, which is the duration

f()
```
```txt
-- Output
Executing the ability!
```

---

## Get Proto:
```lua
<table, function> debug.getproto(<function> f, <int> idx, <bool?> activated)
Aliases: getproto
```
Gets the inner `function` of `f` at `index`.

---

## Get Protos:
```lua
<table> debug.getprotos(<function> f)
Aliases: getprotos
```
Returns a `table` containing the inner `function` `f`.

### Example:
```lua
function f()
    function f1()
        print('hello from function f1')
    end

    function f2()
        print('hello from function f2')
    end
end

for i,v in pairs(getprotos(f)) do
    v()
end
```
```txt
-- Output
hello from function f1
hello from function f2
```

---

## Get Stack:
```lua
<table> debug.getstack(<function> f, <int> idx)
Aliases: getstack
```
Gets the method stack at level or `function` `f`.

---

## Set Stack:
```lua
<void> debug.setstack(<function> f, <int> idx, <table> value)
Aliases: setstack
```
Sets the stack indice at `indice` to `value` at level or `function` `f`.

---

## Get Registry:
```lua
<table> debug.getregistry(<void>)
Aliases: getregistry
```
Returns the Lua registry.

---

## Get Info:
```lua
<table> debug.getinfo(<function> f)
Aliases: getinfo
```
Returns a table of information about `function` `f`.

### Info:
| Name | Type | Description |
| :----: | :----: | :----: |
| name | String | The name of the function. |
| short_src | String | A shorter version of source. |
| what | String | What the function is: Lua = Lua function - C = C function
| currentline | Integer | The line that is currently active. |
| nups | Integer | The number of upvalues that the function has. |
| func | Function | The function that is active. |
| source | String | Where the function was defined. |

### Example:
```lua
table.foreach(getinfo(print), print)
```
```txt
-- Output
name print
short_src [C]
what C
currentline -1
nups 0
func function: 0x000000006a001642
source =[C]
```

---

## Info:
```lua
<variant> debug.info(<function> f, <int> idx)
Aliases: info
```
Allows programmatic inspection of the call stack.

---

## Traceback:
```lua
<string> debug.traceback(<string> message, <number> level = 1)
Aliases: traceback
```
Returns a traceback of the current function call stack as a string.

### Example:
```lua
local function a()
	print(traceback("Specific moment during a()"))
end
 
local function b()
	a()
end
 
local function c()
	b()
end
 
a()
```
```txt
-- Output
Specific moment during a()
@:2 function a
@:13
```

---

## Profile Begin:
```lua
<void> debug.profilebegin(<string> label)
Aliases: profilebegin
```
Opens a microprofiler label.

---

## Profile End:
```lua
<void> debug.profileend(<void>)
Aliases: profileend
```
Closes the top microprofiler label.

---

## Set Metatable:
```lua
<void> debug.setmetatable(<table> Table, <table> New)
```
Sets `Table`'s metatable to `New`.

An alias for `setrawmetatable`.

---

## Get Metatable:
```lua
<void> debug.getmetatable(<table> Table)
```
Returns `Table`'s raw `metatable`, bypassing the `__metatable` field.

An alias for `getrawmetatable`.

---

## Set Memory Category:
```lua
<void> debug.setmemorycategory(<string> Tag)
Aliases: setmemorycategory
```
Assigns a custom tag name to the current thread’s memory category in the Developer Console. Useful for analyzing memory usage of multiple threads in the same script which would otherwise be grouped together under the same tag/name.

---

## Reset Memory Category:
```lua
<void> debug.resetmemorycategory(<void>)
Aliases: resetmemorycategory
```
Resets the tag assigned by `debug.setmemorycategory` to the automatically assigned value (typically, the script name)