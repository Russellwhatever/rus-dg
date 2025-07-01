---
{"dg-publish":true,"permalink":"/02/2501/05-llm-md/03-md-mol-genius/","noteIcon":"","created":"2025-03-25T14:23","updated":"2025-07-01T13:38"}
---

相比于第一性原理计算中的常用软件 VASP，分子动力学常用的计算软件 Gromacs 和Lammps 虽然因为免费和开源的特性，拥有了更大的自由度，但同时也带来了输入文件中写法混乱的问题。以 Gromacs[[05 Zotero Notes/@vanderspoelGROMACSFastFlexible2005\|05 Zotero Notes/@vanderspoelGROMACSFastFlexible2005]][[05 Zotero Notes/@abrahamGROMACSHighPerformance2015\|05 Zotero Notes/@abrahamGROMACSHighPerformance2015]] 为例，其可用于几百万个粒子体系的分子动力学模拟研究，并在对非键作用的计算上具有优势，在生物、医药、材料、化学等领域都有广泛的应用。
【这里写已经写过的：命令行输入复杂、输入文件多种多样等】
在一个典型的分子动力学计算中，主要有文件准备、计算以及对计算结果进行分析和下一步计算等步骤。
# 文件准备阶段
文件准备阶段，需要较为复杂的多种文件：
- 结构文件包括 PDB 文件与 gro 文件。前者主要用于描述蛋白结构信息，现在也被用于其他分子；后者是 GROMACS 独有的结构信息文件
- 拓扑文件：. top 文件包含所有的立场参数，需使用程序 pdb2gmx 生成。如果需要处理特殊分子类型，可能还需要使用. itp 文件、. rtp (残基拓扑文件)、. n2t（原子名称以及类型对照文件）等。
- 数据库文件：可以使用不同数据库与力场列表文件，对不同体系计算与残基处理方式进行设定。
此外，还有 energy.edr、.eps 等指定封装文件格式的文件。复杂的文件与设定之间的取舍，一直为非专业计算人员画下壁垒，一定程度上限制了分子动力学计算的普及。
# 计算数据的分析
针对分子动力学软件输出的轨迹文件，有多种处理方式，但都较为复杂，如 Pteros[[05 Zotero Notes/@yesylevskyyPterosFastEasy2012\|05 Zotero Notes/@yesylevskyyPterosFastEasy2012]]、MDTraj[[05 Zotero Notes/@mcgibbonMDTrajModernOpen2015\|05 Zotero Notes/@mcgibbonMDTrajModernOpen2015]]、TTClust[[05 Zotero Notes/@tubianaTTClustVersatileMolecular2018\|05 Zotero Notes/@tubianaTTClustVersatileMolecular2018]] 等框架，部分功能甚至需要手写 Fortran 处理可视化。
此外，由于分子动力学模拟的计算尺度以 ps 为单位，输出数据是一个巨量数字，甚至可以达到**上万帧**，对其进行分析和处理对经验不丰富的科研人员无疑是一个巨大的挑战。而如果能将该分析步骤交给 AI 进行处理，无疑能在大大降低门槛的同时提高分析效率，从而促进对分子动力学模拟的处理分析。


(1)Van Der Spoel, D.; Lindahl, E.; Hess, B.; Groenhof, G.; Mark, A. E.; Berendsen, H. J. C. GROMACS: Fast, Flexible, and Free. _Journal of Computational Chemistry_ **2005**, _26_ (16), 1701–1718. [https://doi.org/10.1002/jcc.20291](https://doi.org/10.1002/jcc.20291).

(2)Abraham, M. J.; Murtola, T.; Schulz, R.; Páll, S.; Smith, J. C.; Hess, B.; Lindahl, E. GROMACS: High Performance Molecular Simulations through Multi-Level Parallelism from Laptops to Supercomputers. _SoftwareX_ **2015**, _1–2_, 19–25. [https://doi.org/10.1016/j.softx.2015.06.001](https://doi.org/10.1016/j.softx.2015.06.001).

(3)Yesylevskyy, S. O. Pteros: Fast and Easy to Use Open-Source C++ Library for Molecular Analysis. _Journal of Computational Chemistry_ **2012**, _33_ (19), 1632–1636. [https://doi.org/10.1002/jcc.22989](https://doi.org/10.1002/jcc.22989).

(4)McGibbon, R. T.; Beauchamp, K. A.; Harrigan, M. P.; Klein, C.; Swails, J. M.; Hernández, C. X.; Schwantes, C. R.; Wang, L.-P.; Lane, T. J.; Pande, V. S. MDTraj: A Modern Open Library for the Analysis of Molecular Dynamics Trajectories. _Biophysical Journal_ **2015**, _109_ (8), 1528–1532. [https://doi.org/10.1016/j.bpj.2015.08.015](https://doi.org/10.1016/j.bpj.2015.08.015).

(5)Tubiana, T.; Carvaillo, J.-C.; Boulard, Y.; Bressanelli, S. TTClust: A Versatile Molecular Simulation Trajectory Clustering Program with Graphical Summaries. _J. Chem. Inf. Model._ **2018**, _58_ (11), 2178–2182. [https://doi.org/10.1021/acs.jcim.8b00512](https://doi.org/10.1021/acs.jcim.8b00512).