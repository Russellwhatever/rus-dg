---
{"dg-publish":true,"permalink":"/02/2401/24/python/lab2/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-07-01T13:38"}
---

# 1
if the second argument is included in the string, the executable will return True, or else False.
![99 Attachment/Pasted image 20240709151920.png](/img/user/99%20Attachment/Pasted%20image%2020240709151920.png)
Additionally, it's worth mentioning that if you imput a list or tuple, the file can still work  and this is understandable considering the function given is using "in" to judge.
![99 Attachment/Pasted image 20240709150337.png](/img/user/99%20Attachment/Pasted%20image%2020240709150337.png)
Additionally again, this python file can only judge if the char is included but unable to tell its place. We expanded its capablity.
# count_
The executable can quickly echo how many input chars there is in the string. 
![99 Attachment/Pasted image 20240709152506.png](/img/user/99%20Attachment/Pasted%20image%2020240709152506.png)
And if the word is not in the string, it will echo "0"
# get_char_index
This python file will return the index of input character or space. And if you input a word with more than one character, it will only consider the first character. If there is more than 1 provided character included in the string, it will return the first index.
![99 Attachment/Pasted image 20240709153121.png](/img/user/99%20Attachment/Pasted%20image%2020240709153121.png)
If there is no input character in the string, the python file will report an Error, as shown above.
# remove_leading_ending_spaces
Just as the function name says, this function can remove the leading and ending spaces in the provided string. And if there is no leading or ending space, the function will leave the input string unchanged.
![99 Attachment/Pasted image 20240709154137.png](/img/user/99%20Attachment/Pasted%20image%2020240709154137.png)
# extract_substring
The following is my result after running this program.
As we can see,we extract the substring between [a,b),noting that it doesn't consist of the character in the position 'b'.
When we start index exceed the upper bound of the list,it will return a substring "".When the end index exceed the upper bound of the list,its function just equal "input_string[start_index:]".Just like the statements above, it will not give us an error.
When we input a negative index,it will interpret it to the positive as the list's rule. So "-2" is the last 2 position of the string.

![alt text](/img/user/99 Attachment/image.png)

# list_operations
The following is the result of many operations to the list structure. 
- check_element_int_list: if the target element is in the list, this function will then return true.
- count_element_occurrence: This function is to count the number of target element occurred in the list. In the example, we count the element "2" in the list "[1,2,2,3,4,5]",and it returns 2 which is as expected.
- get_element_index: This function is to return the first position that the target number occurs.And then return the position.In the example, we want to find the position of "3",and it returns "2" which is correct.
- extract_sublist: return the target substring by specifying the start and end position.In the example, we want to slice the position of "2" to "4",and it returns[3,4]. Obviously, it implies the position 2 and position 3.
- add_element_to_end: Add an element to the end of list.
By the function test above, we can find that operations concerning list are similar to string. Maybe we can see String as a special type of list which includes of a few element of "char".
![alt text](/img/user/99 Attachment/image-1.png)