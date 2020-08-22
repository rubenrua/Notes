Unicode & Character Sets
========================

> UTF-8 & unicode everywhere


iconv: character set conversion
------
```
iconv -f ISO_8859-1 -t UTF-8 $i > tmpfile
```

MySQL
----

```
CREATE DATABASE mydb
CHARACTER SET utf8mb4
COLLATE utf8mb4_unicode_ci;
```

Useful
------
https://en.wikibooks.org/wiki/Unicode/List_of_useful_symbols
```
␣ ☐ • ► - TODO
★ ☒ ✗ ✘ - KO
☆ ☑ ✓ ✔ - OK
↺  - OTHER
```

Links
------

* http://www.joelonsoftware.com/articles/Unicode.html
* https://www.smashingmagazine.com/2016/11/character-sets-encoding-emoji/
* http://www.emojitracker.com
* https://github.com/migonzalvar/talks/tree/master/2016-11-php-vigo
