# Full Jitter Backoff for Retries

Adds randomness to exponential backoff so retrying clients don't all hit the server at the same time.

```python
import random
import time

# attempts = current retry count
# backoff  = base wait time in seconds (e.g. 1.0)
time.sleep(backoff * (2 ** attempts) + random.uniform(0, 0.1))
```
