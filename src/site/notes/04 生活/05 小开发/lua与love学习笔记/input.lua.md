---
{"dg-publish":true,"permalink":"/04/05/lua-love/input-lua/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-07-01T20:58"}
---

https://github.com/a327ex/boipushy/blob/master/Input.lua
[[04 生活/05 小开发/lua与love学习笔记/love.lua\|love.lua]]
[[04 生活/05 小开发/lua与love学习笔记/classic.lua\|04 生活/05 小开发/lua与love学习笔记/classic.lua]]
## 绑定键位：
```lua
input:bind('1','print')
input:bind('s',function() print(2) end)
input:bind('mouse1','left_click')
```
第一个参数是输入的键，第二个是内部input名/函数操作
## 监听
```lua
function love.update(dt)
    if input:pressed('print') then print('2') end
    if input:released('print') then print('3') end
    if input:down('left_click') then print('4') end
end
```
down是每一帧起效。也可以自定义设置
```lua
    if input:down('left_click', 0.5, 2)
```
每0.5s一次，等待2s执行
```
for instance. If you hold the `x` key down, first `x` will be typed once, there will be a small amount of time (like say 0.3s) where nothing happens, and then a lot of `x` will come following really fast.
```
## sequences
```lua
function love.update(dt)
  if input:sequence('right', 0.5, 'right') then
    -- dash right
  end
end
```
连招，0.5s内按两次
## unbinding
```
input.unbind('1')
```
## 鼠标和手柄的键位名作者改过，如表所示
```lua
-- Mouse
'mouse1'
'mouse2'
'mouse3'
'mouse4'
'mouse5'
'wheelup'
'wheeldown'

-- Gamepad
'fdown' -- fdown/up/left/right = face buttons: a, b...
'fup'
'fleft'
'fright'
'back'
'guide'
'start'
'leftstick' -- left stick pressed or not (boolean)
'rightstick' -- right stick pressed or not (boolean)
'l1'
'r1'
'l2' -- returns a value from 0 to 1
'r2' -- returns a value from 0 to 1
'dpup' -- dpad buttons
'dpdown'
'dpleft'
'dpright'
'leftx' -- returns a value from -1 to 1, the left stick's horizontal position
'lefty' -- same for vertical
'rightx' -- same for right stick
'righty'
```