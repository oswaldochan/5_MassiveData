<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>resumen_3&amp;4</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__left">
    <div class="stackedit__toc">
      
<ul>
<li><a href="#questions">Questions</a>
<ul>
<li><a href="#chapter-3">Chapter 3</a></li>
<li><a href="#chapter-4">Chapter 4</a>
<ul>
<li></li>
<li><a href="#what-are-the-storage-requirements-for-the-batch-layer">What are the storage requirements for the batch layer?</a></li>
<li><a href="#why-using-keyvalue-for-the-batch-layer-isnt-the-best-decision">Why using key/value for the batch layer isn’t the best decision?</a></li>
<li><a href="#what-solution-is-better-instead-of-keyvalue-for-the-batch-layer">What solution is better instead of key/value for the batch layer?</a></li>
<li><a href="#how-does-a-distributed-filesystem-work">How does a distributed filesystem work?</a></li>
<li><a href="#does-a-distributed-filesystem-meet-the-storage-requirements-justify">Does a distributed filesystem meet the storage requirements? Justify</a></li>
<li><a href="#what-is-vertical-partitioning">What is vertical partitioning?</a></li>
</ul>
</li>
</ul>
</li>
</ul>

    </div>
  </div>
  <div class="stackedit__right">
    <div class="stackedit__html">
      <h1 id="questions">Questions</h1>
<h2 id="chapter-3">Chapter 3</h2>
<h3 id="what-could-be-a-result-of-using-a-schemaless-format-like-json">What could be a result of using a schemaless format <em>(like JSON)</em>?</h3>
<p>It could inevitably led to data corruption</p>
<h3 id="why-are-data-corruption-problems-hard-to-debug">Why are data corruption problems hard to debug?</h3>
<p>Because when you notice them, it’s very difficult to trace back what occasioned it, or to detect what generated that corrupted data.<br>
You don’t get a comprehensive alert of how the problem was originated.</p>
<p><strong><em>This doesn’t occur in an enforceable schema, because it will prevent any of those error to happen at the moment of writing the data</em></strong></p>
<h3 id="what-is-apache-thrift">What is Apache Thrift?</h3>
<blockquote>
<p>is a tool that can be used to define statically typed, enforceable schemas. It provides an interface definition language to describe the schema in terms of generic data types, and this description can later be used to automatically generate the actual implementation in multiple programming languages.</p>
</blockquote>
<h3 id="what-are-the-main-components-of-apache-thrift">What are the main components of Apache Thrift?</h3>
<blockquote>
<p><strong>Unions</strong> are useful for representing <em>nodes</em>, <strong>structs</strong> are natural representations of <em>edges</em>, and <em>properties</em> use a combination of both</p>
</blockquote>
<ul>
<li><strong>Nodes</strong>: a single value that may have any of several representations.</li>
<li><strong>Edges</strong>: each edge can be represented as a struct containing two nodes:</li>
<li><strong>Properties</strong>:  contains a node and a value for the property</li>
</ul>
<h3 id="why-is-so-important-that-in-thrift-schemas-can-evolve-over-time">Why is so important that in Thrift schemas can evolve over time?</h3>
<blockquote>
<p>It is a crucial property, because as your business requirements change you’ll need to add new kinds of data, and you’ll want to do so as effortlessly as possible.</p>
</blockquote>
<h3 id="what-is-the-limitation-of-serialization-frameworks">What is the limitation of serialization frameworks?</h3>
<blockquote>
<p>They only check that all required fields are present and are of the expected type. They’re unable to check richer properties like “Ages should be non-negative” or “true-as-of timestamps should not be in the future.” Data not matching these properties would indicate a problem in your system, and you wouldn’t want them written to your master dataset.</p>
</blockquote>
<h2 id="chapter-4">Chapter 4</h2>
<h4 id="but-first-lets-recapitulate-what-we-learnt-about-the-lambda-architecture">But first, let’s recapitulate what we learnt about the Lambda Architecture</h4>
<p><img src="https://github.com/oswaldochan/5_MassiveData/blob/master/cap3&amp;4/images/Anotaci%C3%B3n%202020-05-24%20185546.png?raw=true" alt="enter image description here"></p>
<h3 id="what-are-the-storage-requirements-for-the-batch-layer">What are the <em>storage</em> requirements for the batch layer?</h3>
<p><img src="https://github.com/oswaldochan/5_MassiveData/blob/master/cap3&amp;4/images/Anotaci%C3%B3n%202020-05-24%201855466.png?raw=true" alt=""></p>
<h3 id="why-using-keyvalue-for-the-batch-layer-isnt-the-best-decision">Why using <em>key/value</em> for the batch layer isn’t the best decision?</h3>
<blockquote>
<p>Because it has a lot of things you don’t need: random reads, random writes, and all the machinery behind making those work. In fact, most of the implementation of a key/value store is dedicated to these features you don’t need at all. This means the tool is enormously more complex than it needs to be to meet your requirements, making it much more likely you’ll have a problem with it</p>
</blockquote>
<h3 id="what-solution-is-better-instead-of-keyvalue-for-the-batch-layer">What solution is better instead of <em>key/value</em> for the batch layer?</h3>
<p><strong>Distributed filesystems</strong>, which spread their storage across a cluster of computers. They scale by adding more machines to the cluster. Distributed filesystems are designed so that you have fault tolerance when a machine goes down, meaning that if you lose one machine, all your files and data will still be accessible.</p>
<h3 id="how-does-a-distributed-filesystem-work">How does a distributed filesystem work?</h3>
<blockquote>
<p>■ Files are spread across multiple machines for scalability and also to enable parallel processing.<br>
■ File blocks are replicated across multiple nodes for fault tolerance<br>
<img src="https://github.com/oswaldochan/5_MassiveData/blob/master/cap3&amp;4/images/Anotaci%C3%B3n%202020-05-24%2018554666.png?raw=true" alt=""></p>
</blockquote>
<h3 id="does-a-distributed-filesystem-meet-the-storage-requirements-justify">Does a <em>distributed filesystem</em> meet the storage requirements? Justify</h3>
<p>Yes, it does</p>
<blockquote>
<p><img src="https://github.com/oswaldochan/5_MassiveData/blob/master/cap3&amp;4/images/Anotaci%C3%B3n%202020-05-24%20185826.png?raw=true" alt=""></p>
</blockquote>
<h3 id="what-is-vertical-partitioning">What is vertical partitioning?</h3>
<blockquote>
<p>Although the batch layer is built to run functions on the entire dataset, many computations don’t require looking at all the data. For example, you may have a computation that only requires information collected during the past two weeks. The batch storage should allow you to partition your data so that a function only accesses data relevant to its computation. This process is called <strong>vertical partitioning</strong></p>
</blockquote>

    </div>
  </div>
</body>

</html>
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NTQ2OTU4MTVdfQ==
-->