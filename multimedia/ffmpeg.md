FFMPEG
=======


LINKS
-----

 * https://ffmpeg.org/ffmpeg.html
 * https://libav.org/documentation/
 * https://trac.ffmpeg.org/wiki/FFprobeTips
 * https://trac.ffmpeg.org/wiki/Concatenate *1
 * http://developer.download.nvidia.com/compute/redist/ffmpeg/1511-patch/FFMPEG-with-NVIDIA-Acceleration-on-Ubuntu_UG_v01.pdf
 * http://joinbox.github.io/dash-video/
 * https://github.com/alfg/ffmpeg-commander
 * https://ffmpeg.guide/

TUTORIALS
---------

 * https://img.ly/blog/ultimate-guide-to-ffmpeg/ [INTRO]
 * http://sonnati.wordpress.com/2012/10/19/ffmpeg-the-swiss-army-knife-of-internet-streaming-part-vi/
 * https://opencast.jira.com/wiki/display/MHDOC/ETH+Zurich's+FFmpeg+encoding+profiles
 * http://dranger.com/ffmpeg/tutorial01.html
 * https://github.com/leandromoreira/ffmpeg-libav-tutorial



NOTES
-----

##### MOSCA:

```
ffmpeg -strict unofficial -i #{in} -qscale 2 -vcodec mpeg2video -acodec mp2 -vf "movie=watermark.png[wm]; [in][wm]overlay=main_w-overlay_w-10:main_h-overlay_h-10[out] " #{out}
```

##### TAKE AN IMAGE:

```
ffmpeg -ss #{time} -y -i #{in.video}  -r 1 -vframes 1 -s 640x480 -f image2 #{out}.jpg
```

##### IMAGE TO VIDEO:

```
ffmpeg -nostats  -loop 1  -i image.png  -c:v libx264  -r 30 -t 5.000 -pix_fmt yuv420p  video.mp4
```


##### TRIM:

```
ffmpeg -strict unofficial -i #{in} -sameq -ss #{trim.start} -t #{trim.duration} -acodec copy -vcodec copy  #{out}
ffmpeg -strict unofficial -sameq -ss #{trim.start} -t #{trim.duration} -i #{in} -acodec copy -vcodec copy  #{out}
```

##### CROP:

```
ffmpeg -strict unofficial  -vf crop=in_w-240:in_h-20:120:10  -i #{in}   #{out}
```

##### MP4 faststart (or `qt-faststart`):

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
ffmpeg -i before.mp4 -i after.mp4 -filter_complex hstack hmerge.mp4
ffmpeg -i before.mp4 -i after.mp4 -filter_complex vstack vmerge.mp4
```

##### STABILIZING VIDEO (only with --enable-libvidstab):

```
ffmpeg -i GOPR7182.MP4 -vf vidstabdetect=stepsize=32:shakiness=10:accuracy=10:result=transform_vectors.trf -f null -
ffmpeg -i GOPR7182.MP4 -vf vidstabtransform=input=transform_vectors.trf:zoom=0:smoothing=10,unsharp=5:5:0.8:3:3:0.4 -vcodec libx264 -tune film -acodec copy -preset slow stabilized.mp4
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


##### TEST SRC
```
ffmpeg -f lavfi -i testsrc=duration=10:size=1280x720:rate=30 testsrc.mpg
ffmpeg -f lavfi -i testsrc=duration=10:size=1280x720:rate=30 -vf "drawtext=x=120:y=h-lh-1:fontsize=32:fontcolor=white:shadowcolor=black:shadowx=1:shadowy=1:timecode='00\:00\:00\:00':timecode_rate=30"  -vcodec libx264 testsrc.mp4
```

##### DESKTOP CAPTURE TO V4L2 DEVICE:

```
modprobe v4l2loopback
ffmpeg -f x11grab -r 15 -s 1280x720 -i :0.0+0,0 -vcodec rawvideo -pix_fmt yuv420p -threads 0 -f v4l2 /dev/video0
```

https://github.com/umlaeute/v4l2loopback


##### HIGH QUALITY GIF

```
palette="/tmp/palette.png"

filters="fps=15,scale=320:-1:flags=lanczos"

ffmpeg -v warning -i $1 -vf "$filters,palettegen" -y $palette
ffmpeg -v warning -i $1 -i $palette -lavfi "$filters [x]; [x][1:v] paletteuse" -y $2
```

http://blog.pkh.me/p/21-high-quality-gif-with-ffmpeg.html

##### CREATE ADAPTIVE STREAMING

Dash:
```
ffmpeg -f avfoundation -s 1280x720 -r 30 -i 0:0 -vcodec libx264 -preset ultrafast -keyint_min 0 -g 120 -b:v 1000k -ac 2 -strict 2 -acodec aac -b:a 64k -map 0:v -map 0:a -f dash -min_seg_duration 4000 -use_template 1 -use_timeline 0 -init_seg_name init-\$RepresentationID\$.mp4 -media_seg_name test-\$RepresentationID\$-\$Number\$.mp4 test.mpd
```
```
ffmpeg -f flv -listen 1 -i rtmp://192.168.50.165:1935/live/app -an -c:v copy -b:v 500k -ldash 1 -streaming 1 -use_template 1 -use_timeline 0 -seg_duration 4 -remove_at_exit 1 -f dash /usr/local/var/www/ldash/1.mpd
```

HLS:
```
ffmpeg -f avfoundation -s 1280x720 -r 30 -i 0:0 -vcodec libx264 -preset ultrafast -keyint_min 0 -g 120 -b:v 1000k -ac 2 -strict 2 -acodec aac -b:a 64k -map 0:v -map 0:a -f hls -hls_time 8 test.m3u8
```

