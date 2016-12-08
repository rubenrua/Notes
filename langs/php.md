PHP
===

Links
-----

 * http://php.net
 * http://www.php-fig.org
 * https://wiki.php.net/rfc (https://php-rfc-watch.beberlei.de)
 * http://symfony.com/
 * http://fabien.potencier.org/php-is-much-better-than-you-think.html
 * http://www.phpthewrongway.com/
 * http://phpsadness.com/

Conf
----

 * https://ilia.ws/files/nginx_torontophpug.pdf
 * http://jpauli.github.io/2015/03/05/opcache.html#configuring-opcache and http://librosweb.es/tutorial/la-nueva-extension-opcache-de-php-55/
   * Mind your `opcache.max_accelerated_files` ini setting: Just saw a 100% perf increase, the default (2000) is not enough.


Tools
-----

 * http://cs.sensiolabs.org/ (https://github.com/FriendsOfPHP/PHP-CS-Fixer)
 * https://phpsa.dmtry.me/ (https://github.com/ovr/phpsa)
 * https://blackfire.io
 * https://insight.sensiolabs.com/

Tips
----

 * http://www.garfieldtech.com/blog/readfile-memory
 * http://symfony.com/doc/current/create_framework/index.html


SAD
---

 * All is an array (list, dict, set...)
 * var_dump(0 == 'count'?true:false);
 * Semicolons after statements needed.
 * `<?php` tag
