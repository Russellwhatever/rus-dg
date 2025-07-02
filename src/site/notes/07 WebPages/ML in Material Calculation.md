---
{"dg-publish":true,"permalink":"/07-web-pages/ml-in-material-calculation/","noteIcon":"","created":"2025-04-22T15:02","updated":"2025-06-24T22:53"}
---

目前用在计算材料学中的机器学习主要有三个方面：语言模型/力场模型/晶体结构生成模型

## 1 语言模型（Transformer）

### 1.1 [materialsintelligence/mat2vec: "Unsupervised word embeddings capture latent knowledge from materials science literature", Nature (2019).](https://link.zhihu.com/?target=https%3A//githu%3Cb%3Eb.co%3C/b%3Em/materialsintelligence/mat2vec)

> [Mat2Vec](https://zhida.zhihu.com/search?content_id=253705562&content_type=Article&match_order=1&q=Mat2Vec&zhida_source=entity) 是由 Materials inteligence 团队开发的一个框架，它将材料的化学信息转化为向量表示，然后通过预训练模型进行各种材料属性的预测。这个项目的目的是简化新材料的设计过程，提高材料发现的效率，并促进跨学科的合作。  
> Mat2vec 的核心技术是基于词嵌入([Word Embedding](https://zhida.zhihu.com/search?content_id=253705562&content_type=Article&match_order=1&q=Word+Embedding&zhida_source=entity))的方法，如 Word2Vec和 GloVe，在材料科学领域进行了适应性的改进。在材料科学中，每个材料可以看作是一种“语言”，它的元素组合、晶体结构等特征相当于词汇，Mat2Vec 将这些复杂的特性转化为低维度的连续向量，使得计算机能够理解和处理。

### 1.2 **[MatterGPT: A Generative Transformer for Multi-Property Inverse Design of Solid-State Materials](https://zhuanlan.zhihu.com/p/23417385905/%3C/b%3Ehttps://arxiv.org/abs/2408.07608) (2024) 西安交通/岭南大学**

### 1.3 **MatChat: A large language model and application service platform for materials science 松山湖**

## 2 [通用]力场模型（[Graph NN](https://zhida.zhihu.com/search?content_id=253705562&content_type=Article&match_order=1&q=Graph+NN&zhida_source=entity)/Message passing）

## 3 [CHGNet as a pretrained universal neural network potential for charge-informed atomistic modelling | Nature Machine Intelligence (2023)](https://link.zhihu.com/?target=https%3A//www.nature.com/articles/s42256-023-00716-3)

### 3.1 **[MatterSim: A Deep Learning Atomistic Model Across Elements, Temperatures and Pressures](https://zhuanlan.zhihu.com/p/23417385905/%3C/b%3Ehttps://arxiv.org/abs/2405.04967) (2024)**

### 3.2 **[EquiformerV2: Improved Equivariant Transformer for Scaling to Higher-Degree Representations](https://zhuanlan.zhihu.com/p/23417385905/htt%3C/b%3Eps://arxiv.org/abs/2306.12059) (2024)**

## 4 结构生成模型

### 4.1 **3.1 [Diffusion model](https://zhida.zhihu.com/search?content_id=253705562&content_type=Article&match_order=1&q=Diffusion+model&zhida_source=entity)**

**MatterGen[[05 Zotero Notes/@zeniGenerativeModelInorganic2025\|05 Zotero Notes/@zeniGenerativeModelInorganic2025]]:** [A generative model for inorganic materials design | Nature](https://link.zhihu.com/?target=https%3A//www.nature.com/articles/s41586-025-08628-5) (**2025**)

**ADiT:** [All-atom Diffusion Transformers: Unified generative modelling of molecules and materials](https://link.zhihu.com/?target=https%3A//www.arxiv.org/abs/2503.03965) (**2025**)

### 4.2 Generative Adversarial Network (GAN)

CubicGAN [https://doi.org/10.1002/advs.202100566](https://link.zhihu.com/?target=https%3A//doi.org/10.1002/advs.202100566) （2021）

MatGAN [https://doi.org/10.1038/s41524-020-00352-0](https://link.zhihu.com/?target=https%3A//doi.org/10.1038/s41524-020-00352-0) （2020）

[Generative Adversarial Networks for Crystal Structure Prediction | ACS Central Science](https://link.zhihu.com/?target=https%3A//pubs.acs.org/doi/full/10.1021/acscentsci.0c00426)(**2020**)

[Crystal Structure Prediction Using Generative Adversarial Network with Data-Driven Latent Space Fusion Strategy](https://link.zhihu.com/?target=https%3A//pubs.acs.org/doi/10.1021/acs.jctc.4c01096) （2024方国勇）[[05 Zotero Notes/@chenCrystalStructurePrediction2024\|05 Zotero Notes/@chenCrystalStructurePrediction2024]]

### 4.3 Variational AutoEncoder (VAE)

CDVAE：[Crystal Diffusion Variational Autoencoder for Periodic Material Generation](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2110.06197) （2022）

### 4.4 Other (待分类)

[Crystal structure generation with autoregressive large language modeling | Nature Communications](https://link.zhihu.com/?target=https%3A//www.nature.com/articles/s41467-024-54639-7)(**2024**)

[Deep learning generative model for crystal structure prediction | npj Computational Materials](https://link.zhihu.com/?target=https%3A//www.nature.com/articles/s41524-024-01443-y%3FfromPaywallRec%3Dfalse)(**2024**马琰铭)

[CrystalGRW: Generative Modeling of Crystal Structures with Targeted Properties via Geodesic Random Walks](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2501.08998)（**2025**）

[Generative Models as an Emerging Paradigm in the Chemical Sciences | Journal of the American Chemical Society](https://link.zhihu.com/?target=https%3A//pubs.acs.org/doi/full/10.1021/jacs.2c13467) (**2023**)

[ContinuouSP: Generative Model for Crystal Structure Prediction with Invariance and Continuity](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2502.02026) (**2025**)

## 5 模型整合

### 5.1 [T2MAT (text-to-materials): A universal framework for generating material structures with goal properties from a single sentence](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2407.06489) (2024王金兰)

## 6 Hamiltonians

### 6.1 HamGNN

[Transferable equivariant graph neural networks for the Hamiltonians of molecules and solids | npj Computational Materials](https://link.zhihu.com/?target=https%3A//www.nature.com/articles/s41524-023-01130-4) （2023向红军）

[github.com](https://link.zhihu.com/?target=https%3A//github.com/QuantumLab-ZY/HamGNN)

### 6.2 DeepH

[Deep-learning density functional theory Hamiltonian for efficient ab initio electronic-structure calculation | Nature Computational Science](https://link.zhihu.com/?target=https%3A//www.nature.com/articles/s43588-022-00265-6) （2022）

[[2401.17015] DeepH-2: Enhancing deep-learning electronic structure via an equivariant local-coordinate transformer](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2401.17015) （2024）