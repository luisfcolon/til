# Converting fonts

Convert `.ttf` and `.otf` fonts to `.woff` and `.woff2` formats.

## Requirements:

Clone the following repos and follow their directions. Copy the files created from any `make` commands to `/usr/local/bin`. You will need to have `/usr/local/bin` in your `$PATH`.

* https://github.com/bramstein/sfnt2woff-zopfli
* https://github.com/google/woff2

## Instructions


### Creating .woff

`fonts` is the directory where the fonts are located

```
cd fonts
find . -name '*.otf' -exec sfnt2woff-zopfli {} \;
```

### Creating .woff2

`fonts` is the directory where the fonts are loca
ted

```
for file in fonts/*.otf; do woff2_compress "$file"; done
```

### Notes

* `.woff` files can be slow to generate
* This will create the same font names with new extensions.
    * Example: `MyFont.otf` will become `MyFont.woff` and `MyFont.woff2`

## Todo

* Be able to generate both `.woff` and `.woff2` at the same time.
* Select an output directory
* Allow custom new font names
* Better CLI tool?
* Electron app?
* React app?
