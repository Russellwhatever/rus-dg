---
{"dg-publish":true,"permalink":"/02/2401/24/python/lab10/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-07-01T13:38"}
---

# Looping over list of dictionaries
## 1. intro to dic
![99 Attachment/Pasted image 20240729151743.png](/img/user/99%20Attachment/Pasted%20image%2020240729151743.png)
The first name can be easily printed out.
## 2. print names
![99 Attachment/Pasted image 20240729152732.png](/img/user/99%20Attachment/Pasted%20image%2020240729152732.png)
People's name are printed using a loop.
![99 Attachment/Pasted image 20240729152844.png](/img/user/99%20Attachment/Pasted%20image%2020240729152844.png)
# working with csv files
In this task, we need to process a csv file and compute the total protest number for target state.
Here is my code.
````python
from FudanCSV import get_blm_data
def total_blm_protests(states):
    data= get_blm_data('blm_state.csv')
    total_protests=0
    for state in states:
        for tuple in data:
            if tuple['State']==state:
                total_protests+=tuple['TotalProtests']

    return int(total_protests)
````
We get the data of the csv by calling function in FudanCSV firstly. As the variable data contains a list of dictionaries.
We need to use loop to seek for the target tuple whose state equls to the target,and then add them to the return value.
![99 Attachment/img 2.png](/img/user/99%20Attachment/img%202.png)