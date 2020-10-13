# Recording screenshots and videos in UnityMol
----------

## Screenshot

UnityMol provides a simple way to capture a screenshot using the command line or with the "Save Image" button:

```python
screenshot("/path/to/capture.png", 1920, 1080, transparentBG=False)
```
You can define the size of the image you want to render by changing the resolution width and height.

Note: recording pictures with transparent background takes more time than a simple capture.


## Video

The video recording in UnityMol is based on FFMPEG and this [repo](https://github.com/keijiro/FFmpegOut).
Parts of FFMPEG is licensed under the GPL. See [this page](https://www.ffmpeg.org/legal.html).

The rendered video has a fixed resolution and framerate that you can set from the APIPython command. 

```python
startVideo("/path/to/captureVid.mp4", 1920, 1080, 30)
#...
stopVideo()
```

One can pause and unpause the video to perform some actions (moving molecules / changing representations / loading ...) without recording the intermediate states.

```python
pauseVideo()
unpauseVideo()
```

One can also combine the pause/unpause features with coroutines to wait for certain amount of time or frames. See an example [here](https://github.com/bam93/fair_covid_molvisexp/blob/master/ex2_binding_sites/UMolCovid_ligands.py)

