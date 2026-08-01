# script

record a terminal session to a file (default: typescript)

    script


record with timing info for replay

    script -t 2>timing.log session.log


replay a recorded session

    scriptreplay timing.log session.log



# Real-time Pipe

create a named pipe and stream session output into it

    mkfifo out
    script -f out


a remote user can watch the session live

    cat out


