# wc

count lines, words, and characters in a file

    wc file.txt


count only lines

    wc -l file.txt


count only words

    wc -w file.txt


count only characters

    wc -c file.txt


count lines across multiple files

    wc -l *.py


count lines from stdin

    cat file.txt | wc -l


