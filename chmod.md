# chmod

give read+execute permission recursively to all (owner, group, others)

    chmod -R a+rX directoryname


make a script executable

    chmod +x script.sh


set exact permissions (owner=rwx, group=rx, others=rx)

    chmod 755 script.sh



# Flags

    -R    recursive
    a     all (owner + group + others)
    +     add permission if not already set
    r     read
    X     directories only (lowercase x applies to files too)


