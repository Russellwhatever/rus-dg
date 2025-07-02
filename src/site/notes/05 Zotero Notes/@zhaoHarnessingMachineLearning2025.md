---
{"dg-publish":true,"permalink":"/05-zotero-notes/zhao-harnessing-machine-learning2025/","title":"Harnessing machine learning to enhance transition state search with interatomic potentials and generative models","noteIcon":"","created":"2025-06-13T20:51","updated":"2025-07-02T10:38"}
---

**目的**：对不同的生成模型和势函数进行统一评估
# Results
## TS searching workflow
### **MLIP**
1. optimize 输入结构
2. growing string method(GSM[[05 Zotero Notes/@zimmermanGrowingStringMethod2013\|@zimmermanGrowingStringMethod2013]])：嵌入几何结构、能量和梯度为==MEP==， MEP上的能量最高值即为**TS 初猜**
3. 并进行TS-optimization（Hessian-based restricted-step rational-function-optimization optimization，其中每一步都使用MLIP计算Hessian
4. IRC: comparing the IRC endpoints with the input reactant and product
### **Generative approach**
直接生成**TS初猜** 
## Benchmark MLIP
数据集：transition1x[[05 Zotero Notes/@schreinerTransition1xDatasetBuilding2022\|@schreinerTransition1xDatasetBuilding2022]]。
算了TS-opt和IRC，IRC显示只有一部分是==intended==，因此：energy and force预测使用了所有transition1x数据集的验证集，但TS-search只使用了intended的这部分反应。
**评估**：6 MLIPs（只使用非反应数据集预训练）：
1. TS-search: ==GSM正确率==和==TS正确率==
总体来说，有两类评测指标：
1. Energy and force MAE：最直观的评估标准
2. **success and intended rates**：即上提到的GSM正确率和TS正确率；**TS RMSD**；**能垒MAE**：在端对端TS搜索后才能获得数据，更准确地反应TS搜索能力
