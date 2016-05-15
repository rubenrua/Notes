AJAX
====

TUTORIALES:
-----------

 * 




Tips:
-----

* Ajax globar handle
```js
var proxied = XMLHttpRequest.prototype.open;

XMLHttpRequest.prototype.open = function(method, url, async, user, pass) {
    var self = this;
    console.log("req");
    this.addEventListener("readystatechange", function() {
        if (self.readyState == 4) {
            console.log("response");
            if (self.status < 200 || self.status >= 400) {
                console.log("error");
            }
        }
    }, false);

    proxied.apply(this, Array.prototype.slice.call(arguments));
    };

```

http://api.jquery.com/category/ajax/global-ajax-event-handlers/