m# Other Functions

## Krnl Safe Call
```lua
<variant> KRNL_SAFE_CALL(<function> f, <variant?> Args...)
```
Calls function `f` with `Args` in a `LocalScript` environment.

---

## Handle Teleport:
```lua
<void> HANDLE_TELEPORT(<void>)
```
Handles a teleport.

---

## Unlock Module:
```lua
<void> unlockModule(<ModuleScript> Module)
```
Unlocks `Module`.

---

## Lock Module
```lua
<void> lockModule(<ModuleScript> Module)
```
Locks `Module`.

---

## Run Auto Execute Scripts:
```lua
<void> run_auto_execute_scripts(<void>)
```
Executes all scripts in your `autoexec` directory.

---

## Run Queue On Teleport Scripts:
```lua
<void> run_teleport_queue_scripts(<void>)
```
Executes all scripts that have been created with `queue_on_teleport`.

This will remove all scripts that have been created with `queue_on_teleport`.

---

## Assign Socket:
```lua
<table> assign_socket(<table> Socket, <string> Url)
```
Assigns `Socket`'s connection to `Url`.

---

## Send Socket:
```lua
<void> send_socket(<table> Socket, <string> Message)
```
Sends a message through `Socket`'s connection.

---

## Close Socket:
```lua
<void> close_socket(<table> Socket)
```
Closes `Socket`'s connection.