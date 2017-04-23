JAVASCRIPT
==========

LINKS
-----

* https://developer.mozilla.org/en-US/docs/Web/JavaScript
* http://superherojs.com


JQUERY LINKS
------------

* http://youmightnotneedjquery.com
* http://net.tutsplus.com/tutorials/javascript-ajax/from-jquery-to-javascript-a-reference/


Tips:
-----

* In ES5 use strict mode Always!!!
```js
"use strict";
```

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



* Speak (speech synthesis)
```js
const utterance = new SpeechSynthesisUtterance('apple');
const voice = window.speechSynthesis.getVoices()[0];
utterance.voice = voice;
window.speechSynthesis.speak(utterance);
```


Other:
------

* Understanding async/await in 7 seconds: https://twitter.com/manekinekko/status/855824609299636230