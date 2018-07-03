MONGO
=====

Tips
----
* Update replace in mongodb
```sql
UPDATE foo SET mystr = REPLACE(mystr, ' ', '_');
```
```mongo
db.foo.find({ mystr: /[ ]+/ }).forEach( function(u) { u.mystr = u.mystr.replace(/[ ]/g, "_"); db.foo.save(u); } );
```
http://www.gizmola.com/blog/archives/106-SQL-UPDATE-for-strings-in-MongoDB.html


* Query using JavaScript expressions

```mongo
db.usercollection.find({$where: "isNumber(this.value) && this.name.length > 40"});
```
https://docs.mongodb.com/manual/reference/operator/query/where/


* One subdocument criteria

```mongo
db.scores.find(
   { results: { $elemMatch: { $gte: 80, $lt: 85 } } }
)
```
https://docs.mongodb.com/manual/reference/operator/query/elemMatch/

* Query array with null values

```mongo
db.MultimediaObject.find({"tags":{$elemMatch:{"$in":[null], "$exists":true}}})
```
http://stackoverflow.com/questions/15335197/mongodb-query-array-with-null-values

* Index info query

```mongo
db.collection.totalIndexSize()
db.collection.stats().indexSizes
db.getCollectionNames().map(name => ({totalIndexSize: db.getCollection(name).stats().totalIndexSize, name: name})).sort((a, b) => a.totalIndexSize - b.totalIndexSize).forEach(printjson)
db.serverStatus().tcmalloc.tcmalloc.formattedString
```

https://docs.mongodb.com/manual/tutorial/ensure-indexes-fit-ram/ and https://docs.mongodb.com/v3.2/faq/diagnostics/

SAD
---

* Any like SQLite for MongoDB (for testing)
* PHP current status (No `doctrine/mongodb-odm`, No `api-platform`)
* Spanish Text Index stemming: https://jira.mongodb.org/browse/SERVER-15027 https://groups.google.com/d/msg/mongodb-user/yEnD21E_9q0/WoIR7-jtAAAJ
* Aggregation $group performance: https://jira.mongodb.org/browse/SERVER-4961


Links
-----


 * https://docs.mongodb.org/compass/
 * https://docs.mongodb.com/ecosystem/tools/administration-interfaces/
 * https://www.datadoghq.com/blog/collecting-mongodb-metrics-and-statistics/
