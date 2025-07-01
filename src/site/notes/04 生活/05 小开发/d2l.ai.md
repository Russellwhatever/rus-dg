---
{"dg-publish":true,"permalink":"/04/05/d2l-ai/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-04-18T00:42"}
---

# 基础知识
#Code/pytorch
### - 常用函数：
x = torch.arange(12,dtype=torch.float32).reshape((3,4))
x.sum()
x=torch.zeros(12)
x=torch.zeros_like(y)，可以生成与y形状相同的全零张量
### - 广播机制
![99 Attachment/Pasted image 20240903112009.png](/img/user/99%20Attachment/Pasted%20image%2020240903112009.png)
### - 索引与切片
基本一样
### - 节省内存
![99 Attachment/Pasted image 20240903112202.png](/img/user/99%20Attachment/Pasted%20image%2020240903112202.png)
可以看到，计算后地址发生了改变。我们不希望这样，原因有二：
1. 节省内存
2. 防止其他代码引用了错误的参数
这可以通过使用Y[:]=X+Y来解决，id地址没有发生改变
或者X+=Y，同样不会发生地址的改变
### 转换为其他python对象
#### numpy张量
A=B.numpy()
B=torch.tensor(A)
实现了互相转化
#### python张量（大小只能为1）
a=torch.tensor([3.5])
b=a.item()

