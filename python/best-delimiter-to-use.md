# Best delimiter to use

Choosing a delimiter to join a list into a string can be tricky. How can you 100% ensure the delimiter you choose will be unique? You can use [field seperators](https://en.wikipedia.org/wiki/C0_and_C1_control_codes#Field_separators).

```
chr(29).join(['a', 'b', 'c'])
```

You cannot see `chr(29)` if you were to print that.

`chr(29)` is the GROUP SEPERATOR symbol.
