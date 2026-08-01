# tar

create a gzip-compressed archive

    tar -czf archive.tar.gz directory/


extract a gzip-compressed archive

    tar -xzf archive.tar.gz


extract to a specific directory

    tar -xzf archive.tar.gz -C /target/dir/


list contents of an archive without extracting

    tar -tzf archive.tar.gz


create an uncompressed archive

    tar -cf archive.tar directory/


extract a specific file from an archive

    tar -xzf archive.tar.gz path/to/file.txt


create a bzip2-compressed archive

    tar -cjf archive.tar.bz2 directory/


