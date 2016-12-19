FFMPEG
=======


LINKS
-----

 * https://ffmpeg.org/ffmpeg.html
 * https://libav.org/documentation/
 * https://trac.ffmpeg.org/wiki/FFprobeTips
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
ffmpeg -i before.mp4 -i after.mp4 -filter_complex "[0:v]scale=640:-1[ab], [ab]fps=fps=30[a], [a]pad=1280:720:0:120+((480-in_h)/2) [bg], [1:v]scale=640:-1[bb], [bb]fps=fps=30[b], [bg][b]overlay=w:120+((480-h)/2)" output.mp4
```

##### CONCAT:

```
ffmpeg -i input1.mp4 -i input2.webm \
-filter_complex "[0:0] [0:1] [1:0] [1:1] concat=n=2:v=1:a=1 [v] [a]" \
-map "[v]" -map "[a]" <encoding options> output.mkv *1
```

##### DELAY:

```
ffmpeg -i in.mp4 -itsoffset 00:00.5 -i in.mp4 -map 1:0 -map 0:1 -vcodec copy -acodec copy out.mp4
```

##### EXTRACT AUDIO:

```
ffmpeg -i in.mp4 -vn -acodec copy out.mp4_or_mp3
```


##### CHANGE PIXEL ASPECT RADIO (PAR):

```
MP4Box -par 1=1:1 SCREEN_out.mp4

ffmpeg -i CAMERA.mpg -vf scale=960:540,setsar=1:1 -f mp4 -threads 0 outsar.mp4
```

##### PARALLEL ENCODING:

```
ffmpeg -i source.avi \
  -c:v libx264 -filter:v yadif,scale=-2:288 -preset slower -crf 28 -r 25 -pix_fmt yuv420p -profile:v baseline -tune film -movflags faststart \
  -c:a aac -ar 22050 -ac 1 -ab 32k low.mp4 \
  -c:v libx264 -filter:v yadif,scale=-2:360 -preset slower -crf 25 -r 25 -pix_fmt yuv420p -profile:v baseline -tune film -movflags faststart \
  -c:a aac -ar 22050 -ac 1 -ab 48k medium.mp4 \
  -c:v libx264 -filter:v yadif,scale=-2:576 -preset medium -crf 23 -r 25 -pix_fmt yuv420p -tune film -movflags faststart \
  -c:a aac -ar 44100 -ab 96k high-quality.mp4 \
  -c:v libx264 -filter:v yadif,scale=-2:720 -preset medium -crf 23 -r 25 -pix_fmt yuv420p -tune film -movflags faststart \
  -c:a aac -ar 44100 -ab 96k hd-quality.mp4
```

##### TWO PASS ENCODING:

```
ffmpeg -y -i source.avi -vcodec libx264 -vprofile baseline -level:v 3 -r 25 -preset medium -b:v 1000000 -vf scale=iw*sar:ih -pass 1 -an -f mp4 /dev/null
ffmpeg -y -i source.avi -vcodec libx264 -vprofile baseline -level:v 3 -r 25 -preset medium -b:v 1000000 -vf scale=iw*sar:ih -pass 2 -acodec libfdk_aac -b:a 100000 -ac 2 -ar 44100 -f mp4 -threads 0 out.mp4
```

https://trac.ffmpeg.org/wiki/Encode/H.264#Two-PassExample
