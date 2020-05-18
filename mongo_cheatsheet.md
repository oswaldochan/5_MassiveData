# MongoDB *Cheat Sheet*

## <center/> Show All Databases

```sql
show dbs
```

## <center/>Show Current Database

```sql
db
```

## <center/> Create Or Switch Database

```sql
use acme
```

## <center/>Drop

```sql
db.dropDatabase()
```

## <center/> Create Collection

```sql
db.createCollection('posts')
```

## <center/>Show Collections

```sql
show collections
```

## <center/> Insert Row

```sql
db.posts.insert({
  title: 'Post One',
  body: 'Body of post one',
  category: 'News',
  tags: ['news', 'events'],
  user: {
    name: 'John Doe',
    status: 'author'
  },
  date: Date()
})
```

## <center/>Insert Multiple Rows

```sql
db.posts.insertMany([
  {
    title: 'Post Two',
    body: 'Body of post two',
    category: 'Technology',
    date: Date()
  },
  {
    title: 'Post Three',
    body: 'Body of post three',
    category: 'News',
    date: Date()
  },
  {
    title: 'Post Four',
    body: 'Body of post three',
    category: 'Entertainment',
    date: Date()
  }
])
```

## <center/>Get All Rows

```sql
db.posts.find()
```

## <center/>Get All Rows Formatted

```sql
db.find().pretty()
```

## <center/>Find Rows

```sql
db.posts.find({ category: 'News' })
```

## <center/>Sort Rows

```sql
# asc
db.posts.find().sort({ title: 1 }).pretty()
# desc
db.posts.find().sort({ title: -1 }).pretty()
```

## <center/>Count Rows

```sql
db.posts.find().count()
db.posts.find({ category: 'news' }).count()
```

## <center/>Limit Rows

```sql
db.posts.find().limit(2).pretty()
```

## <center/>Chaining

```sql
db.posts.find().limit(2).sort({ title: 1 }).pretty()
```

## <center/>Foreach

```sql
db.posts.find().forEach(function(doc) {
  print("Blog Post: " + doc.title)
})
```

## <center/>Find One Row

```sql
db.posts.findOne({ category: 'News' })
```

## <center/>Find Specific Fields

```sql
db.posts.find({ title: 'Post One' }, {
  title: 1,
  author: 1
})
```

## <center/>Update Row

```sql
db.posts.update({ title: 'Post Two' },
{
  title: 'Post Two',
  body: 'New body for post 2',
  date: Date()
},
{
  upsert: true
})
```

## <center/>Update Specific Field

```sql
db.posts.update({ title: 'Post Two' },
{
  $set: {
    body: 'Body for post 2',
    category: 'Technology'
  }
})
```

## <center/>Increment Field (\$inc)

```sql
db.posts.update({ title: 'Post Two' },
{
  $inc: {
    likes: 5
  }
})
```

## <center/>Rename Field

```sql
db.posts.update({ title: 'Post Two' },
{
  $rename: {
    likes: 'views'
  }
})
```

## <center/>Delete Row

```sql
db.posts.remove({ title: 'Post Four' })
```

## <center/>Sub-Documents

```sql
db.posts.update({ title: 'Post One' },
{
  $set: {
    comments: [
      {
        body: 'Comment One',
        user: 'Mary Williams',
        date: Date()
      },
      {
        body: 'Comment Two',
        user: 'Harry White',
        date: Date()
      }
    ]
  }
})
```

## <center/>Find By Element in Array (\$elemMatch)

```sql
db.posts.find({
  comments: {
     $elemMatch: {
       user: 'Mary Williams'
       }
    }
  }
)
```

## <center/>Add Index

```sql
db.posts.createIndex({ title: 'text' })
```

## <center/>Text Search

```sql
db.posts.find({
  $text: {
    $search: "\"Post O\""
    }
})
```

## <center/>Greater & Less Than

```sql
db.posts.find({ views: { $gt: 2 } })
db.posts.find({ views: { $gte: 7 } })
db.posts.find({ views: { $lt: 7 } })
db.posts.find({ views: { $lte: 7 } })
```
