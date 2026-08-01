# find

find all .py files under current directory

    find . -name "*.py"


find files modified in the last 7 days

    find . -mtime -7d


find and delete all .DS_Store files

    find . -name ".DS_Store" -delete


find empty files

    find . -type f -empty


find files larger than 100MB

    find . -type f -size +100M



# Custom Examples

Find files by extension, case-insensitive:

    find . -iname "*.jpg"


Find files modified more recently than a reference file:

    find . -newer reference.txt


Find directories only, excluding hidden:

    find . -type d -not -name ".*"


Find and print full path of files owned by current user:

    find . -user $USER -type f -print


Find files with specific permissions:

    find . -type f -perm 644


