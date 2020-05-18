<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>mongo_cheatsheet</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__left">
    <div class="stackedit__toc">
      
<ul>
<li><a href="#mongodb-cheat-sheet">MongoDB Cheat Sheet</a>
<ul>
<li><a href="#center-show-all-databases"> Show All Databases</a></li>
<li><a href="#centershow-current-database">Show Current Database</a></li>
<li><a href="#center-create-or-switch-database"> Create Or Switch Database</a></li>
<li><a href="#centerdrop">Drop</a></li>
<li><a href="#center-create-collection"> Create Collection</a></li>
<li><a href="#centershow-collections">Show Collections</a></li>
<li><a href="#center-insert-row"> Insert Row</a></li>
<li><a href="#centerinsert-multiple-rows">Insert Multiple Rows</a></li>
<li><a href="#centerget-all-rows">Get All Rows</a></li>
<li><a href="#centerget-all-rows-formatted">Get All Rows Formatted</a></li>
<li><a href="#centerfind-rows">Find Rows</a></li>
<li><a href="#centersort-rows">Sort Rows</a></li>
<li><a href="#centercount-rows">Count Rows</a></li>
<li><a href="#centerlimit-rows">Limit Rows</a></li>
<li><a href="#centerchaining">Chaining</a></li>
<li><a href="#centerforeach">Foreach</a></li>
<li><a href="#centerfind-one-row">Find One Row</a></li>
<li><a href="#centerfind-specific-fields">Find Specific Fields</a></li>
<li><a href="#centerupdate-row">Update Row</a></li>
<li><a href="#centerupdate-specific-field">Update Specific Field</a></li>
<li><a href="#centerincrement-field-inc">Increment Field ($inc)</a></li>
<li><a href="#centerrename-field">Rename Field</a></li>
<li><a href="#centerdelete-row">Delete Row</a></li>
<li><a href="#centersub-documents">Sub-Documents</a></li>
<li><a href="#centerfind-by-element-in-array-elemmatch">Find By Element in Array ($elemMatch)</a></li>
<li><a href="#centeradd-index">Add Index</a></li>
<li><a href="#centertext-search">Text Search</a></li>
<li><a href="#centergreater--less-than">Greater & Less Than</a></li>
</ul>
</li>
</ul>

    </div>
  </div>
  <div class="stackedit__right">
    <div class="stackedit__html">
      <h1 id="mongodb-cheat-sheet">MongoDB <em>Cheat Sheet</em></h1>
