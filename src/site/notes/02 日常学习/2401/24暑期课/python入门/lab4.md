---
{"dg-publish":true,"permalink":"/02/2401/24/python/lab4/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-07-01T13:38"}
---

# stack frame tracing
When executing `hours_to_seconds(20)` , it works like this:
```
 hours_to_seconds(20)
    minutes = hours_to_minutes(20)
    seconds = minutes_seconds(1200)
```
4 steps in total. 3 stack frames.
********************************
As for `days_to_seconds(6)`, it's basically the same.
```
days_to_seconds(6)
    hours = days_to_hours(6)
        ...
        ...
    seconds = hours_to_seconds(144)
        minutes = hours_to_minutes(hours)
            ...
            ...
        seconds = minutes_to_seconds(minutes)
            ...
            ...
        ...
    return 
```
5 frame stacks this time.
*******************
3+5=8 stack frames and 1 global frame, concluding a sum of 9 frames in total.
# Visualization
global frame: ![99 Attachment/Pasted image 20240715154314.png](/img/user/99%20Attachment/Pasted%20image%2020240715154314.png)
when executing `hours_to_seconds(20)` , 3 stack frames occurred,  5 executing `days_to_seconds(6)`, 9 in total. 
The visualization answer matches our previous conclusion well.
# updating list in place
Here's the result: ![99 Attachment/Pasted image 20240715154729.png](/img/user/99%20Attachment/Pasted%20image%2020240715154729.png)
After calling the function on list1, list3 changed with it while list2 keeps unchanged. 
By processing `list3 = list1`, a reference relationship is created. In this way, they are now pointing to the same place, where stored data's change can influence both of them. However, `list2=[0,1,2,3]` just create another individual list and therefore has nothing to do with list1 or list3.
We should differentiate the variable type,because we may modify some variables accidently.This will cause our programs running error which is difficult to find.
When we use object references in function calls,we should be careful about the passed reference variables, because it may be modified in the callee function. We should remind the caller that we will modify these variables in the function.
# global vs local variables
![99 Attachment/Pasted image 20240715155846.png](/img/user/99%20Attachment/Pasted%20image%2020240715155846.png)
- global variables: 1
num = 10
- local variables: 1
in function mutiply_local(), num is 40 after calculation
- 'number' and 'multiple' are parameters
- Same with the code results, num after multiple equals to 10, and num after multiple_global(here's a tiny spelling mistake in the source code) equals to 40.