---
{"dg-publish":true,"permalink":"/02/2401/24/python/lab8/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-07-01T13:38"}
---

# lab8 Report
Haoxiang Yang(22300220022) YouWu(22307130158)
# Code analysis
In this work, we are required to manipulate on every pixel complete the function "greyscale". We just need to average the RGB value and fill it to the original position.
Detail code is as follows.
```python
from FudanImageLib import *

def greyscale(img):
    img_h = height(img)
    img_w = width(img)
    for i in range(img_h):
        for j in range(img_w):
            (r,g,b) = img[i][j]
            grey = (r+g+b)//3
            img[i][j] = (grey,grey,grey)

# process the function
img = load_img("1.jpg")
greyscale(img)
save_img(img,"2.jpg")
```