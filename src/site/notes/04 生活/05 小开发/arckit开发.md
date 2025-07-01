---
{"dg-publish":true,"permalink":"/04/05/arckit/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-03-17T13:23"}
---

# 功能
1. 观察结构：
按f focus
正交与透视视图切换
2. 基本编辑功能：点击查看原子的元素和坐标；修改原子坐标
观察：一键展示所有原子的序号；显示与关闭晶胞
3. 文件上的修改功能：归正；把某些原子移到文件最下方；自动识别有几层（纵坐标不同）并能批量移动层
4. 批量操作：保存操作历史为连续文件（同时记录为逐帧的图集，方便记录操作的内容）
# unity教程
![99 Attachment/Pasted image 20250109233724.png](/img/user/99%20Attachment/Pasted%20image%2020250109233724.png)
位置：
this.gameobject.transform.position
this.gameobject.transform.localposition  
或者直接
this.transform.localposition
修改坐标：
this.transform.localposition = new Vector3(x,y,z)
取得时间: Time.time, Time.deltatime

