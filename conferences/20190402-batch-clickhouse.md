Batch
=====
by @javisantana

El nombre de este chiringito, es por que todo el muncho tiene algun batch...


UrbanData Analytics - dataops
-----------------------------
Datapoops by @jmnavarro

* Books: "getting data operations right" and "creating a data driven enterprise with dataops"
* Automation, repeatable, rapid/speed, quality/reliable, self service tool.
* [Superset](https://superset.incubator.apache.org/) para representar datos.
* Schema (no usan nosql) para documentar schemas.


GeoBlink - Scalable architectures based on human behaviour
----------------------------------------------------------
La tecnología es predicible, las personas no. by Miguel Ángel Fajardo and Jorge López-Malla

* Empezaron con postgresql and postgis.
* Ahora: Spark (Amazon EMR), neo4j (cluster con balanceador nginx). Autoescalado de neo4j sobre EFS


Graphext - Uso de Arrow en el mundo real
----------------------------------------
by @crispamares

* Apache Arrow: columnar memory format. ([Del creador de pandas](http://wesmckinney.com/blog/apache-arrow-pandas-internals/) y usa flatbuf ??)
* Multilenguaje: C++, C, js, java, Python, R, Rust...
* En la presentacion Compara: JSON, CSV, Arrow, Parket (tambien de apache, optimizado para disco con snappy), pickle (solo python)
* pros: Zero copy interpretation, GPU support (omnisci), RAPIDS.AI, y mas. Contras: no versión 1 (v0.12.0)
* Pregunta: sqlite? Dice que se fue de mano.


ClickHouse meetup
==================

ClickHouse introduction
-----------------------
By Alexander Zaitsev, Altinity (@alex-zaitsev)

* Benchmark: https://github.com/timescale/tsbs and https://tech.marksblogg.com/benchmarks.html
* SQL like funcional programming (https://clickhouse.yandex/docs/en/query_language/functions/higher_order_functions/)
* Monitoring tool: https://prometheus.io

Check https://www.slideshare.net/Altinity/presentations for the presentation

ClickHouse 2019 new features
----------------------------
By Alexey Milovidov, Yandex (@alexey-milovidov)

* Full text search index (highly experimental)
* HDFS import/export
* And more

From legacy to ClickHouse
-------------------------
by Iago Enriquez, Idealista

```
SELECT
 ADID, PRICE, AREA, ROOMS. HASLIFT, HASGARDEN
FROM merge (ads_schema,
`assets_(chalet|home)_m(201806|201809|201812|201903)`
)
```

* https://github.com/catboost/catboost to  estimate missing values



1027 predictive models in 10 seconds
------------------------------------
by David Pardo Villaverde, Corunet (@dei_biz)

* 250M records/ 60GB
* Clickhouse effect for check anomalies and forecast



Shipping Data from Postgres to Clickhouse
-----------------------------------------
by Murat Kabilov, Adjust
