# Removing rows from files

I recently had the task of taking the first 100 rows from a large file and creating a new file with them. I then had to remove those rows from the original file. My IDE's have all kinds of crazy `on save` formatting so I needed to do it via the terminal.

## Get first 100 rows

Get the first 100 rows of a file and save them into a new file:

```
head -100 some_file.json > new_file_with_100_rows.json
```

## Remove first 100 rows

Now we want to remove the first 100 rows

```
tail -n +100 some_file.json > some_file_without_first_100_rows.json
```