MONGO
=====

Tips
----
* Update replace in mongodb<sup>[1](#1)</sup>
```sql
UPDATE foo SET mystr = REPLACE(mystr, ' ', '_');
```
```mongo
db.foo.find({ mystr: /[ ]+/ }).forEach( function(u) { u.mystr = u.mystr.replace(/[ ]/g, "_"); db.foo.save(u); } );
```

* Query using JavaScript expressions [2]

```mongo
db.usercollection.find({$where: "isNumber(this.value) && this.name.length > 40"}).limit(2);

```


Links
-----


 * https://docs.mongodb.org/compass/
 * https://docs.mongodb.com/ecosystem/tools/administration-interfaces/

<a name="1">[1]</a>: http://www.gizmola.com/blog/archives/106-SQL-UPDATE-for-strings-in-MongoDB.html
<a name="2">[2]</a>: https://docs.mongodb.com/manual/reference/operator/query/where/