# Environment Functions

## Get Global Environment:
```lua
<table> getgenv(<void>)
```
Returns the global exploit environment.

---

## Get Roblox Environment:
```lua
<table> getrenv(<void>)
```
Returns the global Roblox environment.

---

## Get Script Environment:
```lua
<table> getsenv(<LocalScript, ModuleScript> Script)
```
Returns `Script`'s environment.

---

## Get Registry:
```lua
<table> getregistry(<void>)
Aliases: getreg
```
Returns the Lua registry.

---

## Get Garbage Collection:
```lua
<table> getgc(<bool?> IncludeTables = false)
```
Returns all functions and userdata values within the Garbage Collection.

Passing `true` will also return tables.

---

## Get Instances:
```lua
<table> getinstances(<void>)
```
Returns a table of all instances within the game. This includes nil instances.

---

## Get Nil Instances:
```lua
<table> getnilinstances(<void>)
```
Returns a table of all instances within the game that are parented to nil.

---

## Get Instance Cache:
```lua
<table> getinstancecache(<void>)
```
Returns a table of all instances within the cache.

---

## Get Scripts:
```lua
<table> getscripts(<void>)
```
Returns a table of all LocalScripts and ModuleScripts within the game.

---

## Get Loaded Modules:
```lua
<table> getloadedmodules(<void>)
```
Returns a table of all ModuleScripts that are loaded in the game.

---

## Get Connections:
```lua
<table> getconnections(<RBXScriptSignal> Signal)
```
Returns a table of all connections to the specified `Signal`.

### Connections:
| Connection | Description |
| :----: | :---: |
| .Function | The function connected to the connection. |
| :Enable | Enables the connection. |
| :Disable  | Disables the connection.  |
| :Fire | Fires the connection. |

### Example:
```lua
for i,v in pairs(getconnections(TextButton.MouseButton1Click)) do
    v:Fire() -- Fires a MouseButton1Click signal on TextButton
end

for i,v in pairs(getconnections(game.DescendantAdded)) do
    v:Fire(Instance.new("Part")) -- Can also be fired with arguments
end
```

---

## Fire Signal:
```lua
<void> firesignal(<RBXScriptSignal> Signal, <variant?> Args...)
```
Fires all the connections connected to `Signal` with `Args`.

### Example:
```lua
firesignal(TextButton.MouseButton1Click)
firesignal(game.DescendantAdded, Instance.new("Part")) -- Can also be fired with arguments
```

---

## Fire Click Detector:
```lua
<void> fireclickdetector(<Instance> ClickDetector, <number?> Distance = 0, <string?>)
Flag = "MouseClick">
```
Fires the specified `ClickDetector` with provided `Distance` and `Flag`.

If `Distance` is not provided, it will default to 0.

If `Flag` is not provided, it will default to MouseClick.

### Flags:
| Flag | Description |
| :----: | :---: |
| MouseClick | Fires ClickDetector.MouseClick. |
| RightMouseClick | Fires ClickDetector.RightMouseClick. |
| MouseHoverEnter | Fires ClickDetector.MouseHoverEnter. |
| MouseHoverLeave | Fires ClickDetector.MouseHoverLeave. |

---

## Fire Touch Interest:
```lua
<void> firetouchinterest(<BasePart> Part, <BasePart> OtherPart, <uint?> Touching = 0)
```
Fires a `Touched` event on `OtherPart` with `Part`.

The `Touching` argument must be either 0 or 1. (Touched/TouchEnded).

`TouchedPart` is the part you want to touch, and `Part` is the part you want to touch it with.

---

## Fire Proximity Prompt:
```lua
<void> fireproximityprompt(<ProximityPrompt> Prompt)
```
Fires a `Triggered` event on `Prompt`.

---

## Get Hidden Property:
```lua
<variant> gethiddenproperty(<Instance> Object, <string> Property)
```
Returns `Object`'s hidden property `Property`.

