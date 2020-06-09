# Converting fonts

Convert `.ttf` and `.otf` fonts to `.woff` and `.woff2` formats.

## Requirements:

* https://github.com/bramstein/sfnt2woff-zopfli
* https://github.com/google/woff2

## Instructions

Clone the above repos and follow their directions. Copy the files created from the `make` commands to `/usr/localbin`

### Creating .woff

`fonts` is the directory where the fonts are located

```
cd fonts
find . -name '*.otf' -exec sfnt2woff-zopfli {} \;
```

### Creating .woff2

`fonts` is the directory where the fonts are located

```
for file in fonts/*.otf; do woff2_compress "$file"; done
```

### Notes

This will create the same font names with new extensions.

* Example: `MyFont.otf` will become `MyFont.woff` and `MyFont.woff2`

## Todo

* Be able to generate both `.woff` and `.woff2` at the same time.
* Select an output directory
* Allow ability to change the new font names
