# Convert HEIC to jpg or png

My personal use case is sharing photos from my phone to my laptop. They are saved as img.HEIC files - for whatever reason.

```unix
# install imagemagick
brew install imagemagick

# convert to jpg
magick convert IMG_1234.HEIC new_image_name.jpg

# convert to jpg
magick convert IMG_1234.HEIC new_image_name.png
```