---
{"dg-publish":true,"permalink":"/05-zotero-notes/zeni-generative-model-inorganic2025/","title":"A generative model for inorganic materials design","noteIcon":"","created":"2025-04-25T00:06","updated":"2025-07-01T11:57"}
---

随便网上一搜通讯作者，居然就能搜到报道：https://www.mittrchina.com/news/detail/14304
#People人/谢天
#Chemistry化学/ai4chem/DiffusionModel扩散模型/MatternGen
# 模型内容
与直接添加高斯噪声不同，MatterGen 用元素 A、原子坐标 X、周期晶格 L 来确定晶胞。（SI A.1 A.2）

## Generating stable, diversi materials
使用一个较粗糙的生成模型批量生成化学结构，并对其进行评价：稳定（0.1eV/atom vs 最稳定结构）、独特（这里没有详细说明，只说了如果不match就算是新结构![99 Attachment/Pasted image 20250530174318.png](/img/user/99%20Attachment/Pasted%20image%2020250530174318.png)
具体内容在SI D4）
## Chemistry-guided design
找到目标的化学体系most stable需要大批量的DFT计算，这里是使用MLFF（MatterSim，另一篇文献，还没读过）先优化，再根据其稳定性，挑选不那么稳定的进行DFT计算。
Fine-tune面向不同化学体系的MatternGen模型（SI B1）：对三元、四元、五元化学体系分别完全探索、部分探索、未探索，各9个。（SI D6）。与RSS（第一性原理的一种方法，还没仔细看）和Substitution（可能是直接替换原子？）相比，MatterGen在三元和四元体系不如substitution，但五元最高。
> 完全探索：structures near the hull are known but not provided in training
> 部分探索：structures near the hull are provided during training

找到了几个好材料
## Property-guided design

## Discussion
主要创新点：引入原子类型、晶胞参数和晶格的扩散模型；大得多的数据集
不足：模型会更多生成P1对称性的模型，（SI D2）；作者认为去噪过程、架构和数据集拓展可以解决这个问题
展望：鉴于生成模型在图像生成和蛋白质设计等领域的巨大影响，我们相信在未来几年，MatterGen这样的模型会同样改变材料设计，可能可以从催化剂表面拓展到MOF等更广泛的材料中。
# SI
## A1
M= (A, X, L)
# A3
使用了两种流行的连续性数据扩散过程：
### Variance-exploding diffusion 方差爆炸扩散
就是DSM去噪得分匹配过程中使用的去噪过程。
### Variance-preserving diffusion 保方差扩散
【待读】

# Code Available
https://github.com/microsoft/mattergen

问题：
- [x] Checkpoint是干啥的  [completion:: 2025-05-30]
## 使用模型进行生成：
```terminal
export MODEL_NAME=mattergen_base
export RESULTS_PATH=results/  # Samples will be written to this directory

# generate batch_size * num_batches samples
mattergen-generate $RESULTS_PATH --pretrained-name=$MODEL_NAME --batch_size=16 --num_batches 1
```
本地运行：将`pretrained-name=`改为`--model_path=$MODEL_PATH`
## 画图 or 评估自己的模型
plot_benchmark_results.ipynb
## 源代码
### Class DiffusionModule
> 让我为您详细解释 MatterGen 是如何实现化学结构模型的扩散生成的。整个生成过程主要包含以下几个关键部分：
> 
> 1. 入口点和初始化：
> 
> - 从 mattergen/scripts/generate.py 开始，通过 CrystalGenerator 类进行初始化
> 
> - 主要参数包括：
> 
> - batch_size: 每批生成的样本数
> 
> - num_batches: 生成批次数
> 
> - properties_to_condition_on: 条件生成的目标属性
> 
> - diffusion_guidance_factor: 扩散引导因子
> 
> 1. 扩散模型核心组件：
> 
> - DiffusionModule 类（在 mattergen/diffusion/diffusion_module.py）是核心组件，负责：
> 
> - 添加噪声（`_corrupt_batch 方法`）
> 
> - 计算损失（calc_loss 方法）
> 
> - 计算分数（score_fn 方法）
> 
> 1. 去噪器实现：
> 
> - GemNetTDenoiser 类（在 mattergen/denoiser.py）是主要的去噪模型：
> 
> - 输入：包含分数坐标、晶格、原子类型等信息的化学图
> 
> - 输出：预测的噪声和原子类型更新
> 
> 1. 采样过程：
> 
> - PredictorCorrector 类（在 mattergen/diffusion/sampling/pc_sampler.py）实现预测-校正采样：
> 
> - 使用预测器和校正器进行采样
> 
> - 支持离散和连续变量的采样
> 
> - 可以记录生成轨迹
> 
> 1. 晶格扩散：
> 
> - LatticeVPSDE 类（在 mattergen/common/diffusion/corruption.py）处理晶格扩散：
> 
> - 实现方差保持的随机微分方程（VPSDE）
> 
> - 根据原子数量调整晶格参数
> 
> - 控制密度限制
> 
> 1. 生成流程：
>     
>     python
>     
>     Apply to diffusion_mo...
>     
>     # 1. 初始化生成器
>     
>     generator = CrystalGenerator(
>     
>         checkpoint_info=checkpoint_info,
>     
>         properties_to_condition_on=properties_to_condition_on,
>     
>         batch_size=batch_size,
>     
>         num_batches=num_batches
>     
>     )
>     
>     # 2. 准备模型和配置
>     
>     generator.prepare()  # 加载模型和配置
>     
>     # 3. 执行生成
>     
>     generated_structures = generator.generate(
>     
>         output_dir=output_path
>     
>     )
>     
> 
> 1. 生成过程的关键步骤：
> 
> - 加载预训练模型
> 
> - 设置采样配置
> 
> - 创建条件加载器
> 
> - 初始化采样器
> 
> - 执行扩散生成
> 
> - 将生成的晶体结构保存为 CIF 和 extxyz 格式
> 
> 1. 条件生成支持：
> 
> - 支持基于属性的条件生成
> 
> - 支持基于化学组成的条件生成
> 
> - 使用扩散引导因子控制生成过程
> 
> 1. 输出格式：
> 
> - generated_crystals_cif.zip: 包含生成的晶体结构的 CIF 文件
> 
> - generated_crystals.extxyz: 包含所有生成结构的单个文件
> 
> - generated_trajectories.zip: 包含生成过程的轨迹（如果启用）
> 
> 这个实现使用了现代的扩散模型技术，结合了化学和材料科学的特定需求，能够生成具有特定属性的晶体结构。整个过程是端到端的，从噪声采样开始，通过多步去噪过程，最终生成符合要求的晶体结构。
> 
> 您是否需要我详细解释其中的某个具体部分？比如扩散过程的具体实现，或者条件生成的机制？
> 