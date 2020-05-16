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
- **Robustness and fault tolerance**: it must handle technical problems with the machines
- **Low latency reads and updates**: it must access in a matter of milliseconds
- **Scalability**: more data? no problem
- **Generalizatio**n: it must supports a variety of applications
- **Extensibility**: more functionalities with less development cost
- **Ad hoc queries**: it must me able to mine a dataset arbitrarily
- **Minimal maintenance**: self explanatory
- **Debuggability**: if something goes wrong, it must be clear where.

## What are some problems of fully Incremental architectures?
- **Operational complexity**: getting rid of unused parts of the database that occupy memory and can fill the disk, it's dealt by a process called compaction, which adds complexity to the system.
- **Extreme complexity of achieving eventual consistency**:  in order for the system to be *highly available*, it must keep its *consistency*, which is very complex , even with small amounts of data. 
- **Lack of human-fault tolerance**: Any mistake will make the database to be corrupted, and as human mistakes are unavoidable, the system will eventually be corrupted by a human mistake.
---
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0OTE4OTQ2MDMsLTEzMDg2MzI5NCwxMz
g4MjQ0NDkzLC0xOTQzODYyMzk0LDUyMDYzMDkyNCwxMDg1MTI4
ODAxXX0=
-->