# rename

rename files by substituting a pattern (Perl rename / prename)

    rename 's/old/new/' *.txt


rename to lowercase

    rename 'y/A-Z/a-z/' *


add a prefix to all .jpg files

    rename 's/^/prefix_/' *.jpg


add a suffix before the extension

    rename 's/\.txt$/_backup.txt/' *.txt


remove spaces from filenames

    rename 's/ /_/g' *


dry run — print what would be renamed without doing it

    rename -n 's/old/new/' *


rename a sequence of numbered files (zero-pad to 3 digits)

    rename 's/(\d+)/sprintf("%03d",$1)/e' *.png


strip a common prefix

    rename 's/^prefix_//' *.txt


change file extension from .jpeg to .jpg

    rename 's/\.jpeg$/.jpg/' *.jpeg


