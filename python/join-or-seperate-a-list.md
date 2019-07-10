# Join a list

```python
names = ['Luis', 'John', 'Jason', 'Belkis']

# Map with lambda
chr(10).join(list(map(lambda x: f'{x[1]}', enumerate(names))))

>>> 'Luis\nJohn\nJason\nBelkis'

# Or list comprehensions. This is faster
chr(10).join([x[1] for x in enumerate(names)])

>>> 'Luis\nJohn\nJason\nBelkis'
```

### Notes

* `chr(10)` is a newline
* `chr(10).join([1,2,3))` will throw an error