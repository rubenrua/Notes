HTML
=====


Tips
----

 * Tag `<details>`

```html
<details>
 <summary>Summary Goes Here</summary>
 ...this is hidden, collapsable content...
</details>
```

https://gist.github.com/ericclemmons/b146fe5da72ca1f706b2ef72a20ac39d

* Tag `<wbr>`

```html
<p>And the world record for the longest place name in an English-speaking country is...<br>
<i>Taumata<wbr>whakatangihanga<wbr>koauau<wbr>o<wbr>tamatea<wbr>turi<wbr>pukakapiki<wbr>maunga<wbr>horo<wbr>nuku<wbr>pokai<wbr>whenua<wbr>kitanatahu</i></p>
<p>This is the name of a hill in New Zealand.</p>
<p>Here's what it looks like without using the <code>wbr</code> tag...
<i>Taumatawhakatangihangakoauauotamateaturipukakapikimaungahoronukupokaiwhenuakitanatahu</i></p>
```

http://www.quackit.com/html_5/tags/html_wbr_tag.cfm

* Input with camera access

```html
Record camera video
<input type="file" accept="video/*" capture="camcorder">

Take camera picture
<input type="file" accept="image/*" capture="camera">

Record mic audio
<input type="file" accept="audio/*" capture="microphone">
```
http://www.csslab.cl/ejemplos/cam.html

Support: Safari Mobile 6. Android Browser 3.0, Android Chrome 0.16, Firefox Mobile 10.0.

* Select multiple

Row input element with good UX in mobiles and bad UX in desktops (see select2)

Links
------

 * Bootstrap: http://getbootstrap.com/
 * Foundation: http://foundation.zurb.com
 * ANT DESIGN: https://ant.design (for ReactJS)
 * Element: http://element.eleme.io/ (for Vue)
 * HTML5 Video Events and API: https://www.w3.org/2010/05/video/mediaevents.html
 * http://www.wirewax.com/blog/post/building-a-media-source-html5-player/