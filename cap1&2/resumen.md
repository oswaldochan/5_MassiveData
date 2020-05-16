# Questions chapter 1

## At the moment of scaling a RDBMS, what is the problem of using a queue?
Adding queues to write in the database can be a temporal solution, but if the number of requests get larger, the database will become the bottleneck and thus the whole system will function slower.

## At the moment of scaling a RDBMS, what is the problem of sharding?
This can also be a good solution if the database isn't going to keep escalating, because in a few words, sharding means that you divide the database in different parts to share it across multiple machines. 
But, if the number of requests gets larger, this method will get more complex and will reduce the speed of the system.
Also, this can also create fault-tolerance issues and corruption issues

## Why aren't NoSQL databases used more often?
Because 

---

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA3MjY1MDc1LC0xOTQzODYyMzk0LDUyMD
YzMDkyNCwxMDg1MTI4ODAxXX0=
-->