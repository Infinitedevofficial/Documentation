#### [Back to main page](/README.md)

---

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
|[Sound](#26)|
|[Vector](#27)|
|[Vector2D](#28)|
|[Color](#29)|
|[CGameTrace](#30)|
|[PlayerInfo_t](#31)|
|[ResolveData](#32)|
|[PaintStringRenderFlags](#33)|
|[SurfaceStringRenderFlags](#34)|
|[PaintFontCreationFlags](#35)|
|[Stages](#36)|
|[CBasePlayer](#37)|
|[Virtual Key](#38)|
|[ConVar](#39)|
|[CFont](#40)|
|[IFont](#41)|

---

## <a name="0"></a>Penetration
---

#### Penetration.CanPenetrate


##### Parameters:

| Name | Type |
| :--- | :--- | 
| start | Vector | 
| end | Vector |

##### Returns:

| Name | Type | 
| :--- | :--- |
| penetration | bool | 


```lua
Penetration.CanPenetrate(Entity.GetEyePosition(EntityList.GetLocalPlayer()), Entity.GetBonePosition(Enemy, 0)) 
--true if we can penetrate false if we can't
```


#### Penetration.PredictDamage


##### Parameters:

| Name | Type | 
| :--- | :--- |
| start | Vector | 
| end | Vector | 
| target | CBasePlayer |

##### Returns:

| Name | Type | 
| :--- | :--- | 
| damage | int |


```lua
Penetration.PredictDamage(Entity.GetEyePosition(EntityList.GetLocalPlayer()), Entity.GetBonePosition(Enemy, 0), Enemy) 
--will be -1 if invalid parameters or (0 - max damage) if valid
```





[back to Contents](#-1)

---


## <a name="1"></a>Trace
---


#### Trace.GetPointContents


##### Parameters:

| Name | Type | 
| :--- | :--- | 
| point | Vector |

##### Returns:

| Name | Type | 
| :--- | :--- | 
| contents | int | 


```lua
Trace.GetPointContents(Entity.GetEyePosition(EntityList.GetLocalPlayer())) 
--will get point contents of local eye position 
```

#### Trace.GetPointContentsWorld



**Only returns world contents**


##### Parameters:

| Name | Type |
| :--- | :--- | 
| point | Vector | 

##### Returns:

| Name | Type | 
| :--- | :--- | 
| contents | int | 


```lua
Trace.GetPointContentsWorld(Entity.GetEyePosition(EntityList.GetLocalPlayer())) 
--will get point contents of local eye position
```


#### Trace.Line


##### Parameters:

| Name | Type | Description |
| :--- | :--- | :--- |
| start | Vector | 
| end | Vector | 
| skip [-1 if no player] | CBasePlayer | 
| mask | int | 

##### Returns:

| Name | Type |
| :--- | :--- |
| result | CGameTrace | 


```lua
Trace.Line(Entity.GetEyePosition(EntityList.GetLocalPlayer()), Entity.GetBonePosition(Enemy, 0), -1, 0x1).fraction == 1.0
--1.0 means our line did not hit anything
```

#### Trace.Ray


##### Parameters:

| Name | Type | Description |
| :--- | :--- | :--- |
| start | Vector | start position |
| end | Vector | end position |
| mins | Vector | bounding box min |
| max | Vector | bounding box max |
| skip | CBasePlayer | player skipped [-1 if no player] |
| mask | int | Trace Mask |

##### Returns:

| Name | Type | Description |
| :--- | :--- | :--- |
| Trace | CGameTrace | trace result |


```lua
Trace.Ray(Entity.GetEyePosition(EntityList.GetLocalPlayer()), Entity.GetBonePosition(Enemy, 0), Vector.Get(-2,-2,-2), Vector.Get(2,2,2), -1, 0x1).fraction == 1.0
--1.0 means our line did not hit anything
```




[back to Contents](#-1)

---

## <a name="2"></a>Engine
---


#### Engine.ExecuteClientCommand


##### Parameters:

| Name | Type | 
| :--- | :--- |
| command | string |

##### Returns:

| Name | Type | 
| :--- | :--- |
| | |

```lua
Engine.ExecuteClientCommand("say hello from oak!")
--will say hello in chat
```

#### Engine.GetGameDirectory


##### Parameters:

| Name | Type |
| :--- | :--- |
| | |

##### Returns:

| Name | Type |
| :--- | :--- | 
| game directory | string |


```lua
local gamedirectory = Engine.GetGameDirectory()
--this will be your game directory
```

#### Engine.GetLevelName


##### Parameters:

| Name | Type |
| :--- | :--- |
| | |

##### Returns:

| Name | Type |
| :--- | :--- | 
| level name [includes .bsp] | string |


```lua
local levelname = Engine.GetLevelName()
--your level name
```

#### Engine.GetLevelNameShort


##### Parameters:

| Name | Type |
| :--- | :--- |
| | |

##### Returns:

| Name | Type |
| :--- | :--- | 
| level name [example: de_mirage instead of de_mirage.bsp] | string |


```lua
local levelname = Engine.GetLevelNameShort()
--your level name
```

#### Engine.GetLocalPlayer


##### Parameters:

| Name | Type |
| :--- | :--- |
| | |

##### Returns:

| Name | Type |
| :--- | :--- | 
| local player | CBasePlayer |


```lua
local localplayer = Engine.GetLocalPlayer()
--this gets local player but you can also use EntityList.GetLocalPlayer()
```

#### Engine.GetMapGroupName


##### Parameters:

| Name | Type |
| :--- | :--- |
| | |

##### Returns:

| Name | Type |
| :--- | :--- | 
| map group name | string |


```lua
local groupname = Engine.GetMapGroupName()
--map group name
```

#### Engine.GetMaxClients


##### Parameters:

| Name | Type |
| :--- | :--- |
| | |

##### Returns:

| Name | Type |
| :--- | :--- | 
| total number of players | int |


```lua
local numclients = Engine.GetMaxClients()
--total clients, you can also use EntityList.NumberOfPlayers() or GlobalVariables.TotalClients()
```

#### Engine.GetViewAngles


##### Parameters:

| Name | Type |
| :--- | :--- |
| | |

##### Returns:

| Name | Type |
| :--- | :--- | 
| viewangle | Vector |


```lua
local viewangle = Engine.GetViewAngles()
--this gets the local viewangle
```

#### Engine.SetViewAngles


##### Parameters:

| Name | Type |
| :--- | :--- |
| Viewangle | Vector |

##### Returns:

| Name | Type |
| :--- | :--- | 
|  |  |


```lua
Engine.SetViewAngles(Vector.Get(0,89,0))
--this will make you look down
```



[back to Contents](#-1)

---

## <a name="3"></a>DebugOverlay
---

#### DebugOverlay.AddBox


##### Parameters:

| Name | Type |
| :--- | :--- | 
| origin | Vector | 
| mins | Vector |
| maxs | Vector |
| orientation | Vector |
| color | Color |
| duration | float |

##### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
DebugOverlay.AddBox(Vector.Get(0,0,0), Vector.Get(-5,-5,-5), Vector.Get(5,5,5), Vector.Get(0,0,0), Color.Get(255,255,255,255), 3.0)
```

#### DebugOverlay.AddCapsule


##### Parameters:

| Name | Type |
| :--- | :--- | 
| mins | Vector |
| maxs | Vector |
| radius | float |
| color | Color |
| duration | float |

##### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
DebugOverlay.AddCapsule(Vector.Get(-5,-5,-5), Vector.Get(5,5,5), 10.0, Color.Get(255,255,255,255), 3.0)
```

#### DebugOverlay.AddLine


##### Parameters:

| Name | Type |
| :--- | :--- | 
| start | Vector |
| end | Vector |
| color | Color |
| duration | float |
| disabledepth [optional] | bool |

##### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
DebugOverlay.AddLine(Vector.Get(-5,-5,-5), Vector.Get(5,5,5), Color.Get(255,255,255,255), 3.0)
```

#### DebugOverlay.AddSphere


##### Parameters:

| Name | Type |
| :--- | :--- | 
| center | Vector |
| theta | int |
| phi | int |
| radius | float |
| color | Color |
| duration | float |

##### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
--preview unavailable
```

#### DebugOverlay.AddTriangle


##### Parameters:

| Name | Type |
| :--- | :--- | 
| point 1 | Vector |
| point 2 | Vector |
| point 3 | Vector |
| color | Color |
| duration | float |
| disabledepth [optional] | bool |

##### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
DebugOverlay.AddLine(Vector.Get(-5,-5,-5), Vector.Get(5,5,5), Color.Get(255,255,255,255), 3.0)
```


[back to Contents](#-1)

---

## <a name="4"></a>ClientState
---

#### ClientState.GetChokedCommands


##### Parameters:

| Name | Type |
| :--- | :--- | 
| | |

##### Returns:

| Name | Type | 
| :--- | :--- |
| Choked commands | int |


```lua
ClientState.GetChokedCommands()
-- can range from 0 to sv_maxusercmdprocessticks depending on how much ticks we choked
```

#### ClientState.GetCommandAck


##### Parameters:

| Name | Type |
| :--- | :--- | 
| | |

##### Returns:

| Name | Type | 
| :--- | :--- |
| command ack | int |


```lua
ClientState.GetCommandAck()
```

#### ClientState.GetLastOutgoingAck


##### Parameters:

| Name | Type |
| :--- | :--- | 
| | |

##### Returns:

| Name | Type | 
| :--- | :--- |
| command last outgoing ack | int |


```lua
ClientState.GetLastOutgoingAck()
```

#### ClientState.GetLastOutgoingCommand


##### Parameters:

| Name | Type |
| :--- | :--- | 
| | |

##### Returns:

| Name | Type | 
| :--- | :--- |
| command last outgoing command | int |


```lua
ClientState.GetLastOutgoingCommand()
```


[back to Contents](#-1)

---

## <a name="5"></a>Event
---

#### Event.RegisterListener


##### Parameters:

| Name | Type |
| :--- | :--- | 
| listener | function | 

##### Returns:

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


#### Event.GetName


##### Parameters:

| Name | Type |
| :--- | :--- | 
| | | 

##### Returns:

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

#### Event.IsServerEvent


##### Parameters:

| Name | Type |
| :--- | :--- | 
| | | 

##### Returns:

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

#### Event.GetBool


##### Parameters:

| Name | Type |
| :--- | :--- | 
| key | string | 

##### Returns:

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

#### Event.GetFloat


##### Parameters:

| Name | Type |
| :--- | :--- | 
| key | string | 

##### Returns:

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

#### Event.GetInt


##### Parameters:

| Name | Type |
| :--- | :--- | 
| key | string | 

##### Returns:

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


#### Event.GetString


##### Parameters:

| Name | Type |
| :--- | :--- | 
| key | string | 

##### Returns:

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

## <a name="6"></a>Netvars
---

#### Netvars.GetOffset


##### Parameters:

| Name | Type |
| :--- | :--- | 
| table | string | 
| name | string |

##### Returns:

| Name | Type | 
| :--- | :--- |
| netvar offset | int | 


```lua
local m_flDuckAmountOffset = Netvars.GetOffset("DT_CSPlayer", "m_flDuckAmount")
```




[back to Contents](#-1)

---

## <a name="7"></a>GlobalVariables
---

#### GlobalVariables.Realtime


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

##### Returns:

| Name | Type | 
| :--- | :--- |
| realtime | float | 


```lua
GlobalVariables.Realtime()
--time since csgo started
```

#### GlobalVariables.Framecount


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

##### Returns:

| Name | Type | 
| :--- | :--- |
| Framecount | int | 


```lua
GlobalVariables.Framecount()
--total frames rendered
```

#### GlobalVariables.AbsoluteFrametime


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

##### Returns:

| Name | Type | 
| :--- | :--- |
| frame time | float | 


```lua
GlobalVariables.AbsoluteFrametime()
--very accurate frametime
```

#### GlobalVariables.Frametime


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

##### Returns:

| Name | Type | 
| :--- | :--- |
| frame time | float | 


```lua
GlobalVariables.Frametime()
--less accurate frametime
```

#### GlobalVariables.Curtime


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

##### Returns:

| Name | Type | 
| :--- | :--- |
| current time | float | 


```lua
GlobalVariables.Curtime()
--current server time
```

#### GlobalVariables.TotalClients


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

##### Returns:

| Name | Type | 
| :--- | :--- |
| total clients | int | 


```lua
GlobalVariables.TotalClients()
--number of clients or players
```


#### GlobalVariables.Tickcount


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

##### Returns:

| Name | Type | 
| :--- | :--- |
| tickcount | int | 


```lua
GlobalVariables.Tickcount()
--client tickcount
```

#### GlobalVariables.IntervalPerTick


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

##### Returns:

| Name | Type | 
| :--- | :--- |
| interval in time per tick | int | 


```lua
GlobalVariables.IntervalPerTick()
--the interval of time for a tick to increment
```


#### GlobalVariables.InterpolationAmmount


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

##### Returns:

| Name | Type | 
| :--- | :--- |
| ammount | float | 


```lua
GlobalVariables.InterpolationAmmount()
--how much players are interpolated
```



#### GlobalVariables.NetworkProtocol


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

##### Returns:

| Name | Type | 
| :--- | :--- |
| network protocol | int | 


```lua
GlobalVariables.NetworkProtocol()
--current network protocol
```


#### GlobalVariables.Client


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 
|  |  |

##### Returns:

| Name | Type | 
| :--- | :--- |
| are we client or stream | bool | 


```lua
GlobalVariables.Client()
```




[back to Contents](#-1)

---

## <a name="8"></a>InputSystem
---

#### InputSystem.IsKeyPressed


##### Parameters:

| Name | Type |
| :--- | :--- | 
| virtual key | int | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| is pressed | bool | 


```lua
InputSystem.IsKeyPressed(0x09) --vk_tab or tab key
--true if we are holding the tab key
```

#### InputSystem.IsKeyToggled


##### Parameters:

| Name | Type |
| :--- | :--- | 
| virtual key | int | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| did the key toggle | bool | 


```lua
InputSystem.IsKeyPressed(0x09) --vk_tab or tab key
--true if we are toggle the key [once]
```

#### InputSystem.GetCursorPosition


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| cursor position | Vector2D | 


```lua
InputSystem.GetCursorPosition() 
--mouse cursor position
```

#### InputSystem.MouseLeftState


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| mouse left state | float | 


```lua
InputSystem.MouseLeftState()
--value is 0 if clicked once or above 0 if being held down or -1 if not used
```

#### InputSystem.MouseRightState


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| mouse left state | float | 


```lua
InputSystem.MouseRightState()
--value is 0 if clicked once or above 0 if being held down or -1 if not used
```


[back to Contents](#-1)

---

## <a name="9"></a>Memory
---

#### Memory.FindSignature


##### Parameters:

| Name | Type |
| :--- | :--- | 
| module name | string | 
| signature | string |

##### Returns:

| Name | Type | 
| :--- | :--- |
| pointer | int | 


```lua
Memory.FindSignature("engine.dll", "53 56 57 8B DA 8B F9 FF 15")
--setclantag pointer
```

#### Memory.GetModuleHandle


##### Parameters:

| Name | Type |
| :--- | :--- | 
| module name | string | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| handle | int | 


```lua
Memory.GetModuleHandle("engine.dll")
--handle or base address of engine.dll
```

#### Memory.GetProcessAddress


##### Parameters:

| Name | Type |
| :--- | :--- | 
| module name | string | 
| process name | string | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| process pointer | int | 


```lua
Memory.GetProcessAddress("vstdlib.dll", "RandomSeed")
--process address of RandomSeed
```


#### Memory.GetInterfaceAddress


##### Parameters:

| Name | Type |
| :--- | :--- | 
| module name | string | 
| interface version | string | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| interface pointer | int | 


```lua
Memory.GetInterfaceAddress("client.dll", "GameMovement001")
--gets the interface pointer of GameMovement001
```



[back to Contents](#-1)

---

## <a name="10"></a>Cvar
---

#### Cvar.FindCvar


##### Parameters:

| Name | Type |
| :--- | :--- | 
| cvar name | string | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| cvar | ConVar | 


```lua
local svcheats = Cvar.FindCvar("sv_cheats")
```

#### Cvar.IsValid


##### Parameters:

| Name | Type |
| :--- | :--- | 
| cvar | ConVar | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| isvalid | bool | 


```lua
local invalid = Cvar.FindCvar("invalidcvar")
Cvar.IsValid(invalid) --this will be false because the cvar doesnt exist
```

#### Cvar.InvalidCvar


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| invalid cvar value | ConVar | 


```lua
local invalid = Cvar.FindCvar("invalidcvar")
invalid == Cvar.InvalidCvar() --this will be true because the cvar doesnt exist
```

#### Cvar.GetString


##### Parameters:

| Name | Type |
| :--- | :--- | 
| cvar | ConVar | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| value | string | 


```lua
local svcheats = Cvar.FindCvar("sv_cheats")
Cvar.GetString(svcheats) --this will be "0" or "1"
```

#### Cvar.GetInt


##### Parameters:

| Name | Type |
| :--- | :--- | 
| cvar | ConVar | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| value | int | 


```lua
local svcheats = Cvar.FindCvar("sv_cheats")
Cvar.GetInt(svcheats) --this will be 0 or 1
```

#### Cvar.GetFloat


##### Parameters:

| Name | Type |
| :--- | :--- | 
| cvar | ConVar | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| value | float | 


```lua
local svcheats = Cvar.FindCvar("sv_cheats")
Cvar.GetFloat(svcheats) --this will be 0.0 or 1.0
```

#### Cvar.GetBool


##### Parameters:

| Name | Type |
| :--- | :--- | 
| cvar | ConVar | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| value | bool | 


```lua
local svcheats = Cvar.FindCvar("sv_cheats")
Cvar.GetBool(svcheats) --this will be true or false
```



[back to Contents](#-1)

---

## <a name="11"></a>AntiAim
---

#### AntiAim.IsInverted


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| inverter state | bool | 


```lua
AntiAim.IsInverted()
--true if inverted
```

#### AntiAim.GetRange


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| range | float | 


```lua
AntiAim.GetRange()
--between 0.0-120.0 depending on current desync range
```

#### AntiAim.SetRange


##### Parameters:

| Name | Type |
| :--- | :--- | 
| overriden range | float | 

##### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
AntiAim.SetRange(90) --will set our desync range to 90/2 or 45
```

#### AntiAim.SetInverterState


##### Parameters:

| Name | Type |
| :--- | :--- | 
| new state | bool | 

##### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
AntiAim.SetInverterState(true) --will set our inverter to right instead of left
```


#### AntiAim.IsPeeking


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| is peeking | bool | 


```lua
AntiAim.IsPeeking()
--true if peeking
```



[back to Contents](#-1)

---

## <a name="12"></a>Client
---

#### Client.GetDelay


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| delay | float | 


```lua
Client.GetDelay()
--returns ping
```

#### Client.GetTime


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| time | string | 


```lua
Client.GetTime()
--returns time in string with format H:M:S
```


#### Client.GetUsername


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| username | string | 


```lua
Client.GetUsername()
--gives client username
```

#### Client.GetConnectedAddress


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| ip address | string | 


```lua
Client.GetConnectedAddress()
--gives currently connected IP address
```


#### Client.IsConnected


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| is connected to server | bool | 


```lua
Client.IsConnected()
--if true we are connected to a server
```

#### Client.IsInGame


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| is connected to server | bool | 


```lua
Client.IsInGame()
--if true we are in a game or match
```

#### Client.SetClantag


##### Parameters:

| Name | Type |
| :--- | :--- | 
| clantag | string | 
| clanname | string | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| | | 


```lua
Client.SetClantag("Infinite", "Infinite.dev")
--sets clantag
```

#### Client.TimeToTicks


##### Parameters:

| Name | Type |
| :--- | :--- | 
| time | float | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| ticks | int | 


```lua
Client.TimeToTicks(1.0)
--1 second to ticks
```

#### Client.TicksToTime


##### Parameters:

| Name | Type | 
| :--- | :--- |
| ticks | int |

##### Returns:

| Name | Type |
| :--- | :--- | 
| time | float | 


```lua
Client.TicksToTime(16)
--16 ticks to seconds
```


[back to Contents](#-1)

---

## <a name="13"></a>Fakelag
---

#### Fakelag.OverridePacket


##### Parameters:

| Name | Type |
| :--- | :--- | 
| new state | bool | 


##### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
Fakelag.OverridePacket(true)
--if true we will send packet if false we will not send packet
```

#### Fakelag.GetChokedPackets


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 


##### Returns:

| Name | Type | 
| :--- | :--- |
| Choked Packets | int | 


```lua
Fakelag.GetChokedPackets()
--ammount of choked packets
```




[back to Contents](#-1)

---

## <a name="14"></a>HTTP
---

#### HTTP.Post


##### Parameters:

| Name | Type |
| :--- | :--- | 
| URL | string | 
| Body | string | 
| Headers | table of strings |  

##### Returns:

| Name | Type | 
| :--- | :--- |
| response body | string | 


```lua
HTTP.Post("http://unknownwebsite.com/api/test", "test", {""})
```


#### HTTP.Get


##### Parameters:

| Name | Type |
| :--- | :--- | 
| URL | string | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| response body | string | 


```lua
HTTP.Get("http://unknownwebsite.com/get")
```

#### HTTP.IsConnected


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| is connected to internet | bool | 


```lua
HTTP.IsConnected()
--true if connected to the internet
```



[back to Contents](#-1)

---

## <a name="15"></a>HTTPS
---

#### HTTPS.Get


##### Parameters:

| Name | Type |
| :--- | :--- | 
| URL | string | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| response body | string | 



```lua
HTTPS.Get("http://unknownwebsite.com/get")
```

#### HTTPS.Post


##### Parameters:

| Name | Type |
| :--- | :--- | 
| URL | string | 
| Path | string | 
| Body | string | 
| Headers | string | 

##### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 



```lua
HTTPS.Post("https://unknownwebsite.com", "/Post","Body","Header: Header")
```

#### HTTPS.DownloadURLToFile


##### Parameters:

| Name | Type |
| :--- | :--- | 
| URL | string | 
| File | string | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| Successful | bool | 



```lua
HTTPS.Post("https://unknownwebsite.com", "/Post","Body","Header: Header")
```

#### HTTPS.IsConnected


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| is connected to internet | bool | 


```lua
HTTPS.IsConnected()
--true if connected to the internet
```


[back to Contents](#-1)

---

## <a name="16"></a>Menu
---

#### Menu.GetMainMenu


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| Main Menu Name | string | 


```lua
local MainMenuHandle = Menu.OpenMenu(Menu.GetMainMenu()) --Menu.GetMainMenu() returns the main menu name
```

#### Menu.InvalidHandle


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| invalid handle | int | 


```lua
Menu.InvalidHandle() -- it is equal to -5 or invalid handle
```


#### Menu.CreateMenu


##### Parameters:

| Name | Type |
| :--- | :--- | 
| Position | Vector2D | 
| Size | Vector2D | 
| Name | string | 
| Closable | bool | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| created menu handle | int | 


```lua
local NewHandle = Menu.CreateMenu(Vector2D.Get(40,40 + 170),Vector2D.Get(365,100),"New Menu", true) --example
```

#### Menu.OpenMenu


##### Parameters:

| Name | Type |
| :--- | :--- | 
| menu name | string | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| menu handle | int | 


```lua
local MainMenu = Menu.OpenMenu(Menu.GetMainMenu()) --open menu used to open main menu
```


#### Menu.OpenElement


##### Parameters:

| Name | Type |
| :--- | :--- | 
| tab | string | 
| child | string | 
| element | string | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| element handle | string | 


```lua
local FakelagMode = Menu.OpenElement( "AntiAim","Main", "Fakelag") --opens fakelag dropdown
```


#### Menu.CloseHandle


##### Parameters:

| Name | Type |
| :--- | :--- | 
| menu handle | int | 


##### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
Menu.CloseHandle(somemenu) --only use when closing menus
```


#### Menu.CreateSwitch


##### Parameters:

| Name | Type |
| :--- | :--- | 
| menu handle | int | 
| label | string | 
| default value | bool | 


##### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
Menu.CreateSwitch(SomeMenu,"SomeSwitch", false)
```


#### Menu.CreateSlider


##### Parameters:

| Name | Type |
| :--- | :--- | 
| menu handle | int | 
| label | string | 
| min | int |
| max | int |
| default value | int | 


##### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
Menu.CreateSlider(SomeMenu,"SomeSlider", 0,10,5)
```



#### Menu.CreateDropdown


##### Parameters:

| Name | Type |
| :--- | :--- | 
| menu handle | int | 
| label | string | 
| elements | table of strings |
| default value | int | 


##### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
Menu.CreateDropdown(SomeMenu,"SomeDropdown", { "1","2", "3","4"}, 0)
```


#### Menu.CreateMultidropdown


##### Parameters:

| Name | Type |
| :--- | :--- | 
| menu handle | int | 
| label | string | 
| elements | table of strings |
| default value | int | 


##### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
Menu.CreateMultidropdown(SomeMenu,"SomeDropdown", { "1","2", "3","4"}, 0)
```



[back to Contents](#-1)

---

## <a name="17"></a>Doubletap
---

#### Doubletap.GetSpeed


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| current speed | int | 


```lua
Doubletap.GetSpeed()
--doubletap speed
```

#### Doubletap.GetMode


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| current mode | int | 


```lua
Doubletap.GetMode()
--doubletap mode
```

#### Doubletap.GetTolerance


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| current tolerance | int | 


```lua
Doubletap.GetTolerance()
--returns overiden tolerance or 0 if not overiden
```


#### Doubletap.IsCharged


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| charge state | bool | 


```lua
Doubletap.IsCharged()
--true if doubletap is charged
```


#### Doubletap.SetMode

**Overrides for 1 tick**

##### Parameters:

| Name | Type |
| :--- | :--- | 
| new mode | int | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| | |


```lua
Doubletap.SetMode(0)
--sets doubletap mode to shift
```


#### Doubletap.SetSpeed

**Overrides for 1 tick**

##### Parameters:

| Name | Type |
| :--- | :--- | 
| new speed | int | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| | |


```lua
Doubletap.SetSpeed(15)
--doubletap speed will now be 15
```


#### Doubletap.SetTolerance

**Overrides for 1 tick**

##### Parameters:

| Name | Type |
| :--- | :--- | 
| new tolerance | int | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| | |


```lua
Doubletap.SetTolerance(3)
--doubletap tolerance will now be 3
```




[back to Contents](#-1)

---

## <a name="18"></a>EntityList
---

#### EntityList.NumberOfPlayers


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| number of players | int | 


```lua
EntityList.NumberOfPlayers()
```

#### EntityList.NumberOfEntities


##### Parameters:

| Name | Type |
| :--- | :--- | 
| include non networkable | bool | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| number of entities | int | 


```lua
EntityList.NumberOfEntities()
```


#### EntityList.GetHighestEntityIndex


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| highest entity index | int | 


```lua
EntityList.GetHighestEntityIndex()
```


#### EntityList.GetEntityFromHandle


##### Parameters:

| Name | Type |
| :--- | :--- | 
| handle | int | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| entity | CBasePlayer | 


```lua
EntityList.GetEntityFromHandle(somehandle)
```



#### EntityList.GetLocalPlayer


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| local player | CBasePlayer | 


```lua
EntityList.GetLocalPlayer()
```


#### EntityList.GetEntityFromUserID


##### Parameters:

| Name | Type |
| :--- | :--- | 
| user id | int | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| entity | CBasePlayer | 


```lua
EntityList.GetEntityFromUserID(SomeUserID)
```



#### EntityList.GetEntitiesByClassName


##### Parameters:

| Name | Type |
| :--- | :--- | 
| class name | string | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| entities | table of CBasePlayer | 


```lua
EntityList.GetEntitiesByClassName("CBasePlayer")
```


#### EntityList.GetEntitiesByClassID


##### Parameters:

| Name | Type |
| :--- | :--- | 
| class id | int | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| entities | table of CBasePlayer | 


```lua
EntityList.GetEntitiesByClassID(157) --smoke
```


#### EntityList.GetEntities


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| entities | table of CBasePlayer | 


```lua
EntityList.GetEntities()
```


#### EntityList.GetValidPlayers


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| entities | table of CBasePlayer | 


```lua
EntityList.GetValidPlayers()
```


#### EntityList.GetOpponents


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| entities | table of CBasePlayer | 


```lua
EntityList.GetOpponents()
```


#### EntityList.GetPlayers


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  | 

##### Returns:

| Name | Type | 
| :--- | :--- |
| entities | table of CBasePlayer | 


```lua
EntityList.GetPlayers()
```





[back to Contents](#-1)

---

## <a name="19"></a>Paint
---

#### Paint.Line


##### Parameters:

| Name | Type |
| :--- | :--- | 
| start | Vector2D | 
| end | Vector2D |
| color | Color |

##### Returns:

| Name | Type | 
| :--- | :--- |
| | | 


```lua
Paint.Line(Vector2D.Get(40,40), Vector2D.Get(60,40), Color.Default)
```


#### Paint.FilledRectangle


##### Parameters:

| Name | Type |
| :--- | :--- | 
| position | Vector2D | 
| size | Vector2D |
| color | Color |

##### Returns:

| Name | Type | 
| :--- | :--- |
| | | 


```lua
Paint.FilledRectangle(Vector2D.Get(40,40), Vector2D.Get(60,40), Color.Default)
```


#### Paint.Rectangle


##### Parameters:

| Name | Type |
| :--- | :--- | 
| position | Vector2D | 
| size | Vector2D |
| thickness | float |
| color | Color |

##### Returns:

| Name | Type | 
| :--- | :--- |
| | | 


```lua
Paint.Rectangle(Vector2D.Get(40,40), Vector2D.Get(60,40),1.5, Color.Default)
```


#### Paint.String


##### Parameters:

| Name | Type |
| :--- | :--- | 
| position | Vector2D | 
| text | string |
| color | Color |
| flags | PaintStringRenderFlags |
| font | CFont |

##### Returns:

| Name | Type | 
| :--- | :--- |
| | | 


```lua
Paint.String(Vector2D.Get(40,40), "test", Color.Default,PaintStringRenderFlags.LEFT, 0)
```


#### Paint.AddFont


##### Parameters:

| Name | Type |
| :--- | :--- | 
| name | string |
| size | int |
| weight | int |
| flags | PaintFontCreationFlags |


##### Returns:

| Name | Type | 
| :--- | :--- |
| font | CFont | 


```lua
Paint.AddFont("Verdana", 30,400,PaintFontCreationFlags.Shadow)
```


#### Paint.ClearFonts


##### Parameters:

| Name | Type |
| :--- | :--- | 
|  |  |
|  |  |
|  |  |
|  |  |


##### Returns:

| Name | Type | 
| :--- | :--- |
|  |  | 


```lua
Paint.ClearFonts()
--clears fonts
```





[back to Contents](#-1)

---

## <a name="20"></a>Bits
---

#### Bits.has


##### Parameters:

| Name | Type |
| :--- | :--- | 
| bit | int | 
| bit | int |

##### Returns:

| Name | Type | 
| :--- | :--- |
| has | bool | 


```lua
local mustbetrue = Bits.has(48,16) --will be true
--this is the same as mustbetrue = 48 & 16 (C)
```


#### Bits.or


##### Parameters:

| Name | Type |
| :--- | :--- | 
| bit | int | 
| bit | int |

##### Returns:

| Name | Type | 
| :--- | :--- |
| newbit | int | 


```lua
local val = Bits.has(16,32) --will be 48
--this is the same as val = 16 | 32 (C)
```


#### Bits.remove


##### Parameters:

| Name | Type |
| :--- | :--- | 
| bit | int | 
| bit | int |

##### Returns:

| Name | Type | 
| :--- | :--- |
| removedbit | int | 


```lua
local val = Bits.remove(48,16) --will be 32
--this is the same as val = 48 & ~16 (C)
```



#### Bits.add


##### Parameters:

| Name | Type |
| :--- | :--- | 
| bit | int | 
| bit | int |

##### Returns:

| Name | Type | 
| :--- | :--- |
| added bit | int | 


```lua
local val = Bits.add(32,16) --will be 48
--this is the same as val = 32 | 16 (C)
```





[back to Contents](#-1)

---
