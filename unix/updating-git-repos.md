# Updating git repos

At my current job, I work on several repos. Keeping them all up-to-date started to become tedious as the number of repos grew.

I coded this bash function to do it for me.

Most of the repos I work on have the common flow of `develop -> staging -> master`. Those repo names go into `declare -a repos` portion of the script.

Some of the repos only have a master branch. Those repo names go into the `declare -a master_only_repos` portion of the script.

## 
```bash
#!/usr/bin/env bash

. .messaging

update-work-repos() {
  repos_dir="$HOME/path/to/workfolder"

  declare -a repos=(
    "cool-repo-1"
    "cool-repo-2"
    "cool-repo-3"
    "cool-repo-4"
    "cool-repo-5"
    "cool-repo-6"
    "cool-repo-7"
  )

  declare -a master_only_repos=(
    "repo-with-only-master-1"
    "repo-with-only-master-2"
  )

  declare -a branches=(
    "master"
    "staging"
    "develop"
  )

  for repo in "${repos[@]}"
  do
    echo_header $repo

    pushd $repos_dir/$repo > /dev/null
    git stash --include-untracked > /dev/null

    for branch in "${branches[@]}"
    do
      echo_info $branch
      echo
      git checkout $branch
      git pull origin $branch
      git fetch --all > /dev/null
      echo
    done

    popd > /dev/null
    echo
  done

  for repo in "${master_only_repos[@]}"
  do
    echo_header $repo
    echo_info "master"

    pushd $repos_dir/$repo > /dev/null

    echo
    git stash --include-untracked > /dev/null
    git checkout master
    git pull origin master
    git fetch --all > /dev/null
    echo

    popd > /dev/null
  done
}
```

## Notes

### Messaging

The line that sources messaging:

```
. .messaging
``` 

can be found in my [.dotfiles](https://github.com/luisfcolon/dotfiles/blob/master/.dotfiles/.messaging) repo.

### Stashing untracked changes

I try not to run this until I check in and commit all of my work, in any of the branches that are going to be updated. I am human and sometimes I forget, so before each update, there is the line:

```
git stash --include-untracked > /dev/null
```

This will stash everything away, so the script won't have any errors.

Stashing untracked changes can, and most of the time will, have some issues when you try to `git stash apply`.