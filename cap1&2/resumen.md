# Questions
 
## Chapter 1

### At the moment of scaling a RDBMS, what is the problem of using a queue?
Adding queues to write in the database can be a temporal solution, but if the number of requests get larger, the database will become the bottleneck and thus the whole system will function slower.

### At the moment of scaling a RDBMS, what is the problem of sharding?
This can also be a good solution if the database isn't going to keep escalating, because in a few words, sharding means that you divide the database in different parts to share it across multiple machines. 
But, if the number of requests gets larger, this method will get more complex and will reduce the speed of the system.
Also, this can also create fault-tolerance issues and corruption issues.
### Why aren't NoSQL databases used more often?
Because it has some trade-offs, so this systems are not suitable for all cases.
Per example, Hadoop's computations have high latency, and NoSQL databases like Cassandra used a more limited data model.

### What is Lambda Architecture?
> " The Lambda Architecture provides a general-purpose approach to implementing an arbitrary function on an arbitrary dataset and having the function return its results with low latency. "
> "The Lambda Architecture defines a consistent approach to choosing the technologies to implement a data system to and to wiring them together to meet your requirements. "

### What are some desired properties of a Big Data System?
- **Robustness and fault tolerance**: it must handle technical problems with the machines
- **Low latency reads and updates**: it must access in a matter of milliseconds.
- **Scalability**: more data? no problem
- **Generalizatio**n: it must supports a variety of applications.
- **Extensibility**: more functionalities with less development cost.
- **Ad hoc queries**: it must me able to mine a dataset arbitrarily.
- **Minimal maintenance**: self explanatory
- **Debuggability**: if something goes wrong, it must be clear where.

### What are some problems of fully Incremental architectures?
- **Operational complexity**: getting rid of unused parts of the database that occupy memory and can fill the disk, it's dealt by a process called compaction, which adds complexity to the system.
- **Extreme complexity of achieving eventual consistency**:  in order for the system to be *highly available*, it must keep its *consistency*, which is very complex , even with small amounts of data. 
- **Lack of human-fault tolerance**: Any mistake will make the database to be corrupted, and as human mistakes are unavoidable, the system will eventually be corrupted by a human mistake.

### What are the differences between batch, serving and speed layer?
- The **batch** layer is where the the database is precomputed, so it doesn't have to scan the whole database every time a query is made. The **serving** layer is where the last result of the *batch layer* can be viewed and accessed. Finally, the **speed** layer is updated in real time, so whilst the *serving layer* is being updated and replaced with newer data, the last data available can still be accessed.

## Chapter 2
### What does it mean that "data is raw"
In a few words, it means that you can deduct more information from it. Somehow it means the data is *less processed*, and thus, you can get more insights from it because you have more room to play and experiment with your data.
Also there exists the concept of *granularity*, which means that the data is more crumbled.

It's important to notice that:
> Unstructured data is rawer than normalized data

and

>More information doesn't necessarily mean rawer data.

### What does it mean that "data is immutable"
In Big Data Systems, data doesn't get updated or deleted, instead, more data is added, so it handle human faults and gains simplicity
In a immutable schema:
> Rather than storing a current snapshot of the world, as done by the mutable schema, you create a separate record every time a user’s information evolves.
### What does it mean that "data is eternally true"
> The key consequence of immutability is that each piece of data is true in perpetuity. That is, a piece of data, once true, must always be true. Immutability wouldn’t make sense without this property.

### What is a fact?
It's the fundamental unit of data, like *atoms* of data.


### What are the properties of facts?
- **Atomic**: because they can't be divided in smaller pieces
- **Timestamped**: because every piece of data has a *birth date*, which makes apparently duplicated data, unique one from another. 

### What are the advantages of the fact based model?
> - Is queryable at any time in its history.
> - Tolerated human errors.
> - Handles partial information.
> - Has the advantages of both normalized and denormalized forms.

### What is a graph schema?
A way of:
> capturing the structure of a dataset stored using the fact-based model using graphs.

### What are the elements of a graph schema?
- **Nodes**: are the entities in the system.
- **Edges**: are the relationships between nodes.
- **Properties**: are the information about entities.
---
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5MzQ2NTcyLC01NDI4NzIxOTQsLTEzND
Q1NDQ2MTUsLTE0OTE4OTQ2MDMsLTEzMDg2MzI5NCwxMzg4MjQ0
NDkzLC0xOTQzODYyMzk0LDUyMDYzMDkyNCwxMDg1MTI4ODAxXX
0=
-->