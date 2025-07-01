---
{"dg-publish":true,"permalink":"/04/05/lua-love/tick-lua/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-07-01T20:58"}
---

#Code/lua 
[[04 生活/05 小开发/lua与love学习笔记/input.lua\|04 生活/05 小开发/lua与love学习笔记/input.lua]]
[[04 生活/05 小开发/lua与love学习笔记/love.lua\|04 生活/05 小开发/lua与love学习笔记/love.lua]]
[[04 生活/05 小开发/lua与love学习笔记/classic.lua\|04 生活/05 小开发/lua与love学习笔记/classic.lua]]

https://github.com/rxi/tick
必须tick.update(dt)
- 主要有两个函数：
```lua
tick.delay(fn, delay)
tick.recur(fn, delay)
```
分别隔一段时间后执行一次、循环
- 进阶用法
1. :after![99 Attachment/Pasted image 20250112215213.png](/img/user/99%20Attachment/Pasted%20image%2020250112215213.png)
2. :stop
![99 Attachment/Pasted image 20250112215230.png](/img/user/99%20Attachment/Pasted%20image%2020250112215230.png)
3. 使用事件组group
![99 Attachment/Pasted image 20250112215347.png](/img/user/99%20Attachment/Pasted%20image%2020250112215347.png)
