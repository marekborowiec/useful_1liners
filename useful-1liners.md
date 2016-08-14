* Print only line number 101 in file:
```awk
awk 'NR==101' file
```
* Print lines 101-202 in file:
```awk
awk 'NR==101, NR==202' file
```
* Print header with column/field numbers in a tab-separated file:
```awk
awk -F "\t" '{ for (f=0; f<=NF; f++) print f":"$f; exit }' file
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
