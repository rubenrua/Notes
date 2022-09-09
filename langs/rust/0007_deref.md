# 7.- DeRef
2022-08-28

3 years later, very intensive years... it is time to write about Rust again.

Let go to the code directly:

```
#[derive(Debug)]
pub struct Software {
    pub name: &'static str,
}

const fn sw(
    name: &'static str,
) -> Software {
    Software {
        name,
    }
}

pub const SOFTWARES: &[Software] = &[
    sw("Ubuntu 16.04 LTS (Xenial Xerus)"),
    sw("Ubuntu 18.04 LTS (Bionic Beaver)"),
    sw("Ubuntu 20.04 LTS (Focal Fossa)"),
    sw("Ubuntu 22.04 LTS (Jammy Jellyfish)"),

    sw("Django 2.0"),
    sw("Django 2.1"),
    sw("Django 2.2"),
    sw("Django 3.0"),
    sw("Django 3.1"),
    sw("Django 3.2"),
    sw("Django 4.0"),

    sw("Python 3.6"),
    sw("Python 3.7"),
    sw("Python 3.8"),
    sw("Python 3.9"),
    sw("Python 3.10"),
    sw("Python 3.11"),
];
```

I want to use a constant static table with a list of a custom struct. And I need a function whose argument can be the table directly or the output of filtering it:

```
fn f(s: ?????) {
    dbg!(s);
}

fn main() {
    f(SOFTWARES);
    let filtered: Vec<Software> = SOFTWARES
        .iter()
        .filter(|e| e.name.to_lowercase().contains("ubuntu"))
        .collect();
    f(filtered);
}
```

Similar issue than: https://stackoverflow.com/a/44662455


First solution: cloned

```
#[derive(Debug, Clone)]
pub struct Software {
    pub name: &'static str,
}

const fn sw(
    name: &'static str,
) -> Software {
    Software {
        name,
    }
}


pub const SOFTWARES: &[Software] = &[
    sw("Ubuntu 16.04 LTS (Xenial Xerus)"),
    sw("Ubuntu 18.04 LTS (Bionic Beaver)"),
    sw("Ubuntu 20.04 LTS (Focal Fossa)"),
    sw("Ubuntu 22.04 LTS (Jammy Jellyfish)"),

    sw("Django 2.0"),
    sw("Django 2.1"),
    sw("Django 2.2"),
    sw("Django 3.0"),
    sw("Django 3.1"),
    sw("Django 3.2"),
    sw("Django 4.0"),

    sw("Python 3.6"),
    sw("Python 3.7"),
    sw("Python 3.8"),
    sw("Python 3.9"),
    sw("Python 3.10"),
    sw("Python 3.11"),
];



fn f(s: Vec<Software>) {
    dbg!(s);
}

fn main() {
    f(SOFTWARES.to_vec());
    let filtered: Vec<Software> = SOFTWARES
        .iter()
        .filter(|e| e.name.to_lowercase().contains("ubuntu"))
        .cloned()
        .collect();
    f(filtered);
}

```


