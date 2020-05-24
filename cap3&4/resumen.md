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
> **Unions** are useful for representing _nodes_, **structs** are natural representations of _edges_, and _properties_ use a combination of both
- **Nodes**: a single value that may have any of several representations.
- **Edges**: each edge can be represented as a struct containing two nodes: 
- **Properties**:  contains a node and a value for the property
### Why is so important that in Thrift schemas can evolve over time?
> It is a crucial property, because as your business requirements change you’ll need to add new kinds of data, and you’ll want to do so as effortlessly as possible.  

### What is the limitation of serialization frameworks?
> They only check that all required fields are present and are of the expected type. They’re unable to check richer properties like “Ages should be non-negative” or “true-as-of timestamps should not be in the future.” Data not matching these properties would indicate a problem in your system, and you wouldn’t want them written to your master dataset.
> 
## Chapter 4

## 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4MjQ3NjE2NF19
-->