# 1.- Hello World
2019-10-04
Doc link: https://doc.rust-lang.org/book/ch01-00-getting-started.html


Talk is cheap. Show me the code:

```sh
$ cargo new --bin hello && cd hello
$ cat src/main.rs
```
```rust
fn main() {
    println!("Hello, world!");
}
```
```sh
$ cargo run
Hello, world!"
$ cargo expand
```
```rust
#![feature(prelude_import)]
#[prelude_import]
use std::prelude::v1::*;
#[macro_use]
extern crate std;
fn main() {
    {
        ::std::io::_print(::core::fmt::Arguments::new_v1(
            &["Hello, world!\n"],
            &match () {
                () => [],
            },
        ));
    };
}

```

Notes:

 - Hello world. "Rust. Fast, safe and productive - pick three".
 - [`println!`](https://doc.rust-lang.org/src/std/macros.rs.html#147) macro. More info with `cargo expand` or `cargo rustc --profile=check -- -Zunstable-options --pretty=expanded` [src](https://github.com/dtolnay/cargo-expand/)
 - Rust prelude [src](https://doc.rust-lang.org/std/prelude/v1/index.html) ([from](https://twitter.com/focusaurus/status/1177221145587830784))
 - next: std/core/alloc/test... or `format!`/`dbg!`
