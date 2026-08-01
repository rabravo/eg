# cut

extract columns 3 through 9 from a comma-delimited file

    cut --delimiter=, -f3-9 input.csv > output.csv


extract the first field from a colon-delimited file (e.g. /etc/passwd)

    cut -d: -f1 /etc/passwd


extract characters 1-10 from each line

    cut -c1-10 file.txt