HLS on rpi:
```
ffmpeg -framerate 30 -video_size 800x600 -i /dev/video0 c:v mjpeg -q:v 0 -f image2 -update 1 -atomic_writing 1 /tmp/webcam/jpeg/frame.jpg -c:v h264_omx -profile:v high -b:v 2048k -flags +cgop -g 30 -keyint_min 30 -f hls -hls_time 1  -hls_flags delete_segments+program_date_time+temp_file+independent_segments -hls_allow_cache 0 -hls_segment_type fmp4 -hls_list_size 32 -hls_delete_threshold 64 /tmp/webcam/hls/stream.m3u8
```


##### RTSP

```
ffserver -d
ffmpeg -r 25 -s 352x288 -f video4linux2 -i /dev/video0 http://localhost:8090/feed1.ffm
ffplay "rtsp://localhost:5554/test.mpeg4
```

https://stackoverflow.com/questions/37403282/is-there-anyone-who-can-success-real-time-streaming-with-ffserver
https://trac.ffmpeg.org/wiki/StreamingGuide

##### AUDIO PHASE REVERSAL/INVERT

```
ffmpeg -i input.wav -af "aeval='-val(0)':c=same" output.wav
ffmpeg -i {} -acodec aac -ab 128k -ac 1 -af pan="stereo:c0=c0:c1=-1*c1" -ar 44100 -vcodec libx264 -r 25 -crf 22 -pix_fmt yuv420p -s 1280x720 -threads 0 -strict -2 {}
```

##### RAW VIDEO

```
ffmpeg -i test.mp4 -c:v rawvideo -pix_fmt yuv420p test.yuv
ffplay -f rawvideo -pix_fmt yuv420p -s 1280x720 -i test.yuv
ffmpeg -pix_fmts
ffmpeg -i test.mp4  -c:v rawvideo  -an -f rawvideo - | ffplay -i - -f rawvideo -pix_fmt yuv420p -s 2560x1440
```
https://trac.ffmpeg.org/wiki/colorspace  
https://www.facebook.com/permalink.php?story_fbid=2413101932257643&id=100006735798590  
https://mux.com/blog/your-browser-and-my-browser-see-different-colors  


##### AV1

```
ffmpeg -i input.mp4 -c:v libaom-av1 -crf 30 -b:v 0 -strict experimental av1_test.mkv
```

##### REGULAR KEY FRAMES AND SCENE-CUT-BASED (AND GET INFO)

```
ffmpeg -i input.mp4 -force_key_frames "expr:eq(mod(n,25),0)" -x264opts rc-lookahead=25:keyint=50:min-keyint=25 -c:v libx264 -preset faster -crf 23 -c:a copy -movflags faststart -pix_fmt yuv420p -t 300 output.mp4
ffprobe input.mp4 -select_streams v -show_frames  -show_entries frame=key_frame,pict_type,coded_picture_number -of csv
```


##### GET MOV ATOM INFO

```
ffprobe -v trace infile.mp4
#or AtomicParsley infile.mp4 -T 1
#or fq d infile.mp4
```
https://superuser.com/questions/559372/using-ffmpeg-to-locate-moov-atom  
https://gitlab.freedesktop.org/gstreamer/gst-plugins-good/-/blob/1.18/gst/isomp4/qtdemux_types.c#L27  
http://mp4ra.org/#/codecs


##### GET ENCODER INFO (PROFILE & LEVEL)

```
ffprobe -show_streams nvidia_hw_encoding.mp4
ffmpeg -i nvidia_hw_encoding.mp4 -c copy -bsf:v trace_headers -f null -
```


#### DEBUG

```
ffmpeg -hide_banner -loglevel panic -i iphone_H265.mov -acodec copy -vcodec copy -f md5 -
ffmpeg -hide_banner -loglevel panic -i iphone_H265.mov -acodec copy -vcodec copy -f framemd5 -
```
https://trac.ffmpeg.org/wiki/framemd5%20Intro%20and%20HowTo


#### LIST COMMON EXTENSIONS

```
ffmpeg -demuxers -hide_banner | tail -n +5 | cut -d' ' -f4 | xargs -i{} ffmpeg -hide_banner -h demuxer={} | grep 'Common extensions' | cut -d' ' -f7 | tr ',' $'\n' | tr -d '.'
```

#### LIST HW
```
ffmpeg -hwaccels               # Show available HW acceleration methods (aka `AVHWDeviceType` + `HWAccel`[1])
ffmpeg -init_hw_device list    # List hardware devices (aka `AVHWDeviceType`)
```

[1] HWAccel was deleted in commit [5633f9a](https://github.com/FFmpeg/FFmpeg/commit/5633f9a8a221f7511d5ec9b4c57a21c890271ad0). So `-hwaccels` == `-init_hw_device list`  
Note: Internal hw decoders are `AVHWAccel`. External wrapper (or Standalone) decoders are `FFCodec`.  


##### V4L2 LIST FORMATS
```
ffmpeg -hide_banner -f video4linux2 -list_formats all -i /dev/video0
```

#####  VMAF
```
ffmpeg -y -i "{converted}" -i "{original}" -lavfi "[0:v]fps=fps={fps}[input0_0];[1:v]fps=fps={fps}[input1_0];[input0_0][input1_0]libvmaf=log_fmt=json:model_path={model}:log_path={log_path}:ssim=1:psnr=1:n_threads=4" -report -f null -
```
