# 6.- Async .await
2019-11-08

Yesterday, *async.await* syntax hit stable Rust, as part of the 1.39.0 release. Welcome!!!

Reading the announce, I just remembered the [fearless concurrency](https://blog.rust-lang.org/2015/04/10/Fearless-Concurrency.html) blog post from 4 years ago. I am starting to think that these weekly notes are only a list of links that I want to write down. So, let's continue with it, links about *async.await*:

TL:DR: My favorite links from *async.await* is in the announce. Please read the official blog post about this topic: [Async-await on stable Rust!](https://blog.rust-lang.org/2019/11/07/Async-await-stable.html) or, copied from the blog post, check these two  links:

> If you'd like a closer look at how futures work under the hood, take a look at [the executor section](https://rust-lang.github.io/async-book/02_execution/04_executor.html) of the [async book](https://github.com/rust-lang/async-book), or watch the [excellent talk](https://www.youtube.com/watch?v=skos4B5x7qE) that [withoutboats](https://github.com/withoutboats) gave at [Rust LATAM 2019](https://rustlatam.org/) on the topic. ([new video @withoutboats on Pin](https://www.youtube.com/watch?v=shtfSMTwKRw)) ([Pin and suffering from @fasterthanlime](https://fasterthanli.me/articles/pin-and-suffering))

If you want to go deeper into the subject, please, check this two videos from YouTube video channel of [Jon Gjengset](https://twitter.com/jonhoo): [The What and How of Futures and async/await in Rust](https://www.youtube.com/watch?v=9_3krAQtD2k) and [The Why, What, and How of Pinning in Rust](https://www.youtube.com/watch?v=DkMwYxfSYNQ). Long videos, but very interesting too and you have to be very brave to do this kind of videos. Thank you Jon.

Shut up and show me the [code](https://play.rust-lang.org/?version=beta&mode=debug&edition=2018&gist=e04334bf580a8792fc1ba2771e245a72). Example of async code without external libs:
```
use std::future::Future;
use std::pin::Pin;
use std::ptr;
use std::task;

struct ImmediateExecution {
  waker: task::Waker
}

static IMMEDIATE_EXECUTION_VTABLE: &task::RawWakerVTable = &task::RawWakerVTable::new(clone, wake, wake_by_ref, drop);

fn clone(data: *const ()) -> task::RawWaker {
  task::RawWaker::new(data, IMMEDIATE_EXECUTION_VTABLE)
}

fn wake(_: *const ()) {
}

fn wake_by_ref(_: *const ()) {
}

fn drop(_: *const ()) {
}

impl Default for ImmediateExecution {
  fn default() -> Self {

    let raw = task::RawWaker::new(ptr::null(), IMMEDIATE_EXECUTION_VTABLE);
    let waker = unsafe { task::Waker::from_raw(raw) };

    ImmediateExecution { waker }
  }
}

impl ImmediateExecution {
  fn run<F>(&mut self, mut future: F) -> F::Output where F: Future {
    let mut ctx = task::Context::from_waker(&self.waker);

    // spinning loop is busy
    loop {
      let pinned = unsafe { Pin::new_unchecked(&mut future) };

      if let task::Poll::Ready(value) = Future::poll(pinned, &mut ctx) {
        break value;
      } else {
        std::thread::sleep(std::time::Duration::from_millis(1000));
      }
    }
  }
}

async fn test() -> i32 {
  12
}

fn main() {
  let mut execution = ImmediateExecution::default();
  let x = execution.run(test());

  println!("{}", x);
}
```


Add I leave with a song that I don't take it out of my mind:


```
Async await
Async await
Async await
Async await
In the jungle
The mighty jungle
The lion sleeps tonight.
```
