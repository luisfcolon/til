# Creating a rolling release

Put the following code in a script called `rolling-releases` and save it in `/usr/local/bin`

```bash
#!/usr/bin/env bash

git checkout main
git pull origin main
git fetch --all
version=`git tag | sort -V | tail -1`
major=`echo $version | cut -d. -f1`
git tag -d $major
git tag $major
git push --tag --force origin $major
```
