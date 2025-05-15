Image processing
================

Links
-----

* (imagemagick) http://www.imagemagick.org/script/command-line-processing.php
* (scikit) http://blog.yhat.com/posts/image-processing-with-scikit-image.html
* (tesseract.js) https://github.com/naptha/tesseract.js [OCR][WEB]
* (Compress and compare images with different codecs, right in your browser) https://squoosh.app [JS][CompressCompress]


Quality metrics amd other
--------------

* SSIM https://www.cns.nyu.edu/~lcv/ssim/
* MS-SSIM https://ece.uwaterloo.ca/~z70wang/publications/msssim.html
* VIF https://live.ece.utexas.edu/research/Quality/VIF.htm
* PSNR https://en.wikipedia.org/wiki/Peak_signal-to-noise_ratio
* VMAF https://github.com/Netflix/vmaf (videos only)
* AVQT Advanced Video Quality Tool (Apple only)
* MLCVQA https://github.com/microsoft/MLCVQA

```
$ compare -verbose -fuzz 0.4% -metric PSNR -size 176x144 -depth 8 frame_1b.rgba frame_1a.rgba /tmp/diff.png
$ dssim -o difference.png original.png modified.png
```

Color formats
---------------
* GStreamer: https://github.com/GStreamer/gstreamer/blob/main/subprojects/gst-plugins-base/gst-libs/gst/video/video-format.h#L59
* FFmpeg: `ffmpeg -pix_fmts`
* FFmpeg-GStreamer formats maping (from https://gitlab.freedesktop.org/gstreamer/gstreamer/-/blob/main/subprojects/gst-libav/ext/libav/gstavcodecmap.c#L2723):
* DRM Linux: https://github.com/torvalds/linux/blob/master/include/uapi/drm/drm_fourcc.h

| FFMPEG     | GSTREAMER  |
|------------|------------|
| yuv420p    | I420       |
| yuv422p    | Y42B       |
| yuv420p10le| I420_10LE  |
| yuv422p10le| I422_10LE  |
| yuv420p12le| I420_12LE  |
| yuv422p12le| I422_12LE  |
| yuv444     | Y444       |
| yuv444p10le| Y444_10LE  |
| yuv444p12le| Y444_12LE  |


* Other: https://gist.github.com/Jim-Bar/3cbba684a71d1a9d468a6711a6eddbeb


Video and Image Datesets
---------------

* https://github.com/openimages/dataset
* https://research.google.com/youtube8m/
* http://image-net.org
* https://www.pexels.com
* https://github.com/Netflix/vmaf/blob/master/resource/doc/datasets.md
* https://www.cdvl.org/
* https://www.kaggle.com/datasets?tags=13207-Computer+Vision
* https://www.deepmind.com/open-source/kinetics
* https://cocodataset.org/