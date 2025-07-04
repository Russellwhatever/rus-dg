---
{"dg-publish":true,"permalink":"/07-web-pages/icml-2022-se-3-equivariant-graph-neural-networks-with-complete-local-frames-2025-07-03-t215845-0800/","title":"论文笔记 | ICML  2022 | SE(3) Equivariant Graph Neural Networks with Complete Local Frames","noteIcon":"","created":"2025-07-03","updated":"2025-07-03T22:18"}
---

#clipping #AI人工智能/SE3 
from: https://zhuanlan.zhihu.com/p/555600524
author: [[执者失之软件工程本科毕业，软件工程硕士在读，研究：隐私计算、联邦学习\|执者失之软件工程本科毕业，软件工程硕士在读，研究：隐私计算、联邦学习]]
published: 
Failed to fetch

![论文笔记 | ICML  2022 | SE(3) Equivariant Graph Neural Networks with Complete Local Frames](https://pic1.zhimg.com/70/v2-be44dd257aa82a737de81c9786357f70_1440w.avis?source=172ae18b&biz_tag=Post)

论文笔记 | ICML 2022 | SE(3) Equivariant Graph Neural Networks with Complete Local Frames

## SE(3) Equivariant Graph Neural Networks with Complete Local Frames

> **文章信息**  [[05 Zotero Notes/@duSE3EquivariantGraph2022\|@duSE3EquivariantGraph2022]]
>   
> **「来源」** ：Proceedings of the 39th International Conference on Machine Learning（ICML） 2022  
> **「标题」** ：SE(3) Equivariant Graph Neural Networks with Complete Local Frames  
> **「作者」** ：Weitao Du, He Zhang, Yuanqi Du, Qi Meng, Wei Chen, Nanning Zheng, Bin Shao, Tie-Yan Liu  
> **「链接」** ： [proceedings.mlr.press/v](https://link.zhihu.com/?target=https%3A//proceedings.mlr.press/v162/du22e.html)  

## 内容简介

从经典和量子物理学到计算生物学，群等变（例如 SE(3) 等变）是科学中的关键物理对称性。它可以在任意参考变换下实现稳健和准确的预测。有鉴于此，人们投入了大量精力将这种对称性编码到深度神经网络中，这已被证明可以提高下游任务的泛化性能和数据效率。构建 [等变神经网络](https://zhida.zhihu.com/search?content_id=211599404&content_type=Article&match_order=1&q=%E7%AD%89%E5%8F%98%E7%A5%9E%E7%BB%8F%E7%BD%91%E7%BB%9C&zhida_source=entity) 通常会带来较高的计算成本以确保表现力。因此，如何更好地权衡表现力和计算效率在等变深度学习模型的设计中起着核心作用。

在本文中，作者提出了一个框架来构建 SE(3) 等变 [图神经网络](https://zhida.zhihu.com/search?content_id=211599404&content_type=Article&match_order=1&q=%E5%9B%BE%E7%A5%9E%E7%BB%8F%E7%BD%91%E7%BB%9C&zhida_source=entity) ，即 [ClofNet](https://zhida.zhihu.com/search?content_id=211599404&content_type=Article&match_order=1&q=ClofNet&zhida_source=entity) ，该网络可以有效地逼近几何量。受 [微分几何](https://zhida.zhihu.com/search?content_id=211599404&content_type=Article&match_order=1&q=%E5%BE%AE%E5%88%86%E5%87%A0%E4%BD%95&zhida_source=entity) 和物理学的启发，作者将等变的局部完整框架引入到图神经网络中，从而可以将给定阶数的张量信息投影到框架上。局部框架被构造为形成正交基，避免方向退化并确保完整性。由于框架仅通过叉积运算构建，因此该方法在计算上是有效的。文章在两个任务上评估本文提出的方法： [牛顿力学](https://zhida.zhihu.com/search?content_id=211599404&content_type=Article&match_order=1&q=%E7%89%9B%E9%A1%BF%E5%8A%9B%E5%AD%A6&zhida_source=entity) 建模和平衡 [分子构象生成](https://zhida.zhihu.com/search?content_id=211599404&content_type=Article&match_order=1&q=%E5%88%86%E5%AD%90%E6%9E%84%E8%B1%A1%E7%94%9F%E6%88%90&zhida_source=entity) 。广泛的实验结果表明，本文的模型在两种类型的数据集中实现了最佳或具有竞争力的性能。

## 相关理论知识与技术

### SE(3) 组和等方差

在欧几里得空间 $R3\mathbb{R}^{3}\mathbb{R}^{3}$ 中，我们考虑保留任意两点之间距离的仿射变换，即等距群 SE(3)。我们称之为对称群 w.r.t 欧几里得度量，结果证明 SE(3) 可以由平移组和 3D 旋转组 SO(3) 生成。一旦给定一个对称群，定义对称群下“等变”的量是有效的。给定一个函数 $f:Rm→Rnf: \mathbb{R}^{m} \rightarrow \mathbb{R}^{n}$ ，假设对称群 $GG$ 作用在 $Rm\mathbb{R}^{m}$ 和 $Rn\mathbb{R}^{n}$ 上，我们分别用 $TgT_{g}$ 和 $SgS_{g}$ 表示这些作用，那么如果：

$f(Tgx)=Sgf(x),∀x∈Rm and g∈G.f\left(T_{g} x\right)=S_{g} f(x), \quad \forall x \in \mathbb{R}^{m} \text { and } g \in G . \\f\left(T_{g} x\right)=S_{g} f(x), \quad \forall x \in \mathbb{R}^{m} \text { and } g \in G . \\$

则 $fff$ 是 $GG$ 等变的。

### 图神经网络

由于许多身体系统建模独立于观察到的粒子上的标记（置换等方差），因此我们将在本文中使用基于图的消息传递机制（Gilmer 等人，2020）。给定一个图 $G=(V(G),E(G))G=(V(G), E(G))G=(V(G), E(G))$ ，**设 $h_i$ 、 $x_i$ 和 $e_{ij}$ 分别为节点特征、节点位置和边属性**。EGNN (Satorras et al., 2021b) 提供了一种学习等变表示的有效方法，它将边缘消息 $m_{ij}$ 、节点嵌入 $h_i$ 和坐标 $x_i$ 更新为：

$$\begin{aligned} m_{i j} &=\phi_{m}\left(h_{i}, h_{j},\left\|\boldsymbol{x}_{j}-\boldsymbol{x}_{i}\right\|^{2}, e_{i j}\right) \\ \boldsymbol{x}_{i} &=\boldsymbol{x}_{i}+C \sum_{j \neq i}\left(\boldsymbol{x}_{i}-\boldsymbol{x}_{j}\right) \phi_{x}\left(m_{i j}\right) \\ h_{i} &=\phi_{h}\left(h_{i}, \sum_{j \in \mathcal{N}(i)} m_{i j}\right) \end{aligned} $$

其中 $\phi_{m}$ 、 $\phi_{x}$ 和 $\phi_{h}$ 表示三个神经网络。 $CC$ 是归一化因子。

## 方法介绍

本小节提供了 ClofNet 的详细描述。为了保持系统的物理对称性，作者将系统表示为一个空间图，并基于它构建具有三个关键组件的 ClofNet：

- 一个 **标量块** ，其可以将几何张量投影到本文构建的等变帧并将所有系数连接为附加到每个节点的 SO(3) 不变标量表示；
- 一个 **图消息传递块** ，通过在图上传播和聚合标量来学习 SO(3) 不变的边嵌入；
- 一个 **向量化块** ，用于将标量表示反转回张量。

ClofNet 的简要概述如下图所示。

![](https://pic1.zhimg.com/v2-8d062b1655b248adb86c80e08d5465fc_1440w.jpg)

  

### 标量块（Scalarization Block）

标量化模块旨在通过引入一种新颖的局部帧元组将几何张量转换为沿边 SO(3) 不变的标量系数/特征。考虑时间 $tt$ 的粒子对 $(\boldsymbol{x}_i(t), \boldsymbol{x}_j(t))$ ，其中 $\boldsymbol{x}_{j}(t) \in \mathcal{N}\left(\boldsymbol{x}_{i}(t)\right)$ 。 将边缘 SO(3) 不变标量定义为：

$s_{ij} := Scalarize(\boldsymbol{x}_i(t), \boldsymbol{x}_j(t), \mathcal{F}_{i j})$

其中 Scalarize 是局部等变帧 $\mathcal{F}_{i j}\mathcal{F}_{i j}$ 下的标量化操作。

### 图消息传递块

在将几何张量编码为 SO(3) 不变标量 $s_{ij}s_{ij}$ 后，文章首先将它们与其他预定义的节点/边属性 $(h_j, e_{ij})$ 单独嵌入到高维表示中，并利用图消息传递 (GMP) 块通过在图 GX 上传播和聚合信息来学习 SO(3) 不变的边消息嵌入 $m_{ij}$ 。由于该块处理不变标量，因此 ClofNet 是灵活的，因为在执行消息传递时可以应用任何非线性激活，这样输出仍然是不变标量。对于更复杂的任务，本文的模型能够包含注意力机制。

### 向量化块

此块仅对 SO(3) 等变向量输出（或一般张量输出）是必需的。==对于标量输出，在图消息传递块之后的简单池化层就足够了。给定传播的沿边消息 $m_{ij}m_{ij}$ ，向量化块旨在将这些标量转换回等变向量（标量化的逆），这需要将 $m_{ij}$ 与相应的完整帧配对。更准确地说，文章首先将 $m_{ij}$ 投影为一个标量三元组 $\left\{x_{i j}^{a}, x_{i j}^{b}, x_{i j}^{c}\right\}$ ，然后将向量化过程定义为：==

$\\\left(x_{i j}^{a}, x_{i j}^{b}, x_{i j}^{c}\right) \stackrel{\text { Pairing }}{\longrightarrow} x_{i j}^{a} a_{i j}+x_{i j}^{b} b_{i j}+x_{i j}^{c} c_{i j}$

### 算法概览

经过上述的介绍后，ClofNet 的算法概览如下图所示。

![](https://pica.zhimg.com/v2-0cdd519292e9d6d538a44e7ce122e018_1440w.jpg)

  

## 实验分析

本文引入了两个多体（many-body）场景来验证 ClofNet 在逼近复杂几何信息和避免方向退化方面的优势：

- 模拟的牛顿力学系统。
- 真实世界的分子系统。

### 牛顿多体系统（Newtonian many-body system）

在这个实验中，本文利用 ClofNet 来预测由牛顿力场驱动的合成多体系统的未来位置，这是一个典型的等变任务，因为对初始系统状态应用任何旋转或平移都会导致对未来的相同变换系统位置。这项任务的灵感来自 (Kipf et al., 2018; Fuchs et al., 2020; Satorras et al., 2021b)，其中 5 体（5-body）带电系统由静电力场控制。请注意，任何两个粒子之间的力方向在原始设置中始终沿径向方向。为了验证 ClofNet 对任意力方向建模的有效性，文章还在原始系统中施加了两个外力场，一个重力场和一个类似洛伦兹的动力场，这可以提供更复杂的和动态的力方向。

![](https://pic2.zhimg.com/v2-bba8ff9b57e94aacb74166cb053eeeeb_1440w.jpg)

实验结果如上表所示，本文提出的的模型在所有数据集上显着优于所有基线，证明了 ClofNet 在建模几何系统方面的表现力。更重要的是，与之前的任务最先进（SOTA）EGNN相比，ClofNet 在两个更具挑战性的力场场景中表现出更强的建模能力，说明 ClofNet 可以有效地建模除径向之外的复杂力方向。与 TFN 和 SE(3) Transformer 相比，ClofNet 显着缩短的前向时间表明，ClofNet 也比基于球谐函数的等变模型更具时间效率。因为它只处理原始空间中的张量，不包括任何复杂的等变函数。

### 分子系统（Molecular Systems）

为了验证 ClofNet 在实际场景中的有效性，本文在分子系统中称为==平衡构象生成==的基本任务上评估 ClofNet，试图从 2D 分子图预测稳定的 3D 结构。现有的 SOTA 方法之一通过直接估计原子坐标对数密度的梯度场，然后使用估计的梯度场生成稳定的结构来解决该问题（Shi 等人，2021；Xu 等人，2021）。这种方法的主要挑战是原子坐标的这种梯度场是 SE(3) 等变的。按照这种范式，文章利用 ClofNet 来估计原子坐标的梯度场，以说明其在复杂分子系统上的建模能力。

![](https://picx.zhimg.com/v2-6874ce8164c79c0df558c7ac2160dcc1_1440w.jpg)

实验结果如上表所示，ClofNet 在几乎所有指标和数据集上都取得了最好或次优的性能，证明了本文提出的方法的有效性。特别是在 Drugs 数据集上，与采用与我们类似的学习策略的 ConfGF 相比，ClofNet 显着提高了 26.5% COV-mean 和 26.6% COV-median 分数。值得注意的是，ClofNet 还实现了比 DGSM 更好的性能，后者利用了更复杂的动态图构建策略。一种可能的解释是 Drugs 中的分子通常比 QM9 包含更多的原子和复杂的化学官能团（例如苯环），因此基于距离的几何结构不足以模拟这种复杂分布的梯度场。

## 总结

为了更有效、更灵活地表达几何信息，本文开发了一种新的具有完整局部框架的 SE(3) 等变神经网络 (ClofNet)，旨在无损利用张量，而无需结合高维等变函数嵌入。通过提出的局部框架，ClofNet 可以与任何图神经网络合作，而无需担心破坏等方差对称。理论分析和广泛的实证结果验证了 ClofNet 的有效性。将来，文章会将本文所提出的策略扩展到其他（局部）对称群。

发布于 2022-08-19 15:13[图神经网络（GNN）](https://www.zhihu.com/topic/20747184)[ICML22](https://www.zhihu.com/topic/25559103)[深度学习（Deep Learning）](https://www.zhihu.com/topic/19813032)