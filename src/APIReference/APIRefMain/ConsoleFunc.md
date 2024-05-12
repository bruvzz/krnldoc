# Console Functions

## Print:
```lua
<void> rconsoleprint(<string> Text)
```
Prints `Text` into the console.

---

## Info:
```lua
<void> rconsoleinfo(<string> Text)
```
Prints `Text` into the console, with `[INFO]` written before it.

---

## Warn:
```lua
<void> rconsolewarn(<string> Text)
```
Prints `Text` into the console, with `[WARNING]` written before it.

---

## Error:
```lua
<void> rconsoleerr(<string> Text)
```
Prints `Text` into the console, with `[ERROR]` written before it.

---

## Clear:
```lua
<void> rconsoleclear(<void>)
```
Clears all text from the console.

---

## Name:
```lua
<void> rconsolename(<string> Title)
```
Sets the console's title to `Title`.

---

## Input:
```lua
<string> rconsoleinput(<void>)
```
Yields the current thread until the user inputs text and presses Enter. Returns the input they put in.

---

## Close:
```lua
<void> rconsoleclose(<void>)
```
Closes the console.

---

## Console Colors:
| Name | Type |
| :----: | :----: |
| Black | @@BLACK@@ |
| Blue | @@BLUE@@ |
| Green | @@GREEN@@ |
| Cyan | @@CYAN@@ |
| Red | @@RED@@ |
| Magenta | @@MAGENTA@@ |
| Light Gray | @@LIGHT_GRAY@@ |
| Dark Gray | @@DARK_GRAY@@ |
| Light Blue | @@LIGHT_BLUE@@ |
| Light Green | @@LIGHT_GREEN@@ |
| Light Cyan | @@LIGHT_CYAN@@ |
| Light Red | @@LIGHT_RED@@ |
| Light Magenta | @@LIGHT_MAGENTA@@ |
| Yellow | @@YELLOW@@ |
| White | @@WHITE@@ |
<p align="center">
    <img src="https://cdn.discordapp.com/attachments/775967135746621463/922084051194634240/image_1.png">
</p>

### Example:
```lua
rconsolename("console") -- Sets the name of the console to 'console'
rconsoleprint("gamer\n")
rconsoleprint("@@YELLOW@@") -- Changes the text color to Yellow
rconsoleprint("gamer but yellow\n")
rconsoleerr("omg error!")
rconsolewarn("omg warning!")
wait(3)
rconsoleclear() -- Clears all text
wait(1)
rconsoleclose() -- Closes the console
```
You must use `\n` at the end of `rconsoleprint` to make a new line.

`rconsoleinfo`, `rconsolewarn`, and `rconsoleerr` do this automatically.

### Example - Krnl Key Checker:
```lua
local domain = "https://krnl.place"
function get(dir)
    return game:HttpGet(string.format("%s/%s", domain, dir))
end
function key(color)
    rconsoleprint("[")
    rconsoleprint("@@"..color.."@@")
    rconsoleprint("KEY")
    rconsoleprint("@@LIGHT_GRAY@@")
    rconsoleprint("]")
end
function getversion()
    local ver = get("version.txt"):split("")
    return string.format("v%s.%s.%s%s%s", unpack(ver)):lower()
end
function checkingkey()
    rconsolename("krnl "..getversion())
    key("GREEN")
    rconsoleprint(" Please enter your key: ")
    local input = rconsoleinput()
    key("GREEN")
    rconsoleprint(" Checking key. (this might take some time..\n")
    if input == "key" or input == get("getkey.php"):split('value="')[2]:split('" placeholder')[1] then -- very hacky method lol
        key("GREEN")
        rconsoleprint(" Correct key!\n")
        task.wait(0.7)
        rconsoleclose()
    else
        key("RED")
        rconsoleprint(" Incorrect key!\n")
        checkingkey()
    end
end
function inject()
    rconsoleclear()
    rconsoleinfo("Checking version.")
    task.wait(0.7)
    rconsoleinfo("Scanning.")
    task.wait(1)
    key("GREEN")
    rconsoleprint(" Please get a key here: https://cdn.krnl.place/getkey\n")
    checkingkey()
end
inject()
```