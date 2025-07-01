---
{"dg-publish":true,"permalink":"/04/05/lua-love/classic-lua/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-07-01T20:58"}
---

构建类：
```lua
test = Object:extend()
--or
test = Object.extend(Object)
--then
function test.new(self)
    self.x = 100
    self.y = 200
end
--or
function test:new(x, y)
    self.x = x or 100
    self.y = y or 100
end
```
创建实例：
```lua
local p = Test(10,20)
```
[[04 生活/05 小开发/lua与love学习笔记/love.lua\|04 生活/05 小开发/lua与love学习笔记/love.lua]]