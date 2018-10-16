# MYSQL

## Links

* http://www.linuxhispano.net/2013/04/30/comprobar-el-estado-de-la-cache-de-mysql/
* http://www.linuxhispano.net/2013/03/15/modificar-o-activar-el-tamano-de-cache-de-mysql/
* http://dev.mysql.com/doc/refman/5.0/en/slow-query-log.html
* http://www.codeproject.com/Articles/33052/Visual-Representation-of-SQL-Joins
* http://israelolalla.blogspot.com.es/2012/11/mysql-en-cluster-activoactivo.html?m=1
* http://web.archive.org/web/20110606032941/http://dev.mysql.com/tech-resources/articles/hierarchical-data.html
* http://www.sitepoint.com/hierarchical-data-database-2/

## Tips

### Change root passwd

* Step # 1: Stop the MySQL server process.
```
# /etc/init.d/mysql stop
```

* Step # 2: Start the MySQL (mysqld) server/daemon process with the --skip-grant-tables option so that it will not prompt for password
```
# mysqld_safe --skip-grant-tables &
```

* Step # 3: Connect to mysql server as the root user
```
# mysql -u root
```

* Step # 4: Setup new root password
```
mysql> use mysql;
mysql> update user set password=PASSWORD("NEW-ROOT-PASSWORD") where User='root';
mysql> flush privileges;
mysql> quit
```

* Step # 5: Exit and restart MySQL server
```
# /etc/init.d/mysql stop
# /etc/init.d/mysql start
# mysql -u root -p
```

### Easy visualisation of database schemas

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


### Create a database

```sql
CREATE DATABASE databasename CHARACTER SET utf8 COLLATE utf8_swedish_ci;
GRANT ALL PRIVILEGES ON databasename.* TO "wordpressusername"@"hostname" IDENTIFIED BY "password";
FLUSH PRIVILEGES;
EXIT
```


### Query Cache SELECT Options

```sql
SELECT SQL_CACHE id, name FROM customer;
SELECT SQL_NO_CACHE id, name FROM customer;
```
or (adding bc)
```sql
SELECT /*!40001 SQL_NO_CACHE */ * FROM `file`;
```

http://dev.mysql.com/doc/refman/5.0/en/query-cache-in-select.html 

### Show variables
```sql
SHOW VARIABLES;
SHOW VARIABLES LIKE '%';
```

### Aggregate (GROUP BY)
```sql
SELECT id, serial_id, status_id FROM mm INNER JOIN (SELECT mm_id FROM file WHERE perfil_id IN (35,56) GROUP BY mm_id HAVING GROUP_CONCAT(distinct perfil_id ORDER BY perfil_id asc)  = "35,56") AS a ON mm.id = a.mm_id;

```

https://dev.mysql.com/doc/refman/5.7/en/group-by-functions.html


### OTHER

* Use charset `utf8mb4` collate `utf8mb4_unicode_ci`.
