MYSQL
=====

Links
-----
* http://www.linuxhispano.net/2013/04/30/comprobar-el-estado-de-la-cache-de-mysql/
* http://www.linuxhispano.net/2013/03/15/modificar-o-activar-el-tamano-de-cache-de-mysql/
* http://dev.mysql.com/doc/refman/5.0/en/slow-query-log.html
* http://dev.mysql.com/doc/refman/5.0/en/query-cache-in-select.html  SELECT /*!40001 SQL_NO_CACHE */ * FROM `file`;
* http://www.codeproject.com/Articles/33052/Visual-Representation-of-SQL-Joins
* http://israelolalla.blogspot.com.es/2012/11/mysql-en-cluster-activoactivo.html?m=1

Tips
----

* Easy visualisation of database schemas

Install sqlfairy, easy on Ubuntu:

```
$ apt-get install sqlfairy
```

then:

```
$ mysqldump -u root -p -d  matterhorn > mhdb.sql
$ sqlt-graph -f MySQL -o database.png -t png mhdb.sql
```

https://nsaunders.wordpress.com/2009/01/11/easy-visualisation-of-database-schemas-using-sqlfairy/


* Create a database

```sh
$ mysql -u adminusername -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 5340 to server version: 3.23.54

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> CREATE DATABASE databasename;
Query OK, 1 row affected (0.00 sec)

mysql> GRANT ALL PRIVILEGES ON databasename.* TO "wordpressusername"@"hostname"
    -> IDENTIFIED BY "password";
    Query OK, 0 rows affected (0.00 sec)

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.01 sec)

mysql> EXIT
Bye
```
