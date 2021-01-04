# shell-one-liner
Some *funny* one liner that I encounter and used daily ;)
---
Updated Jan . 2021



## REMOVE 1ST LINE IN THE FILE
```
sed '1d' GenoRealAUS-50k_compbio.txt > test_genos
tail -n +2 GenoRealAUS-50k_compbio.txt > test_genos
``` 

## REPLACE A SPECIFIC CHARACTER ON A SPECIFIC COLUMN (in this case, delete the -
```
gawk '{gsub("-","",$4)}1' 9913_ARS1.2_777962_HD_marker_name_180910.map | sed 's/ /\t/g' > tempHD
```

## APPEND A LINE ON TOP OF THE COMMAND
```
gawk 'BEGIN {print "ID Chip Calls..."}; {print $0}' genotype_FINAL.txt > temp0

```

## DISPLAY THE FIRST 30 CHARACTER IN 1ST LINE
```
head -n 5 test_genos | cut -c-30

```

## COMMAND TO SWITCH FROM FIMPUTE TO COMP-BIO ASCII
```
gawk 'NR>1 {printf "%s ", $1 ;{ for(i=1;i<=length($3);i++) {if(i!=length($3)) printf "%s ",substr($3,i,1); else if(i==length($3)) printf "%s\n",substr($3,i,1) }}}' file.gen 
```

## Check columns and print 
```
gawk '{if($3=="I" || $4=="I") print $3"_"$4 }'file.txt | sort | uniq

```
## Remove all comments
```
grep -v ^\# test.txt | grep  .

```
## Remove last character
```
sed 's/.$//' test.txt
```

## Lookup & find duplication
```
gawk '{print $1}' file.txt | uniq -D

```
## Check if any of the col has fewer than 5 columns
```
gawk -F'\t' 'NF!=5 {print}' infile  > newfile

```
## Remove SPACE at the end of each line
```
sed 's/ *$//' > masterkey.txt

```

## will print any line where the third field contains Foo. (Changing print $0 to print $3 would print only that third field)
```
awk -F';' '$3 ~ /Foo/ { print $0 }' file.txt

```

