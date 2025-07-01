---
{"dg-publish":true,"permalink":"/04/05/lua-love/room-and-room-lua/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-07-01T20:58"}
---

https://github.com/a327ex/blog/issues/17
[[04 生活/05 小开发/lua与love学习笔记/room and room.lua\|04 生活/05 小开发/lua与love学习笔记/room and room.lua]]
[[04 生活/05 小开发/lua与love学习笔记/input.lua\|04 生活/05 小开发/lua与love学习笔记/input.lua]]
[[04 生活/05 小开发/lua与love学习笔记/love.lua\|04 生活/05 小开发/lua与love学习笔记/love.lua]]
[[04 生活/05 小开发/lua与love学习笔记/classic.lua\|04 生活/05 小开发/lua与love学习笔记/classic.lua]]

## contains a Stage Object
```lua
Stage = Object:extend()
function Stage:new()
end
function Stage:update(dt)
end
function Stage:draw()
end
```
then in the love
```lua
function love.load()
    current_room = nil
end
function love.update()
    if current_room then current_room:update(dt) end
end
function love.draw()
    if current_room then current_room:draw() end
end

--e.g., gotoRoom('Stage',...)
function gotoRoom(room_type,...)
    current_room = _G[room_type](...)
end
```
当然，这种方法，每次切换房间都会重新加载，且切走之后就没用了
********************
非常简单的游戏和工具软件不太需要这个，但是下面介绍如何保存
```lua
function love.load()
    rooms = {}
    current_room = nil
end

function love.update(dt)
    if current_room then current_room:update(dt) end
end

function love.draw()
    if current_room then current_room:draw() end
end

function addRoom(room_type, room_name, ...)
    local room = _G[room_type](room_name, ...)
    rooms[room_name] = room
    return room
end

function gotoRoom(room_type, room_name, ...)
    if current_room and rooms[room_name] then
        if current_room.deactivate then current_room:deactivate() end
        current_room = rooms[room_name]
        if current_room.activate then current_room:activate() end
    else current_room = addRoom(room_type, room_name, ...) end
end
```
这个和DownWell中的GameObject很相似，使用table储存和切换