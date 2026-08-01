# lftp

connect interactively

    lftp sftp://user@host

connect with a specific port

    lftp sftp://user@host:2222

upload a single file

    lftp -e "put local.css -o /remote/path/local.css; bye" sftp://user@host

upload multiple files

    lftp -e "mput *.html; bye" sftp://user@host:/remote/path/

download a single file

    lftp -e "get /remote/path/file.txt -o ./file.txt; bye" sftp://user@host

mirror local dir to remote (push)

    lftp -e "mirror -R ./local/ /remote/path/; bye" sftp://user@host

mirror remote dir to local (pull)

    lftp -e "mirror /remote/path/ ./local/; bye" sftp://user@host

dry run before mirroring

    lftp -e "mirror -R -n ./local/ /remote/path/; bye" sftp://user@host

mirror only newer files (skip unchanged)

    lftp -e "mirror -R --only-newer ./local/ /remote/path/; bye" sftp://user@host

mirror and delete files on remote not present locally

    lftp -e "mirror -R --delete ./local/ /remote/path/; bye" sftp://user@host

inside interactive shell: navigate and transfer

    lcd /local/path       # change local directory
    lpwd                  # print local working directory
    cd /remote/path       # change remote directory
    ls                    # list remote files
    put file.css          # upload file
    get file.css          # download file
    mirror -R src/ dst/   # push tree
    bye                   # exit

run local shell commands with ! prefix (lls does not exist)

    !ls                   # list local files
    !pwd                  # print local working directory
    !cat file.txt         # read a local file

run a script file

    lftp -f script.lftp
