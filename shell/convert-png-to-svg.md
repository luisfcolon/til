# Convert PNG to SVG

## Requirements

ImageMagick and Potrace

```bash
brew install imagemagick
brew install potrace
```

## Converting

Commands to run:

```bash
convert file.png file.pnm        # png to pnn
potrace file.pnm -s -o file.svg  # pnn to svg
```