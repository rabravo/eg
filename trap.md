# trap

run a cleanup command when the script exits (any exit, including errors)

    trap 'rm -f /tmp/myfile' EXIT


run a command on Ctrl+C (SIGINT)

    trap 'echo "interrupted"; exit 1' INT


handle multiple signals with one handler

    trap 'cleanup' INT TERM EXIT


ignore a signal

    trap '' INT


reset a signal to its default behavior

    trap - INT


list all currently active traps

    trap -p


list all signal names and numbers

    trap -l


cleanup temporary directory on exit

    tmpdir=$(mktemp -d)
    trap 'rm -rf "$tmpdir"' EXIT


print a message and exit cleanly on Ctrl+C

    trap 'echo; echo "caught SIGINT, exiting"; exit 130' INT


re-raise a signal after cleanup (restore default, then resend)

    trap 'rm -f /tmp/myfile; trap - INT; kill -INT $$' INT


run a command after every simple command (debug hook)

    trap 'echo "ran: $BASH_COMMAND"' DEBUG


run a command whenever a function or sourced script returns

    trap 'echo "returned from function"' RETURN


run a command whenever a command fails (with set -e)

    set -e
    trap 'echo "error on line $LINENO"' ERR


