**Last Update: 01/02/2022**


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
|[Virtual Key](#37)|

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


# <a name="1"></a>Trace
---


### Trace.GetPointContents


#### Parameters:

| Name | Type | 
| :--- | :--- | 
| point | Vector |

#### Returns:

| Name | Type | 
| :--- | :--- | 
| contents | int | 


```lua
Trace.GetPointContents(Entity.GetEyePosition(EntityList.GetLocalPlayer())) 
--will get point contents of local eye position 
```

### Trace.GetPointContentsWorld



**Only returns world contents**


#### Parameters:

| Name | Type |
| :--- | :--- | 
| point | Vector | 

#### Returns:

| Name | Type | 
| :--- | :--- | 
| contents | int | 


```lua
Trace.GetPointContentsWorld(Entity.GetEyePosition(EntityList.GetLocalPlayer())) 
--will get point contents of local eye position
```


### Trace.Line


#### Parameters:

| Name | Type | Description |
| :--- | :--- | :--- |
| start | Vector | 
| end | Vector | 
| skip [-1 if no player] | CBasePlayer | 
| mask | int | 

#### Returns:

| Name | Type |
| :--- | :--- |
| result | CGameTrace | 


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

# <a name="5"></a>Event
---

### Event.RegisterListener


#### Parameters:

| Name | Type |
| :--- | :--- | 
| listener | function | 

#### Returns:

| Name | Type | 
| :--- | :--- |
| | | 


```lua
function OnEventFired() 

end

Event.RegisterListener(OnEventFired)

--or

Event.RegisterListener(function()

end)
```


### Event.GetName


#### Parameters:

| Name | Type |
| :--- | :--- | 
| | | 

#### Returns:

| Name | Type | 
| :--- | :--- |
| Event name | string | 


```lua
Event.RegisterListener(function()
  if Event.IsServerEvent() then
    return
  end
  
  local EventName = Event.GetName() --event name
end)
```

### Event.IsServerEvent


#### Parameters:

| Name | Type |
| :--- | :--- | 
| | | 

#### Returns:

| Name | Type | 
| :--- | :--- |
| is server event | bool | 


```lua
Event.RegisterListener(function()
  if Event.IsServerEvent() then -- true if its a server event
    return
  end
  
  local EventName = Event.GetName() 
end)
```

### Event.GetBool


#### Parameters:

| Name | Type |
| :--- | :--- | 
| key | string | 

#### Returns:

| Name | Type | 
| :--- | :--- |
| value | bool | 


```lua
Event.RegisterListener(function()
  if Event.IsServerEvent() then
    return
  end
  
  if Event.GetName() ~= "player_death" then
    return
  end
  
  if Event.GetBool("assistedflash") then --get bool usage
    Print("Someone Assisted this kill with a flash!")
  end
  
end)
```

### Event.GetFloat


#### Parameters:

| Name | Type |
| :--- | :--- | 
| key | string | 

#### Returns:

| Name | Type | 
| :--- | :--- |
| value | float | 


```lua
Event.RegisterListener(function()
  if Event.IsServerEvent() then
    return
  end
  
  if Event.GetName() ~= "player_death" then
    return
  end
  
  
  Print(Event.GetFloat("distance")) -- distance from localplayer to the player whom died
  
  
end)
```

### Event.GetInt


#### Parameters:

| Name | Type |
| :--- | :--- | 
| key | string | 

#### Returns:

| Name | Type | 
| :--- | :--- |
| value | float | 


```lua
Event.RegisterListener(function()
  if Event.IsServerEvent() then
    return
  end
  
  if Event.GetName() ~= "player_death" then
    return
  end
  
  
  Print(Event.GetInt("distance")) -- distance from localplayer to the player whom died in integer form
  
  
end)
```


### Event.GetString


#### Parameters:

| Name | Type |
| :--- | :--- | 
| key | string | 

#### Returns:

| Name | Type | 
| :--- | :--- |
| value | float | 


```lua
Event.RegisterListener(function()
  if Event.IsServerEvent() then
    return
  end
  
  if Event.GetName() ~= "player_death" then
    return
  end
  
  
  Print(Event.GetString("weapon")) -- the weapon name that the killer used to kill the dead player
  
  
end)
```




[back to Contents](#-1)

---

# <a name="6"></a>Netvars
---

### Netvars.GetOffset


#### Parameters:

| Name | Type |
| :--- | :--- | 
| table | string | 
| name | string |

#### Returns:

| Name | Type | 
| :--- | :--- |
| netvar offset | int | 


```lua
local m_flDuckAmountOffset = Netvars.GetOffset("DT_CSPlayer", "m_flDuckAmount")
```




[back to Contents](#-1)

---

# <a name="7"></a>GlobalVariables
---

### GlobalVariables.Realtime


#### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

#### Returns:

| Name | Type | 
| :--- | :--- |
| realtime | float | 


```lua
GlobalVariables.Realtime()
--time since csgo started
```

### GlobalVariables.Framecount


#### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

#### Returns:

| Name | Type | 
| :--- | :--- |
| Framecount | int | 


```lua
GlobalVariables.Framecount()
--total frames rendered
```

### GlobalVariables.AbsoluteFrametime


#### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

#### Returns:

| Name | Type | 
| :--- | :--- |
| frame time | float | 


```lua
GlobalVariables.AbsoluteFrametime()
--very accurate frametime
```

### GlobalVariables.Frametime


#### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

#### Returns:

| Name | Type | 
| :--- | :--- |
| frame time | float | 


```lua
GlobalVariables.Frametime()
--less accurate frametime
```

### GlobalVariables.Curtime


#### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

#### Returns:

| Name | Type | 
| :--- | :--- |
| current time | float | 


```lua
GlobalVariables.Curtime()
--current server time
```

### GlobalVariables.TotalClients


#### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

#### Returns:

| Name | Type | 
| :--- | :--- |
| total clients | int | 


```lua
GlobalVariables.TotalClients()
--number of clients or players
```


### GlobalVariables.Tickcount


#### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

#### Returns:

| Name | Type | 
| :--- | :--- |
| tickcount | int | 


```lua
GlobalVariables.Tickcount()
--client tickcount
```

### GlobalVariables.IntervalPerTick


#### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

#### Returns:

| Name | Type | 
| :--- | :--- |
| interval in time per tick | int | 


```lua
GlobalVariables.IntervalPerTick()
--the interval of time for a tick to increment
```


### GlobalVariables.InterpolationAmmount


#### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

#### Returns:

| Name | Type | 
| :--- | :--- |
| ammount | float | 


```lua
GlobalVariables.InterpolationAmmount()
--how much players are interpolated
```



### GlobalVariables.NetworkProtocol


#### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

#### Returns:

| Name | Type | 
| :--- | :--- |
| network protocol | int | 


```lua
GlobalVariables.NetworkProtocol()
--current network protocol
```


### GlobalVariables.Client


#### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

#### Returns:

| Name | Type | 
| :--- | :--- |
| are we client or stream | bool | 


```lua
GlobalVariables.Client()
```




[back to Contents](#-1)

---

# <a name="8"></a>InputSystem
---

### InputSystem.IsKeyPressed


#### Parameters:

| Name | Type |
| :--- | :--- | 
| virtual key | int | 

#### Returns:

| Name | Type | 
| :--- | :--- |
| is pressed | bool | 


```lua
InputSystem.IsKeyPressed(0x09) --vk_tab or tab key
--true if we are holding the tab key
```

### InputSystem.IsKeyToggled


#### Parameters:

| Name | Type |
| :--- | :--- | 
| virtual key | int | 

#### Returns:

| Name | Type | 
| :--- | :--- |
| did the key toggle | bool | 


```lua
InputSystem.IsKeyPressed(0x09) --vk_tab or tab key
--true if we are toggle the key [once]
```

### InputSystem.GetCursorPosition


#### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

#### Returns:

| Name | Type | 
| :--- | :--- |
| cursor position | Vector2D | 


```lua
InputSystem.GetCursorPosition() 
--mouse cursor position
```

### InputSystem.MouseLeftState


#### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

#### Returns:

| Name | Type | 
| :--- | :--- |
| mouse left state | float | 


```lua
InputSystem.MouseLeftState()
--value is 0 if clicked once or above 0 if being held down or -1 if not used
```

### InputSystem.MouseRightState


#### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

#### Returns:

| Name | Type | 
| :--- | :--- |
| mouse left state | float | 


```lua
InputSystem.MouseRightState()
--value is 0 if clicked once or above 0 if being held down or -1 if not used
```


[back to Contents](#-1)

---

