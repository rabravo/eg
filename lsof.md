# lsof

find the process ID (PID) using a port

    lsof -i:<port>


find dynamic libraries used by a running process

    lsof -p <PID>


find processes accessing a folder or mounted device

    lsof +f -- /path/to/folder


list default file descriptors (stdin, stdout, stderr) for current process

    lsof -a -p $$ -d 0,1,2


