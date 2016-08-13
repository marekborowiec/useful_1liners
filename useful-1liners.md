* Print only line number 101:
```awk
awk 'NR==101'
```
* Print header with column/field numbers in a tab-separated file:
```awk
awk -F "\t" '{for (f=0; f<=NF; f++) print f":"$f; exit }' file
```