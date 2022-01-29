**Last Update: 29/01/2022**


Built in Libraries: ffi bit

<a name="-1"></a>

|Tables|
|--------|
|[Menu](#0)|
|[Client](#1)|
|[GlobalVariables](#2)|
|[InputSystem](#3)|
|[Memory](#4)|
|[AntiAim](#5)|
|[Fakelag](#6)|
|[HTTP](#7)|
|[HTTPS](#8)|
|[Doubletap](#9)|
|[EntityList](#10)|
|[Paint](#11)|
|[Surface2D](#12)|
|[Surface3D](#13)|
|[Bits](#14)|
|[Entity](#15)|
|[Console](#16)|
|[Command](#17)|

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
