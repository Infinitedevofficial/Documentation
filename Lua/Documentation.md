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
|[CBasePlayer](#36)|

---

# <a name="0"></a>Penetration
---

### Penetration.CanPenetrate


#### Parameters:

| Name | Type |
| :--- | :--- | 
| start | Vector | 
| end | Vector |

#### Returns:

| Name | Type | 
| :--- | :--- |
| penetration | bool | 


```lua
Penetration.CanPenetrate(Entity.GetEyePosition(EntityList.GetLocalPlayer()), Entity.GetBonePosition(Enemy, 0)) 
--true if we can penetrate false if we can't
```


### Penetration.PredictDamage


#### Parameters:

| Name | Type | 
| :--- | :--- |
| start | Vector | 
| end | Vector | 
| target | CBasePlayer |

#### Returns:

| Name | Type | 
| :--- | :--- | 
| damage | int |


```lua
Penetration.PredictDamage(Entity.GetEyePosition(EntityList.GetLocalPlayer()), Entity.GetBonePosition(Enemy, 0), Enemy) 
--will be -1 if invalid parameters or (0 - max damage) if valid
```





[back to Contents](#-1)

---

# <a name="2"></a>Engine
---


### Engine.ExecuteClientCommand


#### Parameters:

| Name | Type | 
| :--- | :--- |
| command | string |

#### Returns:

| Name | Type | 
| :--- | :--- |
| | |

```lua
Engine.ExecuteClientCommand("say hello from oak!")
--will say hello in chat
```

### Engine.GetGameDirectory


#### Parameters:

| Name | Type |
| :--- | :--- |
| | |

#### Returns:

| Name | Type |
| :--- | :--- | 
| game directory | string |


```lua
local gamedirectory = Engine.GetGameDirectory()
--this will be your game directory
```


[back to Contents](#-1)

---
