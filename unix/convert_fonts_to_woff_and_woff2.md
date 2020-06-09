# Converting fonts

Convert `.ttf` and `.otf` fonts to `.woff` and `.woff2` formats.

## Requirements:

* https://github.com/bramstein/sfnt2woff-zopfli
* https://github.com/google/woff2

## Instructions

`sfpro` is the directory where the fonts live

### Creating .woff

```
find . -name '*.otf' -exec sfnt2woff-zopfli {} \;
```

### Creating .woff2

```
for file in sfpro/*.otf; do woff2_compress "$file"; done
```
