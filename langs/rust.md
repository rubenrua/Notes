RUST
====

> "Rust. Fast, safe and productive - pick three."
> "I think writing Rust is actually pair programming. You are the driver and compiler is the navigator."


LINKS
-----

* https://www.rust-lang.org
* http://rustbyexample.com
* https://cheats.rs/
* https://caniuse.rs/

BLOGS
-----

* https://blog.rust-lang.org
* https://blog.rust-lang.org/inside-rust/index.html

FFI
-----
* https://doc.rust-lang.org/beta/nomicon/index.html
* https://github.com/rust-lang-nursery/rust-bindgen [(doc)](https://rust-lang.github.io/rust-bindgen/)  (C/C++ -> Rust FFI bindings)
* https://github.com/eqrion/cbindgen [(~doc)](https://michael-f-bryan.github.io/rust-ffi-guide/) (rust -> C bindings)
* [example 1](https://github.com/Michael-F-Bryan/plugins_in_rust), [example 2 with C interface](https://github.com/kmdouglass/rust-libloading-example) (rust -> rust)

Waiting
------

* ABI stability [(note)](https://viruta.org/rust-stable-abi.html) [(note2)](https://gankra.github.io/blah/swift-abi/)[(interoperable_abi)](https://github.com/rust-lang/rust/pull/105586)
* Less dependence on the LLVM project [(note)](https://jason-williams.co.uk/a-possible-new-backend-for-rust) [(gcc)](https://rust-gcc.github.io/) [(gcc2)](https://lwn.net/Articles/871283/)
* Default values for struct fields: https://github.com/rust-lang/rfcs/issues/1594
* Functions with keyword args, optional args, and/or variable-arity argument (varargs) lists: https://github.com/rust-lang/rfcs/issues/323
* Generic SQL bindings: https://github.com/rust-lang/rfcs/issues/798 [(check)](https://github.com/launchbadge/sqlx)
* Warning redefining an OS call: https://fnordig.de/2020/05/02/rust-in-an-instant/
* Implement likely/unlikely intrinsic: https://github.com/rust-lang/rust/issues/26179
* Better C++ interoperability: https://github.com/rustfoundation/interop-initiative/tree/main
* Sandboxed build.rs
* Support defining C-compatible variadic functions https://github.com/rust-lang/rust/issues/44930
* Issues with Linux distros like: https://lwn.net/Articles/912202/
* https://github.com/Speykious/cve-rs
* Matching C performance, Improve state machine codegen: https://rust-lang.github.io/rust-project-goals/2025h1/improve-rustc-codegen.html#improve-state-machine-codegen
* SIMD multiversioning: https://rust-lang.github.io/rust-project-goals/2025h1/simd-multiversioning.html

Code Examples
--------
* https://github.com/rust-lang-nursery/rust-cookbook
* http://zsiciarz.github.io/24daysofrust/

IDEs
----
* [emacs conf](http://willspeak.me/2018/12/08/racing-onwards.html) [other old](https://gist.github.com/jonathandturner/f529be1ed6e25f06952f0600dcfa9a3d)
* https://intellij-rust.github.io/

INTROS
------

* https://speakerdeck.com/hywan/hello-rust-an-overview
* https://fasterthanli.me/blog/2020/a-half-hour-to-learn-rust/


BOOKS
-----

* https://lborb.github.io/book/
* https://nnethercote.github.io/perf-book/introduction.html
* https://rust-lang.github.io/async-book/index.html
* https://doc.rust-lang.org/beta/nomicon/index.html
* https://rustwasm.github.io/docs/book/
* https://rust-unofficial.github.io/patterns/
* https://rust-lang.github.io/api-guidelines/about.html
* https://google.github.io/comprehensive-rust/welcome.html
* https://rust-unofficial.github.io/too-many-lists/first-ownership.html
* https://marabos.nl/atomics/

Other
-------

* https://www.rust-lang.org/en-US/faq.html
* https://readrust.net
* http://www.rustacean.net/
* http://www.arewewebyet.org/
* https://web.stanford.edu/class/cs140e/ (SO)
* https://github.com/nrc/r4cppp (For C++ programmers)
* https://github.com/rochacbruno/py2rs (For Pythonistas)
* https://aochagavia.github.io/blog/rocket---a-rust-game-running-on-wasm/ (wasm)
* https://coaxion.net/blog/category/rust/ (GStreamer)
* https://rust.godbolt.org/ (Compiler explorer)
* https://github.com/ixy-languages/ixy-languages/blob/master/Rust-vs-C-performance.md (performance)
* https://github.com/rust-lang/rustlings (learn)
* https://blog.skylight.io/rust-means-never-having-to-close-a-socket/ (blog entry about Ownership System)
* https://github.com/17cupsofcoffee/tetra/blob/master/docs/FAQ.md#why-is-my-game-running-slow (enable optimizations in debug mode for some dependencies)
