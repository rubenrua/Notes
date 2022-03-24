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

```
$ compare -verbose -fuzz 0.4% -metric PSNR -size 176x144 -depth 8 frame_1b.rgba frame_1a.rgba /tmp/diff.png
$ dssim -o difference.png original.png modified.png
```

Video and Image Datesets
---------------

* https://github.com/openimages/dataset
* https://research.google.com/youtube8m/
* http://image-net.org
* http://mscoco.org
* https://www.pexels.com
* https://github.com/Netflix/vmaf/blob/master/resource/doc/datasets.md
* https://www.cdvl.org/
* https://www.kaggle.com/datasets?tags=13207-Computer+Vision
