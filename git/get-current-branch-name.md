# Getting the current branch name

```bash
$ cd /path/to/some/repo
$ git checkout TIX-123-some-amazing-work
$ git rev-parse --abbrev-ref HEAD
TIX-123-some-amazing-work

$ git checkout master
$ git rev-parse --abbrev-ref HEAD
master
```