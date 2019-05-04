# Search and replace

Replaces each occurence of `string` to `newstring`. This includes substrings.

```vim
:%s/string/newstring/g
```

Same as above but for the current line only.

```vim
:s/string/newstring/g
```

Replaces each occurence of `string` to `newstring`. It asks for confirmation first (_love this one_)

```vim
:%s/string/newstring/gc
```

This will only change `string` to `newstring` on whole word matching, no substrings. It asks for confirmation first.

```vim
:%s/\<string\>/newstring/gc
```

Changes `string` to `newstring` for lines 5 - 12

```vim
:5,12s/string/newstring/g
```

Changes `string` to `newstring` from the current line to the end of the file.

```vim
:.,$s/string/newstring/g	
```

## Notes

### At the end

* Adding `c` to the end of the search and replace command adds the confirmation prompts before any changes are done.
* Adding `I` to the end makes the search case sensitive






