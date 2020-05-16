# Questions chapter 1

## At the moment of scaling a RDBMS, what is the problem of using a queue?
Adding queues to write in the database can be a temporal solution, but if the number of requests get larger, the database will become the bottleneck and thus the whole system will function slower.

## At the moment of scaling a RDBMS, what is the problem of sharding?
This can also be a good solution if the database isn't going to keep escalating, because in a few words, sharding means that you divide the database in different parts to share it across multiple machines. 
But, if the number of requests gets larger, this method will get more complex and will reduce the speed of the system.
Also, this can also create fault-tolerance issues and corruption issues

## Why aren't NoSQL databases used more often?
Because it has some trade-offs, so this systems are not suitable for all cases.
Per example, Hadoop's computations have high latency, and NoSQL databases like Cassandra used a more limited data model.

## What is Lambda Architecture?
> " The Lambda Architecture provides a general-purpose approach to implementing an arbitrary function on an arbitrary dataset and having the function return its results with low latency. "
> "The Lambda Architecture defines a consistent approach to choosing the technologies to implement a data system to and to wiring them together to meet your requirements. "

## What are some desired properties of a Big Data System?
- Robustness and fault tolerance: it must handle technical problems with the machines
- Low latency reads and updates: it must access in a matter of milliseconds
- Scalability: more data? no problem
- Generalization: it must function with a va
---
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTQ0OTU3ODY1LC0xMzA4NjMyOTQsMTM4OD
I0NDQ5MywtMTk0Mzg2MjM5NCw1MjA2MzA5MjQsMTA4NTEyODgw
MV19
-->