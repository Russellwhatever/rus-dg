---
{"dg-publish":true,"permalink":"/05-zotero-notes/schreiner-transition1x-dataset-building2022/","title":"Transition1x - a dataset for building generalizable reactive machine learning potentials","noteIcon":"","created":"2025-06-20T13:59","updated":"2025-07-01T11:57"}
---

数据集地址： https://figshare.com/articles/dataset/Transition1x/19614657/4?file=36035789
具体看Data Records部分：
- 包含原子数、能量、力（每个原子上）和原子坐标（但无SMILES）
- 有的反应产物是另一个反应的反应物，可以用哈希值进行关联分析
- [x] 查看transition1x数据集的hash值关联不同反应的方法  [completion:: 2025-07-01]
DataLoader代码： https://gitlab.com/matschreiner/Transition1x
![99 Attachment/Pasted image 20250620170147.png](/img/user/99%20Attachment/Pasted%20image%2020250620170147.png)
$$\mathcal{G}_{rc}=\{(u,\ v),e_{uv}|e_{uv}\ \in \mathcal{G}_p,\ e_{uv}\ \notin \mathcal{G}_{r;j},\ \forall \mathcal{G}_{r;j}\ \in \{\mathcal{G}_{r;i}\}^{N_r}_{i=1}\}$$