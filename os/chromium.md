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
# or https://chromium.googlesource.com/chromium/src/+/main/docs/linux/build_instructions.md#Arch-Linux
./build/install-build-deps.sh --no-nacl --no-arm --no-chromeos-fonts
dirmd help && file ../../depot_tools/.cipd_bin/dirmd 
./tools/clang/scripts/update.py
# or gn gen --args=use_sysroot=false is_debug=false is_component_ffmpeg=true use_qt=false use_chromium_rust_toolchain=false enable_rust=false proprietary_codecs=true ffmpeg_branding="Chrome" out/Default
gn gen --args="is_component_ffmpeg=true" out/Default
gn args out/Default --list
time ninja -C out/Default chrome chrome_sandbox chromedriver.unstripped
```

See: https://gitlab.archlinux.org/archlinux/packaging/packages/chromium/-/blob/main/PKGBUILD

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
* https://github.com/foutrelis/chromium-launcher/
