# Split up a large into several files

### Splitting up the file

```bash
awk -vc=1 'NR % 50000 == 0 {++c} {print $0 > "large_filename_"c".txt"}' large_filename.txt
```

#### Notes:

* This will split `large_filename.txt` into smaller files with 50,000 lines each. Replace 50000 with the desired line count
* By default this will split by a newline `\n`
* The split up filenames will have the format: 
    * `large_filename_1.txt`
    * `large_filename_2.txt`
    * ...