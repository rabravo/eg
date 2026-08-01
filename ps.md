# ps

show all running processes

    ps aux


show processes for the current user

    ps -u $USER


show a process tree

    ps auxf


find a process by name

    ps aux | grep python


show processes sorted by memory usage

    ps aux --sort=-%mem | head -10


show processes sorted by CPU usage

    ps aux --sort=-%cpu | head -10


