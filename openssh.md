# openssh

copy a file from remote to local

    scp user@host:/remote/path/file.txt /local/path/


copy a file from local to remote

    scp /local/path/file.txt user@host:/remote/path/


copy a directory recursively

    scp -r user@host:/remote/dir/ /local/dir/


open an interactive SFTP session

    sftp user@host


copy your public key to a remote host for passwordless login

    ssh-copy-id user@host


copy a specific key to a remote host

    ssh-copy-id -i ~/.ssh/id_ed25519.pub user@host


start the SSH agent and add your key

    eval "$(ssh-agent -s)"
    ssh-add ~/.ssh/id_ed25519


list keys loaded in the SSH agent

    ssh-add -l


generate a new ed25519 key pair

    ssh-keygen -t ed25519 -C "your_email@example.com"


test an SSH connection without opening a shell

    ssh -T user@host


run a single command on a remote host

    ssh user@host "df -h"



# ~/.ssh/config

define a reusable host alias

    Host myserver
      HostName      192.168.1.10
      User          alice
      IdentityFile  ~/.ssh/id_ed25519
      Port          2222


use a jump host (bastion)

    Host internal
      HostName      10.0.0.5
      User          alice
      ProxyJump     bastion.example.com


enable connection reuse to speed up repeated connections

    Host *
      ControlMaster     auto
      ControlPath       ~/.ssh/sockets/%r@%h:%p
      ControlPersist    10m