<h2 id="center-show-all-databases"><center> Show All Databases</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">show</span> dbs
</code></pre>
<h2 id="centershow-current-database"><center>Show Current Database</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span>
</code></pre>
<h2 id="center-create-or-switch-database"><center> Create Or Switch Database</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">use</span> acme
</code></pre>
<h2 id="centerdrop"><center>Drop</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>dropDatabase<span class="token punctuation">(</span><span class="token punctuation">)</span>
</code></pre>
<h2 id="center-create-collection"><center> Create Collection</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>createCollection<span class="token punctuation">(</span><span class="token string">'posts'</span><span class="token punctuation">)</span>
</code></pre>
<h2 id="centershow-collections"><center>Show Collections</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">show</span> collections
</code></pre>
<h2 id="center-insert-row"><center> Insert Row</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span><span class="token keyword">insert</span><span class="token punctuation">(</span>{
  title: <span class="token string">'Post One'</span><span class="token punctuation">,</span>
  body: <span class="token string">'Body of post one'</span><span class="token punctuation">,</span>
  category: <span class="token string">'News'</span><span class="token punctuation">,</span>
  tags: <span class="token punctuation">[</span><span class="token string">'news'</span><span class="token punctuation">,</span> <span class="token string">'events'</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
  <span class="token keyword">user</span>: {
    name: <span class="token string">'John Doe'</span><span class="token punctuation">,</span>
    <span class="token keyword">status</span>: <span class="token string">'author'</span>
  }<span class="token punctuation">,</span>
  <span class="token keyword">date</span>: <span class="token keyword">Date</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
}<span class="token punctuation">)</span>
</code></pre>
<h2 id="centerinsert-multiple-rows"><center>Insert Multiple Rows</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>insertMany<span class="token punctuation">(</span><span class="token punctuation">[</span>
  {
    title: <span class="token string">'Post Two'</span><span class="token punctuation">,</span>
    body: <span class="token string">'Body of post two'</span><span class="token punctuation">,</span>
    category: <span class="token string">'Technology'</span><span class="token punctuation">,</span>
    <span class="token keyword">date</span>: <span class="token keyword">Date</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
  }<span class="token punctuation">,</span>
  {
    title: <span class="token string">'Post Three'</span><span class="token punctuation">,</span>
    body: <span class="token string">'Body of post three'</span><span class="token punctuation">,</span>
    category: <span class="token string">'News'</span><span class="token punctuation">,</span>
    <span class="token keyword">date</span>: <span class="token keyword">Date</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
  }<span class="token punctuation">,</span>
  {
    title: <span class="token string">'Post Four'</span><span class="token punctuation">,</span>
    body: <span class="token string">'Body of post three'</span><span class="token punctuation">,</span>
    category: <span class="token string">'Entertainment'</span><span class="token punctuation">,</span>
    <span class="token keyword">date</span>: <span class="token keyword">Date</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
  }
<span class="token punctuation">]</span><span class="token punctuation">)</span>
</code></pre>
<h2 id="centerget-all-rows"><center>Get All Rows</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>find<span class="token punctuation">(</span><span class="token punctuation">)</span>
</code></pre>
<h2 id="centerget-all-rows-formatted"><center>Get All Rows Formatted</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>find<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span>pretty<span class="token punctuation">(</span><span class="token punctuation">)</span>
</code></pre>
<h2 id="centerfind-rows"><center>Find Rows</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>find<span class="token punctuation">(</span>{ category: <span class="token string">'News'</span> }<span class="token punctuation">)</span>
</code></pre>
<h2 id="centersort-rows"><center>Sort Rows</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token comment"># asc</span>
<span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>find<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span>sort<span class="token punctuation">(</span>{ title: <span class="token number">1</span> }<span class="token punctuation">)</span><span class="token punctuation">.</span>pretty<span class="token punctuation">(</span><span class="token punctuation">)</span>
<span class="token comment"># desc</span>
<span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>find<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span>sort<span class="token punctuation">(</span>{ title: <span class="token operator">-</span><span class="token number">1</span> }<span class="token punctuation">)</span><span class="token punctuation">.</span>pretty<span class="token punctuation">(</span><span class="token punctuation">)</span>
</code></pre>
<h2 id="centercount-rows"><center>Count Rows</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>find<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">count</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
<span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>find<span class="token punctuation">(</span>{ category: <span class="token string">'news'</span> }<span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">count</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
</code></pre>
<h2 id="centerlimit-rows"><center>Limit Rows</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>find<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token keyword">limit</span><span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">)</span><span class="token punctuation">.</span>pretty<span class="token punctuation">(</span><span class="token punctuation">)</span>
</code></pre>
<h2 id="centerchaining"><center>Chaining</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>find<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token keyword">limit</span><span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">)</span><span class="token punctuation">.</span>sort<span class="token punctuation">(</span>{ title: <span class="token number">1</span> }<span class="token punctuation">)</span><span class="token punctuation">.</span>pretty<span class="token punctuation">(</span><span class="token punctuation">)</span>
</code></pre>
<h2 id="centerforeach"><center>Foreach</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>find<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span>forEach<span class="token punctuation">(</span><span class="token keyword">function</span><span class="token punctuation">(</span>doc<span class="token punctuation">)</span> {
  <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Blog Post: "</span> <span class="token operator">+</span> doc<span class="token punctuation">.</span>title<span class="token punctuation">)</span>
}<span class="token punctuation">)</span>
</code></pre>
<h2 id="centerfind-one-row"><center>Find One Row</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>findOne<span class="token punctuation">(</span>{ category: <span class="token string">'News'</span> }<span class="token punctuation">)</span>
</code></pre>
<h2 id="centerfind-specific-fields"><center>Find Specific Fields</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>find<span class="token punctuation">(</span>{ title: <span class="token string">'Post One'</span> }<span class="token punctuation">,</span> {
  title: <span class="token number">1</span><span class="token punctuation">,</span>
  author: <span class="token number">1</span>
}<span class="token punctuation">)</span>
</code></pre>
<h2 id="centerupdate-row"><center>Update Row</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span><span class="token keyword">update</span><span class="token punctuation">(</span>{ title: <span class="token string">'Post Two'</span> }<span class="token punctuation">,</span>
{
  title: <span class="token string">'Post Two'</span><span class="token punctuation">,</span>
  body: <span class="token string">'New body for post 2'</span><span class="token punctuation">,</span>
  <span class="token keyword">date</span>: <span class="token keyword">Date</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
}<span class="token punctuation">,</span>
{
  upsert: <span class="token boolean">true</span>
}<span class="token punctuation">)</span>
</code></pre>
<h2 id="centerupdate-specific-field"><center>Update Specific Field</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span><span class="token keyword">update</span><span class="token punctuation">(</span>{ title: <span class="token string">'Post Two'</span> }<span class="token punctuation">,</span>
{
  $<span class="token keyword">set</span>: {
    body: <span class="token string">'Body for post 2'</span><span class="token punctuation">,</span>
    category: <span class="token string">'Technology'</span>
  }
}<span class="token punctuation">)</span>
</code></pre>
<h2 id="centerincrement-field-inc"><center>Increment Field ($inc)</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span><span class="token keyword">update</span><span class="token punctuation">(</span>{ title: <span class="token string">'Post Two'</span> }<span class="token punctuation">,</span>
{
  $inc: {
    likes: <span class="token number">5</span>
  }
}<span class="token punctuation">)</span>
</code></pre>
<h2 id="centerrename-field"><center>Rename Field</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span><span class="token keyword">update</span><span class="token punctuation">(</span>{ title: <span class="token string">'Post Two'</span> }<span class="token punctuation">,</span>
{
  $<span class="token keyword">rename</span>: {
    likes: <span class="token string">'views'</span>
  }
}<span class="token punctuation">)</span>
</code></pre>
<h2 id="centerdelete-row"><center>Delete Row</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>remove<span class="token punctuation">(</span>{ title: <span class="token string">'Post Four'</span> }<span class="token punctuation">)</span>
</code></pre>
<h2 id="centersub-documents"><center>Sub-Documents</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span><span class="token keyword">update</span><span class="token punctuation">(</span>{ title: <span class="token string">'Post One'</span> }<span class="token punctuation">,</span>
{
  $<span class="token keyword">set</span>: {
    comments: <span class="token punctuation">[</span>
      {
        body: <span class="token string">'Comment One'</span><span class="token punctuation">,</span>
        <span class="token keyword">user</span>: <span class="token string">'Mary Williams'</span><span class="token punctuation">,</span>
        <span class="token keyword">date</span>: <span class="token keyword">Date</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
      }<span class="token punctuation">,</span>
      {
        body: <span class="token string">'Comment Two'</span><span class="token punctuation">,</span>
        <span class="token keyword">user</span>: <span class="token string">'Harry White'</span><span class="token punctuation">,</span>
        <span class="token keyword">date</span>: <span class="token keyword">Date</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
      }
    <span class="token punctuation">]</span>
  }
}<span class="token punctuation">)</span>
</code></pre>
<h2 id="centerfind-by-element-in-array-elemmatch"><center>Find By Element in Array ($elemMatch)</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>find<span class="token punctuation">(</span>{
  comments: {
     $elemMatch: {
       <span class="token keyword">user</span>: <span class="token string">'Mary Williams'</span>
       }
    }
  }
<span class="token punctuation">)</span>
</code></pre>
<h2 id="centeradd-index"><center>Add Index</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>createIndex<span class="token punctuation">(</span>{ title: <span class="token string">'text'</span> }<span class="token punctuation">)</span>
</code></pre>
<h2 id="centertext-search"><center>Text Search</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>find<span class="token punctuation">(</span>{
  $<span class="token keyword">text</span>: {
    $search: <span class="token string">"\"Post O\""</span>
    }
}<span class="token punctuation">)</span>
</code></pre>
<h2 id="centergreater--less-than"><center>Greater &amp; Less Than</center></h2>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>find<span class="token punctuation">(</span>{ views: { $gt: <span class="token number">2</span> } }<span class="token punctuation">)</span>
<span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>find<span class="token punctuation">(</span>{ views: { $gte: <span class="token number">7</span> } }<span class="token punctuation">)</span>
<span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>find<span class="token punctuation">(</span>{ views: { $lt: <span class="token number">7</span> } }<span class="token punctuation">)</span>
<span class="token number">db</span><span class="token punctuation">.</span>posts<span class="token punctuation">.</span>find<span class="token punctuation">(</span>{ views: { $lte: <span class="token number">7</span> } }<span class="token punctuation">)</span>
</code></pre>

    </div>
  </div>
</body>

</html>
