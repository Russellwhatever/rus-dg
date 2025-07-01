---
{"dg-publish":true,"permalink":"/02/2402/02/9-yhx/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-07-01T13:38"}
---

# 1. 什么是扩散模型？简述扩散模型的训练策略
对已有的数据集，通过连续添加高斯噪声来扩散训练数据，然后再翻转这个噪声过程来学习恢复数据。训练之后，可以将随机采样的噪声传入模型之中，通过学习去噪来生成数据。
# 2. 仍待解决的问题
## 2.1. 支链作用的探究
AF推测残基之间的物理邻近性，主要预测的是蛋白质折叠，但是对于对蛋白质性能更重要的支链folding预测效果并不好
Xu, G.; Wang, Q.; Ma, J. OPUS-Fold: An Open-Source Protein Folding Framework Based on Torsion-Angle Sampling. _J. Chem. Theory Comput._ **2020**, _16_ (6), 3970–3976. [https://doi.org/10.1021/acs.jctc.0c00186](https://doi.org/10.1021/acs.jctc.0c00186).
## 2.2. 蛋白质与配体的结合
蛋白质与小分子配体的结合作用对其性质有重要影响，对蛋白质-配体相互作用进行探究具有重要意义
# 复习
人工智能的关键突破
- 1. 共进化算法
- 2. 卷积残差网络
- 注意力机制：超越传统卷积神经网络的局部限制，可以捕捉到长程相互作用
![99 Attachment/Pasted image 20241216090944.png](/img/user/99%20Attachment/Pasted%20image%2020241216090944.png)