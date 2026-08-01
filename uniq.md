# uniq

remove consecutive duplicate lines (input must be sorted)

    sort file.txt | uniq


count occurrences of each unique line

    sort file.txt | uniq -c


show only duplicate lines

    sort file.txt | uniq -d


show only lines that appear exactly once

    sort file.txt | uniq -u


