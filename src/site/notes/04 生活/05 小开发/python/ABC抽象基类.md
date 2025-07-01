---
{"dg-publish":true,"permalink":"/04/05/python/abc/","noteIcon":"","created":"2025-03-06T16:36","updated":"2025-07-01T20:58"}
---

#Code/python/ABC抽象基类
https://www.cnblogs.com/shengshengwang/p/17949810
简单来说，首先需要from abc import ABC, abstractmethod

此处的ABC即为一个抽象的基类，在想要创建抽象基类的时候就建立ABC的子类，并@abstractmethod
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

# 之后的类即须继承shape
def Circle(Shape):
    def _init_(self, radius):
        self.radius = radius
    def area(self):
        return 3.14*r*r
```
以上为一个示例