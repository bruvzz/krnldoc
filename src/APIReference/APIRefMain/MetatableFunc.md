# Metatable Functions

## Get Raw Metatable:
```lua
<table> getrawmetatable(<table> Table)
Aliases: debug.getmetatable
```
Returns `Table`'s raw metatable, bypassing the `__metatable` field.

---

## Set Raw Metatable:
```lua
<void> setrawmetatable(<table> Table, <table> New)
Aliases: debug.setmetatable
```
Sets `Table`'s metatable to `New`.

---

## Set Read Only:
```lua
<void> setreadonly(<table> Table, <bool> Value)
```
Sets `Table`'s read-only condition to `Value`.

---

## Is Read Only:
```lua
<bool> isreadonly(<table> Table)
```
Returns `Table`'s read-only condition.

---

## Hook Metamethod:
```lua
<function> hookmetamethod(<Instance> Object, <string> Metamethod, <function> f)
```
Hooks the `Metamethod` passed in `Object`'s metatable with `f`. 

A function to call the original metamethod is returned, you must use this function in order to call the original metamethod.

### Example:
```lua
-- __namecall Hook
local OldNamecall
OldNamecall = hookmetamethod(game, "__namecall", function(self, ...)
    return OldNamecall(self, ...)
end)

-- __index Hook
local OldIndex
OldIndex = hookmetamethod(game, "__index", function(self, i)
    return OldIndex(self, i)
end)

-- __newindex Hook
local OldNewIndex
OldNewIndex = hookmetamethod(game, "__newindex", function(self, i, v)
    return OldNewIndex(self, i, v)
end)
```

### Example: Basic Remote Spy
```lua
-- This should not be used as it's just an example.

-- namecalls are functions that have been called with a : (ex. RemoteEvent:FireServer())
local old -- localize the old namecall since we are hooking it (prevent errors on legitimate calls)
old = hookmetamethod(game, "__namecall", function(self, ...)
	-- self = the remote instance
	-- ...  = the arguments
	local args = {...}
	if getnamecallmethod() == "FireServer" then -- check if FireServer is the namecall method
        local Path = self:GetFullName() -- get the remote's path
        local Arguments = table.concat(args, "\n") -- concatenate the arguments into a string
		print(string.format("Path: %s\nArguments:\n%s", Path, Arguments)) -- format and print the data
		-- remote spies that print to the console are not very good, this is just an example
	end
	return old(self, ...) -- return the old namecall
end)
```