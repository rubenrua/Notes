# ELASTICSEARCH

Default port: 9300 (9200 for HTTP interface)

## Links

* https://www.elastic.co/guide/en/elasticsearch/reference/current/getting-started.html
* https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-query-string-query.html#query-string-syntax
* https://www.elastic.co/guide/en/kibana/master/setup.html

## API

* GET /_cat
* GET /_cat/index
* GET /<index>/<type>/<id>?pretty
* GET /<index>/_search?q=*
* GET /<index>/_search?q=k:(v1 OR v2)&from=0&size=20&sort=k:asc