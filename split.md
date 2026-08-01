# split

split a file into fixed-size chunks

    split -b 1G archive.tar.gz archive_part_


split into exactly N pieces

    split -n 10 archive.tar.gz archive_part_


split with numeric suffixes instead of letters

    split -b 1G -d archive.tar.gz archive_part_


split with longer suffix to support many chunks

    split -b 500M --suffix-length=3 archive.tar.gz archive_part_


reassemble chunks into original file

    cat archive_part_* > archive.tar.gz


reassemble numeric suffixes explicitly (when order must be guaranteed)

    cat archive_part_00 archive_part_01 archive_part_02 > archive.tar.gz


reassemble and extract without writing to disk

    cat archive_part_* | tar xzf -


create a tar archive and split it in one command (no full archive on disk)

    tar czf - /path/to/dir | split -b 1G - archive_part_


split an existing tar file into chunks

    split -b 1G archive.tar.gz archive_part_


stream tar to remote server with no local disk usage

    tar czf - /path/to/dir | ssh user@remote "cat > /remote/path/archive.tar.gz"


extract directly on remote with no archive file anywhere

    tar czf - /path/to/dir | ssh user@remote "tar xzf - -C /remote/path/"


verify reassembled archive integrity before extracting

    cat archive_part_* | tar tzf - > /dev/null && echo "OK"


