# Best delimiter to use

Choosing a delimiter to join strings can be tricky. How can you 100% ensure the delimiter you choose will be unique?

```
chr(29).join(['a', 'b', 'c'])
```

You cannot see `chr(29)` if you were to print that.

`chr(29)` is the GROUP SEPERATOR symbol. Read more about them here:

[Field Seperators via Wiki](https://en.wikipedia.org/wiki/C0_and_C1_control_codes#Field_separators)