## Introduction ##
This how to is written for an ipod nano video 2nd generation device. It should be adaptable to other ipods easily.

## Encode and Copy Videos ##
  1. update libgpod to work with gtkpod, rhythmbox et al.:
> > [ftp://64.22.103.45/packages/ubuntu/gutsy/libgpod/libgpod2_0.5.3+actually0.6.0-0.1_i386.deb](ftp://64.22.103.45/packages/ubuntu/gutsy/libgpod/libgpod2_0.5.3+actually0.6.0-0.1_i386.deb)
  1. how to encode videos for your ipod
    * add medibuntu repositories: https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f
    * install ffmpeg (or upgrade to the latest version from medibuntu)
    * install gpac
    * get the pypodconf script (the one for gutsy SVN ffmpeg4 seemed to work better) https://help.ubuntu.com/community/iPodVideoEncoding#head-ebb27b589cb5a6aa0c7fca5837cb0e0eb76b1909
    * now you can encode about any movies and transfer them with gtkpod to your ipod
    * create a playlist on your ipod within gtkpod (name it "video" or similar")
    * you can now copy video files via gtkpod to your ipod
    * have fun