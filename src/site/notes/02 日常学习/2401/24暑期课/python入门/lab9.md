---
{"dg-publish":true,"permalink":"/02/2401/24/python/lab9/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-07-01T13:38"}
---

# 1.Integers in binary form
In this task,we use the funtion "bin()" to convert a decimal number to a binary numbers.The following is the result, and after manually convert these numbers on a piece of paper, they are as expected.


![99 Attachment/image 1.png](/img/user/99%20Attachment/image%201.png)

# 2. Bitwise AND,OR
In this task,we learn the Bitwise AND,OR.We try these two operations with the example numbers.In the following picture we show that the result of runing "&" or "|",as well as the binary form of each numbers to evaluate the correctness of result.Then, we get the conclusion that 172 & 57 = 40 and 89 | 125 = 125.

![99 Attachment/image-1 1.png](/img/user/99%20Attachment/image-1%201.png)
# 3. Bits shifting
![99 Attachment/Pasted image 20240725145129.png](/img/user/99%20Attachment/Pasted%20image%2020240725145129.png)
When shifting to left, there will not be data lost, while shifting to right does cause loss of imformation.  This well explains above phenomenon.
37 << 1 >> 1: keeps the same
37 >>1(this step throws away the less important bit) << 1: different from that at the very beginning.
# 4. Bits replacement
![99 Attachment/Pasted image 20240725150132.png](/img/user/99%20Attachment/Pasted%20image%2020240725150132.png)
Bits replacement can be easily implemented with & and |,  as is shown in the python file.
```
def bits_replace(num1, num2):
    temp1 = num1 & 0b11110000
    temp2 = num2 & 0b00001111
    num = temp1 | temp2
    return num
```
However, if the num1 is bigger than 255, there will be numbers lost when & 0b11110000, so we optimize it by bits shifting:
```
def bits_replace(num1, num2):
    temp1 = num1 >> 4 << 4
    temp2 = num2 & 0b00001111
    num = temp1 | temp2
    return num
```
This not gonna happen.