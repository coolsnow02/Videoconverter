VideoConverter
==============

VideoConverter gem is used for video processing .It makes use of ffmpeg command and streamio-ffmpeg wrapper for reading metadata and transcoding videos.It is used for providing basic functionalities related to video such as:
* Bit-rate
* Resolution
* Thumbnail
* Split
* Cut
* Format conversion

Dependencies: 
------------
Ruby:
ruby 2.0.0

ffmpeg:
ffmpeg-2.5.3

streamio-ffmpeg:
streamio-ffmpeg 1.0.0.

Installation:
------------
ffmpeg installation is given in install.sh file
```Shell
(sudo) gem install videoconverter
```
Supported Formats:
-----------------

|Extensions|
|----------|
|.avi      | 
|.mp4      |  
|.wav      | 
|.mov      |  
|.m4a      | 
|.mkv      | 
|.ogg      |


Usage:
-----
Require the gem

``` ruby
require 'videoconverter'
```

#### resolution(width,height)
Resize the video according to resolution

* Example:

``` ruby
"actions": {"resolution": "320x240"}
```

#### split(no.of parts)
Splitting videos in equal parts

* Example

``` ruby
"actions": {"split": 3 }
```

#### thumbnail(time)
Thumbnail provides an image according to time

* Example

``` ruby
"actions": {"thumbnail": 10}
```

#### bitrate(no.of kilobits per second)
Bitrate of video gives number of kilobits per second

* Example

``` ruby
"actions": {"video_bitrate": 92}
```
#### cut(start_time,end_time)
Cuts the video from given start time to given end time

* Example

``` ruby
"actions": {"cut": "00:00:10-00:01:10"}
```
####ext(extension)
Extension provides a given extension to the video

* Example

``` ruby
 "actions": {"ext": ".avi"}
```

* Example for processing video
``` ruby
request = {"source_url": "http://download.wavetlan.com/SVV/Media/HTTP/MP4/ConvertedFiles/Media-Convert/Unsupported/test7.mp4",
  "actions": 
  {
    "resolution"    : "320x240",
    "video_bitrate" : 92,
    "thumbnail"     : 20,
    "split"         : 3,
    "cut"           : "00:00:10-00:01:10",
    "ext"           : ".avi"
  },
  "directory": "/home/webonise/jobs/"}
VideoConverter.process(request)
```