GSTREAMER
=========

See: https://github.com/rubenrua/GstreamerCodeSnippets


Players:

* https://gitlab.gnome.org/GNOME/totem (OLD GNOME official player)
* https://github.com/philn/glide (Rust+gtk4)
* https://github.com/Rafostar/clapper (GJS+gtk4+OpenGL)
* https://gitlab.gnome.org/guidog/livi (C+gtk4+libadwaita)
* https://github.com/ryd3v/VideoPlayer (Python+Qt)
* https://codeberg.org/comcloudway/melon (Python+Gtk)
* https://gitlab.gnome.org/GNOME/Incubator/showtime (NEW GNOME official player Python+gtk4+libadwaita)
* More at https://github.com/valpackett/awesome-gtk?tab=readme-ov-file#video-players


Rust tools:

* TODO

Other tools:

* https://github.com/selkies-project/selkies (Remote Desktop)
* https://github.com/fastogt/fastocloud (media-server)

Tools to work with gst logs

* https://github.com/gdesmott/gst-log-parser
* https://github.com/philn/gst-log-diff
* https://github.com/rafaelcaricio/gst-log-viewer
* https://blogs.igalia.com/plampe/working-with-webkit-and-gstreamer-logs-in-emacs/

Links

* https://caricio.com/learn-by-example-making-it-easier-to-understand-gstreamer/

Distributions:

* https://gstreamer.freedesktop.org/download/#linux [win, mac, android, ios]
* https://pypi.org/org/gstreamer/ [win, mac]
* Linux distros (gst-plugins-rs: Arch, Alpine) [linux]
* https://formulae.brew.sh/formula/gstreamer [mac, linux]
* https://conan.io/center/recipes/gstreamer [recipes]
* https://vcpkg.io/en/package/gstreamer [recipes]
* flatpak `org.gnome.Sdk`
* https://search.nixos.org/packages?show=gst_all_1.gstreamer
* https://packages.msys2.org/base/mingw-w64-gstreamer [win]
* https://github.com/wingtk/gvsbuild/blob/main/gvsbuild/projects/gstreamer.py [win]
* https://community.chocolatey.org/packages/gstreamer [win]
* https://winget.run/pkg/gstreamerproject/gstreamer [win]
* https://git.openembedded.org/openembedded-core/tree/meta/recipes-multimedia/gstreamer [recipe, embedded]

vs FFmpeg:

 * Both are Open Source and Cross Platform.
 * Both are frameworks to create multimedia apps.
 * Also, Both are tools to do simple multimedia task.
   * transcoder: ffmpeg vs gst-transcoder-1.0
   * media-inspector: ffprobe vs gst-discoverer-1.0
   * player: ffplay vs gst-play-1.0
 * GStreamer plugins can be register in run time and build time., FFmpeg plugins only can be register in build time.
 * GStreamer depends on glib and libffi (glib is a big dependency, sometimes it is an issue to use GStreamer)
 * FFmpeg has AC-3, H.264 and H.265 very good software codecs (w/o patents).
   * GStreamer can use FFmpeg codecs (gstreamer1.0-libav).
 * FFmpeg has more low level optimizations (color conversion for instace https://gitlab.freedesktop.org/gstreamer/orc/-/issues/13)
 * Firefox and Chromium use FFmpeg.
 * FFmpeg don't support webasm by default
 * NVIDIA Deepsteem uses GStreamer
 * [personal opinion] GStreamer framework is easier to use (and more powerful). FFmpeg tools are easier to use (and more powerful)
