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

| Name | Type | Description |
| :--- | :--- | :--- |
| start | Vector | start position |
| end | Vector | end position |

#### Returns:

| Name | Type | Description |
| :--- | :--- | :--- |
| penetration | bool | can penetrate |


```lua
Penetration.CanPenetrate(Entity.GetEyePosition(EntityList.GetLocalPlayer()), Entity.GetBonePosition(Enemy, 0)) 
--true if we can penetrate false if we can't
```


### Penetration.PredictDamage


#### Parameters:

| Name | Type | Description |
| :--- | :--- | :--- |
| start | Vector | start position |
| end | Vector | end position |
| target | CBasePlayer | target |

#### Returns:

| Name | Type | Description |
| :--- | :--- | :--- |
| damage | int | predicted damage |


```lua
Penetration.PredictDamage(Entity.GetEyePosition(EntityList.GetLocalPlayer()), Entity.GetBonePosition(Enemy, 0), Enemy) 
--will be -1 if invalid parameters or (0 - max damage) if valid
```





[back to Contents](#-1)

---

# <a name="1"></a>Trace
---


### Trace.GetPointContents


#### Parameters:

| Name | Type | Description |
| :--- | :--- | :--- |
| point | Vector | position |

#### Returns:

| Name | Type | Description |
| :--- | :--- | :--- |
| contents | int | point contents |


```lua
Trace.GetPointContents(Entity.GetEyePosition(EntityList.GetLocalPlayer())) 
--will get point contents of local eye position 
```

### Trace.GetPointContentsWorld



**Only returns world contents**


#### Parameters:

| Name | Type | Description |
| :--- | :--- | :--- |
| point | Vector | position |

#### Returns:

| Name | Type | Description |
| :--- | :--- | :--- |
| contents | int | point contents |


```lua
Trace.GetPointContentsWorld(Entity.GetEyePosition(EntityList.GetLocalPlayer())) 
--will get point contents of local eye position
```


### Trace.Line


#### Parameters:

| Name | Type | Description |
| :--- | :--- | :--- |
| start | Vector | start position |
| end | Vector | end position |
| skip | CBasePlayer | player skipped [-1 if no player] |
| mask | int | Trace Mask |

#### Returns:

| Name | Type | Description |
| :--- | :--- | :--- |
| Trace | CGameTrace | trace result |


```lua
Trace.Line(Entity.GetEyePosition(EntityList.GetLocalPlayer()), Entity.GetBonePosition(Enemy, 0), -1, 0x1).fraction == 1.0
--1.0 means our line did not hit anything
```

### Trace.Ray


#### Parameters:

| Name | Type | Description |
| :--- | :--- | :--- |
| start | Vector | start position |
| end | Vector | end position |
| mins | Vector | bounding box min |
| max | Vector | bounding box max |
| skip | CBasePlayer | player skipped [-1 if no player] |
| mask | int | Trace Mask |

#### Returns:

| Name | Type | Description |
| :--- | :--- | :--- |
| Trace | CGameTrace | trace result |


```lua
Trace.Ray(Entity.GetEyePosition(EntityList.GetLocalPlayer()), Entity.GetBonePosition(Enemy, 0), Vector.Get(-2,-2,-2), Vector.Get(2,2,2), -1, 0x1).fraction == 1.0
--1.0 means our line did not hit anything
```




[back to Contents](#-1)

---
