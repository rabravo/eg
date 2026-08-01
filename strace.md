# strace

trace all system calls made by a command

    strace ls


attach to a running process by PID

    strace -p 1234


count and summarize system calls

    strace -c ls


filter to specific system calls

    strace -e trace=open,read ls


follow child processes (useful for shells and scripts)

    strace -f bash script.sh


save trace output to a file

    strace -o trace.log ls


show timestamps for each system call

    strace -t ls


show time spent in each system call

    strace -T ls


trace only file-related system calls

    strace -e trace=file ls


trace network-related calls

    strace -e trace=network curl example.com


