# tee

redirect output to both stdout and a file (append)

    date | tee -a filename


redirect output to both stdout and a file (overwrite)

    date | tee filename


write to multiple files at once

    echo "hello" | tee file1.txt file2.txt


