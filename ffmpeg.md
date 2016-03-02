FFMPEG
=======


LINKS
-----

 * https://ffmpeg.org/ffmpeg.html 
 * https://libav.org/documentation/
 * http://sonnati.wordpress.com/2012/10/19/ffmpeg-the-swiss-army-knife-of-internet-streaming-part-vi/
 * https://opencast.jira.com/wiki/display/MHDOC/ETH+Zurich's+FFmpeg+encoding+profiles
 * https://trac.ffmpeg.org/wiki/Concatenate *1
 * http://dranger.com/ffmpeg/tutorial01.html
 * http://developer.download.nvidia.com/compute/redist/ffmpeg/1511-patch/FFMPEG-with-NVIDIA-Acceleration-on-Ubuntu_UG_v01.pdf
 * http://joinbox.github.io/dash-video/
 

NOTES
-----

##### MOSCA:

```
ffmpeg -strict unofficial -i #{in} -qscale 2 -vcodec mpeg2video -acodec mp2 -vf "movie=watermark.png[wm]; [in][wm]overlay=main_w-overlay_w-10:main_h-overlay_h-10[out] " #{out}
```

##### IMAGE:

```
ffmpeg -ss #{time} -y -i #{in.video}  -r 1 -vframes 1 -s 640x480 -f image2 #{out}.jpg
```

##### TRIM:

```
ffmpeg -strict unofficial -sameq -ss #{trim.start} -t #{trim.duration} -i #{in} -acodec copy -vcodec copy  #{out}
```

##### CROP:

```
ffmpeg -strict unofficial  -vf crop=in_w-240:in_h-20:120:10  -i #{in}   #{out}
```

##### MP4 faststart:

```
ffmpeg  .... -movflags faststart ...
```

##### PIXEL ASPECT RATIO:

```
ffmpeg -vf scale=960:540,setsar=1:1 -f mp4 -threads 0  -i #{in}   #{out}
```

##### SIDE BY SIDE:

```
ffmpeg -i before.mp4 -i after.mp4 -filter_complex "[0:v:0]pad=iw*2:ih[bg]; [bg][1:v:0]overlay=w" output.mp4
```

##### CONCAT:

```
ffmpeg -i input1.mp4 -i input2.webm \
-filter_complex "[0:0] [0:1] [1:0] [1:1] concat=n=2:v=1:a=1 [v] [a]" \
-map "[v]" -map "[a]" <encoding options> output.mkv *1
```

##### DELAY:

```
ffmpeg -i in.mp4 -itsoffset 00:00.5 -i in.mp4 -map 1:0 -map 0:1 -vcodec copy -acodec out.mp4
```

##### CHANGE PIXEL ASPECT RADIO (PAR):

```
MP4Box -par 1=1:1 SCREEN_out.mp4

ffmpeg -i CAMERA.mpg -vf scale=960:540,setsar=1:1 -f mp4 -threads 0 outsar.mp4
```

