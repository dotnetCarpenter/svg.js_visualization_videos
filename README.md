Get the svg.js repo
===================

`git submodules update`


Commands for Gource
===================

### To get the caption log data from git:

```
cd svg.js && git log --no-walk --tags --pretty="%at|%an released version %D" | sort
```

### To create a video

```
gource -r 25 --file-filter node_modules -c 4.0 --multi-sampling --logo logo-svg-js-01d-128.png --caption-file gource.caption.txt svg.js/
```

### To save a video via pipe (ffmepg)

```
gource -r 25 --file-filter node_modules -c 4.0 --multi-sampling --logo logo-svg-js-01d-128.png - svg.js/ | ffmpeg -y -r 25 -f image2pipe -vcodec ppm -i - -vcodec libx264 -preset ultrafast -pix_fmt yuv420p -crf 1 -threads 0 -bf 0 svg_history.mp4
```
