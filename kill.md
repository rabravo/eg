# kill

send SIGTERM (graceful shutdown) to a process by PID

    kill 1234


force-kill a process that won't terminate (SIGKILL cannot be caught or ignored)

    kill -9 1234


send a signal by name

    kill -SIGTERM 1234


kill a shell job by job spec instead of PID

    kill %1


list all available signal names and numbers

    kill -l


look up the name for a signal number

    kill -l 9


send SIGHUP (reload config) to a process

    kill -1 1234


pause and resume a process

    kill -SIGSTOP 1234
    kill -SIGCONT 1234


kill all processes matching a name

    killall python


kill by name with pkill

    pkill firefox


find a PID by name, then kill it

    pgrep python
    kill 4567


kill a process by port

    kill $(lsof -t -i:8080)


kill all background jobs in the current shell

    kill $(jobs -p)


send a signal to an entire process group (negative PID)

    kill -15 -1234


