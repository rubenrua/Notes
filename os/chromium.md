Chromium
========

> ~Web~ Chromium is the new universal OS
:_(


build
-----

```
git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git
export PATH="$PATH:$( realpath depot_tools)"
mkdir chromium && cd chromium
fetch --nohooks chromium
cd src
./build/install-build-deps.sh
gn gen out/Default
gn args --args="is_component_ffmpeg=true " out/Default--list
ninja -C out/Default chrome chrome_sandbox chromedriver.unstripped
``

releases
--------

* https://www.chromestatus.com/features/schedule
* https://chromiumdash.appspot.com/releases?platform=Linux
* https://fugu-tracker.web.app/
* https://omahaproxy.appspot.com/

dev
----

* https://www.youtube.com/user/blinkontalks
* https://github.com/keyou/chromium_demo
* https://www.chromium.org/Home/chromium-security/memory-safety/rust-and-c-interoperability

other
----
* https://github.com/stream-projects/stream-video-image

