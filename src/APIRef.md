# API Reference
Welcome to the API Reference.
- Here, you can find all the custom functions that Krnl has.
    - You can find examples and notes for each of the functions.
- Please read below to further understand the reference.

Krnl currently has <ins>**151**</ins> custom functions! (excluding aliases)

---

## Unified Naming Convention:
<p align="center">
    <img src="https://i.imgur.com/llOZTfP.png">
</p>

Krnl follows the [Unified Naming Convention](https://github.com/unified-naming-convention/NamingStandard), which means that Krnl uses **vanilla function names** that can be found on other exploits. UNC makes it easier for script developers since **you won't have to worry about unique function names** such as `is_synapse_function`.

---

## Documentation Format:
<p align="center">
    <img src="https://i.imgur.com/L3kHrZu.png">
</p>

1. The function's full name
2. What the function returns (table, string, number, bool, etc)
    - 1. means that the return values could be **any data type**.
    - 2. `<void>` means that the function **does not have any return values**.
    - 3. `<A, B>` means that the return values can be **more than 1 data type** (ex. `<LocalScript, ModuleScript>`).
3. The actual function name
4. The data type that the parameter accepts (table, string, number, bool, etc)
    - 1. `<variant>` means that the parameter could be **any data type**.
    -  2. `<void>` means that the function **does not have any parameters**.
    - 3. means that the parameter can be **more than 1 data type** (ex. `<LocalScript, ModuleScript>`).
    - 4. `...` means there are **variable amounts of parameters**.
5. If you see a `?` after the data type, it means that that specific parameter is optional.
6. The name of the parameter
    - 1. If you see something like `IncludeTables = false`, it means that if no parameter is provided, it will default to that value. In this case, if we do `getgc()` with no parameters, it will default to `false`.
7. The function's description
    - 1. Some functions may have an example showing how the function is used below the description.

---

## Understanding Parameters:
`<T, X>` refers to functions that can return more than 1 type for that specified argument/return value.
(ex.` <LocalScript, ModuleScript>`)

`?` refers to an optional parameter. (ex. `<bool?>`)

`<void>` refers to functions with no parameters/return values.

`<variant>` refers to parameters/return values that could be any type.

`...` refers to variable amounts of parameters/return values.

`a = b` refers to the function's default value if no parameter is specified

---

## Visual Studio Code Extensions for Krnl:

- [Krnl Execute Extension](https://marketplace.visualstudio.com/items?itemName=kaisei-kto.krnl-execute)

- [krnl-vsc](https://marketplace.visualstudio.com/items?itemName=krnl.krnl-vsc)

- [Krnl Code Snippets](https://marketplace.visualstudio.com/items?itemName=zzerexx.krnl-snippets)

---

## Sources

- [Synapse X Docs](https://docs.synapse.to)

- [Script-Ware Docs](https://dev.script-ware.com/)

- [Krnl Docs](https://krnl.place/docs")

- [ProtoSmasher Docs](https://docs.protosmasher.net)

- [Roblox API Reference](https://create.roblox.com/docs/reference/engine)

*Last Updated: July 27th, 2023*

---

```js
> Closure Functions
checkcaller
clonefunction
getcallingscript
hookfunction
iscclosure
islclosure
isexecutorclosure
loadstring
newcclosure

> Instance Functions
fireclickdetector
getcallbackvalue
getconnections
getcustomasset
gethiddenproperty
gethui
getinstances
getnilinstances
sethiddenproperty
setscriptable

> Metatable Functions
getrawmetatable
hookmetamethod
getnamecallmethod
isreadonly
setrawmetatable
setreadonly

> Misc Functions
identifyexecutor
lz4compress
messagebox
queue_on_teleport
request
setclipboard
setfpscap

> Script Functions
getgc
getgenv
getloadedmodules
getrenv
getrunningscripts
getscriptbytecode
getscriptclosure
getscripthash
getscripts
getsenv
getthreadidentity
setthreadidentity
```