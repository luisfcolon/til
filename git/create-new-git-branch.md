# Bash function to create a new git branch

## Code

```bash
#!/usr/bin/env bash

slugify() {
  echo "$1" | iconv -t ascii//TRANSLIT | sed -E 's/[~\^]+//g' | sed -E 's/[^a-zA-Z0-9]+/-/g' | sed -E 's/^-+\|-+$//g' | tr A-Z a-z
}

cb() {
  local description=$(slugify $2)
  default_branch="develop"

  if [ -z "$3" ]; then
    gc -b $1-${description} origin/$default_branch
  else
    gc -b $1-${description} origin/$3
  fi
}
```

## Usage

I got bored having to do this by hand all of the time. Running this is super simple:

### Default

```bash
cb JIRA-123 'Descrition of the work this branch has'
```

Will result in the branch `JIRA-123-descrition-of-the-work-this-branch-has` that has `edge` as the origin.

### Using another origin

If you need to create a branch using another origin (staging/master) then use the command:

```bash
cb JIRA-123 'Descrition of the work this branch has' staging

# or

cb JIRA-123 'Descrition of the work this branch has' master
```
