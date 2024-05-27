```bash
#!/usr/bin/env bash

generate-password() {
  echo $(date +%s | sha256sum | base64 | head -c 30 ; echo)
}
```
