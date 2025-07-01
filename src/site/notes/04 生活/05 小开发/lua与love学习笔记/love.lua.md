---
{"dg-publish":true,"permalink":"/04/05/lua-love/love-lua/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-07-01T20:58"}
---

```lua
--write
love.filesystem.write("save.dat", raw)
--read
local data = string.split(raw, ",")
```
***********
![99 Attachment/Pasted image 20250116104658.png](/img/user/99%20Attachment/Pasted%20image%2020250116104658.png)
LOVE内部的接受输入方法。但是这样的输入都是全局的，不方便，所以可以使用专门的input模块[[04 生活/05 小开发/lua与love学习笔记/input.lua\|04 生活/05 小开发/lua与love学习笔记/input.lua]]