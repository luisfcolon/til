# Cloning all repos from a github org

## Prequisites

### Log into GitHub

```bash
git auth login
```

### Shell script messaging

You will need to have this dotfile on your system and sourced:
[https://github.com/luisfcolon/dotfiles/blob/master/.dotfiles/.messaging](https://github.com/luisfcolon/dotfiles/blob/master/.dotfiles/.messaging)

## Code

```bash
#!/usr/bin/env bash

. .messaging

clone-all-repos() {
  echo_header "Fetching $1 repos"

  gh repo list $1 --limit 4000 | while read -r repo _; do
    echo_info "Cloning repo $1/$repo"
    gh repo clone "$repo" "$repo"
    echo ""
  done
}
```
