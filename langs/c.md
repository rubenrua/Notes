C
=


Links:
------

* http://cslibrary.stanford.edu/101/
* http://david.rothlis.net/c/compilation_model/
* https://matt.sh/howto-c
* http://www.ploxiln.net/make.html
* https://mattandre.ws/2016/05/make-for-hipsters/
* https://autotools.io/index.html
* http://smalltalk.gnu.org/blog/bonzinip/all-you-should-really-know-about-autoconf-and-automake
* http://c-faq.com/decl/spiral.anderson.html
* https://cdecl.org/ (C ↔ English)
* https://akkadia.org/drepper/dsohowto.pdf
* https://medium.com/nataraj-raghavendra/symbolism-in-nm-4af02e425710
* http://www.avabodh.com/cin/cin.html

Coding style:
-------------

* Linux: https://github.com/torvalds/linux/blob/master/Documentation/process/coding-style.rst
* GNOME: https://developer.gnome.org/programming-guidelines/stable/c-coding-style.html.en

Tips
----

* -Wall and -Wextra on GCC; -Weverything on Clang; /W4 or /Wall on MSVC (-E debug)
* https://best.openssf.org/Compiler-Hardening-Guides/Compiler-Options-Hardening-Guide-for-C-and-C++.html
* http://www.catb.org/esr/structure-packing/
* http://www.catonmat.net/blog/simple-ld-preload-tutorial/ (http://occams-razor.webs.uvigo.es/download/occams-razor-01-03.pdf)
* http://lxr.free-electrons.com/source/Documentation/assoc_array.txt
* http://blog.jpauli.tech/2016/11/30/on-c-performances.html
* https://blog.reverberate.org/2021/04/21/musttail-efficient-interpreters.html
* https://en.wikipedia.org/wiki/Profile-guided_optimization
* Default GCC conf Ubuntu:
```
$ echo "int main() { return 123; }" > tst.c && gcc tst.c -frecord-gcc-switches && readelf -p .GCC.command.line a.out

String dump of section '.GCC.command.line':
  [     0]  GNU C17 13.3.0 -mtune=generic -march=x86-64 -fasynchronous-unwind-tables -fstack-protector-strong -fstack-clash-protection -fcf-protection
```

Tools
-----

* Valgrind and cia: http://valgrind.org/  https://github.com/KDE/heaptrack https://github.com/koute/memory-profiler
* Meson: http://mesonbuild.com/
* Copiler explorer: http://gcc.godbolt.org/
* clang-format: http://releases.llvm.org/7.0.1/tools/clang/docs/ClangForm and GNU indent: https://www.gnu.org/software/indent/
* List BC: https://abi-laboratory.pro/ ([example](https://abi-laboratory.pro/?view=timeline&l=glibc))
* libc alt: [glibc](https://www.gnu.org/software/libc/), [musl](http://musl.libc.org/), [uClibc](https://www.uclibc.org/), [cosmopolitan](https://justine.lol/cosmopolitan/index.html). ([Comparison](http://www.etalabs.net/compare_libcs.html), [more wikipedia](https://en.wikipedia.org/wiki/Linux_kernel_interfaces#The_C_standard_library)) 
* better C: https://github.com/git/git/blob/master/banned.h, https://github.com/microsoft/checkedc, https://github.com/google/wuffs, https://ziglang.org/, https://harelang.org/....


Linking
-----
* https://gitlab.collabora.com/vivek/libcapsule/-/blob/master/doc/Strategy.txt

* https://github.com/hpvb/dynamic-linktime-load (from https://github.com/hpvb/dynload-wrapper)
* https://github.com/yugr/Implib.so

* https://github.com/hpvb/dynamic-linktime-load (from https://github.com/hpvb/dynload-wrapper) using `#pragma weak ffff`
* https://github.com/yugr/Implib.so (from https://stackoverflow.com/questions/45917816/is-there-an-elegant-way-to-avoid-dlsym-when-using-dlopen-in-c) using `ASM trampoline functions`




Books
-----

 * The C Programming Language (by Brian W. Kernighan and Dennis M. Ritchie)
 * Modern C (by Jens Gustedt) // https://gustedt.gitlabpages.inria.fr/modern-c/ 
 * Beej’s Guide to C Programming // http://beej.us/guide/bgc/pdf/bgc_usl_c_1.pdf
