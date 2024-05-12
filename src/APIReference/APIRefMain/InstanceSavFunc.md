# Instance Saving Functions

## Save Instance:
```lua
<void> saveinstance(<Instance?> Object, <string?> FilePath, <table?> Options)
```
Saves the current game into your workspace folder as a `.RBXL` file.

If `Object` is specified, it will save that object and its descendants as a `.RBXM` file.

If `Object` is `game`, it will be saved as a `.RBXL` file.

If `FilePath` is specified, it will write the file to the specified path.

`FilePath` does not need to contain a file extension, only the name of the file.

### Options:

| Name | Type | Default | Description |
| :---- | :---- | :---- | :---- |
| Decompile | Boolean | false | If enabled, `LocalScripts` and `ModuleScripts` will be decompiled. |
| DecompileTimeout | Number | 10 | If the decompilation run time exceeds this value, it will be canceled. This value is in seconds. |
| DecompileIgnore | Table | {"Chat", "CoreGui", "CorePackages"} | Scripts that are a descendant of the specified services will be saved but not decompiled. |
| NilInstances | Boolean | false | If enabled, instances parented to `nil` will be saved. |
| RemovePlayerCharacters | Boolean | true | If enabled, player characters will not be saved. |
| SavePlayers | Boolean | false | If enabled, Player objects and their descendants will be saved. |
| MaxThreads | Number | 3 | The number of decompilation threads that can run at once. More threads allow for more scripts to be decompiled at the same time. |
| ShowStatus | Boolean | true | If enabled, Save Instance progress will be displayed. |
| IgnoreDefaultProps | Boolean | true | If enabled, default properties will not be saved. |
| IsolateStarterPlayer | Boolean | true | If enabled, `StarterPlayer` will be cleared and the saved starter player will be placed into folders. |

### Example - Saving the game to a custom folder:
```lua
makefolder("MySaves")
saveinstance(game, "MySaves/Cool Game")
```

### Example - Saving a specific object with decompiled scripts:
```lua
saveinstance(workspace.CoolModel, "Cool Model", {
    Decompile = true
})
```

---

## Decompile:
```lua
<string> decompile(<Instance> Script)
```
Decompiles `Script` and returns the decompiled output.

### Example:
```lua
local LocalPlayer = game:GetService("Players").LocalPlayer 
local PlayerModule = LocalPlayer.PlayerScripts.PlayerModule
local Decompiled = decompile(PlayerModule) -- Decompiles PlayerModule
setclipboard(Decompiled) -- Copies the decompiled output to your clipboard
```