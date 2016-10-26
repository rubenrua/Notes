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


Links
-----


 * https://docs.mongodb.org/compass/
 * https://docs.mongodb.com/ecosystem/tools/administration-interfaces/
