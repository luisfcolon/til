# Convert HEIC to jpg or png

My personal use case is sharing photos from my phone to my laptop. They are saved as img.HEIC files - for whatever reason.

## Requirements

```bash
brew install imagemagick
```

## Converting

```bash
magick convert IMG_1234.HEIC new_image_name.jpg  # convert to jpg
magick convert IMG_1234.HEIC new_image_name.png  # convert to png
```

## Bulk converting

Note: This will remove the `.HEIC` file

```bash
for filename in *.HEIC; do base="${filename%.[^.]*}"; magick convert $filename $base.jpg; rm $filename; done
```
