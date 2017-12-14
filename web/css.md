CSS
===

Tips
-----

* How to make trim to row/title. using only CSS

```css
h1{
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
}
```
https://coderwall.com/p/yxeiiw


* break long words
```css
.break-long-words {
    -ms-word-break: break-all;
    word-break: break-all;
    word-break: break-word;
    -webkit-hyphens: auto;
    -moz-hyphens: auto;
    hyphens: auto;
}
```


* Using calc in CSS
```css
width: calc(50px * 2);
width: calc(200px / 2);
width: calc(40px + 40px);
width: calc(200px - 80px);
```
http://xitrus.es/blog/80/Cálculos_en_el_CSS_con_calc()_de_CSS3


* Replace text with image
```css
.hide-text {
  text-indent: 100%;
  white-space: nowrap;
  overflow: hidden;
}
```
http://www.zeldman.com/2012/03/01/replacing-the-9999px-hack-new-image-replacement/

* Font size relative to viewport (`vw`, `vw`, `vi` and `vb`)
```css
.center {
  width: 50vw;
}
```

https://developer.mozilla.org/en/docs/Web/CSS/length

* Applying a relative size which includes borders and paddings (box-sizing)

https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing


Links
------

* Reset CSS: http://yuilibrary.com/yui/docs/cssreset/
* Libros Web: https://librosweb.es/libro/css/ and https://librosweb.es/referencia/css/ [ES]
* 12 Fun CSS Text Shadows You Can Copy and Paste: https://designshack.net/articles/css/12-fun-css-text-shadows-you-can-copy-and-paste
* Item blur effect with css3 & jquery: http://tympanus.net/Tutorials/ItemBlur/
* Website Style Guide Resources: http://styleguides.io/
* http://cssreference.io/
