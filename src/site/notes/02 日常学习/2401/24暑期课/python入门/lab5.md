---
{"dg-publish":true,"permalink":"/02/2401/24/python/lab5/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-07-01T13:38"}
---

# 1. create_tuple.py
- By using ![99 Attachment/Pasted image 20240716144809.png](/img/user/99%20Attachment/Pasted%20image%2020240716144809.png)
we successfully get the length of tuple_example and the string converted. 
- An error will occurr by `tuple_example[3]=" 285"` because tuple elements are not allowed to change.
# 2. singleton_tuple.py
![99 Attachment/Pasted image 20240716145652.png](/img/user/99%20Attachment/Pasted%20image%2020240716145652.png)
Here's why: by writing a comma the python will regard it as a tuple consisting of string "apple" and nothing, but without that determinative comma, it's just a string with brackets.
# 3. extract_tuple.py
![99 Attachment/Pasted image 20240716150136.png](/img/user/99%20Attachment/Pasted%20image%2020240716150136.png)
That's what the extract_tuple function do: input a tuple and its begin&end index, it will output a new tuple consisting of elements from the begin_index to end_index(the two end elements are included).
What's more, if the provided index is out of range, an error will not be published. It will just calmly output elements efrom begin_index to the last in the input_tuple into the new tuple.
![99 Attachment/Pasted image 20240716150632.png](/img/user/99%20Attachment/Pasted%20image%2020240716150632.png)
And if you're wondering what will happen if the indexes input are below 0, here's the result ![99 Attachment/Pasted image 20240716151801.png](/img/user/99%20Attachment/Pasted%20image%2020240716151801.png)
Apparenly, it doesn't really matter if the index is below 0 or not. If there are elements in the range ruled by the index, output tuple will contain those elements, or else, a pair of empty brackets.
# 4. unpack_tuple
When we first run the code,we will get fruit_x equal to "apple" and fruit_y equal to "orange". Then we add "(fruit_x, fruit_y) = (fruit_y, fruit_x)",we will swap the value of fruit_x and fruit_y. Fruit_x will change to "orange" and fruit_y will change to "apple".
# 5. number_pairs
To realize the target function, we just need to save each position of list to a tuple according to the index.
Here is the result.
![alt text](/img/user/99 Attachment/image.png)
# 6. sum_of_product
We set result=0 as the accumulation variable and just need to mutiply every tuple element ,then add them.
![alt text](/img/user/99 Attachment/image-1.png)