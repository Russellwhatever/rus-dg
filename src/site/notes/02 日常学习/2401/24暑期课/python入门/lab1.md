---
{"dg-publish":true,"permalink":"/02/2401/24/python/lab1/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-07-01T13:38"}
---

co-authors: Haoxiang Yang(22300220022) and Wu You(22307130158)
## Celsius_to_fahrenheit
Beyond the basic function, we make it more interactive by importing argv from sys. 
To use it, python Celsius_to_fahrenheit.py 100(or other numbers of course). 
This python file can still run with inner parameter, we show it below. Both methods return the same answer.
```
from sys import argv

def celsius_to_fahrenheit(degree_in_celsius):
    if type(degree_in_celsius) == int:
        return degree_in_celsius*9/5+32
    else:
        return int(degree_in_celsius)*9/5+32

print(celsius_to_fahrenheit(100))

print(celsius_to_fahrenheit(argv[1]))
```
And here is the result:
![99 Attachment/Pasted image 20240708155450.png](/img/user/99%20Attachment/Pasted%20image%2020240708155450.png)
## division
The division function code provided by Mr. Cao runs with the ''divided' argument divided by ''divisor' argument. 
![99 Attachment/Pasted image 20240708155902.png](/img/user/99%20Attachment/Pasted%20image%2020240708155902.png)
By changing the two arguments, different results are returned.
About "what does this tell you", hard to really conclude something useful. 
I thinks, as for a division, if the result is larger than 1, that means the **divided** argument is larger than the **divisor**, and if not, the **divisor** is larger. If the results happens to equal to 1, that means the two arguments are the same.
Additionally, when result below 0 taken into consideration, we can only know one of the argument are below 0 and judge their absolute values.
Things can become complex and there must be more ideas about the result about division, but we'll end the discussion here to keep it not too boring.
## circle_property
The function in circle_property.py receives a circle's radius and returns its circumference and area. ![99 Attachment/Pasted image 20240708160306.png](/img/user/99%20Attachment/Pasted%20image%2020240708160306.png)
## hello_returning
In this part, we run the program named `hello_returning.py`.The program is listed below.
```
def hello_returning():
    return "hello"
print(hello_returning())
```
We use the print to verify the correctness of this function,and we also interact in the terminal.The screenshot is as below.

![99 Attachment/image.png](/img/user/99%20Attachment/image.png)
## hello_printing

In this part, we run `hello_printing.py`. It print a "hello" in the terminal.We can also input `hello_printing()` to call the function to print the result.
![99 Attachment/image-1.png](/img/user/99%20Attachment/image-1.png)
The difference between hello_printing() and hello_returning():
`hello_printing()` function call the `print` function to print `hello` to the terminal. And it does not have any returning values.
While the `hello_returning()` function just return a string of `hello` to the caller, doesn't print it to the terminal.