---
{"dg-publish":true,"permalink":"/05-zotero-notes/chen-graph-networks-universal2019/","title":"Graph Networks as a Universal Machine Learning Framework for Molecules and Crystals","tags":["ZoteroNotes"],"noteIcon":"","created":"2025-03-08T10:05","updated":"2025-07-01T11:57"}
---

#Chemistry化学/ML机器学习势函数 
- 两大局限：晶体与分子分开训练；缺乏全局状态的描述 （不同温度等）
- MEGNet 将一举解决上述两个问题，可以视为 CGCNN 的超集
# 方法
- V E 分别指代无晶格周期性和有晶格周期性的原子集合。整个工作用材料表述所有的分子和晶体
![99 Attachment/Pasted image 20250403175532.png](/img/user/99%20Attachment/Pasted%20image%2020250403175532.png)
三个属性：原子属性 V、键属性 E、全局状态属性 u。然后每一步依次用其他所有属性更新其中一种属性，先更新键属性 E，再更新原子属性 V，最后更新状态属性 u。
## 首先更新键属性
![99 Attachment/Pasted image 20250403180343.png](/img/user/99%20Attachment/Pasted%20image%2020250403180343.png)
类似。
## 具体的 update function $\phi_{e},\phi_{\nu},\phi_{u}$
都是有两层隐藏层的算子 
![99 Attachment/Pasted image 20250403181333.png](/img/user/99%20Attachment/Pasted%20image%2020250403181333.png)
## 其他
在每个 MEGNet 模块前增加两个密集层（全连接层）对输入进行预处理（以提高灵活性和准确性）
![99 Attachment/Pasted image 20250403181638.png](/img/user/99%20Attachment/Pasted%20image%2020250403181638.png)
## 参数
分子：
![99 Attachment/Pasted image 20250403181757.png](/img/user/99%20Attachment/Pasted%20image%2020250403181757.png)
# 相关文献-后续
[[05 Zotero Notes/@chenUniversalGraphDeep2022\|05 Zotero Notes/@chenUniversalGraphDeep2022]]