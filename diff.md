# diff

compare two files line by line

    diff file1.txt file2.txt


show a unified diff (more readable, used in patches)

    diff -u file1.txt file2.txt


ignore whitespace differences

    diff -w file1.txt file2.txt


compare two directories recursively

    diff -r dir1/ dir2/


create a patch file

    diff -u original.txt modified.txt > changes.patch


apply a patch

    patch original.txt < changes.patch


