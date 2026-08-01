# ssh-keygen

generate an RSA public/private key pair

    ssh-keygen -t rsa -C "user@example.com"


copy public key to a remote machine (preferred method)

    ssh-copy-id -i ~/.ssh/id_rsa.pub user@remote.machine


copy public key to remote manually

    cat ~/.ssh/id_rsa.pub | ssh user@remote.machine "cat >> ~/.ssh/authorized_keys"


