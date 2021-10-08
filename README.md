# In progress project -  do not rely on this project!

**Update 2021-10-08**: If you are experiencing difficulties with pybind, you may need to fully qualify the `module` (`::pybind11::module`).

**Update 2021-09-30**: Dependency managemend while testing out different libraries is not very easy, so those changes will not be pushed here. I would like to do the decoding on the python side, but as far as I understand is that I am missing additional headerinfo for the decoding to work. Otherwise it is just bytestream-kauderwelsch.

**Update 2021-09-22**: I am trying to find an easy way to decode the frames without too much software bloat.

# UnrealReceiver
C++ WebRTC Bridge for Unreal Engine PixelStreaming

Unreal Engine released PixelStreaming with its 4.27 version. I want to be able to receive the images and use them as 2D numpy arrays for batch assembly in machine learning.
To test this project, you need to have a PixelStreaming project running in the background.

For my testing purposes, I have a very simple project of the player pawn following a spline, rendered in only 1024x768@30FPS s.t. my computer doesn't notice it much.

Many aspects are still hardcoded as this project is in progress. The ultimate goal is to use this bridge as a lightweight programm informing Pytorch or Tensorflow batches on our compute cluster.

## Progress so far

I have, with the help of Tensorworks' WebRTC Bridge (https://github.com/TensorWorks/Unreal-PixelStreaming-RTP-Bridge), libdatachannel (subproject), and the Unreal Engine PixelStreaming sample, implemented this repo so far.
I have introduced Python bindings for the functions so that I can easier prototype decoding.
I can verify, with the relay over the old winsocket, that the frames are received as planned.

## Open Issues

While I am getting the frames as I expect, I cannot decode them.
I have tried saving the frames in files and decoding with multiple settings using ffmpeg, but to no avail (I assume this is because I need some h264 metainfo).
GStreamer can decode the packages over the relay, but simply concatenating the rtp bodies does not seem to do the trick.

The winsocket really needs to be removed and/or exchanged with something that runs on linux as well.

## Collaboration

I would greatly appreciate help with this project. It is an integral part of my thesis, but not the main focus of it.
I am working in Berlin time and will respond during work hours when I can spare time.

## Legal Details

I would like to acknowledge funding provided by the German government to the Gauss Centre for Supercomputing via the InHPC-DE project (01—H17001).


