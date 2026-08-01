# ssh

connect to a remote machine

    ssh user@remote.machine


connect through a proxy (jump host)

    ssh -J proxy.user@proxy.machine user@target.machine



# SSH Tunnel

forward local port 2222 to remote port 22 (copy files via tunnel)

    ssh -v -4 -L 2222:localhost:22 user@target.machine -N -f


forward local port to a remote postgres server on port 5432

    ssh -v -4 -L 2222:localhost:5432 user@db.target.machine -N -f


check if remote postgres is accepting connections through tunnel

    pg_isready -h localhost -p 2222


copy file from remote to local through tunnel

    scp -P 2222 user@localhost:/remote/file /local/path


copy file from local to remote through tunnel

    scp -P 2222 /local/file user@localhost:/remote/path



# Proxy Jump via Config

add to ~/.ssh/config

    Host target.machine
      User         target.user
      HostName     target.machine
      ProxyCommand ssh proxy.user@proxy.machine nc %h %p 2>/dev/null


