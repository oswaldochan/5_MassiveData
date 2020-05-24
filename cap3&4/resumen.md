# Questions 

## Chapter 3
### What could be a result of using a schemaless format _(like JSON)_?
It could inevitably led to data corruption

### Why are data corruption problems hard to debug?
Because when you notice them, it's very difficult to trace back what occasioned it, or to detect what generated that corrupted data.
You don't get a comprehensive alert of how the problem was originated.

**_This doesn't occur in an enforceable schema, because it will prevent any of those error to happen at the moment of writing the data_**

### What is Apache Thrift?
>  is a tool that can be used to define statically typed, enforceable schemas. It provides an interface definition language to describe the schema in terms of generic data types, and this description can later be used to automatically generate the actual implementation in multiple programming languages. 

### What are the main components of Apache Thrift?
- **Nodes**: a single value that may have any of several representations.
- **Edges**: each edge can be represented as a struct containing two nodes
- **Properties**:
## Chapter 4
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTAwMDc2NTczXX0=
-->