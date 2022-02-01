**Last Update: 29/01/2022**


Built in Libraries: ffi bit

<a name="-1"></a>

|Tables|
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

### Menu.GetMainMenu

**Returns Main menu as string**

```lua
local MainMenuHandle = Menu.OpenMenu(Menu.GetMainMenu())
```

### Menu.InvalidHandle

**Returns Invalid Handle as int**

```lua
local ismenuvalid = Menu.OpenMenu("invalidmenu") == Menu.InvalidHandle() --will be true since the menu we are trying to open doesnt exist
```

### Menu.OpenMenu


#### Parameters:

| Name | Type | Description |
| :--- | :--- | :--- |
| Menu name | string | the name of the menu |

#### Returns:

| Name | Type | Description |
| :--- | :--- | :--- |
| MenuHandle | int | Handle of the new menu |


```lua
local MainMenuHandle = Menu.OpenMenu(Menu.GetMainMenu())
```

### Menu.OpenElement


#### Parameters:

| Name | Type | Description |
| :--- | :--- | :--- |
| tab | string | tab name |
| child | string | child name |
| element | string | element name |

#### Returns:

| Name | Type | Description |
| :--- | :--- | :--- |
| Element Handle | int | Handle of the new Handle |

```lua
local FakelagMode = Menu.OpenElement("AntiAim","Main", "Fakelag")
```

### Menu.CloseHandle

**Does not work on Main Menu**

#### Parameters:

| Name | Type | Description |
| :--- | :--- | :--- |
| menu | int | the handle of the menu |



```lua
local NewMenu = Menu.CreateMenu(Vector2D.new(40,40),Vector2D.new(365,150),"TestMenu", true) --this creates the new menu
Menu.CloseHandle(NewMenu) --this will close the menu
```



[back to Contents](#-1)

---
