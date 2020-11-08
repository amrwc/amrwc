# Converting

Using ImageMagick and FFmpeg.

```console
brew install ffmpeg imagemagick
```

## GIF to GIF with loss of quality

The `-fuzz` option does most of the colour compression. Adjust the value to try
out different results.

```console
# thinking.gif (2.6MB) -> thinking2.gif (874KB)
convert thinking.gif -coalesce -fuzz 10% +dither -layers Optimize +map thinking2.gif
```

Source: <https://imagemagick.org/discourse-server/viewtopic.php?p=130527&sid=65ab5b007e15da3e7e0e33b1e2277936#p130527>

## GIF to MP4

```console
# thinking.gif (2.6MB) -> thinking.mp4 (150KB)
ffmpeg -i thinking.gif -movflags faststart -pix_fmt yuv420p -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" thinking.mp4
```

Source: <https://unix.stackexchange.com/a/294892>
