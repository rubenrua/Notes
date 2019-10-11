# 3.- About C++
2019-10-12

This week, during a GStreamer training surrounded by C and C++ developers, the sparks almost start to fly with this sentence.

> "Rust: what C++ would be if invented nowadays"

I already have read a lot of times, and like I am not a C++ developer, I never cared about it. But as a PHP developer I can put me in the other's shoes.

C++ is powerful language with ∞ apps/libs like [ClickHouse](https://github.com/ClickHouse/ClickHouse), [Chromium](https://chromium.googlesource.com/chromium/src.git/+/refs/heads/master), QT, [TensorFlow](https://github.com/tensorflow/tensorflow), [OpenCV](https://github.com/opencv/opencv), almost all game engines... A C++ developer should be very proud to have this hammer.

But the fist argumentation against Rust was that it is not OOP. While the people were arguing about that, I could not forget a presentation of [J. Daniel Garcia](https://www.arcos.inf.uc3m.es/jdgarcia/), an active member of the ISO C++ standards committee, whose title was "[Inheritance = Base class of all problems, OOP must die](https://usingstdcpp.org/2014/12/05/la-herencia-es-la-clase-base-de-todos-los-problemas/)". [Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a rusty classic topic but it always is good to check the [criticisms](https://en.wikipedia.org/wiki/Object-oriented_programming#Criticism) about your tools/paradigma/styles...

I also discovered from J. Daniel Garcia the higher drawback that I know of Rust, his great dependence on LLVM and its lack of standardization. I would like to know what is his current opinion about Rust.

On the other hand, Rust makes me a passionate programmer and I couldn't stop thinking about points that IMHO make rust a better hammer than C++.

* The Rust community is awesome, and that's the reason why Rust is voted most loved language for the 3rd Year in a Row in Stack Overflow Developer Survey (like [Fabien Potencier](http://github.com/fabpot)  says [Community > Docs > Code](https://twitter.com/fabpot/status/994475614588559360)).
* Cargo: After work with pip, maven, npm, composer... I can't work with a modern package manager.
* I like the functional programming style. And Rust’s design has taken inspiration from many existing languages and techniques, and one significant influence is functional programming. For instance, check their type system.
* IMHO, the C++ legacy code is the worst part of C++, the same as the legacy PHP is the worst part of PHP. This thing usually happens with overweight languages with a lot of features. that's why it's very important to isolate complexity as much as possible.
* At the university, I always hated the C ++ templates, the Rust generics (more similar to Scala) seem for me a better solution. Rust lifetimes is a very complex concept, but very powerful; I think that C ++ doesn't have any similar. 
* Immutability by default, the strict compiler...


The next C++ release, C++20, will be in one year and it will be a very good language, I am happy to can use it in future projects. But as a  passionate Rust developer, I like to think that Rust is being for C++ what Scala was for Java.

Please Don't forget:

> A new scientific truth does not triumph by convincing its opponents and making them see the light, but rather because its opponents eventually die. — Thomas Kuhn.

> There are only two kinds of languages, the ones people complain about, and the ones nobody uses — Bjarne Stroustrup


Notes:

 - next: Improve my C++ and read more it.
