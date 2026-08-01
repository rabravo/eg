# screen

create a named screen session

    screen -S sessionName


create a named session and run a command inside it

    screen -S sessionName cmd arg1 arg2


detach from a running session

    Ctrl+A then D


list all screen sessions

    screen -ls


attach to a named session

    screen -r sessionName


kill a detached session by name

    screen -S sessionName -X quit


