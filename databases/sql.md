# SQL

## Comands

| MySQL                            | POSTGRESQL        |  SQLite
|----------------------------------|-------------------|----------------------
| use database                     | \c database       |
| show databases                   | \l                | .databases
| show tables                      | \dt               | .tables
| describe tablename               | \d+ tablename     | .schema tablename
| QUERY\G                          | \x QUERY          | .mode MODE
| LOAD DATA INFILE '<file>'        | \i <file>         |
| SELECT ... INTO OUTFILE '<file>' | \o <file>         | .dump <table>


http://www.linuxjournal.com/content/mariadbmysql-postgresql-and-sqlite3-comparing-command-line-interfaces