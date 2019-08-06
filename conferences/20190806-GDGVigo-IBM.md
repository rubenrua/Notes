An afternoon with IBM Research developers
=======

06-08-2019
https://www.meetup.com/en-AU/GDGVigo/events/263457111/

Testing approaches for backend projects
-----------
by Jorge J. Barroso (@flipper83)

### (JS) Test aceptacion http y mock la bbdd (MongoDB)

App con https://strapi.io

Test con [co-supertest](https://github.com/avbel/co-supertest) y [chai](https://www.chaijs.com/)

IDE: visual studio code


### (Kotlin) Test aceptación http y mock de los repositorios de Sprint

App con Spring Boot

Test con Junit y [mockk](https://mockk.io/)

IDE: IntelliJ IDEA

Al poner los mocks más arriba, funciona más rapido.


### (Python) Test aceptación socket request y mockeo de agentes externo lentos.

App con python

Test con Unitest y [mocker](https://labix.org/mocker)

No es http pero es lo mismo. Hay peticiones y respuestas.

IDE: Pycharm


WebAssembly with Rust
-----------
by Juan Gómez (@Longor)

###  Webassenbly:

binario (nota: sólo 4 tipos i32, i64, f32, f64), seguro y rápido???

Es rápido en ejecutar si lo comparas con JS (no parse, no GC, no re-optimize, menos compile+optimize ver [@linclark](https://www.smashingmagazine.com/2017/05/abridged-cartoon-introduction-webassembly/#) ). Si lo compras con ASM....ufff

Why Webassenbly? The web is the platform.

Usamos Js por encima de nuestras posibilidades.

Futuro web assembly: threads, GC y tooling

### Rust: Velocidad, seguro y productivo.

* It is loved by devs: https://insights.stackoverflow.com/survey/2019#most-loved-dreaded-and-wanted
* It is green: https://greenlab.di.uminho.pt/wp-content/uploads/2017/09/paperSLE.pdf
* John Carmack likes it: https://twitter.com/id_aa_carmack/status/1094419108781789184?lang=en

DEMO1:

```
cargo generate --git https://github.com/rustwasm/wasm-pack-template.git --name my-project
cd my-project
wasm-pack build
wasm-pack test --headless --firefox
```


DEMO2:

Simulador cuántico en Webassenbly con rust. (FF: 8s vs 6s en JS)


What I've learned this year teaching Python
-------------
by Salva de la Puente (Ya no tiene/usa twitter!!! felicidades)

https://github.com/Fictizia/Master-en-Programacion-con-Python_ed1



Novedades de python:

* Los `dict` garantizan el orden de inserción de sus elementos.
* Cadenas de plantillas.
* Anotaciones de variables.
* Dataclasses.
* Turtle graphics.

Para dar un curso se invierte un montón de tiempo. 10/12 horas por cada 8 horas. Rendimiento del 22%.

https://en.wikipedia.org/wiki/Amdahl%27s_law
