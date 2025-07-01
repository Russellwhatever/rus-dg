---
{"dg-publish":true,"permalink":"/02/2401/24/python/lab7/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-07-01T13:38"}
---

# Geometrical index calculation
# 1. calculating Index
![99 Attachment/Pasted image 20240722144930.png](/img/user/99%20Attachment/Pasted%20image%2020240722144930.png)
B: img$[3][12]$
## 2. Mirror/Flip an Image
![99 Attachment/Pasted image 20240722145645.png](/img/user/99%20Attachment/Pasted%20image%2020240722145645.png)
### (1) 
For even cases, there are two midpoints, the indices of which are $5+width/ /2 -1$ and $5+width/ /2$ respectively.(**5 is the index of A**)
Given the image has a width of 8 pixels, the indices of M and N are 8 and 9.
### (2)
For odd cases, there is only 1 midpoint with its index $5+width/ /2$ .
Given the image has a width of 7 pixels, the index of M should be 8.
### (3)
The loop should be like this:
```python
for i in range(high_img):
    for j in range(3,3+width//2):
        # process
```
In `calculating_index.py`, we wrote a function in this way and verified its reliability.
In this way, the python file take in a picture named 'OhtoAi.png' and create a processed picture "test.png":
![99 Attachment/OhtoAi 1.png|300](/img/user/99%20Attachment/OhtoAi%201.png)
![99 Attachment/test.png|300](/img/user/99%20Attachment/test.png)
Here we decided to change a area (start with a horizonal originate of 1000 and width of half of that of the whole picture) into white. It returned as we had wished, therefore proved the reliability of the loop.
# Cropping an image in half horizontally
In this task, we complete this "crop_top_half.py" to finish the target function. 
Fist of all, Computing the new_height is necessary, in which we use to create a new image. 
Then, we make the new created image's pixels equal to corresponding position. 
The following is our result.
![99 Attachment/img 1.png](/img/user/99%20Attachment/img%201.png)