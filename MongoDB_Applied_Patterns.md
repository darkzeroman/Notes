### MongoDB Applied Patterns

Many to Many Joins:

```
// db.product schema    { "_id": "My Product",      "category_ids": [ "My Category", ... ] }    // db.category schema{ "_id": "My Category" }
```