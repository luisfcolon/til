# Split up a csv into several files

### Requirements

```bash
brew install parallel
```

### Splitting up the file

```bash
cat large_csv_filename.csv | parallel --header : --pipe -N 2000 'cat > smaller_csv_filename_{#}.csv'
```

#### Notes:

* `{#}` in the smaller csv filename is the index of the file. If the csv is split into two files:
    * `smaller_csv_filename_1.csv`
    * `smaller_csv_filename_2.csv`
* `parallel --header` maintains the CSV headers per file
* The number 2000 is the number of rows you want per file