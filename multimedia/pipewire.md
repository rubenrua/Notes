https://lwn.net/Articles/847412/

> a media stream by passing a memfd or dma-buf file descriptor

https://venam.nixers.net/blog/unix/2021/06/23/pipewire-under-the-hood.html

> NB: If you want to know more about protocol/format design in general refer to [RFC 3117](https://datatracker.ietf.org/doc/html/rfc3117).

https://www.youtube.com/watch?v=jBrsW6eancA



https://itso.dk/?p=730


https://bootlin.com/blog/an-introduction-to-pipewire/  (from https://news.ycombinator.com/item?id=32629624)

TOOLS
-------
https://gitlab.freedesktop.org/ryuukyu/helvum
https://github.com/wwmm/easyeffects
https://github.com/EHfive/pw-capture


EXAMPLES
--------
* xdp-screen-cast.py: https://gitlab.gnome.org/-/snippets/19

* pipewiresink to feed firefox
```
gst-launch-1.0 -v  videotestsrc pattern=ball ! "video/x-raw,format=YUY2,width=640,height=480" ! videorate ! identity silent=false ! pipewiresink stream-properties="p,node.description=DSLR,node.name=DSLR,media.role=Camera,media.class=Video/Source"
```

* pipewiresrc from weston

```
gst-launch-1.0 pipewiresrc ! video/x-raw,format=BGRx ! ...
```

1) pipewire plugin: next confing file (from version 7???)

```
[pipewire-output]
name=rrrrwestonpipe
mode=1920x1080@60.0
```


2) pipewire backend: `weston -B pipewire` (from version 13?? )


* Other

```
pw-dump | jq '.[] | select(.info.props["media.class"] =="Video/Source") | .info.props."node.name" + " | " +.info.props."node.description" + " | " + (.id|tostring)'
pw-dump | jq '.[] | select(.info.props["media.class"] // "" | contains("Video")) | .info.props."media.class" + " | " + .info.props."node.name" + " | " + .info.props."node.description" + " | " + (.id | tostring)'
```
