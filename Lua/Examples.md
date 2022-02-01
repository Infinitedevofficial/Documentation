#### [Back to main page](/README.md)

---
<a name="-1"></a>

|Examples|
|--------|
|[Animated Clantag](#0)| 

---


### <a name="0"></a>Animated Clantag


#### With FFI

```lua
-- @region: engine stuff
local _set_clantag = ffi.cast('int(__fastcall*)(const char*, const char*)', Memory.FindSignature('engine.dll', '53 56 57 8B DA 8B F9 FF 15'))
local _last_clantag = nil
local set_clantag = function(v)
  if v == _last_clantag then return end
  _set_clantag(v, v)
  _last_clantag = v
end
-- @endregion

-- @region: animations stuff
local build_tag = function(tag)
  local ret = { ' ' }


  -- [0] = B
  -- [1] = Bo
  -- [2] = Bob
  -- etc...
  for i = 1, #tag do
    table.insert(ret, tag:sub(1, i))
  end


  -- [0] = B
  -- [1] = Bo
  -- [2] = Bob
  -- [3] = Bo
  -- [4] = B
  for i = #ret - 1, 1, -1 do
    table.insert(ret, ret[i])
  end

  return ret
end

local tag = build_tag('BoberHook')
-- @endregion


RegisterCallback(CreateMove(),function()

    local iter = math.floor(math.fmod(GlobalVariables.Tickcount() / 16, #tag + 1) + 1)

    set_clantag(tag[iter])

end)

```

#### Without FFI

```lua
-- @region: engine stuff

local _last_clantag = nil
local set_clantag = function(v)
  if v == _last_clantag then return end
  Client.SetClantag(v, v)
  _last_clantag = v
end
-- @endregion

-- @region: animations stuff
local build_tag = function(tag)
  local ret = { ' ' }


  -- [0] = B
  -- [1] = Bo
  -- [2] = Bob
  -- etc...
  for i = 1, #tag do
    table.insert(ret, tag:sub(1, i))
  end


  -- [0] = B
  -- [1] = Bo
  -- [2] = Bob
  -- [3] = Bo
  -- [4] = B
  for i = #ret - 1, 1, -1 do
    table.insert(ret, ret[i])
  end

  return ret
end

local tag = build_tag('BoberHook')
-- @endregion




RegisterCallback(CreateMove(),function()

    local iter = math.floor(math.fmod(GlobalVariables.Tickcount() / 16, #tag + 1) + 1)

    set_clantag(tag[iter])

end)
```


[back to Contents](#-1)

---
