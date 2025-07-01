---
{"dg-publish":true,"permalink":"/05-zotero-notes/joshi-allatom-diffusion-transformers2025/","title":"All-atom diffusion transformers: Unified generative modelling of molecules and materials","noteIcon":"","created":"2025-06-13T20:54","updated":"2025-07-01T11:57"}
---


模型名字：ADiT
看起来倒像是vae：
（1）自动编码器，将分子和材料统一的全原子表示映射到潜在嵌入空间
（2）训练扩散模型，生成新的潜在嵌入
（3）自动编码器可以解码来采样新的分子或材料
# introduction
介绍了一下已有的扩散模型：都是基于特定体系
- 小分子的生成：Hoogeboom et al., 2022 用两个独立的扩散过程生成原子类型和3D结构；
- 生物分子：将原子团视为刚体，并在联合扩散过程中加入rotation（这一维度）
- 晶体和材料：扩散过程需要额外处理周期性，对原子类型、分数坐标、晶格长度、晶格角度进行操作
本文（统一模型）：
1. 认为都是3D空间的子集，使用每个原子的categorical、continuous属性，形成了一个统一的表示。
2. ==一个VAE（Kingma and Welling, 2014）==把分子和晶体插进了一个共同的latent space
3. 隐空间扩散：Diffusion Transformer（这又是啥？ Rombach et al., 2022; Peebles and Xie, 2023）
4. classifier-free guidance（Ho and Salimans, 2022）采样潜在空间，用VAE decoder重建分子或晶体
怎么证明有效的：
1. 在QM9（分子）和MP20（材料）上一起训练，获得了很好的效果，超过专门模型（没说具体咋超过的，也许是取长补短呢）
2. DFT计算表明，SUN率5-6%，比之前方法的4-5%好了25%（...）
3. validity rate：用两个数据集一起训练的比单独训练的好，说明有效果
4. 在GEOM-DRUGS（大分子）数据集上训练，ADiTs相等或超过最新的模型。
# ADiT的具体训练步骤
- [x] ADiT的具体步骤 有时间再看  [completion:: 2025-07-01]