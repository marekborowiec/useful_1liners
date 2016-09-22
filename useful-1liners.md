* Print only line number 101 in file:
```awk
awk 'NR==101' file
```
* Print lines 101-202 in file:
```awk
awk 'NR==101, NR==202' file
```
* Print every 4th line in a file:
```awk
awk '0 == NR % 4' file
```
* Print header with column/field numbers in a tab-separated file:
```awk
awk -F "\t" '{ for (f=1; f<=NF; f++) print f":"$f; exit }' file
```
* Rename multiple files (`/bin/sh` executes):
```awk
ls * | awk '{ print "mv "$1" "$1 }' | sed 's/to_replace/replace_with/2' | /bin/sh
```
* Remove duplicate, nonconsecutive lines (no need to sort first):
```awk
awk '!a[$0]++' file
```
* Put every other line next to the one above, separated by `tab`:
```awk
awk 'ORS=NR%2 ? "\t" : "\n"' file
```
* Print section of file between two regexes:
```awk
awk '/regex1/, /regex2/' file
```
* Print average of third column:
```awk
awk '{ sum += $3 } END { if (NR > 0) print sum / NR }' file
```
* Sort on 3rd column, then print fields 2 through 5 of a tabular file, and align output:
```bash
sort -nk 3 file | cut -f 2-5 | column -t
```
