---
{"dg-publish":true,"permalink":"/02/2501/03/03-hw-revised/","noteIcon":"","created":"2025-03-16T13:42","updated":"2025-07-01T13:38"}
---

# 未修改前
优化器：`Adam`, `lr = 0.01`
```python
optimizer = torch.optim.Adam(

    model.parameters(),  

    lr=0.01 )
```
隐藏神经元为10；训练100epoch
![99 Attachment/Pasted image 20250316151906.png](/img/user/99%20Attachment/Pasted%20image%2020250316151906.png)
最终训练精度97%，测试精度93%
# 修改优化器为 SGD 并将学习系数改为 `lr = 0.05`
![99 Attachment/Pasted image 20250316153011.png](/img/user/99%20Attachment/Pasted%20image%2020250316153011.png)
最终训练精度为90%，最终测试精度为83%，均有所降低
## 更改神经网络结构
隐藏层神经元数量为50
```python
model = nn.Sequential(

    nn.Linear(4, 50),  

    nn.ReLU(),       

    nn.Linear(50, 3),  

)
```
![99 Attachment/Pasted image 20250316153415.png](/img/user/99%20Attachment/Pasted%20image%2020250316153415.png)
最终训练精度为92%，最终测试精度为83%。
# 修改激活函数为 Sigmoid ()
```python
model = nn.Sequential(

    nn.Linear(4, 50),  

    nn.Sigmoid(),       

    nn.Linear(50, 3),  

)
```
![99 Attachment/Pasted image 20250316153648.png](/img/user/99%20Attachment/Pasted%20image%2020250316153648.png)
最终训练精度为90%，测试精度为80%。观察损失函数与迭代次数的关系，注意到损失降低速度曲线的凸度明显降低。
# 增加迭代次数至1000
于是增加迭代次数 `epoch_num = 1000 `
![99 Attachment/Pasted image 20250316153913.png](/img/user/99%20Attachment/Pasted%20image%2020250316153913.png)
最终训练精度为95%，最终测试精度为97%。相比之前结果均有显著提升。
其混淆矩阵如图![99 Attachment/Pasted image 20250316154003.png](/img/user/99%20Attachment/Pasted%20image%2020250316154003.png)