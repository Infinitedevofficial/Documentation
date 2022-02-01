**Last Update: 29/01/2022**


Built in Libraries: ffi bit

<a name="-1"></a>

|Index|
|--------|
|[Penetration](#0)| 
|[Trace](#1)| 
|[Engine](#2)| 
|[DebugOverlay](#3)| 
|[ClientState](#4)| 
|[Event](#5)| 
|[Netvars](#6)| 
|[GlobalVariables](#7)| 
|[InputSystem](#8)| 
|[Memory](#9)| 
|[Cvar](#10)| 
|[AntiAim](#11)| 
|[Client](#12)| 
|[Fakelag](#13)| 
|[HTTP](#14)|
|[HTTPS](#15)|
|[Menu](#16)|
|[Doubletap](#17)|
|[EntityList](#18)|
|[Paint](#19)|
|[Bits](#20)|
|[Entity](#21)|
|[Surface](#22)|
|[World](#23)|
|[Console](#24)|
|[Callback](#25)|
|[Vector](#26)|
|[Vector2D](#27)|
|[Color](#28)|
|[CGameTrace](#29)|
|[PlayerInfo_t](#30)|
|[ResolveData](#31)|
|[PaintStringRenderFlags](#32)|
|[SurfaceStringRenderFlags](#33)|
|[PaintFontCreationFlags](#34)|
|[Stages](#35)|

---

# <a name="0"></a>Menu
---

### Menu.CreateMenu


#### Parameters:

| Name | Type | Description |
| :--- | :--- | :--- |
| Position | Vector2D | start position |
| Size | Vector2D | size of the menu |
| Name | string | name of the menu |
| Closable | bool | if true the menu can be closed |

#### Returns:

| Name | Type | Description |
| :--- | :--- | :--- |
| MenuHandle | int | Handle of the new menu |


```lua
Menu.CreateMenu(Vector2D.new(40,40),Vector2D.new(365,150),"Test Menu", true)
```





[back to Contents](#-1)

---
