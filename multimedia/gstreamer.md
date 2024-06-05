GSTREAMER
=========

See: https://github.com/rubenrua/GstreamerCodeSnippets


Players:

* https://gitlab.gnome.org/GNOME/totem (GNOME official player)
* https://github.com/philn/glide (Rust+gtk4)
* https://github.com/Rafostar/clapper (GJS+gtk4+OpenGL)
* https://gitlab.gnome.org/guidog/livi (C+gtk4+libadwaita)
* https://github.com/ryd3v/VideoPlayer (Python+Qt)
* https://codeberg.org/comcloudway/melon (Python+Gtk)

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
