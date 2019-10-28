# bash4bioinformatics
Quick references to useful bash commands for bioinformatics


*Following lists frequently used bash commands for bioinformatics research. They are particularly useful to manupulate textual data in tabular form.*


===

### From tab-delimited file named xxx.bed, extract the 1st, 2nd, and 3rd columns
```
awk -F'\t' 'BEGIN {OFS="\t"}{print $1, $2, $3}' xxx.bed
```

### From tab-delimited file named xxx.gtf, extract rows with 3rd column named "exon"
```
awk -F'\t' 'BEGIN {OFS="\t"}{if($3=="exon") print $0}' xxx.gtf
```

### Skip the first row from xxx.txt
```
tail -n +2 xxx.txt
```

### Sort by 1st column then by 2nd column (numerically)
```
sort -k1,1 -k2,2n xxx.bed
```

### Simple for-loop to change extension of three files from *.txt to *.bed
```
for NAME in file1 file2 file3
do
	mv "$NAME".txt "$NAME".bed
done
```

### Remove quotes (") from xxx.txt
```
sed 's/"//g' xxx.txt
```

### From a folder, find all file names containing "MCF-7" and save the list of files as a text file
```
find '/path/to/files/' | grep MCF-7 > list_mcf7.txt
```

### From xxx.tsv find rows with the first column named "MYC"
```
grep -e "^MYC\t" xxx.tsv
```

### Find all files from subdirectorie and move them to current directory
```
find . -mindepth 2 -type f -print -exec gmv --backup=t {} . \;
```

### Delete subdirectories if empty
```
find . -mindepth 1 -type d -prune -print -exec rmdir {} \;
```
