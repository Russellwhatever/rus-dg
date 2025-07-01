---
{"dg-publish":true,"permalink":"/02/2501/03/09-transformer/","noteIcon":"","created":"2025-04-17T20:15","updated":"2025-07-01T13:38"}
---

# 1 应用 NLP 模型
## 1.1 中英文互译
```python
translator = pipeline("translation_en_to_zh", model="Helsinki-NLP/opus-en-zh", device=0)
```
![99 Attachment/Pasted image 20250420210153.png](/img/user/99%20Attachment/Pasted%20image%2020250420210153.png)
成功翻译 
## 1.2 使用其他语言进行互相翻译
更换参数：
```python
translator = pipeline("translation_en_to_fr", 
                      model="Helsinki-NLP/opus-mt-en-fr", 
                      device=0)
```
成功将英语翻译为法语
![99 Attachment/Pasted image 20250420213859.png](/img/user/99%20Attachment/Pasted%20image%2020250420213859.png)
将法语翻译为英语
![99 Attachment/Pasted image 20250420214407.png](/img/user/99%20Attachment/Pasted%20image%2020250420214407.png)
# 2 使用 ollama 命令行
```bash
ollama run qwen2.5:3b
```
![99 Attachment/Pasted image 20250420214500.png](/img/user/99%20Attachment/Pasted%20image%2020250420214500.png)
# 3 使用 Ollama 脚本调用方式
(见提交文件夹中 Ollama-translator.py)
## 3.1 中英互译
![99 Attachment/Pasted image 20250420220044.png](/img/user/99%20Attachment/Pasted%20image%2020250420220044.png)
![99 Attachment/Pasted image 20250420220130.png](/img/user/99%20Attachment/Pasted%20image%2020250420220130.png)
## 3.2 其他语言
仍然选择了英语与法语的互译
![99 Attachment/Pasted image 20250420220222.png](/img/user/99%20Attachment/Pasted%20image%2020250420220222.png)
![99 Attachment/Pasted image 20250420220253.png](/img/user/99%20Attachment/Pasted%20image%2020250420220253.png)
可以看到，翻译结果都是正确的。