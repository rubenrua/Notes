JAVASCRIPT
==========

LINKS
-----

* https://developer.mozilla.org/en-US/docs/Web/JavaScript
* http://superherojs.com
* https://htmldom.dev/

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

or

```
var msg = new SpeechSynthesisUtterance();
var voices = window.speechSynthesis.getVoices();
msg.voice = voices[50];
msg.voiceURI = 'native';
msg.text = 'Gosh! I do believe my browser can talk';
speechSynthesis.speak(msg);
```
from: https://twitter.com/pragdave/status/1227998341256097794

* The Intl.RelativeTimeFormat and Intl.ListFormat API
```js
// not always have to use numeric value in the output.
const rtf = new Intl.RelativeTimeFormat('en', { numeric: 'auto' });
rtf.format(-1, 'day');
// → 'yesterday'
rtf.format(0, 'day');
// → 'today'
rtf.format(-1, 'week');
// → 'last week'

const lf = new Intl.ListFormat('en');
lf.format(['Frank']);
// → 'Frank'
lf.format(['Frank', 'Christine']);
// → 'Frank and Christine'
lf.format(['Frank', 'Christine', 'Flora']);
// → 'Frank, Christine, and Flora'
lf.format(['Frank', 'Christine', 'Flora', 'Harrison']);
// → 'Frank, Christine, Flora, and Harrison'
```

* List video capabilities
```js
RTCRtpSender.getCapabilities('video')
```
from: https://twitter.com/maniksach/status/1352696407648477184?s=20

Also check navigator.mediaCapabilities.decodingInfo()
and https://ott.dolby.com/codec_test/index.html or https://html5test.co
or https://cconcolato.github.io/media-mime-support/

* List media devices constraints
```
navigator.mediaDevices.getSupportedConstraints()
```
from: https://webrtchacks.com/bad-lighting-fix-with-javascript-webcam-exposure/

* MediaStreamTrack and MediaStreamTrackProcessor
from: https://developer.mozilla.org/en-US/docs/Web/API/MediaStreamTrack and https://webrtchacks.com/how-to-make-virtual-backgrounds-transparent-in-webrtc/
from: https://developer.mozilla.org/en-US/docs/Web/API/MediaStreamTrackProcessor , sample https://simple-mediastream-to-canvas.glitch.me/

Other:
------

* Understanding async/await in 7 seconds: https://twitter.com/manekinekko/status/855824609299636230
* https://paul.kinlan.me/detecting-text-in-an-image/
* https://developer.chrome.com/articles/shape-detection/
