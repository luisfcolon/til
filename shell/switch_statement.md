# Bash Switch Statement (case)

Use `case` to branch on a variable. Cleaner than a chain of `if/elif` when matching multiple patterns.

```bash
case $BRANCH in
  develop)
    echp "develop env"
    ;;
  staging)
    echo "staging env"
    ;;
  main|master)
    echo "prod env"
    ;;
  *)
    echo "default / fallback"
    ;;
esac
```
