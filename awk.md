# awk

print the second field of each line (space-delimited)

    awk '{print $2}' file.txt


print lines where the third field is greater than 100

    awk '$3 > 100' file.txt


print the number of fields in each line

    awk '{print NF}' file.txt


sum all values in the first column

    awk '{sum += $1} END {print sum}' file.txt


use a custom field delimiter (comma)

    awk -F, '{print $1}' file.csv


print lines matching a pattern

    awk '/error/' file.txt


print line numbers alongside output

    awk '{print NR, $0}' file.txt


