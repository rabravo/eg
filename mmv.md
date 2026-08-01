# mmv

rename *.jpeg to *.jpg

    mmv '*.jpeg' '#1.jpg'


add a prefix to all .txt files

    mmv '*.txt' 'prefix_#1.txt'


move all .log files into a subdirectory

    mmv '*.log' 'logs/#1.log'


rename using two wildcards

    mmv 'foo*bar*' 'new#1baz#2'


dry run — print what would happen without doing it

    mmv -n '*.jpeg' '#1.jpg'


copy instead of move

    mmv -c '*.txt' 'backup/#1.txt'


create symlinks

    mmv -s '*.txt' 'links/#1.txt'


strip a common prefix

    mmv 'prefix_*' '#1'


change case (lowercase) using a shell loop workaround (mmv is case-sensitive)

    mmv '[A-Z]*' '#1'