But we can do it better avoid cloning. After reading [a similar issue in the Rust forum](https://users.rust-lang.org/t/solved-function-taking-slice-of-objects-as-well-as-slice-of-references-to-objects/13553/3) a solution using `AsRef` jumps to the scenario:

```
#[derive(Debug)]
pub struct Software {
    pub name: &'static str,
}

const fn sw(
    name: &'static str,
) -> Software {
    Software {
        name,
    }
}

impl AsRef<Software> for Software {
    fn as_ref(&self) -> &Software {
        self
    }
}

pub const SOFTWARES: &[Software] = &[
    sw("Ubuntu 16.04 LTS (Xenial Xerus)"),
    sw("Ubuntu 18.04 LTS (Bionic Beaver)"),
    sw("Ubuntu 20.04 LTS (Focal Fossa)"),
    sw("Ubuntu 22.04 LTS (Jammy Jellyfish)"),

    sw("Django 2.0"),
    sw("Django 2.1"),
    sw("Django 2.2"),
    sw("Django 3.0"),
    sw("Django 3.1"),
    sw("Django 3.2"),
    sw("Django 4.0"),

    sw("Python 3.6"),
    sw("Python 3.7"),
    sw("Python 3.8"),
    sw("Python 3.9"),
    sw("Python 3.10"),
    sw("Python 3.11"),
];


fn f<T: AsRef<Software>>(s: &[T]) {
    for e in s {
        let sw: &Software = e.as_ref();
        dbg!(sw);
    }
}

fn main() {
    f(SOFTWARES);
    let filtered: Vec<&Software> = SOFTWARES
        .iter()
        .filter(|e| e.name.to_lowercase().contains("ubuntu"))
        .collect();
    f(&filtered);
}
```


But impl AsRef<T> for T looks ugly. Playing with generating ASM and [rustfilt](https://github.com/luser/rustfilt) we can see the diff between the two `f` implemented:
 * Using `<&T as core::convert::AsRef<U>>::as_ref`
 * Using `<test::Software as core::convert::AsRef<test::Software>>::as_ref`

```
$ cargo rustc -- --emit asm
...
$ rg ":$"\|"callq" target/debug/deps/test-1d62123dabc4ebef.s | rustfilt | rg 'test::f:' -A 30 | rg ":$"\|"callq "
test::f:
.Lfunc_begin255:
.Ltmp1100:
        callq   core::slice::iter::<impl core::iter::traits::collect::IntoIterator for &[T]>::into_iter
.LBB255_2:
.Ltmp1101:
        callq   <core::slice::iter::Iter<T> as core::iter::traits::iterator::Iterator>::next
.LBB255_15:
.Ltmp1102:
.LBB255_5:
.LBB255_6:
.Ltmp1103:
.Ltmp1104:
        callq   <&T as core::convert::AsRef<U>>::as_ref
.Ltmp1105:
.Ltmp1106:
.Ltmp1107:
        callq   core::fmt::ArgumentV1::new_display
        callq   core::fmt::ArgumentV1::new_display
        callq   core::fmt::ArgumentV1::new_display
        callq   core::fmt::ArgumentV1::new_debug
.Ltmp1108:
        callq   core::fmt::Arguments::new_v1_formatted
        callq   *std::io::stdio::_eprint@GOTPCREL(%rip)
.Ltmp1109:
.Ltmp1110:
.Lfunc_end255:
test::f:
.Lfunc_begin256:
.Ltmp1111:
        callq   core::slice::iter::<impl core::iter::traits::collect::IntoIterator for &[T]>::into_iter
.LBB256_2:
.Ltmp1112:
        callq   <core::slice::iter::Iter<T> as core::iter::traits::iterator::Iterator>::next
.LBB256_15:
.Ltmp1113:
.LBB256_5:
.LBB256_6:
.Ltmp1114:
.Ltmp1115:
        callq   <test::Software as core::convert::AsRef<test::Software>>::as_ref
.Ltmp1116:
.Ltmp1117:
.Ltmp1118:
        callq   core::fmt::ArgumentV1::new_display
        callq   core::fmt::ArgumentV1::new_display
        callq   core::fmt::ArgumentV1::new_display
        callq   core::fmt::ArgumentV1::new_debug
.Ltmp1119:
        callq   core::fmt::Arguments::new_v1_formatted
        callq   *std::io::stdio::_eprint@GOTPCREL(%rip)
.Ltmp1120:
.Ltmp1121:
.Lfunc_end256:
```


But why [`Impl AsRef<T> for T` in not the core](https://users.rust-lang.org/t/impl-asref-t-for-t-in-the-core/80847/2)? I did a mini-reseach finding  a closed PR with the same idea [Make AsRef and AsMut reflexive](https://github.com/rust-lang/rust/pull/39397). Also the topic is an example of [Supporting blanket impls in specialization by the pro @nikomatsakis](https://smallcultfollowing.com/babysteps/blog/2016/10/24/supporting-blanket-impls-in-specialization/).


One more thing. In this case other posible solution could be use a slice of reference for the contant static table:

```
#[derive(Debug)]
pub struct Software {
    pub name: &'static str,
}

const fn sw(
    name: &'static str,
) -> Software {
    Software {
        name,
    }
}

pub const SOFTWARES: &[&Software] = &[
    &sw("Ubuntu 16.04 LTS (Xenial Xerus)"),
    &sw("Ubuntu 18.04 LTS (Bionic Beaver)"),
    &sw("Ubuntu 20.04 LTS (Focal Fossa)"),
    &sw("Ubuntu 22.04 LTS (Jammy Jellyfish)"),

    &sw("Django 2.0"),
    &sw("Django 2.1"),
    &sw("Django 2.2"),
    &sw("Django 3.0"),
    &sw("Django 3.1"),
    &sw("Django 3.2"),
    &sw("Django 4.0"),

    &sw("Python 3.6"),
    &sw("Python 3.7"),
    &sw("Python 3.8"),
    &sw("Python 3.9"),
    &sw("Python 3.10"),
    &sw("Python 3.11"),
];


fn f(s: &[&Software]) {
    dbg!(s);
}

fn main() {
    f(SOFTWARES);
    let filtered: Vec<&Software> = SOFTWARES
        .iter()
        .filter(|e| e.name.to_lowercase().contains("ubuntu"))
        .copied()
        .collect();
    f(&filtered);
}
```

But explicity copy the references is needed. Or not? That's for another day.
