# Krnl Library

## Require:
```lua
<table> Krnl:Require(<string> Module)
```
Returns a module.

Only modules in the Vendor library can be required. (Hook, Promise, Thread, Maid, Signal)

### Example:
```lua
local Hook = Krnl:Require("Hook")
```

---

## Load Async:
```lua
<variant> Krnl:LoadAsync(<string> Url)
```
Loads the contents of `Url` as a chunk.

Equivalent to `loadstring(game:HttpGet(Url))()`.

### Example:
```lua
Krnl:LoadAsync("https://pastebin.com/raw/A8hgfe3A")
```
```txt
-- Output
hello
```