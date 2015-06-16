## Prerequisites ##
Most how-to's here use ffmpeg or mencoder. While ffmpeg is part of the standard ubuntu repositories, mencoder requires Medibuntu repositories.

```
sudo apt-get install ffmpeg mencoder
```

## How to Extract audio from mpeg files ##
```
ffmpeg -i file.mpg -f mp3 newfile.mp3
```

## MXF to MPEG-2 with Stereo Audio ##
```
ffmpeg -i file.mxf -vcodec copy -acodec mp2 -ac 2 output.mpg
```

## How to rebuild AVI Index ##
```
mencoder -idx input.avi -ovc copy -oac copy -o output.avi`
```


## How to convert RealMedia (.rm) to Audio Video Interleave (.avi) ##
```
mencoder FILE1.rm -ovc lavc -oac mp3lame -o FILE2.avi
```

## How to convert .flv to .mpg ##
Basic (use ffmpeg defaults):
```
ffmpeg -i original_file.flv new_file.mpg
```
to use more advanced settings check the [list of endless options](http://www.ffmpeg.org/ffmpeg.html#SEC5). For dvd output quality you can use short hands like:
```
ffmpeg -i original_file.flv -target dvd new_file.mpg
```
The most important settings explained:
```
ffmpeg -i original_file.flv -ab 56 -ar 22050 -b 500 -s 320×240 new_file.mpg

 -b bitrate: set the video bitrate in kbit/s (default = 200 kb/s)
 -ab bitrate: set the audio bitrate in kbit/s (default = 64)
 -ar sample rate: set the audio samplerate in Hz (default = 44100 Hz)
 -s size: set frame size. The format is WxH (default 160×128 )
```

## Youtube Video Download with Clipgrab ##
Clipgrab is an easy to use Video Downloader for Youtube
Clipgrab installation:
```
sudo add-apt-repository ppa:clipgrab-team/ppa
sudo apt-get update
sudo apt-get install clipgrab
```

## How to convert jpeg to pdf ##
Using ImageMagick in the images folder:
```
convert *.jpg document.pdf
```
or
```
convert *.jpg +compress document.pdf
```

## How to extract images from pdf ##
Using pdfimages the images will be numbered (i.e. image-xxx.filetype)
```
pdfimages -j file.pdf ./folder/image
```