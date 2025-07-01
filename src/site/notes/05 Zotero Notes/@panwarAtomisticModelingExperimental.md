---
{"dg-publish":true,"permalink":"/05-zotero-notes/panwar-atomistic-modeling-experimental/","title":"Atomistic modeling and experimental study of dopant segregation induced morphology transition in ZnO nanoparticles","noteIcon":"","created":"2025-05-19T14:58","updated":"2025-07-01T11:57"}
---

研究ZnO晶体的结构差异、提及自由能的降低以及**掺杂剂的界面偏析**会导致不同的生长机制。
- 使用离子散射光谱和紫外光电子能谱对掺杂样品进行了研究，证实了偏析和Zn空位的形成。
- 采用Wulff构建方式建模
- 根据计算的表面能设计了路线图，以了解ZnO纳米颗粒中的形态转变
## 计算方法
- 用力场进行计算，ZnO的结构取自文献34
- 建模（这一段描述的详细地反常，是不是有什么神秘的方法？）：不同角度切，保留不同深度（因此表面并不完全一样），relax（使用METADISE code，文献41），取能量最低的表面构型进行进一步计算
- ZnO的极性表面还需要进行一些偶极平衡，我看起来还挺新奇的，不过不急着了解
- 可能结构有很多，因此使用了**多目标遗传算法（MOGA）进行初筛**。
# 结果分析
## 1 Structural Analysis
XRD：Al和Mg分别掺入ZnO
都只有ZnO的六方纤锌矿结构；Mg浓度增加出现了向高角度偏移的峰，说明Mg导致了晶格收缩；Mg和Al离子半径都很小，但Al掺杂**没有导致晶格收缩，可能是因为强烈的Segregation向晶面偏析，大多数存在于晶体表面而不是内部。**
- W-H分析：量化掺杂粉末的局部应变