---
{"dg-publish":true,"permalink":"/02/2401/24/python/lab3/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-07-01T13:38"}
---

# first_occurrence
Based on what we've learned this class, we finished two versions of python functions(in the uploaded first_occurrence.py, **first_occurrence(nums, threshold)** and **another_func(nums, threshold)**), both of which work satisfyingly.
first_occurrence() function uses three **if** and another_func() function sets 'return -1' as default value.
Here's the report(functions' name are changed into instructed form):
![99 Attachment/Pasted image 20240711154701.png](/img/user/99%20Attachment/Pasted%20image%2020240711154701.png)
# sum_every_kth
The following is the after-debugging codes
```python
def sum_every_kth(start, end, k):
    if k >=0 or start <= end:
        return None

    total = 0
    for number in range(start, end, k):
        total += number

    return total
```
In this code,the question tell us "k<0",so we only need to take the condition that k<0 and start>end into consideration. 
In the code,we can find that the variable "total" should be initial as 0. In the loop structure, "k-1" should be "k", and in the loop content, total is the sum of number so that we modify it.

Here is the run result which is as our expect.
![alt text](/img/user/99 Attachment/image.png)