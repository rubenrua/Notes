# 4.- Cargo
2019-10-20

Last week, one point I love from rust is

> Cargo: After work with pip, maven, npm, composer... I can't work with a modern package manager.

When I have to test a quick patch in a C/C++ library, I use a workaround in Ubuntu to avoid all the dependencies headaches: using Ubuntu/Debian package manager:

```
apt-get install devscripts

apt-get source libgstreamer-plugins-bad1.0-0
sudo apt-get build-dep libgstreamer-plugins-bad1.0-0
cd gst-plugins-bad1.0-1.14.5
dpkg-buildpackage -b -uc
```

It works fine for patches, but it is only a workaround. Creating a development workspace for a C/C++ is miscellaneous, sometimes easy, sometimes hard, sometimes well documented, sometimes ... With cargo, working in a rust project is very comfortable. Having a modern package manager is a must for a new programming language.

But cargo is more:

* Cargo allows static compilation:

```
rustup target add x86_64-unknown-linux-musl
cargo build --target x86_64-unknown-linux-musl
ldd target/x86_64-unknown-linux-musl/release/bin
# not a dynamic executable
file target/x86_64-unknown-linux-musl/release/bin
# ELF 64-bit LSB executable, x86-64, version 1 (GNU/Linux), statically linked, BuildID[sha1]=de25e6720a53afe8ba4e17428d1b324e37094cee
```

* Cargo allows cross compilation. [From linux to windows example](https://stackoverflow.com/questions/31492799/cross-compile-a-rust-application-from-linux-to-windows)

```
cargo build --release --target "$ARCH-pc-windows-gnu"
cargo test --target "$ARCH-pc-windows-gnu"
```

* Cargo allows [cheap tricks for high-performance](https://deterministic.space/high-performance-rust.html)

* Cargo also includes tools to fix the code (cargo fix), to formatting code according to the style guidelines (cargo fmt) and recommend lints to catch common mistakes (cargo clippy). I love these tools and It should be inside any rust CI tool.

```
cargo fmt -- --check
touch ./src/*.rs && cargo clippy --no-default-features -- -A clippy::cast_ptr_alignment -A clippy::new_ret_no_self -Aclippy::or_fun_call -A clippy::cast_lossless -A clippy::too_many_arguments
```


* And, if it was not enough, also has a lot of plugins with new features like:

  * [cargo-expand](https://github.com/dtolnay/cargo-expand)
  * [cargo-deny](https://github.com/EmbarkStudios/cargo-deny)
  * [cargo-watch](https://github.com/passcod/cargo-watch)
  * [cargo-geiger](https://github.com/anderejd/cargo-geiger)
  * [cargo-c](https://github.com/lu-zero/cargo-c)
  * [flamegraph](https://github.com/flamegraph-rs/flamegraph).
  * [cargo-edit](https://github.com/killercup/cargo-edit)

Check the complete list in the [cargo wiki](https://github.com/rust-lang/cargo/wiki/Third-party-cargo-subcommands)
