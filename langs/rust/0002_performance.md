# 2.- Performance
2019-09-29

*A leopard never changes its spots*; I enjoy performance issues, and [Rust is leading most of the TechEmpower web framework benchmarks](https://news.ycombinator.com/item?id=20402082). See [benchmarks](https://www.techempower.com/benchmarks/#section=data-r18&hw=ph&test=fortune) and [src](https://github.com/TechEmpower/FrameworkBenchmarks/tree/master/frameworks/Rust/actix).

Rust is a [multi-paradigm system programming language](https://en.wikipedia.org/wiki/Rust_(programming_language)) whose performance is *similar* to C. ([Note1](https://benchmarksgame-team.pages.debian.net/benchmarksgame/fastest/gcc-rust.html), [Note2](https://github.com/ixy-languages/ixy-languages/blob/master/Rust-vs-C-performance.md) and [Note3](https://www.viva64.com/en/b/0733/)).

Currently, performance is not only about execution time, but it is also about development time too. And Rust is a more productive language than C. Two examples:

 * Watch the ["Full Stack Fest 2015: Rewriting a Ruby C Extension in Rust, by Yehuda Katz" video](https://www.youtube.com/watch?v=2BdJeSC4FFI) or this fantastic [summary by Steve Klabnik](https://gist.github.com/steveklabnik/1a3ec0ca676aaddf766e).


```rust
extern crate libc;
mod buf; // a small buffer struct + impl, not shown
use buf::Buf;

#[no_mangle]
pub extern "C" fn tr_str_is_blank(b: Buf) -> bool {
    let s = b.as_slice().unwrap();

    s.chars().all(|c| c.is_whitespace())
}
```


 * or read the [Declarative memory management](https://amos.me/blog/2019/declarative-memory-management/) blog post by Amos.

 ```rust
 fn main() -> Result<(), std::io::Error> {
    let paths = ["sample4.txt"];

    // check all documents
    let mut results = vec![];
    for path in &paths {
        let result = check(path)?;
        results.push(result);
    }

    // report them all
    for result in results {
        report(result);
    }

    Ok(())
}

fn report(result: Option<Mistake>) {
    if let Some(mistake) = result {
        println!("{}", mistake);
    }
}

struct Mistake {
    path: &'static str,

    text: String,
    locations: Vec<usize>,
}

use std::io::Error as E;

fn check(path: &'static str) -> Result<Option<Mistake>, E> {
    let text = std::fs::read_to_string(path)?;

    let locations: Vec<_> = text.match_indices(",").map(|(index, _)| index).collect();

    Ok(if locations.is_empty() {
        None
    } else {
        Some(Mistake {
            path,
            text,
            locations,
        })
    })
}

use std::fmt;

impl Mistake {
    fn line_bounds(&self, index: usize) -> (usize, usize) {
        let len = self.text.len();

        let before = &self.text[..index];
        let start = before.rfind("\n").map(|x| x + 1).unwrap_or(0);

        let after = &self.text[index + 1..];
        let end = after.find("\n").map(|x| x + index + 1).unwrap_or(len);

        (start, end)
    }
}

impl fmt::Display for Mistake {
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        for &location in &self.locations {
            let (start, end) = self.line_bounds(location);
            let line = &self.text[start..end];

            let line_number = self.text[..start].matches("\n").count() + 1;
            let comma_index = location - start;

            write!(f, "{}: commas are forbidden:\n\n", self.path)?;

            // print the line, with line number
            write!(f, "{:>8} | {}\n", line_number, line)?;

            // indicate where the comma is
            write!(f, "{}^\n\n", " ".repeat(11 + comma_index))?;
        }
        Ok(())
    }
}
 ```

 * or compare a GStreamer/Gtk element in rust Vs the boilerplate C version [more info](https://coaxion.net/blog/2016/05/writing-gstreamer-plugins-and-elements-in-rust).



Notes:

 - Iterators usually are more efficient than using an index (like `for`s in C), because Rust enforces bounds checks.
 - [actix](https://github.com/actix/actix) is an Actor framework for Rust with [a small, pragmatic, and extremely fast rust web framework](https://github.com/actix/actix-web).
 - next: String vs &str