---

## Set Hidden Property:
```lua
<void> sethiddenproperty(<Instance> Object, <string> Property, <variant> Value)
```
Sets `Object`'s hidden property `Property` to `Value`.

---

### Example:
```lua
local Object = workspace.Terrain
local Property = "Decoration"
local Value = true
sethiddenproperty(Object, Property, Value)
```

### Temporary Set Hidden Property Fix:
```lua
-- If some properties dont work, execute this beforehand
getgenv().sethiddenproperty = function(obj, prop, value)
    setscriptable(obj, prop, true)
    obj[prop] = value
end
```

---

## Get Properties:
```lua
<table> getproperties(<Instance> Object)
```
Returns all properties of `Object`.

---

### Example:
```lua
local t = {}
for Property,Value in pairs(getproperties(game:GetService("Players"))) do
    table.insert(t, Property)
end
print(table.concat(t, "\n"))
```
```txt
-- Output
BubbleChat
Parent
DataCost
ClassicChat
numPlayers
Attributes
RespawnTime
localPlayer 
className 
Archivable 
archivable 
Tags 
LocalPlayer 
SourceAssetId 
NumPlayers 
ServerGitHash 
RobloxLocked 
numExpectedDirectChildren 
MaxPlayersInternal 
PreferredPlayers 
AttributesReplicate 
Name 
ClassName 
PreferredPlayersInternal 
MaxPlayers 
AttributesSerialize 
CharacterAutoLoads 
```

---

## Set Simulation Radius:
```lua
<void> setsimulationradius(<int> Radius, <int?> MaxRadius)
```
Sets the local player's `SimulationRadius` to `Radius` with optional `MaxRadius`.

---

## Get Script Bytecode:
```lua
<string> getscriptbytecode(<Instance> Script)
```
Returns `Script`'s bytecode.

---

## Get Script Hash:
```lua
<string> getscripthash(<Instance> Script)
```
Returns `Script`'s hashed bytecode. (SHA_384)

---

## Get Thread Context:
```lua
<uint> getthreadcontext(<void>)
Aliases: getthreadidentity
```
Returns the current thread context.

---

## Set Thread Context:
```lua
<void> setthreadcontext(<uint> Context)
Aliases: setidentity
```
Sets the current thread's context to `Context`.

---

## Loadstring:
```lua
<function> loadstring(<string> Chunk, <string?> ChunkName)
```
Loads `Chunk` as a Lua function with optional `ChunkName` and returns it.

---

## Set Scriptable:
```lua
<void> setscriptable(<Instance> Object, <string> Property, <bool> Scriptable)
```
Sets `Object`'s `Property` to be scriptable or not.

### Example:
```lua
print(workspace.Terrain.Decoration) -- Errors with message: Decoration is not a valid member of Terrain "Workspace.Terrain"

setscriptable(workspace.Terrain, "Decoration", true) -- Sets the "Decoration" property to be scriptable

print(workspace.Terrain.Decoration) -- Works without having to use gethiddenproperty!
```
<ins>Non-scriptable properties are also known as hidden properties.</ins>

---

## Get Callback Value:
```lua
<function> getcallbackvalue(<Instance> Object, <string> Signal)
Aliases: getcallbackmember
```
Allows you to get the function back from callbacks. This value is traditionally write-only.

### Example:
```lua
local event = Instance.new("BindableFunction")
event.OnInvoke = print 

local callback = getcallbackvalue(event, "OnInvoke")
callback("example")
```
```txt
-- Output
example
```

---

## Get Module Unlocked:
```lua
<bool> getmoduleunlocked(<ModuleScript> Module)
```
Returns true if `Module` is unlocked.

---

## Set Module Unlocked:
```lua
<void> setmoduleunlocked(<ModuleScript> Module, <uint> Unlocked)
```
Sets `Module`'s unlocked state to `Unlocked`.