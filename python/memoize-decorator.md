# Memoize decorator

This is a super duper simple memoize class. May not work for all cases. It is intended to decorate functions that are **[idempotent](https://en.wikipedia.org/wiki/Idempotence)**. 

My first use was for a restful GET api call using an id.

```python
class Memoize:
    def __init__(self, item):
        self.item = item
        self.cache = {}

    def __call__(self, *args):
        key = str(list(filter(None, args)))

        if key not in self.cache:
            self.cache[key] = self.item(*args)

        return self.cache[key]
```

Then in some other place

```
# import the Memoize class

@Memoize
def user_info(user_id)
    return client.get(f"https://someapiendpoint/users/{user_id})
```
 
