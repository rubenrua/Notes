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
<a name="1">[1]</a>: http://www.gizmola.com/blog/archives/106-SQL-UPDATE-for-strings-in-MongoDB.html
