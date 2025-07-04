---
{"dg-publish":true,"permalink":"/02/2501/03/04-hw-revised/","noteIcon":"","created":"2025-03-17T23:16","updated":"2025-07-01T13:38"}
---

<p align="right">报告人：杨皓翔(22300220022)</p>
<p align="right">2025/03/19</p>
<p align="right">(GPU 版本)</p>

## 1 未修改前
训练用时：1min 32s
精确度：98.52%
混淆矩阵 
![99 Attachment/Pasted image 20250320140846.png](/img/user/99%20Attachment/Pasted%20image%2020250320140846.png)
## 2 修改
手写识别过程分别使用了数字2（在线文档中下载）、3和5（本人手写）
![99 Attachment/2.png](/img/user/99%20Attachment/2.png)
![99 Attachment/3 1.png](/img/user/99%20Attachment/3%201.png)

![99 Attachment/5 1.png](/img/user/99%20Attachment/5%201.png)
### 2.1 池化方式
将平均池化改为最大池化
用时：1min 44s
测试精度：98.60%
![99 Attachment/Pasted image 20250320141322.png](/img/user/99%20Attachment/Pasted%20image%2020250320141322.png)
分别对课程文件提供的手写数字2、我自己写的数字3、5进行识别：
2、3识别成功，5均识别失败为4
### 2.2 修改激活函数
将 `Sigmoid()` 修改为 `ReLU()`
![99 Attachment/Pasted image 20250320142725.png](/img/user/99%20Attachment/Pasted%20image%2020250320142725.png)
误差精度很大，且难以迅速收敛；反复比较，确为 ReLU 修改导致的结果。
混淆矩阵如下
![[99 Attachment/Pasted image 2025032014300png\|99 Attachment/Pasted image 2025032014300png]]
### 2.3 修改全连接层数为2层
```python
model = nn.Sequential(

    nn.Conv2d(1, 6, kernel_size=5, stride=1, padding=2),

    nn.ReLU(),

    nn.MaxPool2d(kernel_size=2, stride=2, padding=0),

    nn.Conv2d(6, 16, kernel_size=5, stride=1, padding=0),

    nn.ReLU(),

    nn.MaxPool2d(kernel_size=2, stride=2, padding=0),

    nn.Flatten(),

    nn.Linear(16 * 5 * 5, 120),

    nn.ReLU(),

    nn.Linear(120, 10)

).to(device)
```
精确度为9.8%，混淆矩阵如下
![[99 Attachment/Pasted image 2025032014364png\|99 Attachment/Pasted image 2025032014364png]]
### 2.4 更改学习率 lr = 1
精确度有了很大提升，在1min 35s 训练后达到了99.06%。混淆矩阵如下：
![99 Attachment/Pasted image 20250320143941.png](/img/user/99%20Attachment/Pasted%20image%2020250320143941.png)
使用该模型对上述的2、3、5图片进行识别，2、5识别正确，3识别错误为8。
### 2.5 增加训练次数 epoch=20
训练精度达到99.09%，提升并不明显。其混淆矩阵如图：
![99 Attachment/Pasted image 20250320144604.png](/img/user/99%20Attachment/Pasted%20image%2020250320144604.png)
对上述的2、3、5三张图片进行识别，**全部正确**，说明该模型获得了可用的成果。
