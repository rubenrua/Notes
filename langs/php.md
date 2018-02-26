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
 * https://fr.slideshare.net/slideshow/embed_code/key/vNydONlVgNYNRx
 * https://github.com/phpinternalsbook/PHP-Internals-Book
 * https://3v4l.org
 * http://www.phpbenchmarks.com/en

Conf
----

 * See NGINX at [web note](/web/web.md)
 * https://getcomposer.org/doc/articles/autoloader-optimization.md
 * http://blog.jpauli.tech/2015/03/05/opcache.html#configuring-opcache and http://librosweb.es/tutorial/la-nueva-extension-opcache-de-php-55/ and https://symfony.com/doc/current/performance.html
   * Mind your `opcache.max_accelerated_files` ini setting: Just saw a 100% perf increase, the default (2000) is not enough.


Tools
-----

 * http://cs.sensiolabs.org/ (https://github.com/FriendsOfPHP/PHP-CS-Fixer)
 * https://phpsa.dmtry.me/ (https://github.com/ovr/phpsa)
 * https://blackfire.io
 * https://insight.sensiolabs.com/
 * https://github.com/phpstan/phpstan
 * https://github.com/phpro/grumphp

Tips
----

 * http://www.garfieldtech.com/blog/readfile-memory
 * http://symfony.com/doc/current/create_framework/index.html


SAD
---

 * Legacy PHP code
 * All is an array (list, dict, set...) [See php-ds](https://github.com/php-ds)
 * var_dump(0 == 'count'?true:false);
 * Semicolons after statements needed.
 * `<?php` tag
 * Override private methods
 * $a=null;var_dump($a == $a[0]);
 * Performance: https://github.com/symfony/symfony/pull/25474 and https://github.com/symfony/symfony/pull/24866