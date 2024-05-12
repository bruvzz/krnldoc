# Drawing Library

## New Drawing:
```lua
<userdata> Drawing.new(<string> Class)
```
Returns a new `Drawing object` with `Class`.

---

## Clear Drawings:
```lua
<void> Drawing.clear(<void>)
Aliases: Drawing.Clear
```
Removes all `Drawing object`'s.

---

## Fonts:
| Font | Value |
| :----: | :----: |
| UI | 0 |
| System | 1 |
| Plex | 2 |
| Monospace | 3 |

<p align="center">
    <img src="https://i.imgur.com/PSBpdpJ.png">
</p>

---

## Base Properties:
| Name | Type | Default |
| :----: | :----: | :----: |
| Visible | Boolean | false |
| Transparency | Number | 1 |
| Color | Color3 | 0, 0, 0 |
| :Remove | Function | N/A |
| :Destroy | Function | N/A |
| ZIndex | Integer | 0 |

- These properties apply to all Drawing objects.
- Transparency is the opposite than on normal GUI elements. 1 means fully opaque while 0 means fully transparent.

---

## Drawing Classes & Properties:

- `*` indicates a ***read-only*** property.
- `**` indicates a ***write-only*** property.

### Line:
| Name | Type | Default |
| :----: | :----: | :----: |
| Thickness | Number | 2 |
| From | Vector2 | 0, 0 |
| To | Vector2 | 0, 0 |

### Text:
| Name | Type | Default |
| :----: | :----: | :----: |
| Text | String | Text |
| Size | Number | 18 |
| Center | Boolean | false |
| Outline | Boolean | false |
| OutlineColor | Color3 | 0, 0, 0 |
| Position | Vector2 | 0, 0 |
| TextBounds | Vector2 | N/A |
| Font | Drawing.Fonts | Drawing.Fonts.UI |

### Image:
| Name | Type | Default |
| :----: | :----: | :----: |
| Data | String | N/A |
| Size | Vector2 | 0, 0 |
| Position | Vector2 | 0, 0 |
| Rounding | Number | 0 |

### Circle:
| Name | Type | Default |
| :----: | :----: | :----: |
| Thickness | Number | 2 |
| NumSides | Number | 250 |
| Radius | Number | 20 |
| Position | Vector2 | 0, 0 |
| Filled | Boolean | false |

### Square:
| Name | Type | Default |
| :----: | :----: | :----: |
| Thickness | Number | 2 |
| Size | Vector2 | 100, 100 |
| Position | Vector2 | 0, 0 |
| Filled | Boolean | true |

### Quad:
| Name | Type | Default |
| :----: | :----: | :----: |
| Thickness | Number | 2 |
| PointA | Vector2 | 0, 0 |
| PointB | Vector2 | 0, 0 |
| PointC | Vector2 | 0, 0 |
| PointD | Vector2 | 0, 0 |
| Filled | Boolean | false |

### Triangle:
| Name | Type | Default |
| :----: | :----: | :----: |
| Thickness | Number | 2 |
| PointA | Vector2 | 0, 0 |
| PointB | Vector2 | 0, 0 |
| PointC | Vector2 | 0, 0 |
| PointD | Vector2 | 0, 0 |
| Filled | Boolean | true |

### Example:
```lua
local Line = Drawing.new("Line")
Line.Visible = true
Line.Transparency = 1
Line.Color = Color3.fromRGB(255,255,255)
Line.From = Vector2.new(0,0)
Line.To = Vector2.new(400,200)
Line.Thickness = 1

local Text = Drawing.new("Text")
Text.Visible = true
Text.Transparency = 1
Text.Color = Color3.fromRGB(255,255,255)
Text.Text = "krln"
Text.Size = 18
Text.Center = true
Text.Outline = true
Text.OutlineColor = Color3.fromRGB(0,0,0)
Text.Position = Vector2.new(700,400)
Text.Font = Drawing.Fonts.System

local Image = Drawing.new("Image")
Image.Visible = true
Image.Transparency = 1
Image.Data = game:HttpGet("https://i.imgur.com/T80x8dv.png")
Image.Size = Vector2.new(128,128)
Image.Position = Vector2.new(130,130)
Image.Rounding = 0

local Circle = Drawing.new("Circle")
Circle.Visible = true
Circle.Transparency = 1
Circle.Color = Color3.fromRGB(255,255,255)
Circle.Thickness = 1
Circle.NumSides = 64
Circle.Radius = 100
Circle.Filled = false
Circle.Position = Vector2.new(400,400)

local Square = Drawing.new("Square")
Square.Visible = true
Square.Transparency = 1
Square.Color = Color3.fromRGB(255,255,255)
Square.Thickness = 1
Square.Size = Vector2.new(200,200)
Square.Position = Vector2.new(850,300)
Square.Filled = true

local Quad = Drawing.new("Quad")
Quad.Visible = true
Quad.Transparency = 1
Quad.Color = Color3.fromRGB(255,255,255)
Quad.Thickness = 1
Quad.PointA = Vector2.new(700,100)
Quad.PointB = Vector2.new(600,100)
Quad.PointC = Vector2.new(650,350)
Quad.PointD = Vector2.new(800,250)
Quad.Filled = false

local Triangle = Drawing.new("Triangle")
Triangle.Visible = true
Triangle.Transparency = 1
Triangle.Color = Color3.fromRGB(255,255,255)
Triangle.Thickness = 1
Triangle.PointA = Vector2.new(600,400)
Triangle.PointB = Vector2.new(500,700)
Triangle.PointC = Vector2.new(800,600)
Triangle.Filled = true

wait(10)
Drawing.clear()
```