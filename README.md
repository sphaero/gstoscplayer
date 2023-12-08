# gstoscplayer

Gstreamer Videoplayer controlled through OSC

# Building a specific version of gstreamer?

```bash
git clone https://github.com/GStreamer/gst-build
cd gst-build
git checkout origin/$GST_VERSION
meson builddir
ninja -C builddir
```
Using the lib
```
cd builddir
ninja devenv
```
