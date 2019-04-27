# Undo a git rebase

`git reflog` will output something like:

```
6eca582 HEAD@{0}: reset: moving to HEAD
6eca582 HEAD@{1}: rebase -i (finish): returning to refs/heads/dev/some-branch
6eca582 HEAD@{2}: rebase -i (start): checkout some-branch
6eca582 HEAD@{3}: commit: S
b3bfebb HEAD@{4}: commit: This is the commit I want to go back to
6d7d093 HEAD@{5}: rebase -i (finish): returning to refs/heads/dev/some-branch
```

To go back to a previous commit after a rebase:

```
git reflog

git reset --hard HEAD@{4}
```