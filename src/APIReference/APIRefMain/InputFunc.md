# Input Functions:

## Is Roblox Active:
```lua
<bool> isrbxactive(<void>)
```
Returns `true` if the main window is in focus.

This must return `true` for the other functions to work.

You do not need to call it, but the main window has to be focused for the other functions to work.

---

## Keyboard:

### Key Press:
```lua
<void> keypress(<uint> Keycode)
```
Simulates a key press for the specified `Keycode`.

You can find a list of Keycodes [here](https://learn.microsoft.com/en-us/windows/win32/inputdev/virtual-key-codes).

### Key Release:
```lua
<void> keyrelease(<uint> Keycode)
```
Simulates a key release for the specified `Keycode`.

---

## Left Mouse Button:

### Click:
```lua
<void> mouse1click(<void>)
```
Simulates a left mouse button click.

### Press:
```lua
<void> mouse1down(<void>)
```
Simulates a left mouse button press.

### Release:
```lua
<void> mouse1up(<void>)
```
Simulates a left mouse button release.

---

## Right Mouse Button:

### Click:
```lua
<void> mouse2click(<void>)
```
Simulates a right mouse button click.

### Press:
```lua
<void> mouse2down(<void>)
```
Simulates a right mouse button press.

### Release:
```lua
<void> mouse2up(<void>)
```
Simulates a right mouse button release.

---

## Mouse Movement:

### Scroll:
```lua
<void> mousescroll(<int> PX)
```
Scrolls the mouse wheel virtually by `PX` pixels.

### Move Relative:
```lua
<void> mousemoverel(<int> X, <int> Y)
```
Moves the mouse cursor relative to the current mouse position to coordinates `X` and `Y`.

### Move Absolute:
```lua
<void> mousemoveabs(<int> X, <int> Y)
```
Moves the mouse cursor relative to the top left corner of the focused window to coordinates `X` and `Y`.

---

## Example:
```lua
repeat
    task.wait()
until isrbxactive() -- Waits until Roblox is focused

local Viewport = workspace.CurrentCamera.ViewportSize
mousemoveabs(Viewport.X / 2, Viewport.Y / 2) -- Moves your cursor to the center of the window
```