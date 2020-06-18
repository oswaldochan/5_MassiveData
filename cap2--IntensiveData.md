[TOC]

# Chapter 2: Data models and query languages

## Relational model vs Document model

### What was the original purpose of RDBMS and what are their current purposes?

Originally, is was intended to be used for transaction processing (entering sales or banking trans‐
actions, airline reservations, stock-keeping in warehouses) and batch processing (customer invoicing, payroll, reporting).

Currently, it is used in online publishing, discussion, social networking, ecommerce, games, software-as-a-service productivity applications, or much more.

### What are the main reasons people want to adopt NOSQL databases?

- A need for greater scalability than relational databases can easily achieve, including very large datasets or very high write throughput.
- A widespread preference for free and open source software over commercial database product.
-  Specialized query operations that are not well supported by the relational model.
-  Frustration with the restrictiveness of relational schemas, and a desire for a more dynamic and expressive data mode.

### What is impedance mismatch?

In SQL data models, an awkward translation layer is required between the objects in the application code and the database model of tables, rows, and columns. The disconnect between the models is sometimes called an impedance mismatch

### What is the advantage of using _ID_’s in a database?

The advantage of using an ID is that because it has no meaning to humans, it never needs to change: the ID can remain the same, even if the information it identifies changes. Anything that is meaningful to humans may need to change sometime in the future—and if that information is duplicated, all the redundant copies need to be updated. That incurs write overheads, and risks inconsistencies (where some copies of the information are updated but others aren’t

### How have document models handled _one-to-many relationships_?

By storing nested records (one-to-many relationships, like `positions` , `education` , and
`contact_info`) within their parent record rather than in a separate table.

```json
{
    "user_id": 251,
    "first_name": "Bill",
    "last_name": "Gates",
    "summary": "Co-chair of the Bill & Melinda Gates... Active blogger.",
    "region_id": "us:91",
    "industry_id": 131,
    "photo_url": "/p/7/000/253/05b/308dd6e.jpg",
     "positions": [
        {"job_title": "Co-chair", "organization": "Bill & Melinda Gates Foundation"},
        {"job_title": "Co-founder, Chairman", "organization": "Microsoft"}
        ],
    "education": [
        {"school_name": "Harvard University", "start": 1973, "end": 1975},
        {"school_name": "Lakeside School, Seattle", "start": null, "end": null}
        ],
    "contact_info": {
        "blog": "http://thegatesnotes.com",
        "twitter": "http://twitter.com/BillGates"
        }
}
```

### What are the main arguments in the Relational vs Document battle?

The main arguments in favor of the document data model are schema flexibility, better performance due to locality, and that for some applications it is closer to the data structures used by the application. The relational model counters by providing better support for joins, and many-to-one and many-to-many relationships.

_It’s not possible to say in general which data model leads to simpler application code; it depends on the kinds of relationships that exist between data items._

## Query language for Data

### What is an imperative language?

An imperative language tells the computer to perform certain operations in a certain order. You can imagine stepping through the code line by line, evaluating conditions, updating variables, and deciding whether to go around the loop one more time.

### What is a declarative language and what are its advantage?

In a declarative _query_ language, like SQL or relational algebra, you just specify the pattern of the data you want—what conditions the results must meet, and how you want the data to be transformed (e.g., sorted, grouped, and aggregated)—but not how to achieve that goal. It is up to the database system’s query optimizer to decide which indexes and which join methods to use, and in which order to execute various parts of the query.

A declarative query language is attractive because it is typically more concise and easier to work with than an imperative API. But more importantly, it also hides implementation details of the database engine, which makes it possible for the database system to introduce performance improvements without requiring any changes to queries.

Also, declarative languages often lend themselves to parallel execution.

Finally, the advantages are not limited to databases, but can also have applications in other areas, such as web development, like in CSS.

### What is _MapReduce_?

MapReduce is a programming model for processing large amounts of data in bulk across many machines, popularized by Google.

MapReduce is neither a declarative query language nor a fully imperative query API, but somewhere in between: the logic of the query is expressed with snippets of code, which are called repeatedly by the processing framework. It is based on the` map` (also known as collect ) and `reduce` (also known as fold or inject ) functions that exist in many functional programming languages.

## Graph-like Data Models

### When is recommended to use a graph data model?

As the connections within your data become more complex (_many-to-many relationships_), it becomes more natural to start modeling your data as a _graph_. 

A graph consists of two kinds of objects: vertices (also known as nodes or entities) and edges (also known as relationships or arcs). Many kinds of data can be modeled as a graph. Typical examples include: 

- Social graphs 

  ​	Vertices are people, and edges indicate which people know each other. 

- The web graph 

  ​	Vertices are web pages, and edges indicate HTML links to other pages. 

- Road or rail networks 

  ​	Vertices are junctions, and edges represent the roads or railway lines between them.  

### What are the elements of _Property Graphs_?

In the property graph model, each _vertex_ consists of:

- A unique identifier

- A set of outgoing edges

- A set of incoming edges

- A collection of properties (key-value pairs)

Each _edge_ consists of:

- A unique identifier

- The vertex at which the edge starts (the tail vertex)

- The vertex at which the edge ends (the head vertex)

- A label to describe the kind of relationship between the two vertices

- A collection of properties (key-value pairs

Some important aspects of this model are:
1. Any vertex can have an edge connecting it with any other vertex. There is no schema that restricts which kinds of things can or cannot be associated.
2. Given any vertex, you can efficiently find both its incoming and its outgoing edges, and thus traverse the graph—i.e., follow a path through a chain of vertices —both forward and backward. 
3. By using different labels for different kinds of relationships, you can store several different kinds of information in a single graph, while still maintaining a clean data model.

### What is cypher?

Cypher is a declarative query language for property graphs, created for the Neo4j graph database

### What are the elements of _Triple-Stores Model_?

In a triple-store, all information is stored in the form of very simple three-part statements: (subject, predicate, object). For example, in the triple (`Jim, likes, bananas`), `Jim`  is the subject, `likes` is the predicate (verb), and` bananas` is the object.  The subject of a triple is equivalent to a _vertex_ in a graph. The object is one of two  things:
- A value in a primitive datatype, such as a string or a number. In that case, the  predicate and object of the triple are equivalent to the key and value of a property  on the subject vertex. For example, (lucy, age, 33) is like a vertex `lucy` with properties {`"age":33`} .

- Another vertex in the graph. In that case, the predicate is an edge in the graph,  the subject is the tail vertex, and the object is the head vertex. For example, in  (lucy, marriedTo, alain) the subject and object `lucy` and `alain` are both vertices,  and the predicate `marriedTo` is the label of the _edge_ that connects them.

### In a few words, what is the main difference between the two main NoSQL models?

- _Document databases_ target use cases where data comes in self-contained documents and relationships between one document and another are rare.

- _Graph databases_ go in the opposite direction, targeting use cases where anything is potentially related to everything

