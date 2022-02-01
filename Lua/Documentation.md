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

### Engine.GetLevelName


#### Parameters:

| Name | Type |
| :--- | :--- |
| | |

#### Returns:

| Name | Type |
| :--- | :--- | 
| level name [includes .bsp] | string |


```lua
local levelname = Engine.GetLevelName()
--your level name
```

### Engine.GetLevelNameShort


#### Parameters:

| Name | Type |
| :--- | :--- |
| | |

#### Returns:

| Name | Type |
| :--- | :--- | 
| level name [example: de_mirage instead of de_mirage.bsp] | string |


```lua
local levelname = Engine.GetLevelNameShort()
--your level name
```

### Engine.GetLocalPlayer


#### Parameters:

| Name | Type |
| :--- | :--- |
| | |

#### Returns:

| Name | Type |
| :--- | :--- | 
| local player | CBasePlayer |


```lua
local localplayer = Engine.GetLocalPlayer()
--this gets local player but you can also use EntityList.GetLocalPlayer()
```

### Engine.GetMapGroupName


#### Parameters:

| Name | Type |
| :--- | :--- |
| | |

#### Returns:

| Name | Type |
| :--- | :--- | 
| map group name | string |


```lua
local groupname = Engine.GetMapGroupName()
--map group name
```

### Engine.GetMaxClients


#### Parameters:

| Name | Type |
| :--- | :--- |
| | |

#### Returns:

| Name | Type |
| :--- | :--- | 
| total number of players | int |


```lua
local numclients = Engine.GetMaxClients()
--total clients, you can also use EntityList.NumberOfPlayers() or GlobalVariables.TotalClients()
```

### Engine.GetViewAngles


#### Parameters:

| Name | Type |
| :--- | :--- |
| | |

#### Returns:

| Name | Type |
| :--- | :--- | 
| viewangle | Vector |


```lua
local viewangle = Engine.GetViewAngles()
--this gets the local viewangle
```

### Engine.SetViewAngles


#### Parameters:

| Name | Type |
| :--- | :--- |
| Viewangle | Vector |

#### Returns:

| Name | Type |
| :--- | :--- | 
|  |  |


```lua
Engine.SetViewAngles(Vector.Get(0,89,0))
--this will make you look down
```



[back to Contents](#-1)

---

# <a name="3"></a>DebugOverlay
---

### DebugOverlay.AddBox


#### Parameters:

| Name | Type |
| :--- | :--- | 
| origin | Vector | 
| mins | Vector |
| maxs | Vector |
| orientation | Vector |
| color | Color |
| duration | float |

#### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
DebugOverlay.AddBox(Vector.Get(0,0,0), Vector.Get(-5,-5,-5), Vector.Get(5,5,5), Vector.Get(0,0,0), Color.Get(255,255,255,255), 3.0)
```

### DebugOverlay.AddCapsule


#### Parameters:

| Name | Type |
| :--- | :--- | 
| mins | Vector |
| maxs | Vector |
| radius | float |
| color | Color |
| duration | float |

#### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
DebugOverlay.AddCapsule(Vector.Get(-5,-5,-5), Vector.Get(5,5,5), 10.0, Color.Get(255,255,255,255), 3.0)
```

### DebugOverlay.AddLine


#### Parameters:

| Name | Type |
| :--- | :--- | 
| start | Vector |
| end | Vector |
| color | Color |
| duration | float |
| disabledepth [optional] | bool |

#### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
DebugOverlay.AddLine(Vector.Get(-5,-5,-5), Vector.Get(5,5,5), Color.Get(255,255,255,255), 3.0)
```

### DebugOverlay.AddSphere


#### Parameters:

| Name | Type |
| :--- | :--- | 
| center | Vector |
| theta | int |
| phi | int |
| radius | float |
| color | Color |
| duration | float |

#### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
--preview unavailable
```

### DebugOverlay.AddTriangle


#### Parameters:

| Name | Type |
| :--- | :--- | 
| point 1 | Vector |
| point 2 | Vector |
| point 3 | Vector |
| color | Color |
| duration | float |
| disabledepth [optional] | bool |

#### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
DebugOverlay.AddLine(Vector.Get(-5,-5,-5), Vector.Get(5,5,5), Color.Get(255,255,255,255), 3.0)
```


[back to Contents](#-1)

---

# <a name="4"></a>ClientState
---

### ClientState.GetChokedCommands


#### Parameters:

| Name | Type |
| :--- | :--- | 
| | |

#### Returns:

| Name | Type | 
| :--- | :--- |
| Choked commands | int |


```lua
ClientState.GetChokedCommands()
-- can range from 0 to sv_maxusercmdprocessticks depending on how much ticks we choked
```

### ClientState.GetCommandAck


#### Parameters:

| Name | Type |
| :--- | :--- | 
| | |

#### Returns:

| Name | Type | 
| :--- | :--- |
| command ack | int |


```lua
ClientState.GetCommandAck()
```

### ClientState.GetLastOutgoingAck


#### Parameters:

| Name | Type |
| :--- | :--- | 
| | |

#### Returns:

| Name | Type | 
| :--- | :--- |
| command last outgoing ack | int |


```lua
ClientState.GetLastOutgoingAck()
```

### ClientState.GetLastOutgoingCommand


#### Parameters:

| Name | Type |
| :--- | :--- | 
| | |

#### Returns:

| Name | Type | 
| :--- | :--- |
| command last outgoing command | int |


```lua
ClientState.GetLastOutgoingCommand()
```


[back to Contents](#-1)

---

