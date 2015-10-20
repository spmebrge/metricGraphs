In order to gather the runtimes from the Time.txt file, make sure that the newline is removed from it first) and then run the following commands.


awk -v col=3 '{if(NR%col){printf "%s ",$0 }else {printf "%s\n",$0}} ' Time.txt | awk '{ print $1 "\t" $3 "\t" $5}' > TimeParsed.txt


Once have the data in the format :

22_32_1 1m28.788s       1m13.682s

RUN:
awk '{split($2, a,"s"); split(a[1],first,"m"); split($3, b, "s"); split(b[1], second, "m"); print $1 "\t" first[1] "\t" first[2] "\t" second[1] "\t" second [2];}' TimeParsed.txt > MSParse.txt

to achieve:

22_32_1 1       28.788  1       13.682


Then That file can be set into columns
awk -v col=4 '{if(NR%col){printf "%s ",$0 }else {printf "%s\n",$0}} ' MSParse.txt


These can then be placed into libreoffice for further data analysis.







For the data without pin

awk '{split($2, a,"s"); split(a[1],first,"m"); print $1 "\t" first[1] "\t" first[2];}' TimeNoPin.txt > TimeParsed.txt

awk -v col=8 '{if(NR%col){printf "%s ",$0 }else {printf "%s\n",$0}} ' TimeParsed.txt | awk '{ print $1 "\t" $3 "\t" $4 "\t" $5 "\t" $7 "\t" $8 "\t" $9 "\t" $11 "\t" $12 "\t" $13 "\t" $15 "\t" $16}'

