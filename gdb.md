GDB
====

Tips
----
* TL;DR:
```
    s(tep) - Execute the current line, stop at the first possible occasion.
    n(ext) - Continue execution until the next line in the current function is reached or it returns.
    finish - Execute until selected stack frame returns.    
    stepi - Execute one machine instruction, then stop and return to the debugger.   
    l(ist) - Displays 11 lines around the current line or continue the previous listing.
    b(reak) - Set a breakpoint (depending on the argument provided).
    p(rint) - Evaluate the expression in the current context and print its value. There’s also pp to display using pprint instead.
    r(eturn) - Continue execution until the current function returns.
    q(uit) - Quit the debugger.
    info - info about thread, stack, frame, args, locals, variables, breakpoints    
```

* `thread apply all bt` or `bt full`

* `CFLAGS='-O0 -ggdb3'`

* Breakpoints:
```
g_assert_not_reached();
G_BREAKPOINT();
#define G_BRAKPOINT() __asm__ __volatile__ ("int $03");       // https://github.com/GNOME/glib/blob/2.68.1/glib/gbacktrace.h#L46
__builtin_trap();     // https://clang.llvm.org/docs/LanguageExtensions.html#builtin-trap
```
https://github.com/chromium/chromium/blob/d9d917c05c2a781d58ec15e3182e1dbd24c6530c/base/debug/debugger_posix.cc  


or

```
break do_quert
break fields.c:172
```
* Printfs:
```
__builtin_printf
__builtin_dump_struct      // https://clang.llvm.org/docs/LanguageExtensions.html#builtin-dump-struct
```

* Args
```
gdb --args gst-launch-1.0 videotestsrc num-buffers=200 pattern=1 ! video/x-raw, framerate=25/1 ! autovideoconvert  !  fakesink
```

* Batch
```
gdb -batch -n -ex 'set pagination off' -ex run -ex bt -ex 'bt full' -ex 'thread apply all bt full' --args hello
```

* Logging
```
(gdb) set logging on
(gdb) set logging file my_god_object.log
(gdb) show logging
```
https://stackoverflow.com/questions/5941158/gdb-print-to-file-instead-of-stdout

* Function
```
(gdb) define fn
> finish
> next
> end
```
https://stackoverflow.com/questions/1262639/multiple-commands-in-gdb-separated-by-some-sort-of-delimiter


* Reload shares
```
info shared
shared .
# set auto-solib-add off # to disable outload
```

* Set source code directories
```
function (void) at  file.c:66
file.c: No such file or directory.
(gdb) dir /tmp/pr/PK_4.4.6211.0/source/modules/stub
Source directories searched: /tmp/pr/PK_4.4.6211.0/source/modules/stub:$cdir:$cwd
```

* Inspect memory mappings
```
(gdb) catch syscall exit exit_group
(gdb) run
(gdb) info proc map
```
from https://fasterthanli.me/articles/whats-in-the-box


gdbinit
----
https://github.com/rubenrua/dotfiles/blob/master/.gdbinit

Links
-----

* https://gist.github.com/chrislongo/3351197
* https://raw.githubusercontent.com/camercu/dotfiles/master/gdbinit
* https://www.cs.swarthmore.edu/~newhall/unixhelp/howto_gdb.php
* https://ccrma.stanford.edu/~jos/stkintro/Useful_commands_gdb.html
* https://www-archive.mozilla.org/unix/debugging-faq
* https://stackoverflow.com/questions/6517423/how-to-do-an-specific-action-when-a-certain-breakpoint-is-hit-in-gdb
* https://wiki.st.com/stm32mpu/wiki/GDB_commands
* https://eocanha.org/blog/2021/04/27/gstreamer-webkit-debugging-by-instrumenting-source-code-1-3/
* TODO
